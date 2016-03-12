[back]: https://github.com/rafaelrinaldi/til/tree/master/git
[hugo]: https://www.hugobessa.com.br

# Signing Git commits

## Why

Because after reading [this blog post](http://mikegerwitz.com/papers/git-horror-story.html) (sent by my dear friend [Hugo Bessa][hugo]) I got paranoid. It's a little effort that can avoid a lot of trouble.

## The problem

1. User changes the commit author using the `--author` option
2. The commit then introduces a new bug (blaming the new author)
3. Crackers explore this breach :skull:
4. An audit will not be able to identify who was the commit author

## The solution

Since Git `1.7.2`, one can sign commits (and tags) using their own GPG key.

### How

* Install [`gpg`](https://www.gnupg.org). You can install it from Homebrew:
```sh
$ brew install gpg
```
* Generate a fresh key:
```sh
$ gpg --gen-key # Default options are fine
```
* Now list all secret keys and copy the content from the `sec` row after the first `/`. Something like this:
```sh
$ gpg --list-secret-keys
/Users/your-user/.gnupg/secring.gpg
---------------------------------------
sec   XXXXX/YYYYYYYY 2015-01-01
uid                  Your Name (Your Comment) <your@email.com>
ssb   XXXXX/ZZZZZZZZ 2015-01-01

# What you want is that YYYYYYYY
```
* Register your key to your Git configuration file:
```sh
$ git config --global user.signingkey your-key
```
* You can now sign commits by using `git commit -S`. You might want to add it as an alias to your `.gitconfig`:
```sh
[alias]
  commit = commit -S
```
* Profit :moneybag:

## Further Reading

* [Email Self-defence](https://emailselfdefense.fsf.org)
* [GNU Privacy Guard Howto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)
* [Beginners Guide to GnuPG](http://ubuntuforums.org/showthread.php?t=680292)

---

[← Back][back]
