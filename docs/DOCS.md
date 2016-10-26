# Making Offline Docs

The docs are built using [MkDocs](http://www.mkdocs.org).

Once you have installed the `mkdocs` binary on the system, navigate to the root folder of the __redis-modules-redoc__ source (this will be the same directory holding the __mkdocs.yml__ file) and run:

```bash
mkdocs build
```

You should find the HTML output in the newly created `site` directory. You can open the `index.html` locally on your desktop, as well as store the directory elsewhere.

__Note:__ _The site will work better when running through a basic local webserver like [SimpleHttpServer](http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python). Which is commonly already available on modern systems.
