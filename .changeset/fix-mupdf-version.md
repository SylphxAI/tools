---
"@sylphlab/tools-pdf": patch
"@sylphlab/tools-pdf-mcp": patch
---

fix(tools-pdf): pin mupdf to version 1.3.6 to resolve import errors

The latest version of mupdf (2.x) changed its package exports and no longer exports './mupdfjs', causing ERR_PACKAGE_PATH_NOT_EXPORTED errors. This fix pins the mupdf dependency to ^1.3.6, which is the last known working version.

Fixes #20
