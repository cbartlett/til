[back]: https://github.com/rafaelrinaldi/til/tree/master/elixir
[iex]: http://elixir-lang.org/docs/stable/iex/IEx.html
[repl]: https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop
[elixir]: http://elixir-lang.org
[plataformatec]: http://plataformatec.com.br
[plataformatec-blog-post]: http://blog.plataformatec.com.br/2016/03/how-to-quit-the-elixir-shell-iex
[gh-george]: https://github.com/georgeguimaraes

# Exiting IEx

As most modern languages, [Elixir][elixir] does have a really nice [REPL][repl] called [IEx][iex].  

I'm pretty new to the language myself and after messing around with the interactive shell for a while I tried to quit and... Well... It didn't worked.  
The muscle memory made me go with `Ctrl-C` which did something I didn't wanted and then I naturally tried `Ctrl-D` also without success.

I finally gave up and looked up online which lead me to a [very specific blog post on the subject][plataformatec-blog-post] by the folks at [Plataformatec][plataformatec].

It turns out that the proper way to close it is `Ctrl-\`.

---

[← Back][back]
