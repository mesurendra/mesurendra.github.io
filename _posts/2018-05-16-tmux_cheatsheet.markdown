---
layout: post
title: Tmux Cheatsheet
date: 2018-05-16
Tags: Linux
---

### Start Tmux
```shell
> tumx
```

### Session

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

### Split Pane

Vertical split

```shell
> C-b, %
```

Horizontal split

```shell
> C-b, "
```

Navigate Pane

```shell
> C-b, <arrow key>
```


Closing pane

```shell
> exit
> C-d
```


### Windows

Creating new window:

```shell
> C-b, c

```

#### Navigate windows

Previous window

```shell
> C-b, p
```

Next window

```shell
> C-b, n
```

Using window number

```shell
> C-b, <number>
```






