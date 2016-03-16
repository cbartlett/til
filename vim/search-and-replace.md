[arglist]: http://vimdoc.sourceforge.net/htmldoc/editing.html#arglist
[back]: https://github.com/rafaelrinaldi/til/tree/master/vim
[buffers]: http://vimdoc.sourceforge.net/htmldoc/windows.html#:buffers

# Search and replace

This is probably the biggest deal breaker for people new to Vim. In other editors is something trivial to accomplish but in Vim it's a bit tricky.

There are plenty of ways to do this, but the way I like the most is relying on the [arglist][arglist] to do the job. Think of it as a subset of the [buffers list][buffers].

Let's say you want to change instances of `jquery` to `zepto` in your JavaScript files. The first thing is to populate the arglist with the files you want to change:

```
:args source/scripts/**/*.js
```

Notice that arglist accepts globbing, which is really convenient.

Now we have to perform a search and replace operation across all these files and for that we use `:argdo`:

```
:argdo s/jquery/zepto/ge | update
```

* The `e` flag will prevent messages from non matched results from our output
* `update` will actually write our changes to disk

Happy refactoring :wave:

---

[← Back][back]
