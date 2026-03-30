# VS Code Setup Guide

This setup is designed for a keyboard-first workflow.
The goal is to reduce context switching, avoid tab replacement, and make debugging fast and predictable.

---

## Files

Place these files in your project:

```text
.vscode/
 ├── settings.json
 └── keybindings.json
```

---

## Key ideas

* No mouse dependency
* Navigation without scrolling
* Open references without losing current context
* Minimal UI during focus
* Consistent debugging controls

---

## Keybindings

### Navigation

| Key     | Action                           |
| ------- | -------------------------------- |
| cmd + w | Open definition to the side      |
| cmd + 1 | Show symbols in current file     |
| cmd + e | Add next occurrence to selection |

### Focus

| Key     | Action          |
| ------- | --------------- |
| cmd + q | Toggle Zen Mode |

### Debugging

| Key     | Action           |
| ------- | ---------------- |
| cmd + d | Toggle breakpoint |
| cmd + 5 | Start / Continue |
| cmd + 1 | Step Over        |
| cmd + 2 | Step Into        |
| cmd + 3 | Step Out         |
| cmd + 4 | Restart          |
| cmd + 6 | Stop             |

---

## Debugging behavior

Step Over
Executes the current line and moves to the next one without entering functions.

Step Into
Enters the function being called on the current line.

Step Out
Runs the rest of the current function and returns to the caller.

Continue
Runs until the next breakpoint.

Restart
Stops and starts the session again.

Stop
Ends the debugging session.

---

## settings.json

```json
{
  "workbench.colorTheme": "Visual Studio Dark",
  "git.autofetch": true,
  "liveServer.settings.donotVerifyTags": true,
  "editor.acceptSuggestionOnEnter": "off",
  "github.copilot.enable": {
    "*": false,
    "plaintext": false,
    "markdown": false,
    "scminput": false
  },
  "terminal.integrated.initialHint": false,
  "python.analysis.typeCheckingMode": "basic",
  "gitlens.ai.model": "vscode",
  "gitlens.ai.vscode.model": "copilot:gpt-4.1",

  "workbench.editorAssociations": {
    "*.md": "vscode.markdown.preview.editor"
  },

  "editor.dragAndDrop": false,
  "editor.rulers": [],

  "workbench.editor.enablePreview": false,
  "workbench.editor.enablePreviewFromCodeNavigation": false,
  "workbench.editor.enablePreviewFromQuickOpen": false,
  "workbench.editor.openSideBySideDirection": "right",

  "workbench.secondarySideBar.defaultVisibility": "hidden",

  "zenMode.hideStatusBar": true,
  "zenMode.hideActivityBar": true,
  "zenMode.hideLineNumbers": false,
  "zenMode.fullScreen": false,
  "zenMode.centerLayout": true,

  "terminal.integrated.hideOnStartup": "always",

  "[dart]": {
    "editor.rulers": []
  }
}
```

---

## keybindings.json

```json
[
  { "key": "cmd+q", "command": "-workbench.action.quit" },
  { "key": "cmd+q", "command": "workbench.action.toggleZenMode" },

  { "key": "cmd+e", "command": "-workbench.action.quickOpenPreviousEditor" },
  { "key": "cmd+e", "command": "editor.action.addSelectionToNextFindMatch" },

  { "key": "cmd+d", "command": "-editor.action.addSelectionToNextFindMatch" },
  { "key": "cmd+d", "command": "editor.debug.action.toggleBreakpoint" },

  { "key": "cmd+w", "command": "-workbench.action.closeActiveEditor" },
  { "key": "cmd+w", "command": "editor.action.revealDefinitionAside" },

  { "key": "cmd+1", "command": "-workbench.action.focusFirstEditorGroup" },
  {
    "key": "cmd+1",
    "command": "workbench.action.debug.stepOver",
    "when": "inDebugMode && debugState == 'stopped'"
  },
  {
    "key": "cmd+1",
    "command": "workbench.action.gotoSymbol",
    "when": "!inDebugMode"
  },

  { "key": "cmd+2", "command": "-workbench.action.focusSecondEditorGroup" },
  {
    "key": "cmd+2",
    "command": "workbench.action.debug.stepInto",
    "when": "inDebugMode && debugState == 'stopped'"
  },

  { "key": "cmd+3", "command": "-workbench.action.focusThirdEditorGroup" },
  {
    "key": "cmd+3",
    "command": "workbench.action.debug.stepOut",
    "when": "inDebugMode && debugState == 'stopped'"
  },

  { "key": "cmd+4", "command": "-workbench.action.focusFourthEditorGroup" },
  {
    "key": "cmd+4",
    "command": "workbench.action.debug.restart",
    "when": "inDebugMode"
  },

  { "key": "cmd+5", "command": "-workbench.action.focusFifthEditorGroup" },
  {
    "key": "cmd+5",
    "command": "workbench.action.debug.continue",
    "when": "inDebugMode"
  },
  {
    "key": "cmd+5",
    "command": "workbench.action.debug.start",
    "when": "!inDebugMode"
  },

  { "key": "cmd+6", "command": "-workbench.action.focusSixthEditorGroup" },
  {
    "key": "cmd+6",
    "command": "workbench.action.debug.stop",
    "when": "inDebugMode"
  }
]
```

---

## Notes

* `cmd + w` no longer closes tabs
* `cmd + q` no longer quits the app
* `cmd + d` no longer adds the next selection match
* Editor rulers are disabled globally and for Dart files
* Some default shortcuts are overridden

---

## Typical usage

1. Use `cmd + 1` to navigate within a file
2. Use `cmd + w` to inspect definitions without losing context
3. Use `cmd + e` for quick multi-edit
4. Use `cmd + d` to toggle breakpoints quickly
5. Start debugging with `cmd + 5`
6. Control execution with number keys

---

This setup works best when you stop relying on scrolling and start treating navigation as a structural operation.
