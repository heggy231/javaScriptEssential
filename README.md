# javaScriptEssential
javascript essential training notes

# ch6) DOM
browser is o bj
BOM - browser object model

- window.innerWidth tells you the width of your widow
- window.open() opens up new tab window

Resource
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference
list all the properties and methods for window

- window.document
one of the properties in the window object which html document sits
you can call it directly also
- document = window.document

# DOM
head vs body
- head is invisible part of document (meta, title, link)
- body has visible part

## DOM Properties
https://developer.mozilla.org/en-US/docs/Web/API/document
- document.body; // the body element
- document.title; // the document title
- document.URL; // the document URL

## DOM Methods
// Get the element with a specified ID:
document.getElementById("some-ID");

# javaScript structural outline:
- Add script tag right before closing of body tag
<!DOCTYPE HTML>
<html>
<body>
  

<script type="text/javascript">
var tabLinks;
var tabPanels;

</script>
</body>
</html>