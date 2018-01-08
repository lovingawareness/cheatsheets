# vim cheatsheet

## References:

1. ["Vim Cheat Sheet"](https://vim.rtorr.com/) 

### Plugins:

1. [altercation/vim-colors-solarized](https://github.com/altercation/vim-colors-solarized) - Solarized is a popular color scheme. Check out this repo for preview images.
1. [itchyny/lightline.vim](https://github.com/itchyny/lightline.vim) - A really neat status line to show at the bottom of the vim window.
1. [tpope/vim-sensible](https://github.com/tpope/vim-sensible) - "Sensible defaults" for vim. I'm not sure what makes a default "sensible" but it seems to work well.
1. [rstacruz/sparkup](https://github.com/rstacruz/sparkup) - A neat utility for expanding shortcodes into HTML. Like typing in `ol > li*2` and hitting `Ctrl+e` will expand this to `<ol><li></li><li></li></ol>` with carriage returns and tabbing for the nested elements.
1. [junegunn/fzf](https://github.com/junegunn/fzf) - 
1. [edkolev/tmuxline.vim](https://github.com/edkolev/tmuxline.vim) - Generates a status line for [tmux](tmux.md) that looks neat like the lightline status line for vim. After installing this, I generated my tmux theme with `:Tmuxline lightline` followed by `:TmuxlineSnapshot ~/.tmuxtheme`. I then enabled this as the theme for tmux by adding `if-shell "test -f ~/.tmuxtheme" "source ~/.tmuxtheme"` to my `~/.tmux.conf` config file.
