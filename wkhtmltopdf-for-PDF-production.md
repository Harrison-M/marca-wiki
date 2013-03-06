We are using the wkhtmltopdf libraris for conversion of html to pdf of documents.

At this time, the library must be install manually based on architecture.  You will find the libraries at
[http://code.google.com/p/wkhtmltopdf/](http://code.google.com/p/wkhtmltopdf/).  Select the appropriate library for your architecture and install in an appropriate place (currently we are using /usr/local/bin/).
Note that you need the library particular to function (the file names are descriptive); i.e., the "topdf" not the "toimage."

This install requires an addition to parameters.yml (since it is architecture specific):

    wkhtmltopdf_path: /path/wkhtmltopdf-_xxxx_

The library is used by Knp/SnappyBundle which is installed by composer.

The use of it is in the DocController:  createPdfAction calls the htmlPrintAction (in order to use the relative links to the css we have to basically create the html first and then pass it into the converter).