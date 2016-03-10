[back]: https://github.com/rafaelrinaldi/til/tree/master/npm

# npm run (silently)

When you run an npm script with `npm run`, by default it'll print everything that's going on under the hood:

```json
{
  "scripts": {
    "greet": "echo 'Hello!'"
  }
}
```

If we run our `greet` script:

```sh
$ npm run greet

> @ greet /Users/doughnut/dev/greetings
> echo 'Hello!'

Hello!
```

This is fine and often a desired behavior for the context of a task runner but what if you wanted to pipe out the output to another script? That wouldn't work because would send the whole log information, which is not what you want.

That's when `--silent` (aliased to `-s`) comes in handy:

```json
{
  "scripts": {
    "greet": "npm run time -s | xargs printf 'Hello! The time is %s'",
    "time": "date +%H:%M"
  }
}
```

If we run the fancier `greet` script now:

```sh
$ npm run greet

> @ greet /Users/doughnut/dev/greetings
> npm run time -s | xargs printf 'Hello! The time is %s'

Hello! The time is 23:19
```

This is only possible because we're using `-s` to retrieve the raw output of `time`. Very useful when you want to pipe the output of scripts into another scripts.

---

[← Back][back]
