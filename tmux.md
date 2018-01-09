# tmux cheatsheet

How did I get here? More importantly, how do I get out without breaking anything? That's sometimes how I feel when I'm in a new situation or using a new tool.

Case in point, tmux. I like how it looks when I see screenshots of other people's tmux setups, with multiple tiled windows, but I get mixed up with the keyboard shortcuts and panic quit more often than not.

I'm writing this right now while in a tmux tiled window, so it's really in my best immediate interest to get this logged.

I also find it befuddling to understand in other guides that `C-b` means holding the Control key and pressing the `b` key. When I'm looking for answers, I've already got a big cognitive load and can't really process that translation. So I'll just spell it out here.

* `ctrl+b` / `C-b` - This is the first key combo you'll press to do anything with tmux. All tmux commands will start with pressing this. _For some reason, on my Mac after using byobu this command key is actually `ctrl+a` like with `screen`, as byobu offered this to me as a choice and I chose what I was used to with screen._
* `ctrl+b, then %` / `C-b %` - After doing the core tmux command key, hold in Shift and press the `5` key to get the `%` percent symbol. This will split the tmux window vertically, so there are two tiles side-by-side.
* `ctrl+b, then left or right arrows` - Using the arrow keys like this will switch the active tile in the horizontal group created by `ctrl+b, then %`.
* `ctrl+b, then "` / `C-b "` - This splits the current pane horizontally, so you have a top and bottom to the pane.
* `ctrl+b, then up and down arrows` - This will switch between the upper and lower panes created by `ctrl+b, then "`.
* `ctrl+b, then c` - Create a new tmux window. These are shown on the bottom bar with indicators like `0:vim*` (the current window I'm in) or `1:../cheatsheets-` for another window in this same directory that doesn't have focus. When it does have focus, it changes to `1:../cheatsheets*` and the original window with vim open is `0:vim*`.
* `ctrl+b, then b or n` - `b` is for back, `n` is for next tmux window.
* `ctrl+b, then d` - Detach from the current tmux session, leaving it running in the background. Back at the command line, use `tmux ls` to list the current tmux sessions. Use the first number on the line as the tmux session number. Let's say you see `4: 2 windows (created Sat Dec 30 14:12:50 2017) [130x16]`, then you'd run `tmux attach-session -t 4` to resume/re-attach to that one. Or you can resume the last-opened tmux session with `tmux a`.
* `tmux attach-session -d` - This re-attaches to a session and disconnects any other viewers on the session, so if you're switching from a laptop with lower resolution/smaller screen to a desktop computer with a bigger screen, this will ensure you use all of the bigger screen real estate.
* `tmux ls` - List existing tmux sessions.
* `tmux attach-session -t 0` - Re-attach to tmux session 0. The session number is indicated on the left of each line listed with `tmux ls`.
* `Ctrl+b, then $` - Renames the current tmux session. When you want to re-attach to the session, you'll see the session name you give it rather than the session number.

## References:

1. [A Gentle Introduction to tmux](https://hackernoon.com/a-gentle-introduction-to-tmux-8d784c404340)
1. [A Quick and Easy Guide to tmux](http://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)
1. [Is there any way to redraw tmux window when switching smaller monitor to bigger one?](https://stackoverflow.com/a/7819465/1141603)
1. [tmux Tutorial — Split Terminal Windows Easily](https://lukaszwrobel.pl/blog/tmux-tutorial-split-terminal-windows-easily/)
1. [How do I rename a session in tmux?](https://superuser.com/questions/428016/how-do-i-rename-a-session-in-tmux)
