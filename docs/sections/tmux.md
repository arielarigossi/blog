
## tmux: 

Is a terminal multiplexer that allows you to manage multiple terminal sessions from a single 
window. Here's a quick reference guide to some of the most useful tmux commands.


# Cheatsheet 

## Starting and Attaching Sessions 
| Action                     | Command / Key Combination   | Description                                   |
| -------------------------- | --------------------------- | --------------------------------------------- |
| Start a new session        | tmux                        | Starts a new tmux session.                    |
| Start a new named session  | tmux new -s session_name    | Starts a new session with the specified name. |
| List all sessions          | tmux ls                     | Lists all active tmux sessions.               |
| Attach to the last session | tmux attach                 | Attaches to the most recently used session.   |
| Attach to a named session  | tmux attach -t session_name | Attaches to a specific session by name.       |
| Detach from a session      | Ctrl+b d                    | Detaches from the current session.            |


---


## Session Management 
| Action                  | Key Combination / Command         | Description                            |
| ----------------------- | --------------------------------- | -------------------------------------- |
| Rename current session  | Ctrl+b $                          | Renames the current session.           |
| Switch between sessions | Ctrl+b s                          | Lists sessions to switch between them. |
| Kill a specific session | tmux kill-session -t session_name | Terminates the specified session.      |
| Kill all sessions       | tmux kill-server                  | Terminates all tmux sessions.          |


---


## Window Management 
| Action                  | Key Combination | Description                      |
| ----------------------- | --------------- | -------------------------------- |
| Create a new window     | Ctrl+b c        | Opens a new window.              |
| List all windows        | Ctrl+b w        | Displays a list of all windows.  |
| Next window             | Ctrl+b n        | Switches to the next window.     |
| Previous window         | Ctrl+b p        | Switches to the previous window. |
| Select window by number | Ctrl+b [0-9]    | Switches to window number 0–9.   |
| Rename current window   | Ctrl+b ,        | Renames the current window.      |
| Close current window    | Ctrl+b &        | Closes the current window.       |


---


## Pane Management 
| Action                  | Key Combination    | Description                                      |
| ----------------------- | ------------------ | ------------------------------------------------ |
| Split pane horizontally | Ctrl+b "           | Splits the current pane horizontally.            |
| Split pane vertically   | Ctrl+b %           | Splits the current pane vertically.              |
| Toggle between panes    | Ctrl+b o           | Moves to the next pane.                          |
| Navigate panes          | Ctrl+b + Arrow Key | Moves to the pane in the direction of the arrow. |
| Swap pane with previous | Ctrl+b {           | Swaps current pane with the previous one.        |
| Swap pane with next     | Ctrl+b }           | Swaps current pane with the next one.            |
| Kill current pane       | Ctrl+b x           | Closes the current pane.                         |


---


## Resizing Panes 
| Action | Key Combination | Description | 
| --- | --- | --- | 
| Resize pane up | Ctrl+b Ctrl+↑ | Increases pane height upwards. | 
| Resize pane down | Ctrl+b Ctrl+↓ | Decreases pane height downwards. | 
| Resize pane left | Ctrl+b Ctrl+← | Decreases pane width to the left. | 
| Resize pane right | Ctrl+b Ctrl+→ | Increases pane width to the right. | 


---


## Copy and Paste Mode 
| Action | Key Combination | Description | 
| --- | --- | --- | 
| Enter copy mode | Ctrl+b [ | Enters copy mode for scrolling and copying. | 
| Navigate in copy mode | Arrow Keys or PgUp/PgDn | Moves cursor in copy mode. | 
| Start selection | Space (in copy mode) | Begins text selection in copy mode. | 
| Copy selection | Enter (in copy mode) | Copies selected text. | 
| Paste copied text | Ctrl+b ] | Pastes the copied text into the pane. | 


---


## Command Prompt and Help 
| Action                | Key Combination | Description                                  |
| --------------------- | --------------- | -------------------------------------------- |
| Enter command mode    | Ctrl+b :        | Opens the tmux command prompt.               |
| List all key bindings | Ctrl+b ?        | Displays all tmux key bindings and commands. |


---


## Miscellaneous Commands 
| Action                                | Key Combination / Command              | Description                                   |
| ------------------------------------- | -------------------------------------- | --------------------------------------------- |
| Reload tmux configuration             | Ctrl+b : then source-file ~/.tmux.conf | Reloads the tmux configuration file.          |
| Show system time                      | Ctrl+b t                               | Displays the current system time.             |
| Suspend tmux (detach without exiting) | Ctrl+b d                               | Detaches from the session without closing it. |


---


## Scripting and Automation 
| Action | Command | Description | 
| --- | --- | --- | 
| Send commands to a session | tmux send-keys -t session_name 'command' C-m | Sends a command to a specific session. | 
| Create session and run command | tmux new -s session_name -d 'command' | Creates a session and runs a command. | 


---


## Configuration Tips 
| Setting | Configuration | Description | 
| --- | --- | --- | 
| Configuration file location | ~/.tmux.conf | Default tmux configuration file path. | 
| Set prefix key to Ctrl+a | In ~/.tmux.conf:unbind C-bset -g prefix C-abind C-a send-prefix | Changes the default prefix key to Ctrl+a. | 
| Enable mouse support | In ~/.tmux.conf:set -g mouse on | Enables mouse interaction within tmux. | 
| Set default terminal mode to 256 colors | In ~/.tmux.conf:set -g default-terminal "screen-256color" | Enables 256-color support. | 

