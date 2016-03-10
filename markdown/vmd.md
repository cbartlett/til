[back]: https://github.com/rafaelrinaldi/til/tree/master/markdown
[vmd]: https://github.com/yoshuawuyts/vmd
[gh-md-parser]: https://github.com/github/markup
[electron]: https://github.com/atom/electron

# vmd

[`vmd`][vmd] is a nice [Electron][electron] application that renders markdown files _almost_ exactly as they would be rendered by the [GitHub Markdown parser][gh-md-parser].

## Usage

It has a CLI that takes either a file or the content of the stdin.

```sh
$ # Read from a file
$ vmd README.md
$ # Read from the stdin
$ cat README.md | vmd
```

It's also really nice for previewing a file that you're editing in Vim:

```
:! vmd %
```

---

[← Back][back]
