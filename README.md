# Hi everyone👋

> [!NOTE]
> My cat's name is `ねこねこ`

# ⌐◨-◨

```bash
function parse_git_branch {
    git branch --no-color 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ [\1]/'
}
function promps {
    local  BLUE="\[\e[1;34m\]"
    local  RED="\[\e[1;31m\]"
    local  GREEN="\[\e[1;32m\]"
    local  WHITE="\[\e[00m\]"
    local  GRAY="\[\e[1;37m\]"
    local  Mag="\[\e[1;35m\]"
    local  LIGHT_B="\[\e[0;34m\]"
    local  LIGHT_GREEN="\[\e[0;36m\]"
    case $TERM in
        xterm*) TITLEBAR='\[\e]0;\W\007\]';;
        *)      TITLEBAR="";;
    esac
    local BASE="\u@\h"
#    PS1="${TITLEBAR}${GREEN}${BASE}${WHITE}:${BLUE}\W${GREEN}\$(parse_git_branch)${BLUE}\$${WHITE} "

     PS1="${LIGHT_GREEN}\u${GREEN}\w:${GREEN}\$(parse_git_branch)${BLUE}\$${WHITE}: \n->> "
}
promps
source ~/.bashrc
eval "$(/opt/homebrew/bin/brew shellenv)"
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"
```

```vim
syntax on
colorscheme molokai
set tabstop=4
set shiftwidth=4
set encoding=utf-8
set incsearch
set ignorecase
set smartcase
set hlsearch
set backspace=indent,eol,start
" コピペさん
set clipboard=unnamed,autoselect

if &term =~ "xterm"
    let &t_SI .= "\e[?2004h"
    let &t_EI .= "\e[?2004l"
    let &pastetoggle = "\e[201~"

    function XTermPasteBegin(ret)
        set paste
        return a:ret
    endfunction
    inoremap <special> <expr> <Esc>[200~ XTermPasteBegin("")
endif

inoremap {<Enter> {}<Left><CR><ESC><S-o>
inoremap [<Enter> []<Left><CR><ESC><S-o>
inoremap (<Enter> ()<Left><CR><ESC><S-o>

```
