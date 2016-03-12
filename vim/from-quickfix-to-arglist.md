[back]: https://github.com/rafaelrinaldi/til/tree/master/vim
[vimcasts]: https://vimcasts.org
[vimcasts-article]: http://vimcasts.org/episodes/project-wide-find-and-replace

# From quickfix to arglist

One of the things that bothers me in Vim is that there's no default way to run a command through the quickfix list.

We have to choose from `:argdo`, `:bufdo`, `:tabdo` and `:windo` to run a command in multiple contexts, but there's no `:qfdo` or something.

Recently I've read a [really nice article][vimcasts-article] on [Vimcasts.org][vimcasts] about _find and replace_ (which is probably the most well known deal breaker for people new to Vim) and found the following snippet:

```viml
command! -nargs=0 -bar Qargs execute 'args' QuickfixFilenames()
function! QuickfixFilenames()
  let buffer_numbers = {}
  for quickfix_item in getqflist()
    let buffer_numbers[quickfix_item['bufnr']] = bufname(quickfix_item['bufnr'])
  endfor
  return join(map(values(buffer_numbers), 'fnameescape(v:val)'))
endfunction
```

This will expose the `:Qargs` command which will enable us to move whatever is on the quickfix list into the arglist.

Most plugins will output stuff to the quickfix list so this little command can be very helpful on exposing that data.

---

[← Back][back]
