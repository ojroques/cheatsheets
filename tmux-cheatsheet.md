# TMUX cheatsheet

`prefix` refers to `CTRL-b` by default.


## Session management

- Create a new tmux session named `session_name`:
``` Shell
tmux new -s session_name
```
- Attach to an existing tmux session named `session_name`:
``` Shell
tmux a -t session_name
```
- Switch to an existing session named `session_name`:
``` Shell
tmux switch -t session_name
```
- List existing tmux sessions: `prefix s` or
``` Shell
tmux ls
```
- Detach the currently attached session: `prefix d` or
``` Shell
tmux detach
```
- Kill an existing tmux session named `session_name`:
``` Shell
tmux kill-session -t session-name
```
- Rename the current session to `session_name`: `prefix $` or
``` Shell
tmux rename-session -t session_name
```


## Window management

- Create a new window: `prefix c`
- Move to the next window: `prefix n`
- Move to the previous window: `prefix p`
- Rename the current window: `prefix ,`
- Select windows 0 through 9: `prefix 0-9`
- List windows: `prefix w`
- Kill the current window: `prefix &`


## Pane management

- Create a horizontal pane: `prefix %`
- Create a vertical pane: `prefix "`
- Switch to next pane: `prefix o`
- Move  between panes: `prefix arrow-keys`
- Enable scrolling: `prefix [`
- Toggle fullscreen: `prefix z`
- Resize pane: `hold prefix arrow-keys`
- Swap with next pane: `prefix }`
- Swap with previous pane: `prefix {`
- Kill the current pane: `prefix x`


## Copy and paste
- Enter copy mode: `prefix [`
- Start selection: `CTRL-Space`
- Copy into tmux clipboard: `ALT-w`
- Paste from tmux clipboard: `prefix ]`