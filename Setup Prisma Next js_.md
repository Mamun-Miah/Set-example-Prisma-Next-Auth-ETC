# **Set up Prisma Next.js:**

| npm install prisma tsx \--save-devnpm install @prisma/clientnpx prisma init |
| :---- |

**Prisma/schema.prisma:** 

| *generator client {  provider \= "prisma-client-js"}datasource db {  provider \= "mysql"  url      \= env("DATABASE\_URL")}model User {  id        String   @id @default(cuid())  username  String   @unique  email     String   @unique  password  String  role      String   @default("user")  createdAt DateTime @default(now())  updatedAt DateTime @updatedAt}* |
| :---- |

**Env setup Example:**

| *DATABASE\_URL="mysql://USERNAME:PASSWORD@localhost:3306/DATABASE\_NAME"* |
| :---- |

**Migration:**

| npx prisma migrate dev \--name init |
| :---- |

**Lib initialize:**

[**https://www.prisma.io/docs/guides/nextjs\#25-set-up-prisma-client**](https://www.prisma.io/docs/guides/nextjs#25-set-up-prisma-client)

| *import { PrismaClient } from '@prisma/client'* |
| :---- |

| *const globalForPrisma \= global as unknown as {    prisma: PrismaClient}const prisma \= globalForPrisma.prisma || new PrismaClient()if (process.env.NODE\_ENV \!== 'production') globalForPrisma.prisma \= prismaexport default prisma* |
| :---- |

