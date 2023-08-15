<h1 align="center" style="border-bottom: none;">⚡️@didik-mulyadi/nodejs-api-doc</h1>
<h3 align="center">A package to generate the API docs with multiple UI based on the open API file.</h3>
<br />
<p align="center">
  <p align="center">
    <a href="https://www.npmjs.com/package/@didik-mulyadi/nodejs-api-doc">
      <img alt="npm latest version" src="https://img.shields.io/npm/v/@didik-mulyadi/nodejs-api-doc/latest.svg">
    </a>
    <a href="https://www.npmjs.com/package/@didik-mulyadi/nodejs-api-doc">
      <img alt="npm bundle size" src="https://img.shields.io/bundlephobia/min/@didik-mulyadi/nodejs-api-doc">
    </a>
    <img alt="Visitors count" src="https://visitor-badge.laobi.icu/badge?page_id=@didik-mulyadi~nodejs-api-doc.visitor-badge&style=flat-square&color=0088cc">
    <a href="https://www.npmjs.com/package/@didik-mulyadi/nodejs-api-doc">
      <img alt="NPM license" src="https://img.shields.io/npm/l/@didik-mulyadi/nodejs-api-doc">
    </a>
    <p align="center">
      <a href="https://github.com/didikmulyadi/nodejs-api-doc/issues/new?template=bug_report.md">Bug report</a>
      ·
      <a href="https://github.com/didikmulyadi/nodejs-api-doc/issues/new?template=feature_request.md">Feature request</a>
    </p>
  </p>
</p>
<br />
<hr />

At this point, we are focus on to implement multiple UI API docs for Nest.JS and Express and working with others library that is generate the open api doc. but, in the future we will create our open api doc generation, "One Code for All Frameworks".

## Installation 🚀

Install `@didik-mulyadi/nodejs-api-doc` using pnpm/npm/yarn:

```bash
pnpm add @didik-mulyadi/nodejs-api-doc

# OR

npm install @didik-mulyadi/nodejs-api-doc

# OR

yarn add @didik-mulyadi/nodejs-api-doc
```

## Usage 💻

After we setup the package correctly, we can switch the UI in your docs with this. <br/>

Example the path is `/docs

1. Use Swagger UI, `/docs?ui=swagger`
2. Use Stoplight UI, `/docs?ui=stoplight`
3. Use Redoc UI, `/docs?ui=redoc`

## Implementation 💻

Here's an example of how to use this package:

## nodejs-api-doc with Nest Fastify + @nest/swagger

Step:

1. Modify your `src/main.ts`
2. Create a swagger config with `new DocumentBuilder()`
3. Generate open api document object with `SwaggerModule.createDocument(app, config)`
4. Setup nodejs-api-doc with `new NestApiDoc`
5. Start nodejs-api-doc with `nodejsApiDoc.start()`

```typescript
import { NestApiDoc } from '@didik-mulyadi/nodejs-api-doc'

async function bootstrap() {
  const app = await NestFactory.create<NestFastifyApplication>(
    AppModule,
    new FastifyAdapter()
  )
  // swagger
  const config = new DocumentBuilder()
    .setTitle('Node.js API Docs')
    .setDescription('This API provides ...')
    .setVersion('0.0.1')
    .build()
  const document = SwaggerModule.createDocument(app, config)

  // nodejs-api-doc
  const nestApiDoc = new NestApiDoc(app, document, {
    defaultUI: 'stoplight',
    customPath: '/docs',
  })
  nestApiDoc.start()

  // Run the nestjs
  await app.listen(8080, '0.0.0.0')
}
```

## Configuration options ⚙️

### Working with Helmet

#### Nest.JS Fastify Helmet

```typescript
import { NestApiDoc, helmetConfig } from '@didik-mulyadi/nodejs-api-doc';

async function bootstrap() {
  ...
  await app.register(helmet, helmetConfig.nodeApiDocHelmetOption);
  ...
}
```

## Bugs or Requests 🐛

If you found any issue or have a good suggestion, feel free to open an [issue](https://github.com/didikmulyadi/nodejs-api-doc/issues/new)

## TODO

We are still updating this package, to make it more usefull and easy to use. Here are the next that author want to do

- [] Add an example in `examples` directory for Nest.js Fastify Swagger
- [] Add an example in `examples` directory for Nest.js Express Swagger
- [] Add support Express.js

## Find Me 📖

Reach me on:

[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/https://www.linkedin.com/in/didikmulyadi/) [![Medium](https://img.shields.io/badge/Medium-12100E?logo=medium&logoColor=white)](https://medium.com/@https://didikmulyadi.medium.com/)
