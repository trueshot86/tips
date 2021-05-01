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
Plug 'mattn/sonictemplate-vim'

Plug 'hrsh7th/vim-vsnip'
Plug 'hrsh7th/vim-vsnip-integ'
call plug#end()

map <C-n> :LspDocumentDiagnostics<CR>
map <C-l> :LspRename<CR>
map <S-f> :LspDocumentFormatSync<CR>

inoremap <expr><CR>  pumvisible() ? "<C-y>" : "<CR>"
inoremap <expr><TAB>  pumvisible() ? "\<C-n>" : "\<TAB>"
inoremap <expr><S-TAB>  pumvisible() ? "\<C-p>" : "\<S-TAB>"

let g:sonictemplate_vim_template_dir = ['~/.vim/template']
let g:lsp_diagnostics_echo_cursor = 1
```

```
:PlugInstall

:LspInstallServer

:PlugClean
```

同じ関数や変数へのカーソル移動は　gd から n 連打

テンプレートになるファイルは、テンプレートディレクトリ/言語名/ファイル名のような配置をします。ファイル名には命名規則があります。[種類]-[テンプレート名].[拡張子]のようにします。種類はbase・file・snipの3種類で、baseは何も書いていない時に呼び出され、fileはbuffer名とテンプレート名が一致し、まだ何も書いていないときに呼び出されます。すでに何かを書いているとsnipが呼ばれます。

root@Yuris-PC:~# vi .vim/template/python/snip-ore.py

テンプレートファイルでは、変数などが使えます。
{{_name_}}だとファイル名。{{_cursor_}}でテンプレートを出した後のカーソルの位置。少し凝ったもので、{{_input_:var}}とすると、テンプレートを呼び出すときに、varの部分を何にするのか聞かれ、それが入ります。詳細は:help sonictemplate-vim-writetemplateに書かれています。

インデントがずれるときは :set paste を打ってから貼り付け。

linux cli でchrome起動時に socks指定で sshからvpnつかたような感覚
root@Yuris-PC:~# google-chrome --proxy-server="socks5://127.0.0.1:10000" --no-sandbox
