# rbtools package

This package allows creating a custom toolbar with buttons to execute atom commands or nodejs code.

## Current support

### Icon types

- `atomIcon` uses Atom's icons in `Styleguide` (accessible using `Ctrl`+`Shift`+`g`)

### Action types

- `atomCommand` allows the use of commands introduced on Atom's command window (accessible using `Ctrl`+`Shift`+`p`)
- `nodeCommand` allow to introduce a raw nodejs code to be executed. Currently, the `child_process` module is auto included before the value into `Action` parameter in the menu model JSON file

## Example

```
{
    "Basic Menu": {
        "Buttons": [
            {
                "Name"      : "Reload window",
                "Type"      : "button",
                "Tooltip"   : "Reload Window",
                "IconType"  : "atomIcon",
                "Icon"      : "sync",
                "ActionType": "atomCommand",
                "Action"    : "window:reload",
                "Params"    : []
            },
            {
                "Name"      : "Open with notepad++",
                "Type"      : "button",
                "Tooltip"   : "Open with notepad++",
                "IconType"  : "atomIcon",
                "Icon"      : "file",
                "ActionType": "nodeCommand",
                "Action"    : "child_process.execFile('C:\\Program Files\\Notepad++\\notepad++.exe', [\"$1\"]);",
                "Params"    : ["$currentFile"]
            },
            {
                "Name"      : "open (CMD) terminal here",
                "Type"      : "button",
                "Tooltip"   : "open (CMD) terminal here",
                "IconType"  : "atomIcon",
                "Icon"      : "browser",
                "ActionType": "nodeCommand",
                "Action"    : "child_process.execFile('cmd', ['/C', 'start', '/d', '$1', 'cmd.exe'])",
                "Params"    : ["$currentFolder"]
            },
            {
                "Name"      : "open (PowerShell) terminal here",
                "Type"      : "button",
                "Tooltip"   : "open (PowerShell) terminal here",
                "IconType"  : "atomIcon",
                "Icon"      : "terminal",
                "ActionType": "nodeCommand",
                "Action"    : "child_process.execFile('cmd', ['/C', 'start', '/d', '$1', 'powershell.exe', '-WindowStyle', 'Maximized'])",
                "Params"    : ["$currentFolder"]
            }
        ]
    }
}

```

## Preview

![simple screenshot](https://github.com/LeonMike/rbtools/blob/master/simple%20preview.png?raw=true)
