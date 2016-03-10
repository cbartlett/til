[back]: https://github.com/rafaelrinaldi/til/tree/master/elm
[elm]: http://elm-lang.org
[elm-debug-log]: http://package.elm-lang.org/packages/elm-lang/core/2.1.0/Debug#log
[elm-signal]: http://package.elm-lang.org/packages/elm-lang/core/2.1.0/Signal
[fp]: https://en.wikipedia.org/wiki/Functional_programming

# Logging in Elm

Coming from JavaScript I automatically go with an equivalent of `console.log()` to quickly test operations in a language. In [Elm][elm] we have [`Debug.log`][elm-debug-log].  
However, Elm is a language built on top of [FP][fp] concepts, including immutability and <u>pure functions with no side effects</u>. This can get tricky because `Debug.log` does have side effects.

## What to do then?

Let's say I have a [`Signal`][elm-signal] and I want to log all the values flowing through it. We "inject" the log function and map it to our `Signal`:

```elm
Signal.map (Debug.log "Values: ") signal
```

It took me some time to get it but I rarely use logging these days. I'd rather rely on the compiler.

---

[← Back][back]
