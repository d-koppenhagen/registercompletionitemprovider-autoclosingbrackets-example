# registerCompletionItemProvider-autoClosingBrackets-example README

This repo is just for reproducing the vscode issue [111764](https://github.com/microsoft/vscode/issues/111764).

## Steps to reproduce

1. Open the repo in vscode
2. `npm install`
3. Run the Debugger command "Run Extension"
4. (optional) configure your workspace / editor with `"editor.autoClosingBrackets": "always"` if not set to default or set to something different
5. Open a workspace containing a AsciiDoc-File with content like the following:
  ```adoc
  :appdir: src/app

  include
  ```
5. Start the autocompletion by typing `::` after the `include` (`include::`)
6. The autocompletion should open. Choose the `{appdir}` option from the list

**Result**: The `"editor.autoClosingBrackets": "always"` setting will now fire and add an additional closing curly bracket after the auto-completed content (`}`).
The cursor is place before the added bracket. So the result will look like this (with `|` representing the cursor):

```adoc
include::{appdir}|}
```