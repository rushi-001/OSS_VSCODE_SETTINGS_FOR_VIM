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
    // --- Vim keymapping ---
    
    // Exit insert mode by typing "JJ"
    "vim.insertModeKeyBindings": [
        {
            "before": ["J", "J"],
            "after": ["<Esc>"]
        }
    ],

    // Exit visual mode by typing "JJ"
    "vim.visualModeKeyBindings": [
        {
            "before": ["J", "J"],
            "after": ["<Esc>"]
        }
    ],

    // Define leader key (spacebar)
    "vim.leader": "<space>",

    // Normal mode leader keybindings
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

    // Visual mode leader keybindings
    "vim.visualModeKeyBindingsNonRecursive": [
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

    // Let VS Code handle these keys (so they don't get blocked by Vim extension)
    "vim.handleKeys": {
        "<C-p>": false // Restore Ctrl+P (Quick Open)
    }

    // --- End Vim keymapping ---
}
```

## 📌 `keybindings.json(Open Keyboard Shortcuts JSON)`
```jsonc
[
    // Vim-style pane navigation inside VS Code
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
    }
]
```
