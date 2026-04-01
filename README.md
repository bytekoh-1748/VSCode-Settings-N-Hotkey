# VS Code Setup Guide

This setup is designed for a keyboard-first workflow.
The goal is to reduce context switching, avoid tab replacement, and make debugging fast and predictable.

---

## Files

Place these files in your project:

```text
.vscode/
 ├── settings.json
 ├── keybindings_mac.json
 └── keybindings_windows.json
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
| cmd (ctrl) + w | Open definition to the side      |
| cmd (ctrl) + 1 | Show symbols in current file     |
| cmd (ctrl) + e | Add next occurrence to selection |

### Search

| Key     | Action          |
| ------- | --------------- |
| cmd (ctrl) + f | Open search     |
| cmd (ctrl) + g | Next match      |
| cmd (ctrl) + r | Previous match  |

### Focus

| Key     | Action          |
| ------- | --------------- |
| cmd (ctrl) + q | Toggle Zen Mode |

### Debugging

| Key     | Action           |
| ------- | ---------------- |
| cmd (ctrl) + d | Toggle breakpoint |
| cmd (ctrl) + 5 | Start / Continue |
| cmd (ctrl) + 1 | Step Over        |
| cmd (ctrl) + 2 | Step Into        |
| cmd (ctrl) + 3 | Step Out         |
| cmd (ctrl) + 4 | Restart          |
| cmd (ctrl) + 6 | Stop             |

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
  "window.customTitleBarVisibility": "windowed",

  "zenMode.hideStatusBar": true,
  "zenMode.hideActivityBar": true,
  "zenMode.hideLineNumbers": false,
  "zenMode.fullScreen": false,
  "zenMode.centerLayout": true,
  "zenMode.showTabs": "none",

  "terminal.integrated.hideOnStartup": "always",

  "[dart]": {
    "editor.rulers": []
  },
  "[c]": {
    "editor.rulers": []
  },
  "[cpp]": {
    "editor.rulers": []
  },
  "[python]": {
    "editor.rulers": []
  }
}
```

---

## Keybindings files

Use the platform-specific file below and copy its contents into your VS Code user `keybindings.json`.

* macOS: `.vscode/keybindings_mac.json`
* Windows: `.vscode/keybindings_windows.json`

---

## Notes

* `cmd (ctrl) + w` no longer closes tabs
* `cmd (ctrl) + q` no longer quits the app
* `cmd (ctrl) + d` no longer adds the next selection match
* Search navigation uses `cmd (ctrl) + g` for next and `cmd (ctrl) + r` for previous
* Zen Mode hides tabs
* The custom title bar is hidden in full screen
* Editor rulers are disabled globally and for Dart, C, C++, and Python files
* Some default shortcuts are overridden

---

## Typical usage

1. Use `cmd (ctrl) + 1` to navigate within a file
2. Use `cmd (ctrl) + w` to inspect definitions without losing context
3. Use `cmd (ctrl) + f`, `cmd (ctrl) + g`, and `cmd (ctrl) + r` to search and move between matches
4. Use `cmd (ctrl) + e` for quick multi-edit
5. Use `cmd (ctrl) + d` to toggle breakpoints quickly
6. Start debugging with `cmd (ctrl) + 5`
7. Control execution with number keys

---

This setup works best when you stop relying on scrolling and start treating navigation as a structural operation.
