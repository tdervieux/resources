[full document here](https://hackernoon.com/a-gentle-introduction-to-tmux-8d784c404340)

## Getting In and Out

#### Create a session
```tmux```

#### Using Prefix
`ctrl+b`

Or run a command
`crtl+b :mycommand`

#### Exit and close tmux session
```exit```

#### Detach (exit but not close)
```ctrl+b d```

#### List all tmux session
```
> tmux ls
0: 1 windows (created Tue Mar 19 09:26:54 2019) [129x39]]
```

#### Attach to a session
```tmux attach-session -t 3```

or 
```tmux a -t 0```

to the last session
```tmux a #```

#### Naming Sessions

To start a new session with a specific name we can just do the below:

```tmux new -s [name of session]```

With named sessions in place, now when we do tmux ls we see the session name instead. Likewise, we can then attach a session by using the name:

```tmux a -t [name of session]```


## Managing Panes

#### To split a pane horizontally:
```ctrl+b "```

#### To split pane vertically:
```ctrl+b %```

#### Switch Pane
```ctrl+b <release key> [arrow key]```

#### Resize Pan
```ctrl+b [arrow key]```

or for five spaces
```ctrl+b :resize-pane -[U|D|L|R] 5```
