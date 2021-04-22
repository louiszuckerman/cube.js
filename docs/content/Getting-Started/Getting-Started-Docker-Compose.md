---
title: Docker Compose
permalink: /getting-started/docker-compose
category: Getting Started
menuOrder: 3
---

This guide will help you get Cube.js running using Docker
Compose.

> LOOM VIDEO HERE

## 1. Create a Docker Compose file

Create a `docker-compose.yml` file with the following content:

```yaml
version: '2.2'

services:
  cube:
    image: cubejs/cube:latest
    ports:
      # 4000 is a port for Cube.js API
      - 4000:4000
      # 3000 is a port for Playground web server
      # it is available only in dev mode
      - 3000:3000
    environment:
      - CUBEJS_DEV_MODE=true
    volumes:
      - cube:/cube/conf

volumes:
  cube:
```

### Network config for Linux Users

For Linux, add the following line to your `docker-compose.yml`

```yaml
network_mode: 'host'
```

## 2. Configure Cube.js

<!-- prettier-ignore-start -->
[[info |]]
| This step assumes that you have the necessary credentials to access a
| database instance. If you are unable to connect to a database instance,
| please use a Docker image to run a local database in your development
| environment.
<!-- prettier-ignore-end -->

The [Developer Playground][ref-devtools-playground] has a database connection
wizard that loads when Cube.js is first started up and no `.env` file is found.

> CONNECTION WIZARD SCREENSHOT HERE

## 3. Run Cube.js

```bash
$ docker-compose up -d
```

Check if the container is running:

```bash
$ docker-compose ps
```

## 4. Open Developer Playground

Head to [http://localhost:4000](http://localhost:4000) to open [Developer
Playground][ref-devtools-playground].

You can generate Data Schema files using Developer Playground. Once schema files
are generated you can execute queries on the Build tab in the Playground.

## Next Steps

Generating Data Schema files in Developer Playground is a good first step to
start modelling your data. You can [learn more about Cube.js Data
Schema][ref-cubejs-schema] for complex data modelling techniques.

Learn how to [query Cube.js with REST API][ref-rest-api] or [use Javascript
client library and integrations with frontend
frameworks][ref-frontend-introduction].

### Configuration with cube.js file

When using the `cube.js` file for configuration, you need to add it to the
`volumes` definition in your `docker-compose.yml`:

```yaml
volumes:
  - ./schema:/cube/conf/schema
  - ./cube.js:/cube/conf/cube.js
```

[ref-config]: /config
[ref-connecting-to-the-database]: /connecting-to-the-database
[ref-cubejs-schema]: /getting-started-cubejs-schema
[ref-devtools-playground]: /dev-tools/dev-playground
[ref-env-vars]: /reference/environment-variables
[ref-frontend-introduction]: /frontend-introduction
[ref-rest-api]: /rest-api
