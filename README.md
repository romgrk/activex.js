
# ol-resources

This repository is a compilation of scripts and resources for OL related stuff.

 - [jscript.js][1] is a stdlib for the workflow (list of functions below)
 - [cotg.polyfill.js][2] allows you to test COTG's Photo, Signature and
     Annotations widgets directly form the browser.
 - [cotg.extension.js][3] contains the above, plus a number of useful functions
     documented below
 - [rest.js][4] is a wrapper around the Rest API
 - [repository.js][5] is a wrapper around the workflow data repository
 - [examples/users_cotg_ie.js][6] is a script to retrieve the user list from a
     COTG repository as JSON

## rest.js

Usage:
```js
var api = new RestAPI(
  'user',                 /* required */
  'password',             /* required */
  'http://localhost:9340' /* optionnal */
)
var version = api.files.serviceVersion()
```

Advanced examples can be found here:
 - [examples/rest_workflow.js](https://github.com/romgrk/ol-resources/blob/master/examples/rest_workflow.js)
 - [examples/rest_browser.js](https://github.com/romgrk/ol-resources/blob/master/examples/rest_browser.js)

## cotg.extension.js

The functions provided by this file are `Promise` based.

`cotg.getSignature(width, height)` triggers the signature widget and resolves to
a SVG signature data. E.g.
```js
cotg.getSignature(500, 200)
  .then(function(svg) {
    document.querySelector('img').src = 'data:image/xml+svg,' + svg })
```

`cotg.getPicture(options)` triggers the camera widget and resolves to
an image URI. E.g.
```js
cotg.getPicture({ width: 100, height: 100, quality: 50 })
  .then(function(uri) { document.querySelector('img').src = uri })
```

`cotg.getDate(date)` triggers the date widget and resolves to a date. E.g.
```js
cotg.getDate({ width: 100, height: 100, quality: 50 })
  .then(function(date) { /* ... */ })
```

`cotg.readFile(path)` reads a file on the device and resolves to the file content.

`cotg.writeFile(path, content)` writes a file on the device and resolves when
done.


## jscript.js
 - Workflow variables/logging
   - [get(name)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L14)
   - [set(name, value)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L15)
   - [log(msg)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L16)
   - [err(msg)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L17)
   - [exp(string)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L18)
   - [xml(string)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L19)
   - [toString(value)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L20)
   - [format()](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L22)
 - file manipulation
   - [readFile(path)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L34)
   - [writeFile(path, content)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L42)
   - [writeFileWithEncoding(path, content, encoding)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L49)
   - [readBinaryFile(path)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L59)
   - [writeBinaryFile(path, content)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L67)
   - [writeBinaryTextToFile(path, content)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L76)
   - [appendFile(path, content)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L98)
   - [deleteFile(path)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L105)
   - [moveFile(source, destination)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L111)
   - [copyFile(source, destination, overwrite)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L116)
   - [listFolders(path)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L121)
   - [listFiles(path)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L131)
   - [fileExists(path)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L149)
   - [folderExists(path)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L154)
   - [createFolder(path)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L159)
   - [join()](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L177)
   - [sanitizeFilename(filename)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L181)
 - XML manipulation
   - [loadXML(filename)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L191)
   - [createDOM()](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L200)
   - [createElement(tagName, value)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L210)
   - [createElements(description)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L222)
   - [appendChildren(element, children)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L233)
   - [extractNodes(dom, selectors)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L239)
   - [cloneNodes(dom, selectors)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L249)
   - [extractNode(dom, selector)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L253)
   - [extractNodeValue(dom, selector)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L257)
   - [addAttribute(element, name, value)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L267)
 - base64 encoding/decoding
   - [atob(text)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L283)
   - [btoa(binary)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L292)
   - [writeDecodedBase64(text, to)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L301)
 - Metadata API
   - [getMetaDocuments(filename)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L338)
 - Sending emails
   - [sendEmail(options)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L412)
 - Making HTTP requests
   - [fetch(options, callback)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L465)
   - [queryString(params)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L515)
   - [httpGET(url, data)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L523)
   - [httpPOST(url, data)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L530)
 - Making SQL queries
   - [sqlQuery(query, connectionString)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L544)
   - [sqlExecute(query, connectionString)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L569)
   - [escapeSql(val)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L577)
   - [interpolate(query, record)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L581)
 - String manipulation
   - [rightpad(str, len, ch)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L603)
   - [leftpad(str, len, ch)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L611)
   - [trim(string)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L619)
   - [escapeXml(unsafe)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L623)
   - [unescapeXml(safe)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L635)
 - Running shell commands
   - [runCommand(cmd)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L653)
   - [execCommand(cmd, cwd)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L658)
   - [sleep(seconds)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L666)
 - Reading Excel files
   - [readExcelAsRows(path, sheetNumber)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L678)
   - [readExcelAsJS(path, sheetNumber)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L715)
 - & others
   - [binaryToString(binary)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L740)
   - [stringToBinary(text, charSet)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L750)
   - [assign(target)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L768)
   - [keys(object)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L779)
   - [values(object)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L786)
   - [entries(object)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L793)
   - [not(fn)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L806)
   - [debug(msg, indent)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L820)
   - [escapeChars(value)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L842)
   - [fmt(msg, indent)](https://github.com/romgrk/ol-resources/blob/master/jscript.js#L846)


[1]: https://github.com/romgrk/ol-resources/blob/master/jscript.js
[2]: https://github.com/romgrk/ol-resources/blob/master/dist/cotg.polyfill.js
[3]: https://github.com/romgrk/ol-resources/blob/master/dist/cotg.extension.js
[4]: https://github.com/romgrk/ol-resources/blob/master/rest.js
[5]: https://github.com/romgrk/ol-resources/blob/master/repository.js
[6]: https://github.com/romgrk/ol-resources/blob/master/examples/users_cotg_ie.js

