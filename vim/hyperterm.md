[back]: https://github.com/rafaelrinaldi/til/tree/master/vim
[twitter-thread]: https://twitter.com/rafaelrinaldi/status/757699595149385728
[hyperterm]: https://hyperterm.org
[fish]: http://fish.sh

> Quick and dirty way of having context-specific Vim settings for [HyperTerm][hyperterm] (in [fish][fish])

## The problem

[Today I was wondering][twitter-thread] the best way to set specific settings in Vim for HyperTerm and ended up using this quick and dirty solution that does the job.

So, there are quite a few ways to approach context-specific styling in Vim, but the easiest way that I can think of is using environment variables to do the check.

## The solution

The idea is:

* Create a fish function `hyper` that opens up HyperTerm with `$TERM_PROGRAM` set to `hyperterm`
* Add a check on `.vimrc` for that specific variable and do whatever

```fish
# config.fish

function hyper -d 'Open HyperTerm with proper $TERM_PROGRAM exported'
  set -x TERM_PROGRAM 'hyperterm'
  open /Applications/HyperTerm.app
end
```

```viml
" .vimrc

if $TERM_PROGRAM == 'hyperterm'
  syntax off
  set colorcolumn=
  set nolist
  " (...)
endif
```

It works!

So, probably the best way to do this is through plugins (since `0.7.0` you can specify session variables) or something else but this solution does the job for now.

❤ HyperTerm ❤

---

[← Back][back]
