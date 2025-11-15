# OSS VSCode Settings for Vim

This repo contains my personal configuration for **VS Code** using the  
[Vim extension (`vscodevim.vim`)](https://open-vsx.org/vscode/item?itemName=vscodevim.vim).  

With these settings, VS Code behaves much closer to **Vim/Neovim** by adding:  
- Custom keymaps (e.g., `JJ` to exit insert mode)  
- Leader key shortcuts (`<space>` + key combos)  
- Vim-style pane navigation (`Ctrl+h/j/k/l`)  
- Restored native VS Code shortcuts (like `Ctrl+p` for Quick Open) 

---

## 📌 `settings.json`

```jsonc
{
    // --- Vim keymapping (Extention: VIM / vscodevim.vim) ---

    // ___ Define leader key (spacebar) ___
    "vim.leader": "<space>",

    // ___ Let VS Code handle these keys (so they don't get blocked by Vim extension) ___
    "vim.handleKeys": {
        "<C-p>": false
    },

    // ___ Normal mode keybindings ___
    "vim.normalModeKeyBindingsNonRecursive": [
        {
            // <leader> + y → Copy to clipboard
            "before": ["<leader>", "y"],
            "commands": ["editor.action.clipboardCopyAction"]
        },
        {
            // <leader> + e → Toggle file explorer sidebar
            "before": ["<leader>", "e"],
            "commands": ["workbench.action.toggleSidebarVisibility"]
        }
    ],

    // ___ Insert mode keybindings ___
    "vim.insertModeKeyBindings": [
        {
            // KK to exit insert mode
            "before": ["K", "K"],
            "after": ["<Esc>"]
        }
    ],

    // ___ Visual mode keybindings ___
    "vim.visualModeKeyBindingsNonRecursive": [
        {
            // KK to exit visual mode
            "before": ["K", "K"],
            "after": ["<Esc>"]
        },
        {
            // <leader> + y → Copy selection to clipboard
            "before": ["<leader>", "y"],
            "commands": ["editor.action.clipboardCopyAction"]
        },
        {
            // <leader> + e → Toggle file explorer sidebar
            "before": ["<leader>", "e"],
            "commands": ["workbench.action.toggleSidebarVisibility"]
        }
    ],

    // --- End Vim keymapping ---
}
```

## 📌 `keybindings.json(Open Keyboard Shortcuts JSON)`
```jsonc
[
    // --- Vim-style pane navigation inside VS Code (Extention: VIM / vscodevim.vim) ---
    {
        "key": "ctrl+h",
        "command": "workbench.action.navigateLeft"
    },
    {
        "key": "ctrl+j",
        "command": "workbench.action.navigateDown"
    },
    {
        "key": "ctrl+k",
        "command": "workbench.action.navigateUp"
    },
    {
        "key": "ctrl+l",
        "command": "workbench.action.navigateRight"
    },
    // --- Jump to Hint Keybindings (Extention: Jump to Hint / shuworks.vscode-jump-to-hint) ---
    {
      "key": "shift+enter",
      "command": "jumpToHint.jumpByWord",
      "when": "editorTextFocus && vim.mode == 'Normal'"
    },
    {
      "key": "shift+f",
      "command": "jumpToHint.jumpBySearch",
      "when": "editorTextFocus && vim.mode == 'Normal'"
    }

]
```
