### What is Prisma?
`Prisma` is an ORM for Typescript, that allows you to define your database schema and models in a `schema.prisma` file, and then generate a type-safe client that can be used to interact with your database from your backend.

The Prisma schema file is found at `/prisma/schema.prisma`.

### The underlying database
The default database is an `SQLite` database, which is great for development and quickly spinning up a proof-of-concept but is not recommended for production.

You can change the database to use by changing the `provider` in the datasource block to either `postgresql` or `mysql`, and then updating the connection string within environment variables to point to your database.

### The Prisma Client
The Prisma client is located at `src/server/db.ts` and is a global variable exported to be used in your API routes.

The Prisma Client is used to send queries to your database.

You can get a reference of the client like so:

```ts
const { PrismaClient } = require("@prisma/client");

const prisma = new PrismaClient();
```

After that, you can query your database like so:

```ts
const users = await prisma.user.findMany();
```

Whenever the prisma schema changes, the prisma client needs to be regenerated with the following command:

```bash
prisma generate
```

