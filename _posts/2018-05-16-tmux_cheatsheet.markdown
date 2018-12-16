---
layout: post
title: Cheatsheet
date: 2018-05-16
Tags: Linux
---
### TMUX cheetsheet

#### Start Tmux
```shell
> tumx
```

#### Session

Create a new session with a name

```shell
> tmux new -s <session-name>
```

List of existing session

```shell
> tmux ls
```

Attach to the existing session

```shell
> tmux attach -t <session name/number>
```

Rename tmux session

```shell
> tmux rename-session -t <previous name/no> <new-name>
```

Detach when inside tmux without ending the session

```shell
> tmux detach

```

#### Pane

Split pane
```shell
# Vertical split
> C-b, %

# Horizontal split
> C-b, "
```

Navigate Pane

```shell
> C-b, <arrow key>
```


Close pane

```shell
> exit
> C-d
```

#### Windows

```shell
# create new windows
> C-b, c

# Move cursor to previous window
> C-b, p

# Move cursor to next window
> C-b, n

#Move cursor using window number
> C-b, <number>
```





