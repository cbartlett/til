[back]: https://github.com/rafaelrinaldi/til/tree/master/markdown
[cheatsheets]: https://github.com/rafaelrinaldi/cheatsheets

# Escaping Backticks

Yesterday I was adding some commands to [my personal Vim cheatsheet][cheatsheets] and found out that escaping backticks in markdown can be a bit tricky.

I tried a few options, the good old `\` and even `<code>` but none of them worked. Turns out that the best way to do it is by wrapping your content with double backticks:

<code>\`\` Content \`\`</code>

Note that you also need some whitespace around your content.

`` Yay, backticks → ` ``

---

[← Back][back]
