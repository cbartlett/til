[back]: https://github.com/rafaelrinaldi/til/tree/master/tmux
[clipper]: https://github.com/wincent/clipper
[pasteboard]: https://github.com/ChrisJohnsen/tmux-MacOSX-pasteboard
[tmux-yank]: https://github.com/tmux-plugins/tmux-yank

# Clipboard

tmux doesn't ship with a great solution for clipboard. It's a pain to copy stuff
to the system clipboard. Today I found a nice way to do that.

## Requirements

You'll need to install [`reattach-to-user-namespace`][pasteboard].

```sh
$ # Easy install via Homebrew
$ brew install reattach-to-user-namespace
```

This is a tool made to solve the problem of local clipboard access on both tmux
and screen.

## Settings

Now you just need to make tmux interact with this tool.

```tmux
# Set default shell (I use `fish`, make sure you add yours)
set-option -g default-command "reattach-to-user-namespace -l fish"

# Send tmux buffer contents to OS clipboard whenever `y` is pressed
bind -t vi-copy y copy-pipe "reattach-to-user-namespace pbcopy"
```

## Usage

Now whenever you enter scroll mode, select something and hit <kbd>y</kbd> it
should be automatically available on your system clipboard.


## Related

- [Clipper][clipper]
- [Tmux Yank][tmux-yank]

---

[← Back][back]
