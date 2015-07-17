xpages_theme_dtd
================

The project delivers a DTD for XPages Themes, to enable content assist.

Content assist is managed by specifying the location of the relevant DTD in the relevant XML resource. If the DTD is accessible from the resource and IDE (i.e. Domino Designer), content assist provides elements and attributes hierarchically and can be used to validate the XML file.

However, if a DTD is specified, I've found problems loading an XPage if the DTD is not accessible from the server.

### Using in an NSF (Online)
The easiest option is using a publicly-accessible URL. That means the same location is accessible for Domino Designer and the XPages runtime, regardless of the location of the Domino server.

Enter the following code at the top of a Theme resource:
```XML
<!DOCTYPE theme PUBLIC
"-//Paul Withers, Intec Systems Ltd//DTD XPages Theme 1.0//EN"
"https://raw.github.com/paulswithers/xpages_theme_dtd/master/theme_1_0.dtd">
```
That will point to the dtd resource in this project.

However, you must remove the lines before building and testing the application on the server, otherwise the XPages runtime will not be able to parse the file.

### Using in an NSF (Offline)
If you want to access the content assist while working offline, you'll need a local copy of the file. The easiest option is to copy the content from the above URL and paste into a text file. Save it locally on your file system, e.g. to "C:\temp\theme_1_0.dtd".

Then enter the following code at the top of a Theme resource:
```XML
<!DOCTYPE theme SYSTEM
"-//Paul Withers, Intec Systems Ltd//DTD XPages Theme 1.0//EN"
"C:\temp\theme_1_0.dtd">
```
Whether processing from a local Domino server or from a local NSF, the file will still be accessible.

As before, you must remove the lines before building and testing the application on the server, otherwise the XPages runtime will not be able to parse the file.

### Adding to Snippets
For more details about how to add the DTD reference to the Snippets view in Domino Designer, see http://www.intec.co.uk/enabling-typeahead-content-assist-in-themes-and-using-the-eclipse-snippets-view/
