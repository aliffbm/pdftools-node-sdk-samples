# Samples for the PDF Tools Node.js SDK

This sample project helps you get started with the  PDF Tools Node.js SDK.

The sample JS scripts illustrate how to perform PDF-related actions (such as converting to and from the PDF format) using 
the SDK. **Please note that the PDF Tools Node.js SDK supports only server side use cases.**

## Prerequisites
The sample application has the following requirements:
* Node.js : Version 10.13 or above. Node installation instructions can be found 
[here](https://nodejs.org/en/download/).


## Authentication Setup

The credentials file and corresponding private key file for the samples is ```pdftools-api-credentials.json``` and ```private.key``` 
respectively. Before the samples can be run, replace both the files with the ones present in the downloaded zip file at 
the end of creation of credentials via [Get Started](https://www.adobe.io/apis/documentcloud/dcsdk/gettingstarted.html?ref=getStartedWithServicesSdk) workflow.

The SDK also supports providing the authentication credentials at runtime, without storing them in a config file. Please
refer this [section](#create-a-pdf-file-from-a-docx-file-by-providing-in-memory-authentication-credentials) to 
know more.

## Quota Exhaustion

If you receive ServiceUsageError during the Samples run, it means that trial credentials have exhausted their usage quota. 
Please [contact us](https://www.adobe.com/go/pdftoolsapi_requestform) to get paid credentials.

## Build with npm

Run the following command to build the project:
```$xslt
npm install
```

Note that the PDF Tools SDK is listed as a dependency in the package.json and will be downloaded automatically.

## A Note on Logging
For logging, this SDK uses the [log4js API](https://www.npmjs.com/package/log4js) . 
Upon running, the SDK searches for a file ```config/pdftools-sdk-log4js-config.json``` in the working directory, and reads the
logging properties from there. If no configuration file is provided, default logging, i.e. logging INFO logs to the console is enabled. The clients can change the logging settings as per their needs.

## Running the samples

The following sub-sections describe how to run the samples. Prior to running the samples, check that the configuration 
file is set up as described above and that the project has been built.

The samples code is available under the ```src``` folder. Test 
files used by the samples can be found in the ```resources``` folder. When executed, all samples create an ```output``` 
child folder under the project root directory to store their results.

### Create a PDF File
These samples illustrate how to convert files of some formats to PDF. Refer the sdk documentation of create-pdf-operation.js 
to see the list of all supported media types which can be converted to PDF.

#### Create a PDF File From a DOCX File 

The sample script ```create-pdf-from-docx.js``` creates a PDF file from a DOCX file.

```$xslt
node src/createpdf/create-pdf-from-docx.js
```

#### Create a PDF File From a DOCX Readable Stream

The sample script ```create-pdf-from-docx-stream.js``` creates a PDF file from a readable DOCX stream.

```$xslt
node src/createpdf/create-pdf-from-docx-stream.js
```

#### Create a PDF File From a DOCX File (Write to an OutputStream)

The sample script ```create-pdf-from-docx-to-output-stream.js``` creates a PDF file from a DOCX file. Instead of saving the result to a 
local file, it writes the result to an output stream.

```$xslt
node src/createpdf/create-pdf-from-docx-to-output-stream.js
```

#### Create a PDF File From a DOCX File (By providing in-memory Authentication credentials)

The sample script ```create-pdf-with-inmemory-auth-credentials.js``` highlights how to provide in-memory auth credentials
for performing an operation. This enables the clients to fetch the credentials from a secret server during runtime, 
instead of storing them in a file.

Before running the sample, authentication credentials need to be updated as per the instructions in the script. 
```$xslt
node src/createpdf/create-pdf-with-inmemory-auth-credentials.js
```

#### Create a PDF File From a DOCX File(By providing custom value for timeouts)
The sample script ```create-pdf-with-custom-timeouts``` highlights how to provide the custom value for connection timeout and read timeout.
```$xslt
node src/createpdf/create-pdf-with-custom-timeouts.js
```

####  Create a PDF File From a PPTX File 

The sample script ```create-pdf-from-pptx.js``` creates a PDF file from a PPTX file.

```$xslt
node src/createpdf/create-pdf-from-pptx.js
```

#### Create a PDF File From Static HTML (via Zip Archive)

The sample script ```create-pdf-from-static-html.js``` creates a PDF file from a zip file containing the input HTML file and its resources. 
Please refer the sdk documentation of create-pdf-operation.js to see instructions on the structure of the zip file.

```$xslt
node src/createpdf/create-pdf-from-static-html.js
```


#### Create a PDF File From Dynamic HTML (via Zip Archive)

The sample script ```create-pdf-from-dynamic-html.js``` converts a zip file, containing the input HTML file and its resources, along with the input data to a PDF file. The input data is used by the javascript in the HTML file to manipulate the HTML DOM, thus effectively updating the source HTML file. This mechanism can be used to provide data to the template HTML dynamically and then, convert it into a PDF file.

```$xslt
node src/createpdf/create-pdf-from-dynamic-html.js
```

### Export PDF To Other Formats
These samples illustrate how to export PDF files to other formats. Refer to the documentation of export-pdf-operation.js
to see the list of supported export formats.

#### Export a PDF File To a DOCX File 

The sample script ```export-pdf-to-docx.js``` converts a PDF file to a DOCX file.

```$xslt
node src/exportpdf/export-pdf-to-docx.js
```

#### Export a PDF File To an Image Format (JPEG)

The sample script ```export-pdf-to-jpeg.js``` converts a PDF file's pages to JPEG images. Note that the output is a zip archive 
containing the individual images.

```$xslt
node src/exportpdf/export-pdf-to-jpeg.js
```

### Combine PDF Files
These samples illustrate how to combine multiple PDF files into a single PDF file.

#### Combine Multiple PDF Files

The sample script ```combine-pdf.js``` combines multiple PDF files into a single PDF file. The combined PDF file contains all pages
of the source files.

```$xslt
node src/combinepdf/combine-pdf.js
```

#### Combine Specific Pages of Multiple PDF Files

The sample script ```combine-pdf-with-page-ranges.js``` combines specific pages of multiple PDF files into into a single PDF file.
 
```$xslt
node src/combinepdf/combine-pdf-with-page-ranges.js
```

### OCR PDF File
These samples illustrate how to apply OCR(Optical Character Recognition) to a PDF file and convert it to a searchable copy of your PDF. The supported input format is application/pdf.

#### Convert a PDF File into a Searchable PDF File

The sample script ```ocr-pdf.js``` converts a PDF file into a searchable PDF file.

```$xslt
node src/ocr/ocr-pdf.js
```

#### Convert a PDF File into a Searchable PDF File while keeping the original image

The sample script ```ocr-pdf-with-options.js``` converts a PDF file to a searchable PDF file with maximum fidelity to the original image and default en-us locale. Refer to the documentation of ocr-options.js
to see the list of supported OCR locales and OCR types.

```$xslt
node src/ocr/ocr-pdf-with-options.js
```

### Compress PDF File

The sample illustrates how to reduce the size of a PDF file.

#### Reduce PDF File Size

The sample script ```compress-pdf.js``` reduces the size of a PDF file.

```$xslt
node src/compresspdf/compress-pdf.js
```

### Linearize PDF File

The sample illustrates how to convert a PDF file into a Linearized (also known as "web optimized") PDF file. Such PDF files are 
optimized for incremental access in network environments.

#### Convert a PDF File into a Web Optimized File

The sample script ```linearize-pdf.js``` optimizes the PDF file for a faster Web View.

```$xslt
node src/linearizepdf/linearize-pdf.js
```

### Protect PDF File

The sample illustrates how to secure a PDF file with a password.

#### Convert a PDF File into a Password Protected PDF File

The sample script ```protect-pdf.js``` converts a PDF file into a password protected PDF file.

```$xslt
node src/protectpdf/protect-pdf.js
```

### Rotate Pages

The sample illustrates how to rotate pages in a PDF file.

#### Rotate Pages in PDF File

The sample script ```rotate-pdf-pages.js``` rotates specific pages in a PDF file.

```$xslt
node src/rotatepages/rotate-pdf-pages.js
```

### Delete Pages

The sample illustrates how to delete pages in a PDF file.

#### Delete Pages from PDF File

The sample script ```delete-pdf-pages.js``` removes specific pages from a PDF file.

```$xslt
node src/deletepages/delete-pdf-pages.js
```

### Reorder Pages

The sample illustrates how to reorder the pages in a PDF file.

#### Reorder Pages in PDF File

The sample script ```reorder-pdf-pages.js``` rearranges the pages of a PDF file according to the specified order.

```$xslt
node src/reorderpages/reorder-pdf-pages.js
```

### Insert Pages

The sample illustrates how to insert pages in a PDF file.

#### Insert Pages into a PDF File

The sample script ```insert-pdf-pages.js``` inserts pages of multiple PDF files into a base PDF file.

```$xslt
node src/insertpages/insert-pdf-pages.js
```

### Replace Pages

The sample illustrates how to replace pages of a PDF file.

#### Replace PDF File Pages with Multiple PDF Files

The sample script ```replace-pdf-pages.js``` replaces specific pages in a PDF file with pages from multiple PDF files.

```$xslt
node src/replacepages/replace-pdf-pages.js
```

### Licensing

This project is licensed under the MIT License. See [LICENSE](LICENSE.md) for more information.
