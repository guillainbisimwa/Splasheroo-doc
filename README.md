---
noteId: "5946a7d0add711ed8ba0d566f9e2e13f"
tags: []

---

Getting Started
---------------

### Prerequisites

You're going to need:

 - **Node.js**

### Getting Set Up

1. Fork this repository on Github.
2. Clone *your forked repository* (not this original one) to your hard drive with `git clone https://github.com/YOURUSERNAME/node-slate.git`
3. `cd node-slate`
4. Initialize and start Slate:

```shell
npm install
npm run build
npm start
```

You can now see the docs at http://localhost:4567. Whoa! That was fast!

### Commands

Compile documentation to static site in `./build`:

```shell
npm run build
```

Run a dev server that live-reloads at http://localhost:4567:

```shell
npm start
```

Publish your docs to `origin/gh-pages` branch:

```shell
npm run deploy
```

Gulp Task
---------

Slate API documentation generation is also available as a Gulp task with the
[gulp-node-slate](https://github.com/center-key/gulp-node-slate) plugin.

<br>

---
[MIT License](LICENSE.txt)
