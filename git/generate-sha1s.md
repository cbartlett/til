[back]: https://github.com/rafaelrinaldi/til/tree/master/git
[git-hash-object]: https://git-scm.com/docs/git-hash-object
[jacob-clark]: https://www.jacob.uk.com
[openssl]: https://openssl.org
[sha1]: https://en.wikipedia.org/wiki/SHA-1

# Generate SHA1s from Git

You can generate [SHA1][sha1] strings using Git's builtin [`git-hash-object`][git-hash-object]:

```sh
$ echo "Value from the stdin" | git hash-object --stdin
47a90d8e6b2463ccb4ae841100af6212a446a379
```

Unexpected behavior but it can handy, specially if you don't have [`openssl`][openssl] available.

Shout out to [Jacob Clark][jacob-clark] for pointing that out.

---

[← Back][back]
