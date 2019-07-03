"===> basic settings {
  set nocompatible
  filetype on
  filetype indent on
  filetype plugin on
  filetype plugin indent on
  syntax on
  let &t_ut=''
  set ai si ts=2 sw=2 st=2 "auto/smart indet, tabstop, shiftwidth, softtabstop
  set tw=0 indentexpr=
  set list listchars=tab:▸\ ,trail:▫
  set nu relativenumber
  set cursorline
  set showcmd ls=2 "laststatus
  set wildmenu
  set wrap
  set hlsearch incsearch ignorecase smartcase
  exec "nohlsearch"
  set backspace=indent,eol,start
  let &t_SI = "\<Esc>]50;CursorShape=1\x7"
  let &t_SR = "\<Esc>]50;CursorShape=2\x7"
  let &t_EI = "\<Esc>]50;CursorShape=0\x7"
  set autochdir
  au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif
"} <===

"===> map settings {
  let mapleader=" "
  nnoremap <LEADER>r :source $MYVIMRC<CR>
  "trun off hightlight in search
  nnoremap <LEADER><CR> :nohlsearch<CR> 

  nnoremap <LEADER>w :w<CR>
  nnoremap <LEADER>q :q<CR>
  nnoremap <LEADER>Q :q!<CR>

  "open a new window in right direction
  " vertically split window to right
  nnoremap <LEADER>v :set splitright<CR>:vs<CR>
  " move cursor in windows
  nnoremap <C-h> <C-w>h
	nnoremap <C-j> <C-w>j
	nnoremap <C-k> <C-w>k
  nnoremap <C-l> <C-w>l
  " make horizontal window to vertical window
  nnoremap <LEADER>V <C-w>t<C-w>H
  " resize window
  nnoremap <left> :vertical resize -5<CR>
  nnoremap <right> :vertical resize +5<CR>

  " tabe mapping
  nnoremap tu :tabe<CR>
  nnoremap t- :-tabnext<CR>
  nnoremap t= :+tabnext<CR>

  "open vimrc
  nnoremap <LEADER>rc :e /home/scott/.vim/vimrc<CR>

	" copy in visual mode
  vnoremap <C-c> "+y<ESC>

"} <===

"=== vim-plug ===
call plug#begin('~/.vim/plugged')
  Plug 'mhinz/vim-startify'
  Plug 'plasticboy/vim-markdown'
  Plug 'iamcco/markdown-preview.nvim', { 'do': { -> mkdp#util#install() } }
  Plug 'scrooloose/nerdtree'
  Plug 'vim-airline/vim-airline-themes'
  Plug 'vim-airline/vim-airline'
  Plug 'connorholyday/vim-snazzy'
  Plug 'vim-scripts/fcitx.vim'
  Plug 'mbbill/undotree'
	Plug 'ycm-core/YouCompleteMe'
	Plug 'Xuyuanp/nerdtree-git-plugin'
	Plug 'dhruvasagar/vim-table-mode', { 'on': 'TableModeToggle' }
call plug#end()

"===> plug settings {
  "===> vim-snazzy {
    let g:lightline = {
    \ 'colorscheme': 'snazzy',
    \ }
    let g:SnazzyTransparent = 1
    color snazzy
  "} <===
  "===> vim-markdown {
    " disable folding
    let g:vim_markdown_folding_disabled = 1 
    let g:vim_markdown_math = 1
  "} <===
  "===> markdown-preview.nvim {
    " set to 1, the nvim will auto close current preview window when change from markdown buffer to another buffer
    let g:mkdp_auto_close = 1
    " hot key to open or close it
    nnoremap <LEADER>p <Plug>MarkdownToggle
  "} <===
  
  "===> nerdtree {
    "  hot key
    nnoremap ff :NERDTreeToggle<CR>
    "  icons
    let g:NERDTreeDirArrowExpandable = '+'
    let g:NERDTreeDirArrowCollapsible = '-'
    "  location of nerdtree
    let g:NERDTreeWinPos='left'
    "  size of nerdtree
    let g:NERDTreeSize=30
    "  show line number
    let g:NERDTreeShowLineNumbers=1
    "  don't show hidden files
    let g:NERDTreeHidden=0
    " open nerdtree even if there is no content in this file
    "autocmd vimenter * if !argc()|NERDTree|endif
    " shut down nerdtree when it is the only thing in the window
    autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif
    " open nerdtree when the vim is opened
    "autocmd vimenter * NERDTree
  "} <===

	"===> nerdtree-git-plugin {
		let g:NERDTreeIndicatorMapCustom = {
    \ "Modified"  : "✹",
    \ "Staged"    : "✚",
    \ "Untracked" : "✭",
    \ "Renamed"   : "➜",
    \ "Unmerged"  : "═",
    \ "Deleted"   : "✖",
    \ "Dirty"     : "✗",
    \ "Clean"     : "✔︎",
    \ "Unknown"   : "?"
    \ }

	"} <===

  "===> undotree {
	  let g:undotree_DiffAutoOpen = 0
		nnoremap <LEADER>u :UndotreeToggle<CR>
	"} <===

	"===> vim-table-mode {
		let g:table_mode_corner='|'
		map <LEADER>tm :TableModeToggle<CR>
	  function! s:isAtStartOfLine(mapping)
	  	let text_before_cursor = getline('.')[0 : col('.')-1]
	  	let mapping_pattern = '\V' . escape(a:mapping, '\')
	  	let comment_pattern = '\V' . escape(substitute(&l:commentstring, '%s.*$', '', ''), '\')
	  	return (text_before_cursor =~? '^' . ('\v(' . comment_pattern . '\v)?') . '\s*\v' . mapping_pattern . '\v$')
	  endfunction

	  inoreabbrev <expr> <bar><bar>
	  			\ <SID>isAtStartOfLine('\|\|') ?
	  			\ '<c-o>:TableModeEnable<cr><bar><space><bar><left><left>' : '<bar><bar>'
	  inoreabbrev <expr> __
	  			\ <SID>isAtStartOfLine('__') ?
	  			\ '<c-o>:silent! TableModeDisable<cr>' : '__'
	 "} <===

  "===> airline {
    let g:airline_theme='bubblegum'
    if !exists('g:airline_symbols')
      let g:airline_symbols = {}
    endif
    " unicode symbols
    let g:airline_left_sep = '»'
    let g:airline_left_sep = '▶'
    let g:airline_right_sep = '«'
    let g:airline_right_sep = '◀'
    let g:airline_symbols.crypt = '🔒'
    let g:airline_symbols.linenr = '☰'
    let g:airline_symbols.linenr = '␊'
    let g:airline_symbols.linenr = '␤'
    let g:airline_symbols.linenr = '¶'
    let g:airline_symbols.maxlinenr = ''
    let g:airline_symbols.maxlinenr = '㏑'
    let g:airline_symbols.branch = '⎇'
    let g:airline_symbols.paste = 'ρ'
    let g:airline_symbols.paste = 'Þ'
    let g:airline_symbols.paste = '∥'
    let g:airline_symbols.spell = 'Ꞩ'
    let g:airline_symbols.notexists = 'Ɇ'
    let g:airline_symbols.whitespace = 'Ξ'
    "} <===
"} <===
