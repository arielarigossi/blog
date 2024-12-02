
### Vim 
 
- **Established History** : Vim has been around since 1991, and it has a large, mature user base.
 
- **Stability** : Vim is known for its stability and performance. It is highly reliable, with a very stable release cycle.
 
- **Extensive Documentation** : Vim comes with extensive built-in documentation and has many resources available online.
 
- **Plugins** : Vim has a robust plugin ecosystem, although its native plugin management can be cumbersome.

### Neovim 
 
- **Modernized Codebase** : Neovim was forked from Vim to address some of the limitations of Vim's codebase. It aims to improve maintainability and extendibility.
 
- **Asynchronous Job Control** : Neovim supports asynchronous plugins and job control, allowing for a more responsive editing experience.
 
- **Built-in Terminal Emulator** : Neovim includes a built-in terminal emulator, making it easy to run terminal commands and scripts within the editor.
 
- **Embedded API** : Neovim has a well-documented API for external applications, allowing for integration and automation.
 
- **Lua Integration** : Neovim uses Lua for configuration and scripting, which is faster and more flexible compared to Vimscript.

## Some manual configuration setup.

2. **Basic Configuration** Neovim's configuration file is located at `~/.config/nvim/init.vim`. You can create this file and add basic settings to get started:

```vim
" Basic settings
set number              " Show line numbers
set relativenumber      " Show relative line numbers
set tabstop=4           " Number of spaces that a <Tab> in the file counts for
set shiftwidth=4        " Number of spaces to use for each step of (auto)indent
set expandtab           " Use spaces instead of tabs
set smartindent         " Smart indentation
set cursorline          " Highlight the current line
set wildmenu            " Visual autocomplete for command menu
set ignorecase          " Ignore case in search patterns
set smartcase           " Override 'ignorecase' if search pattern contains upper case
set clipboard=unnamedplus  " Use the system clipboard

" Plugin management
call plug#begin('~/.local/share/nvim/plugged')
" Add plugins here
call plug#end()

" Theme
syntax enable           " Enable syntax highlighting
set background=dark     " Set background to dark
colorscheme desert      " Set colorscheme
```
3. **Plugin Management** Neovim doesn't come with a built-in plugin manager. One popular choice is [vim-plug](https://github.com/junegunn/vim-plug) .
#### Installing vim-plug: 


```sh
curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

#### Example Configuration with Plugins: 


```vim
call plug#begin('~/.local/share/nvim/plugged')

" File explorer
Plug 'preservim/nerdtree'

" Status line
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'

" Syntax highlighting
Plug 'sheerun/vim-polyglot'

" Git integration
Plug 'tpope/vim-fugitive'

" Autocompletion
Plug 'hrsh7th/nvim-cmp'
Plug 'hrsh7th/cmp-nvim-lsp'
Plug 'neovim/nvim-lspconfig'
Plug 'hrsh7th/cmp-buffer'
Plug 'hrsh7th/cmp-path'
Plug 'hrsh7th/cmp-cmdline'

call plug#end()
```
4. **Setting Up Language Server Protocol (LSP)** 
Neovim has built-in support for LSP, which allows for powerful code autocompletion and navigation.

#### Example LSP Configuration: 


```vim
lua << EOF
local nvim_lsp = require('lspconfig')

-- Enable LSP for Python
nvim_lsp.pyright.setup{}

-- Enable LSP for JavaScript/TypeScript
nvim_lsp.tsserver.setup{}

-- Configure nvim-cmp for autocompletion
local cmp = require'cmp'
cmp.setup({
  snippet = {
    expand = function(args)
      vim.fn["vsnip#anonymous"](args.body) -- For `vsnip` users.
    end,
  },
  mapping = {
    ['<C-b>'] = cmp.mapping(cmp.mapping.scroll_docs(-4), { 'i', 'c' }),
    ['<C-f>'] = cmp.mapping(cmp.mapping.scroll_docs(4), { 'i', 'c' }),
    ['<C-Space>'] = cmp.mapping(cmp.mapping.complete(), { 'i', 'c' }),
    ['<C-y>'] = cmp.config.disable, -- Specify `cmp.config.disable` if you want to remove the default `<C-y>` mapping.
    ['<C-e>'] = cmp.mapping({
      i = cmp.mapping.abort(),
      c = cmp.mapping.close(),
    }),
    ['<CR>'] = cmp.mapping.confirm({ select = true }), -- Accept currently selected item. Set `select` to `false` to only confirm explicitly selected items.
    ['<Tab>'] = cmp.mapping(function(fallback)
      if cmp.visible() then
        cmp.select_next_item()
      elseif vim.fn  == 1 then
        feedkey("<Plug>(vsnip-expand-or-jump)", "")
      else
        fallback()
      end
    end, { 'i', 's' }),
    ['<S-Tab>'] = cmp.mapping(function()
      if cmp.visible() then
        cmp.select_prev_item()
      elseif vim.fn["vsnip#jumpable"](-1) == 1 then
        feedkey("<Plug>(vsnip-jump-prev)", "")
      end
    end, { 'i', 's' }),
  },
  sources = cmp.config.sources({
    { name = 'nvim_lsp' },
    { name = 'vsnip' }, -- For vsnip users.
  }, {
    { name = 'buffer' },
  })
})

EOF
```
5. **Running Neovim** 
To start Neovim, simply open your terminal and type:


```sh
nvim
```

From here, you can start editing files and use the installed plugins.
6. **Learning Resources**  
- **[Neovim Documentation]() ** : Official documentation is a great place to start.
 
- **[Neovim GitHub](https://github.com/neovim/neovim) ** : The source code and issue tracker can be useful for troubleshooting.
 
- **[Neovim Community]() ** : Various community resources including chat and forums.

## Installing Markdown plugin as example:

Markdown preview plugin for Neovim, you can use the [markdown-preview.nvim](https://github.com/iamcco/markdown-preview.nvim)  plugin. Here are the steps to install and configure it:1. **Install vim-plug (if not already installed)** If you haven't installed `vim-plug` yet, you can install it by running the following command:

```sh
curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
2. **Add the Plugin to Your init.vim** Open your Neovim configuration file (`~/.config/nvim/init.vim`) and add the following lines to include the `markdown-preview.nvim` plugin:

```vim
call plug#begin('~/.local/share/nvim/plugged')

" Other plugins...

" Markdown Preview
Plug 'iamcco/markdown-preview.nvim', { 'do': 'cd app && npm install' }

call plug#end()
```
3. **Install the Plugin** After adding the plugin to your `init.vim`, open Neovim and run:

```vim
:PlugInstall
```
This will install the `markdown-preview.nvim` plugin and its dependencies.4. **Configuration** 
Optionally, you can add some configurations for the Markdown preview plugin. Here are a few settings you might find useful:


```vim
" Set the keybinding to open markdown preview
let g:mkdp_auto_start = 0
let g:mkdp_auto_close = 1
let g:mkdp_refresh_slow = 0
let g:mkdp_command_for_global = 0
let g:mkdp_open_to_the_world = 0
let g:mkdp_open_ip = ''
let g:mkdp_browser = ''
let g:mkdp_echo_preview_url = 0
let g:mkdp_browserfunc = ''
let g:mkdp_markdown_css = ''
let g:mkdp_highlight_css = ''
let g:mkdp_port = ''
let g:mkdp_page_title = '「${name}」'
let g:mkdp_filetypes = ['markdown']
let g:mkdp_theme = 'light'
```
5. **Using the Plugin** 
To preview a Markdown file, open the file in Neovim and use the following command:


```vim
:MarkdownPreview
```

This will open a browser window displaying the rendered Markdown. You can also close the preview with:


```vim
:MarkdownPreviewStop
```
For convenience, you can map these commands to keybindings in your `init.vim`:

```vim
nnoremap <leader>mp :MarkdownPreview<CR>
nnoremap <leader>ms :MarkdownPreviewStop<CR>
```
6. **Ensure Dependencies are Installed** The `markdown-preview.nvim` plugin requires Node.js and npm to be installed on your system. You can check if they are installed by running:

```sh
node -v
npm -v
```

The "connection refused" error usually means that the Markdown preview server isn't able to communicate with your browser. Let's troubleshoot and ensure everything is set up correctly.
1. **Check Plugin Installation** Make sure the `markdown-preview.nvim` plugin was installed successfully. In Neovim, run:

```vim
:PlugStatus
```
Verify that `iamcco/markdown-preview.nvim` is listed and marked as installed.2. **Verify Dependencies** Ensure `markdown-preview.nvim` installed its Node.js dependencies correctly. Navigate to the plugin directory and check:

```sh
cd ~/.local/share/nvim/plugged/markdown-preview.nvim/app
npm install
```

This should reinstall the necessary Node.js packages.
3. **Configuration Check** Ensure your `init.vim` has the correct configuration. Specifically, check the `mkdp_port` and `mkdp_open_ip` settings. Here’s a minimal example:

```vim
" Set the port for the preview server
let g:mkdp_port = '8480'

" Allow the preview server to be accessed externally
let g:mkdp_open_ip = '127.0.0.1'
```
4. **Firewall/Network Issues** Ensure there are no firewall or network issues blocking the connection. Check if port `8480` is open:

```sh
sudo ufw allow 8480
```
This command works for `ufw` (Uncomplicated Firewall) on Linux. Adjust as necessary for other firewall software.5. **Manually Start and Access the Server** 
Try manually starting the server and accessing it directly from your terminal. Navigate to the plugin directory and run:


```sh
cd ~/.local/share/nvim/plugged/markdown-preview.nvim/app
npm start
```
Then, open a browser and go to `http://127.0.0.1:8480`.6. **Browser Configuration** Ensure your browser is correctly set to open the Markdown preview URL. If you have custom browser settings in your `init.vim`, verify they are correct:

```vim
let g:mkdp_browser = ''  " Leave empty to use default browser
```
7. **Debugging Output** 
Enable verbose logging in Neovim to get more information:


```vim
let g:mkdp_echo_preview_url = 1
```

This will echo the preview URL in Neovim’s command line, allowing you to see the exact URL it’s trying to open.
8. **Check Server Status** If the server is running but not accessible, you might have another service conflicting with the port. Check for other services using port `8480`:

```sh
lsof -i:8480
```

## This is a cheat sheet of basic Neovim shortcuts for common tasks:

### Navigation 
| Command | Description | 
| --- | --- | 
| h, j, k, l | Move left, down, up, right | 
| 0 | Move to the beginning of the line | 
| $ | Move to the end of the line | 
| w | Move forward to the start of a word | 
| b | Move backward to the start of a word | 
| gg | Move to the top of the file | 
| G | Move to the bottom of the file | 
| :n | Move to line n | 
| Ctrl + u | Scroll up half a page | 
| Ctrl + d | Scroll down half a page | 

### Inserting Text 
| Command | Description | 
| --- | --- | 
| i | Insert before the cursor | 
| a | Insert after the cursor | 
| I | Insert at the beginning of the line | 
| A | Insert at the end of the line | 
| o | Open a new line below the current line | 
| O | Open a new line above the current line | 

### Selecting and Manipulating Text 
| Command | Description | 
| --- | --- | 
| v | Start visual mode (select characters) | 
| V | Start visual line mode (select lines) | 
| Ctrl + v | Start visual block mode | 
| y | Yank (copy) selected text | 
| d | Delete selected text | 
| c | Change (delete and enter insert mode) | 
| p | Paste after the cursor | 
| P | Paste before the cursor | 
| u | Undo | 
| Ctrl + r | Redo | 

### Deleting Text 
| Command | Description | 
| --- | --- | 
| x | Delete character under the cursor | 
| dw | Delete word | 
| dd | Delete current line | 
| d$ | Delete to the end of the line | 
| d0 | Delete to the beginning of the line | 

### Searching and Replacing 
| Command | Description | 
| --- | --- | 
| /pattern | Search for pattern | 
| n | Move to the next match | 
| N | Move to the previous match | 
| :%s/old/new/g | Replace all occurrences of old with new | 
| :noh | Remove search highlighting | 

### Buffers and Windows 
| Command | Description | 
| --- | --- | 
| :e filename | Open a file | 
| :w | Save the current file | 
| :q | Quit the current window | 
| :wq | Save and quit | 
| :bd | Close the current buffer | 
| :ls | List all open buffers | 
| :bnext or :bn | Go to the next buffer | 
| :bprev or :bp | Go to the previous buffer | 
| :sp filename | Open a file in a new horizontal split | 
| :vsp filename | Open a file in a new vertical split | 
| Ctrl + w + w | Switch between windows | 
| Ctrl + w + q | Close the current window | 

### Miscellaneous 
| Command | Description | 
| --- | --- | 
| :!command | Execute an external command | 
| :set number | Show line numbers | 
| :set relativenumber | Show relative line numbers | 
| :syntax on | Enable syntax highlighting | 


### Getting Started with NvChad 
1. **Installation** 
First, ensure you have Neovim installed. Then, follow these steps to install NvChad:


```sh
# Backup your existing Neovim configuration if necessary
mv ~/.config/nvim ~/.config/nvim.bak

# Clone the NvChad repository
git clone https://github.com/NvChad/NvChad ~/.config/nvim --depth 1 && nvim
```

After running the above commands, NvChad will set up its configuration, and when you open Neovim, it will install the necessary plugins.
2. **Basic Usage** 
NvChad provides various keybindings and features out of the box. Here are some of the key features and shortcuts:
 
- **File Explorer** : NvChad uses `nvim-tree.lua` for file exploration. You can toggle the file explorer with `<leader> e`.
 
- **Buffer Navigation** : Switch between buffers using `Tab` and `Shift+Tab`.
 
- **Terminal** : Toggle the integrated terminal with `<leader> t`.
 
- **Search** : NvChad uses Telescope for fuzzy finding and searching. Common commands include: 
  - `<leader> ff` to find files.
 
  - `<leader> fg` to live grep.
 
  - `<leader> fb` to search buffers.
 
- **Git Integration** : NvChad includes Git signs and commands via `gitsigns.nvim` and `fugitive.vim`.
3. **Customization** NvChad is designed to be highly customizable. The primary configuration files are located in `~/.config/nvim/lua/core`. You can also add your own custom configurations. 
- **Custom Configurations** : Create a directory called `custom` inside `~/.config/nvim/lua/` and add your custom configurations there.
 
- **Example Custom Configuration** : 
  - Create a file `~/.config/nvim/lua/custom/chadrc.lua`:

```lua
local M = {}

M.ui = {
  theme = "gruvbox", -- set your preferred theme
}

M.plugins = {
  user = function(use)
    use { "folke/tokyonight.nvim" } -- an example of adding a new plugin
  end,
}

return M
```
4. **Updating NvChad** 
To update NvChad, simply pull the latest changes from the repository:


```sh
cd ~/.config/nvim
git pull
```

### Additional Resources 
 
- **[NvChad Documentation]() ** : The official documentation provides comprehensive guides and tutorials.
 
- **[NvChad GitHub Repository](https://github.com/NvChad/NvChad) ** : The source code and issue tracker.

### Step by step guide for basic file editing task.

##### To copy text from one buffer and paste it into another buffer in Neovim, follow these steps:


1. **Open the First Buffer** 
First, open the file or buffer from which you want to copy text.


```vim
:e path/to/firstfile
```

2. **Enter Visual Mode and Select Text** 
Use visual mode to select the text you want to copy.
 
- For character-wise selection:


```vim
v
```
Then use arrow keys or `h`, `j`, `k`, `l` to select the desired text.
 
- For line-wise selection:


```vim
V
```
Then use `j` or `k` to select multiple lines.
 
- For block-wise selection:


```vim
Ctrl + v
```

Then use arrow keys to select the block of text.
3. **Yank (Copy) the Selected Text** 
After selecting the text, yank (copy) it using:


```vim
y
```
4. **Open the Second Buffer** 
Now, open the second buffer where you want to paste the text. You can either open an existing file or create a new one.

To open another buffer in a new split:
 
- Horizontal split:


```vim
:sp path/to/secondfile
```
 
- Vertical split:


```vim
:vsp path/to/secondfile
```

Or just open it in the current window:


```vim
:e path/to/secondfile
```
5. **Navigate to the Desired Location** 
Move the cursor to the location in the second buffer where you want to paste the text.
6. **Paste the Text** 
Paste the yanked text at the cursor position using:


```vim
p
```

This will paste the text after the cursor. To paste before the cursor, use:


```vim
P
```

### Example Workflow 
 
1. Open the first file:


```vim
:e firstfile.txt
```
 
2. Select the text in visual mode:


```vim
Vjj  " Select the current and next two lines
```
 
3. Yank the selected text:


```vim
y
```
 
4. Open the second file in a vertical split:


```vim
:vsp secondfile.txt
```
 
5. Move the cursor to the desired location and paste:


```vim
p
```

### Using Registers for Advanced Copy-Pasting 

If you need to copy-paste between multiple files frequently, you can use registers to store and recall yanked text.
 
1. **Yank to a Specific Register** :

```vim
"ay  " Yank to register 'a'
```
 
2. **Paste from a Specific Register** :

```vim
"ap  " Paste from register 'a'
```

This way, you can store multiple yanks in different registers (a-z) and recall them as needed.

### Dealing with buffers in neovim:

 buffers represent open files or files that can be edited. Here’s how you can open, switch, and close buffers effectively:

### Opening a Buffer 

#### Open a File in a New Buffer 
 
1. **Open a file directly** :

```vim
:e path/to/filename
```
 
2. **Open a file in a new split window** : 
  - Horizontal split:

```vim
:sp path/to/filename
```
 
  - Vertical split:

```vim
:vsp path/to/filename
```
 
3. **Open a file in a new tab** :

```vim
:tabnew path/to/filename
```

### Switching Between Buffers 
 
- **List all open buffers** :

```vim
:ls
```
 
- **Switch to the next buffer** :

```vim
:bnext
```
 
- **Switch to the previous buffer** :

```vim
:bprev
```
 
- **Switch to a specific buffer by its number (as shown in `:ls` output)** :

```vim
:buffer <buffer_number>
```
 
- **Switch to a buffer by name** :

```vim
:b filename
```

### Closing a Buffer 

#### Close the Current Buffer 
 
1. **Close the current buffer** :

```vim
:bd
```
 
2. **Force close the current buffer (without saving changes)** :

```vim
:bd!
```

#### Close a Specific Buffer 
 
1. **Close a specific buffer by its number** :

```vim
:bd <buffer_number>
```
 
2. **Close a specific buffer by name** :

```vim
:bd filename
```

#### Close All Buffers Except the Current One 
 
1. **Close all other buffers** :

```vim
:bufdo bd
```

### Additional Tips 
 
- **Close the buffer and switch to the next buffer** :

```vim
:bnext | bd #
```
 
- **Close the buffer and switch to the previous buffer** :

```vim
:bprev | bd #
```

#### Cut text from one buffer and paste it into another buffer in Neovim, follow these steps:

### Step-by-Step Guide 

#### 1. Open the First Buffer 

Open the file or buffer from which you want to cut text.


```vim
:e path/to/firstfile
```

#### 2. Enter Visual Mode and Select Text 

Use visual mode to select the text you want to cut.
 
- For character-wise selection:


```vim
v
```
Then use arrow keys or `h`, `j`, `k`, `l` to select the desired text.
 
- For line-wise selection:


```vim
V
```
Then use `j` or `k` to select multiple lines.
 
- For block-wise selection:


```vim
Ctrl + v
```

Then use arrow keys to select the block of text.

#### 3. Cut (Delete) the Selected Text 

After selecting the text, cut (delete) it using:


```vim
d
```

#### 4. Open the Second Buffer 

Now, open the second buffer where you want to paste the text. You can either open an existing file or create a new one.

To open another buffer in a new split:
 
- Horizontal split:


```vim
:sp path/to/secondfile
```
 
- Vertical split:


```vim
:vsp path/to/secondfile
```

Or just open it in the current window:


```vim
:e path/to/secondfile
```

#### 5. Navigate to the Desired Location 

Move the cursor to the location in the second buffer where you want to paste the text.

#### 6. Paste the Text 

Paste the cut text at the cursor position using:


```vim
p
```

This will paste the text after the cursor. To paste before the cursor, use:


```vim
P
```

### Example Workflow 
 
1. Open the first file:


```vim
:e firstfile.txt
```
 
2. Select the text in visual mode:


```vim
Vjj  " Select the current and next two lines
```
 
3. Cut (delete) the selected text:


```vim
d
```
 
4. Open the second file in a vertical split:


```vim
:vsp secondfile.txt
```
 
5. Move the cursor to the desired location and paste:


```vim
p
```

### Using Registers for Advanced Cut-Pasting 

If you need to cut-paste between multiple files frequently, you can use registers to store and recall cut text.
 
1. **Cut to a Specific Register** :

```vim
"ad  " Cut (delete) to register 'a'
```
 
2. **Paste from a Specific Register** :

```vim
"ap  " Paste from register 'a'
```

This way, you can store multiple cuts in different registers (a-z) and recall them as needed.


