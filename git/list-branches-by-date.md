[back]: https://github.com/rafaelrinaldi/til/tree/master/git
[for-each-ref]: https://git-scm.com/docs/git-for-each-ref
[fzf]: https://github.com/junegunn/fzf
[pick]: https://github.com/calleerlandsson/pick
[thoughtbot]: https://thoughtbot.com

# List branches by date

While `branch -a` is helpful, more often than not I want to get the branches list sorted by their modification date.

I recently discovered a neat feature of Git that can be used to accomplish that, it's the [`for-each-ref`][for-each-ref].
It's pretty much an easy way to loop through the refs list and format the output. A `--format` option is provided where we can specify how the program will spit out the data. It also gives us stuff like hash and reference name for free.

## Putting things together

The most accurate and consistent way I found to properly list branches by date was by doing the following:

```sh
$ git for-each-ref --sort='-authordate:iso8601' --format='%(refname)' refs/heads
refs/heads/fix/caffe-endpoint
refs/heads/master
refs/heads/fix/article-order
refs/heads/fix/pagination-german
refs/heads/fix/intl-errors
```

This does the job but it's also nice to see when a branch was modified alongside with its name, so let's improve the output for that:

```sh
$ git for-each-ref --sort='-authordate:iso8601' --format=' %(authordate:relative)%09%(refname:short)' refs/heads
 17 hours ago	fix/caffe-endpoint
 3 days ago	master
 4 days ago	fix/article-order
 5 days ago	fix/pagination-german
 5 days ago	fix/intl-errors
```

Much better.

## Taking it to the next level

Personally, most of the times when I want to see a list of branches I also want to switch to them right away. So why not make that happen with a single command?

One of my favorite CLI tools is [`pick`][pick], built by the awesome people at [Thoughtbot][thoughtbot]. It takes a list of stuff and creates an interactive list view out of it. We can combine it with the `checkout` command to achieve exactly what we want:

```sh
$ git checkout $(git for-each-ref --sort='-authordate:iso8601' --format=' %(authordate:relative)%09%(refname:short)' refs/heads | pick | cut -f2)
```

![Interactive List](git-checkout-pick.gif)

### fzf

You can also use [`fzf`][fzf] to accomplish the same thing.

```
$ git checkout $(git for-each-ref --sort='-authordate:iso8601' --format=' %(authordate:relative)%09%(refname:short)' refs/heads | cut -f2 | fzf)
```

Pretty useful isn't?

## Use it as a Git alias

I personally like to assign helpers like this to Git aliases. You can do that by editing your `$HOME/.gitconfig` file:

```gitconfig
[alias]
  branches = "!sh -c \"git checkout $(git for-each-ref --sort='-authordate:iso8601' --format=' %(authordate:relative)%09%(refname:short)' refs/heads | pick | cut -f2)\""
```

---

[← Back][back]
