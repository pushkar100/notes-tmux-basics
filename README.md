# TMux Basics (Notes)
Short Notes &amp; Quick Reference on TMux (Terminal Multiplexer)

## Contents
- [TMux Basics (Notes)](#tmux-basics--notes-)
  * [Source of these Notes:](#source-of-these-notes-)
  * [Tmux cheetsheet:](#tmux-cheetsheet-)
  * [Installing TMux on Mac(Using Homebrew):](#installing-tmux-on-mac-using-homebrew--)
  * [Installing TMux on Mac(Without Homebrew):](#installing-tmux-on-mac-without-homebrew--)
  * [TMux Github Page:](#tmux-github-page-)
  * [Advantages of Tmux:](#advantages-of-tmux-)
  * [Starting TMux:](#starting-tmux-)
  * [Killing (Closing) TMux session:](#killing--closing--tmux-session-)
  * [The `<ctrl-b>` prefix:](#the---ctrl-b---prefix-)
    + [Open a Window Pane (Similar to Windows in Vim):](#open-a-window-pane--similar-to-windows-in-vim--)
    + [Focusing on One Pane (Zooming/Fullscreen):](#focusing-on-one-pane--zooming-fullscreen--)
    + [Switching Between Panes:](#switching-between-panes-)
    + [Resizing the Current Pane:](#resizing-the-current-pane-)
    + [Open a Tab:](#open-a-tab-)
    + [Moving Between Tabs:](#moving-between-tabs-)
    + [Close/Kill a Window(Tab):](#close-kill-a-window-tab--)
    + [Renaming a Window(Tab):](#renaming-a-window-tab--)
  * [TMux Sessions:](#tmux-sessions-)
    + [Listing All the Sessions:](#listing-all-the-sessions-)
    + [Renaming a Tmux session:](#renaming-a-tmux-session-)
    + [Re-attaching(resume) a background tmux session:](#re-attaching-resume--a-background-tmux-session-)
    + [Detach(close) a tmux session:](#detach-close--a-tmux-session-)
    + [Switching between Tmux Sessions (Tmux terminals):](#switching-between-tmux-sessions--tmux-terminals--)
    + [Killing(Delete) a Tmux Session/Terminal:](#killing-delete--a-tmux-session-terminal-)
  * [Creating a tmux "configuration" file:](#creating-a-tmux--configuration--file-)
    + [Changing the prefix and adding shortcuts(key bindings) to the `.tmux.conf` file:](#changing-the-prefix-and-adding-shortcuts-key-bindings--to-the--tmuxconf--file-)


## Source of these Notes: 

https://www.youtube.com/watch?v=rc-v6eHdaN4&list=PLbkWnfz63JbWlZSq964DCMW64dM06_qht&index=3#t=44.909563)

## Tmux cheetsheet: 

https://tmuxcheatsheet.com/

## Installing TMux on Mac(Using Homebrew):

http://macappstore.org/tmux/

## Installing TMux on Mac(Without Homebrew):

https://gist.github.com/Fi5t/3bd299ea0bedc0b08b99b29787f57660

## TMux Github Page:

https://github.com/tmux/tmux

## Advantages of Tmux:

- Create Windows & Panes: Multiple & zooming functionality
- Maintains or restores old sessions
- Can create different sessions
- Can ssh into a server and install Tmux - create sessions - multiple people can work and coordinate.

## Starting TMux:

Type `tmux` on the CLI. (Alternate: `tmux new` to start a new tmux session)

## Killing (Closing) TMux session:

Type `<ctrl-b>` and write `:kill-session` (Hit Enter) - You will be back on the basic bash termial.

## The `<ctrl-b>` prefix:

Most of the Tmux commands begin with `<ctrl-b>`. It is the **default prefix** in TMux.

### Open a Window Pane (Similar to Windows in Vim):

- **Prefix** and then `%` = Opens a pane Vertically.
- **Prefix** and then `"` = Opens a pane Horizontally.
- Type `exit`             = Closes that pane. (Easy method)
- **Prefix** and then `x` = Gives an option to kill the current pane session(Alternative to 'exit')

### Focusing on One Pane (Zooming/Fullscreen):

- **Prefix** and then `z` = Opens up the current pane in full screen.

Press the SAME command to COME OUT of full screen mode! - `z` is a TOGGLE

### Switching Between Panes:

- **Prefix** and then `<ARROW-KEY>`     = Switches to pane pointed to by the pressed arrow key.

### Resizing the Current Pane:

- `<ctrl-b>` (DO NOT LET GO of Control key) and `<ARROW-KEY>`     = Increases/Decreases pane in the direction of the arrow key. Does not work on mac - Refer 'http://superuser.com/questions/863295/adjusting-screen-split-pane-sizes-in-tmux/863397' for solution. 

### Open a Tab:

A TMux tab can have multiple window panes

- **Prefix** and then `c`     = Opens a new tab (We can see the tabs list in the bottom bar) 

`*` indicates current window/tab.

### Moving Between Tabs:

- **Prefix** and then `p`     = Goes to previous tab
- **Prefix** and then `n`     = Goes to next tab

Last tab wraps around to the first when we press `n`. Similarly for `p`

### Close/Kill a Window(Tab):

- **Prefix** and then `&`     = Closes or kills the current window - asks for confirmation (Goes back to previous window)

### Renaming a Window(Tab):

Default names are something like '0:bash', '1:bash', etc.

- **Prefix** and then `,`     = Pressing the comma will allow us to edit the current window name (On the bottom bar)

## TMux Sessions:

### Listing All the Sessions:

- `tmux list-sessions`    = Lists all the tmux sessions ('attachment' next to a session means that that session is open inside a terminal. If 'attachment' is not there, it means the session is running in the background - not open in a terminal) 

Shortcut: `tmux ls`

### Renaming a Tmux session:

Using `tmux list-session`' will list sessions with session# next to them. It is hard to identify sessions with numbers. Therefore, we can give our sessions names so that we can identify it (& give the session meaning depending on what we are doing inside it.)

- To rename a session: Goto that session(terminal) & type **Prefix** and then `$`.

(OR)

- Start a Tmux session by giving it a name: Open a new terminal and run `tmux new -s <nameforsession>`. This opens tmux in the terminal with the given name.

### Re-attaching(resume) a background tmux session:

Open a new terminal & Run the command `tmux attach -t <nameofsessiontoresume>`.

(You may pre-check & post-check the attachment with 'tmux list-sessions') (Shortcut: `tmux a -t <namesessiontoresume>`)

(Note: If you have only one session then just typing `tmux a` in a new terminal is enough to resume it)

### Detach(close) a tmux session:

- **Prefix** and then `d`   = Detaches the tmux session. (Goes back to the regular bash terminal) (The detached session can later be resumed - see `tmux attach`)

### Switching between Tmux Sessions (Tmux terminals):

- **Prefix** and then `(` [or] `)`. (Wraps around)

### Killing(Delete) a Tmux Session/Terminal:

- `tmux kill-session -t <sessionname>`
- `tmux kill-session`   = Will kill the current tmux session - the terminal you are on).

Killing vs Detachment - Kill: stops sessions and no resumption possible. Detach: Session can be resumed later.

## Creating a tmux "configuration" file:

The file must be named `.tmux.conf` and stored in the **HOME** folder(~). (Create one if it does not exist)

### Changing the prefix and adding shortcuts(key bindings) to the `.tmux.conf` file:

A sample `~/.tmux.conf` file:

```
# Send prefix: SETS Prefix to <ctrl-a> (easier) instead of <ctrl-b>
set-option -g prefix C-a
unbind-key C-a
bind-key C-a send-prefix

# Use 'Alt' & 'arrow' keys to switch panes (Easier than <ctrl-b> & <arrow>)
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# 'Shift' & 'arrow' to switch windows (Easier than <ctrl-b> & 'n' or 'p')
bind -n S-Left previous-window
bind -n S-Right next-window

# Mouse mode: (Allow mouse to select windows/panes & resize panes)
set -g mouse on
# (Not recommended - but a helpful backup - USE KEYS AS MUCH AS POSSIBLE)

# Set easier window split keys: (Prefix + h(or)v is better than % and ")
bind-key v split-window -h
bind-key h split-window -v

# Easy config reload: (Reload tmux config w/o closing & reopening tmux)
# Press PREFIX & the letter 'r'
bind-key r source-file ~/.tmux.conf \; display-message "tmux.conf reloaded." 
```


A better tmux conf file:

```
# allow reload of this file with PRE r
bind r source-file ~/.tmux.conf \; display "Reloaded."

# switch prefix to control-a, unmap b, allow double-a to go through
set -g prefix C-a
unbind C-b
bind C-a send-prefix

# -r repeat time (Default 500 millis)
set -g repeat-time 2000

# colors
# set -g default-terminal "screen-256color"

# mouse mode (scrolling, etc)
# tmux 2.1
setw -g mouse on

# tmux < 2.1
# setw -g mode-mouse on
# # set -g mouse-select-pane on
# set -g mouse-resize-pane on
# set -g mouse-select-window on

# remove delay
set -sg escape-time 1

# set {window,pane} index to start at 1
set -g base-index 1
setw -g pane-base-index 1


# remap split panes
# bind | split-window -h
# bind - split-window -v

# vim style through panes
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R

# vim style through windows (PRE Control-H/L)
bind -r C-h select-window -t :-
bind -r C-l select-window -t :+

# vim style through resizing
bind -r H resize-pane -L 5
bind -r J resize-pane -D 5
bind -r K resize-pane -U 5
bind -r L resize-pane -R 5

# vim style movement (PRE [ then hjkl)
set-window-option mode-keys vi
```
