# Contributions

If you'd like you help with the documentation, please do. All pull requests welcome. :)

# Working with the Docs

The docs are generated in a few different steps:

The __API.MD__, __BLOCK.MD__, and __TYPES.MD__, and __INTRO.MD__ are dropped directly into the `docs` directory from [here](https://github.com/antirez/redis/tree/unstable/src/modules).

The __INTRO.MD__ is renamed to __index.md__ and should reside in the `docs` directory root.

The __DEFINES.MD__ is derived from the [`redismodule.h`](https://github.com/antirez/redis/blob/unstable/src/redismodule.h) header file (manually for now).

The __FUNCTIONS.MD__ holds API info the __RMUtil Module__ helper. The data is derived towards the bottom of [this MD file](https://github.com/RedisLabs/RedisModulesSDK/blob/master/FUNCTIONS.md) viewed in "raw" mode.

From here any code examples, or deeper dives into other topics are highly encourged.

# Building Docs

The docs are built using [MkDocs](http://www.mkdocs.org).

Once you have installed the `mkdocs` binary on the system, navigate to the root folder of the __redis-modules-redoc__ source (this will be the same directory holding the __mkdocs.yml__ file.

## Live Build

You can work on the docs with a live browser refresh on changes by using the "preview" server included with __MkDocs__:

First navigate to the directory that contains the `mkdocs.yml` file and then run:

```bash
mkdocs serve
```

You should receive some console output providing the local content address. Generally your content will be served at `http://127.0.0.1:8000`

> Change the port by adding it after the `serve` command (`mkdocs serve <port>`)

## HTML Compile

If you'd like an "offline" build of the compiled documentation site, navigate to the directory that holds the `mkdocs.yml` and run:

```bash
mkdocs build
```

You should find the HTML output in the newly created `site` directory. You can open the `index.html` locally in your browser.

When regenerating the site, run:

```bash
mkdocs build --clean
```

__Note:__ _The site will work better when running through a basic local webserver like [SimpleHttpServer](http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python). Which is commonly available on most modern systems._