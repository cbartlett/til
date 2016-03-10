[back]: https://github.com/rafaelrinaldi/til/tree/master/npm
[npm-scripts]: https://docs.npmjs.com/misc/scripts
[npm-scripts-info]: https://github.com/srph/npm-scripts-info
[npm-scripts-info-reporters]: https://github.com/srph/npm-scripts-info/issues/3#issuecomment-188016455

# npm run (list)

If you rely on [npm scripts][npm-scripts] for running tasks you probably don't keep all the available tasks in your mind.  
Once in a while you'll need a way to list them all. Turns out that if you do not pass in any arguments for `npm run` (or `npm run-script`), it'll do that for you. See this output from a project of mine:

```sh
$ npm run
Scripts available in  via `npm run-script`:
  build
    npm run cleanup && npm run scripts
  compress
    NODE_ENV=production npm run scripts
  deploy
    node tools/deploy.js
  scripts
    rollup -c
```

Really useful for people jumping into the project.

## Fancier output

Alright we already have a way to list all the tasks available but they don't say much to a human, right? All you see is the command that task is going to execute.  

Looking for a better alternative I stumbled upon [`npm-scripts-info`][npm-scripts-info] which is a simple but effective solution. It adds a new key to the npm manifest that let's you specify a description for each task:

```json
{
  "scripts-info": {
    "build": "Build styles, scripts and templates to `/public`",
    "compress": "Minify styles and scripts for production usage",
    "deploy": "Deploy files under `/public` to the staging server",
    "scripts": "Build scripts (with inline source maps)"
  }
}
```

Create a task to execute `npm-scripts-info`:

```json
{
  "scripts": {
    "help": "npm-scripts-info"
  }
}
```

Run the `help` task:

```sh
$ npm run help -s
build:
  Build styles, scripts and templates to `/public`
compress:
  Minify styles and scripts for production usage
deploy:
  Deploy files under `/public` to the staging server through FTP
scripts:
  Build scripts (with inline source maps)
```

Much better.  

If you want to customize the output [there's a new release that supports "reporters"][npm-scripts-info-reporters], so you can pretty much do whatever you want.

---

[← Back][back]
