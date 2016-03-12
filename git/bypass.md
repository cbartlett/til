[back]: https://github.com/rafaelrinaldi/til/tree/master/git
[git-update-index]: https://www.kernel.org/pub/software/scm/git/docs/git-update-index.html

# bypass

There's a very handy Git command that allows to ignore changes to a file. To do that, you can use Git's builtin [`git-update-index`][git-update-index] with the `--assume-unchanged` flag.

I know this trick for some time now but I always forget the command, so let's use an alias to solve this:

```sh
$ git config --global alias.bypass 'update-index --assume-unchanged'
```

This will expose the `bypass` alias which is way more intuitive.

## Usage

```sh
$ git status
## master
 M log.txt

$ git bypass log.txt
$ git status
## master

$ # It works!
```

---

[← Back][back]
