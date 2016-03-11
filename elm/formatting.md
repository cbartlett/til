[back]: https://github.com/rafaelrinaldi/til/tree/master/elm
[elm-format]: https://github.com/avh4/elm-format
[elm-styleguide]: http://elm-lang.org/docs/style-guide
[elm-vim]: https://github.com/ElmCast/elm-vim
[esformatter]: https://github.com/millermedeiros/esformatter
[eslint]: http://eslint.org

# formatting

Similar to tools like [esformatter][esformatter] and [ESLint][eslint] for JavaScript, there's also a really nice code formatter for Elm called [`elm-format`][elm-format].

It will enforce the [language default code standards][elm-styleguide], which is one of the things that I really like about Elm.

## Install

1. Download and unzip the latest binary (currently `0.2.0-alpha`)
2. Move to `/usr/local/bin`
3. Compile the binary

```sh
$ curl -L https://github.com/avh4/elm-format/releases/download/0.2.0-alpha/elm-format-0.2.0-alpha-mac-x64.tgz | tar -xzv
$ mv elm-format /usr/local/bin/
$ chmod +x /usr/local/bin/elm-format
```

## Vim

Just make sure that you have the [`elm-vim`][elm-vim] plugin installed.

If you want to format files right after they're saved, add this to your `.vimrc`:

```viml
let g:elm_format_autosave = 1
```

---

[← Back][back]
