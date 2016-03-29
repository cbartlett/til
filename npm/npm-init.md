[back]: https://github.com/rafaelrinaldi/til/tree/master/npm
[npm]: https://npmjs.org
[promzard]: https://github.com/npm/promzard
[npm-init]: https://github.com/rafaelrinaldi/dotfiles/blob/master/npm-init.js

# npm init

It's just boring having to manually setup an [`npm`][npm] manifest. `npm init` is here to help us automate this task.

## The `--yes` flag

The `--yes` flag (aliased to `-y`) will bypass the default interactive mode:

```sh
$ npm init -y
$ ls
package.json
```

This can be specially handy for quick prototypes.

## Custom format

You can also customize the format of the manifest by creating a `~/.npm-init.js` file. It's simply a Node.js module and all you have to do is to folllow the default manifest format and key names:

```js
/**
 * - Start modules at v1.0.0
 * - Implement a "test" task
 * - Use tape for tests
 * - Default license is MIT
 */
module.exports = {
  version: '1.0.0',
  license: 'MIT',
  scripts: {
    test: 'tape test.js'
  },
  devDependencies: {
    tape: '*'
  }
};
```

Let's see if it works:

```sh
$ mkdir module && cd module
$ npm init -y
$ cat package.json
{
  "version": "1.0.0",
  "license": "MIT",
  "scripts": {
    "test": "tape test.js"
  },
  "devDependencies": {
    "tape": "*"
  },
  "name": "",
  "description": ""
}
```

It does! :tada:

### Interactive prompt

You can even have a custom interactive prompt (thanks to [`promzard`][promzard]) without having to install anything:

```js
/**
 * Will prompt for module name and description.
 * Note that `prompt()` is added by default and it's equivalent of
 * importing promzard.
 */
module.exports = {
  name: prompt('Module name', 'best-module-ever', name => name),
  description: prompt('Description', 'Best module ever published', description => description)
};
```

The `-y` flag is optional here but will provide a less verbose output:

```sh
$ npm init -y
Module name: (best-module-ever)
Description: (Best module ever published)
Wrote to /Users/jarvis/dev/best-module-ever/package.json:

{
  "name": "best-module-ever",
  "description": "Best module ever published",
  "version": "1.0.0",
  "license": "MIT",
  "scripts": {
    "test": "tape test.js"
  },
  "devDependencies": {
    "tape": "*"
  }
}
```

Cool, isn't it? [This is the one I use][npm-init].

Having a custom manifest format setup is useful to enforce consistency on your modules without relying on external tools like generators.

---

[← Back][back]
