# Java-Script-Context-Menu-Builder
Use a premade context menu with java script.

![screenshot](https://github.com/Monnapse/Java-Script-Context-Menu-Builder/blob/main/preview.png?raw=true)

Example
```
const contextMenu = ContextMenu()
contextMenu.newOption("open", "Open/Preview", e=>{console.log(e);});
contextMenu.newOption("download", "Download", e=>{console.log(e);});
contextMenu.newOption("rename", "Rename", e=>{console.log(e);});
contextMenu.newOption("delete", "Delete", e=>{console.log(e);});
contextMenu.newOption("info", "File Information", e=>{console.log(e);});
contextMenu.buildContextMenu(ContextMenuStyleTypes.Default);
contextMenu.addShowChecksFunction((event)=>{
    console.log(event);
    return false;
});
contextMenu.startShowFunctionality();
```
