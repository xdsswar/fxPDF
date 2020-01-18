# fxPDF
This is a PDF viewer libary written in JavaFX. I used icons from [MaterialDesign](https://material.io/resources/icons/) 
and the [Apache PDFBox®](https://pdfbox.apache.org/) library.
## How does it work?
The PDFRenderer render a page as an Image and this is displayed in an ImageView. One problem that results from this is that you cannot copy the text, for example.
## Integrate it into your own projects
You can use the viewer with more options (`PDFViewer`) or the smaller version, where you can disable the controls (`Viewer`).
### PDFViewer
```java
PDF pdf = new PDF(file); // Create a PDF 
PDFViewer v = new PDFViewer(pdf); // The PDFViewer object
root.getChildren().add(v); // Add the Viewer to the root-Pane
```
### Viewer
```java
PDF pdf = new PDF(file); // Create a PDF 
Viewer v = new Viewer(pdf); // The Viewer object
v.setDisableZoomButtons(true); // By default true
v.setDisableNextPageButtons(true); //By default true
v.setViewerType(ViewerType.LIST); // Standard is IMAGE (For more information see below)
root.getChildren().add(v); // Add the Viewer to the root-Pane
```
```java
//Methods
v.updateViewer(); // Refresh the page
v.loadPage(int pageNumber); // ViewerType Image: load the page of the PDF | ViewerType LIST: not implemented yet
v.leftPage(); // Switch to the previous page (Will only affect the viewer if ViewerType is LIST.)
v.rightPage(); // Switch to the next page (Will only affect the viewer if ViewerType is LIST.)
v.getCurrentPageNumber(); // Returns the number of the current visible page
v.getScaleFactor(); Returns the scale factor (float)
```
#### ViewerType LIST and IMAGE
##### LIST
The ViewType LIST displays the pages of the PDF below each other in a ScrollPane.
##### Image
The ViewType IMAGE displays each page of the PDF individually. You can navigate using buttons.
## Hotkeys
### PDFViewer
- `Control + O` Open a FileDialog to load a new PDF.
- `Control + Q` Close the Window
- `F11` Toggle Fullscreen
### Viewer
- `Control + Left` Left Page
- `Control + Right` Right Page
- `Control + +` Zoom In
- `Control + -` Zoom Out
## Upcoming Features / Not implemented
- When viewerType is LIST:
  - Zooming
  - loadPage: scroll to the given pageNumber
- More Function for the class `PDF`
