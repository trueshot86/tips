# tips

```
curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

```
set expandtab
set tabstop=4
set shiftwidth=4

call plug#begin('~/.vim/plugged')
Plug 'prabirshrestha/asyncomplete.vim'
Plug 'prabirshrestha/asyncomplete-lsp.vim'
Plug 'prabirshrestha/vim-lsp'
Plug 'mattn/vim-lsp-settings'
Plug 'mattn/vim-lsp-icons'

Plug 'hrsh7th/vim-vsnip'
Plug 'hrsh7th/vim-vsnip-integ'
call plug#end()

map <C-n> :LspDocumentDiagnostics<CR>
map <C-l> :LspRename<CR>

inoremap <expr><CR>  pumvisible() ? "<C-y>" : "<CR>"
inoremap <expr><TAB>  pumvisible() ? "\<C-n>" : "\<TAB>"
inoremap <expr><S-TAB>  pumvisible() ? "\<C-p>" : "\<S-TAB>"
```

```
:PlugInstall

:PlugClean
```

同じ関数や変数へのカーソル移動は　gd から n 連打
