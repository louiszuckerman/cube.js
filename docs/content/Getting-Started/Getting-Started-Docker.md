---
title: Docker
permalink: /getting-started/docker
category: Getting Started
menuOrder: 2
redirect_from:
  - /getting-started-docker
---

This guide will help you get Cube.js running using Docker.

> LOOM VIDEO HERE

## 1. Create a new project

In a new folder for your project, run the following command:

```bash
docker run -p 4000:4000 -v cube:/cube/conf -e CUBEJS_DEV_MODE=true cubejs/cube
```

## 2. Open Developer Playground

<!-- prettier-ignore-start -->
[[info |]]
| This step assumes you can connect to a database instance. If you're unable
| to connect to a remote instance, please use a Docker image to run one in
| your local development environment.
<!-- prettier-ignore-end -->

Head to [http://localhost:4000](http://localhost:4000) to open [Developer
Playground][ref-devtools-playground].

The [Developer Playground][ref-devtools-playground] has a database connection
wizard that loads when Cube.js is first started up and no `.env` file is found.

> CONNECTION WIZARD SCREENSHOT HERE

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
