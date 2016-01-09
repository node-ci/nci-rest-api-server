# nci-rest-api-server

REST api server for [nci](https://github.com/node-ci/nci).

To enable add this plugin to the `plugins` section at server config:

```json
{
    "plugins": [
        "nci-rest-api-server"
    ],
    "http": {
        "host": "127.0.0.1",
        "port": 3000,
        "url": "http://127.0.0.1:3000"
    },
....
}
```

after that you can access api according to your server `http.host` and
`http.port` options.

## API routes

Note that currently destructive api methods (project removing/renaming)
protected by randomly generated token which will be print to the server log
at start.

### POST /api/0.1/builds

Create build by running given project.

Body parameters:
 - `project` - project to build
 - `withScmChangesOnly` - if true then build will be started only if
there is scm changes for project
 - `queueQueued` - if true then currently queued project can be queued
again

### PATCH /api/0.1/projects/:name

Rename project.

Body parameters:
 - `name` - new project name

### DELETE /api/0.1/projects/:name

  Remove project.
