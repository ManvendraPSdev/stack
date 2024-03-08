![Stack Logo](/assets/logo.png)

<h2 align="center">
    <a href="https://docs.stackframe.co">Documentation</a>
    | <a href="https://stackframe-demo.vercel.app/">Demo</a>
    | <a href="https://stackframe.co/">Stackframe (hosting)</a>
</h4>

Stack is an open-source, self-hostable, and highly customizable authentication and user management system.

We provide frontend and backend libraries for Next.js, React, and JavaScript. You can set it up in one minute and scale with the project as it grows. Think of it as Supabase Auth or next-auth, but better.

Here is an example of the sign-up page you get out of the box:

![Stack Sign Up Page](/assets/signup-page.png)

## Features

- Composable React components & hooks
- OAuth (Google, Facebook, GitHub, etc.)
- Email and password authentication (with email verification and password reset)
- Easy to set up with proxied providers
- User management & analytics
- User-associated metadata with client-/server-specific permissions
- **100% open-source!**

## Installation

To get started with Stack, you need to [create a Next.js project](https://nextjs.org/docs/getting-started/installation) using the App router. Then, you can install Stack by running the following command:

```bash
npm install @stackframe/stack
```

For setup, refer to [our documentation](https://docs.stackframe.co).

## Development

This is for you if you want to contribute to the Stack project.

### Setup

Make sure you have `pnpm` installed alongside Node v20. Next, ensure you created `.env.local` files by copying `.env` in each of the subpackages in the `packages` folder and filling out the variables. You will need to start a Postgres database; you can do this with the following command:

```sh
docker run -it --rm -e POSTGRES_PASSWORD=password -p "5432:5432" postgres
```

Then:

```sh
pnpm install

# Run code generation (repeat this after eg. changing the Prisma schema)
pnpm run codegen

# After starting a Postgres database and filling the corresponding variables in .env.local, push the schema to the database:
# for production databases, use `deploy` instead. See: https://www.prisma.io/docs/orm/prisma-migrate/understanding-prisma-migrate/mental-model#prisma-migrate-in-a-staging-and-production-environment
pnpm run prisma:server -- migrate reset


# Start the dev server
pnpm run dev
```

You can also open Prisma Studio to see the database interface and edit data directly:

```sh
pnpm run prisma:server -- studio
```

### Database migrations

If you make changes to the Prisma schema, you need to run the following command to create a migration:

```sh
pnpm run prisma:server -- migrate dev
```
