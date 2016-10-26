# Contributions

If you'd like you help with the documentation, please do. All pull requests welcome. :)

# Working with the Docs

The docs are built using [MkDocs](http://www.mkdocs.org).

Once you have installed the `mkdocs` binary on the system, navigate to the root folder of the __redis-modules-redoc__ source (this will be the same directory holding the __mkdocs.yml__ file.

## Live Build

You can work on the documentation with a live browser refresh on changes by using the built in webserver in __MkDocs__:

First navigate to the directory that contains the `mkdocs.yml` file and then run:

```bash
mkdocs serve
```

You should receive some console output providing the local content address. Generally your content will be served at `http://127.0.0.1:8000`

> Change the port by adding it to the `serve` command (`mkdocs serve <port>`)

## HTML Compile

If you'd like an "offline" build of the compiled documentation site, navigate to the directory that holds the `mkdocs.yml` and run:

```bash
mkdocs build
```

You should find the HTML output in the newly created `site` directory. You can open the `index.html` locally in your browser.

__Note:__ _The site will work better when running through a basic local webserver like [SimpleHttpServer](http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python). Which is commonly already available on modern systems.