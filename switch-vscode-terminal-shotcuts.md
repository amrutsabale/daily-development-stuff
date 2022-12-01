### Tested on Mac
go to File -> Preferences -> Keyboard shortcuts,

![json file option](https://user-images.githubusercontent.com/41994367/204996464-b0d2feee-c160-4725-bd01-67829c908ad3.png)


Just add the following lines in your keybindings.json.
````
[
   { "key": "cmd+shift+j", "command": "workbench.action.terminal.focusNext" },
   { "key": "cmd+shift+k", "command": "workbench.action.terminal.focusPrevious" }
]
````
