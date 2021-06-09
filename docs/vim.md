## vim

Consider learning vim (especially if you are working on HPC platforms).

Here's an interactive intro on what vim is and how to use it:

[https://www.openvim.com](https://www.openvim.com)


### Cheat Sheet

Here's a link to a cheat sheet for VIM:

[https://devhints.io/vim](https://devhints.io/vim)

### My ~/.vimrc

Here's the content of my `~/.vimrc`

```bash
set exrc
set secure
" tabstop:          Width of tab character
" softtabstop:      Fine tunes the amount of white space to be added
" shiftwidth        Determines the amount of whitespace to add in normal mode
" expandtab:        When on uses space instead of tabs
:set tabstop=4
:set softtabstop=4
:set shiftwidth=4
:set expandtab
set clipboard=unnamed
" show line numbers
set number
" display white spaces
:set listchars=eol:$,tab:>-,trail:~,extends:>,precedes:<
:set list
set nocompatible              " be iMproved, required
filetype off                  " required
" key strokes / short cuts
map j gj
map k gk
map $ g$
map 0 g0
map J 10j
map K 10k
map L 10l
map H 10h
" enable syntax coloring
:syntax on
autocmd BufRead,BufNewFile *.tex,*.tikz set filetype=tex
autocmd BufRead,BufNewFile *.tex set spell spelllang=en_us
autocmd BufRead,BufNewFile *.txt set spell spelllang=en_us
:syntax spell toplevel
autocmd FileType * set tabstop=4|set shiftwidth=4|set softtabstop=4|set noexpandtab
autocmd FileType python,cpp,c,cmake,plaintex,tex,matlab set tabstop=4|set shiftwidth=4|set softtabstop=4|set expandtab
:colorscheme darkspace
autocmd FileType c,cpp,python,plaintex,tex,matlab autocmd BufWritePre <buffer> :%s/\s\+$//e
" use 256 color scheme
let &t_Co=256
:set colorcolumn=75
```

This remaps some of the standard keys to shortcuts. It also enables some features (for example spell checking and color mode).
