# Migrating from Supabase to Drizzle ORM in Next.js

## Table of Contents
- [Project Structure](#project-structure)
- [Why Migrate to Drizzle ORM?](#why-migrate-to-drizzle-orm)
- [Migration Steps](#migration-steps)
  - [1. Initial Setup](#1-initial-setup)
  - [2. Database Configuration](#2-database-configuration)
  - [3. Schema Definition](#3-schema-definition)
  - [4. Database Migrations](#4-database-migrations)
  - [5. Query Migration](#5-query-migration)
- [References and Documentation 📚](#references-and-documentation-📚)

## Project Structure
```bash
your-nextjs-project/
├── drizzle/               # Generated migrations directory
├── src/
│   ├── db/
│   │   ├── index.ts      # Database connection
│   │   └── schema.ts     # Schema definitions
│   └── app/              # Next.js application code
├── drizzle.config.ts     # Drizzle configuration
├── .env                  # Environment variables
└── package.json
```

## Why Migrate to Drizzle ORM?
Drizzle ORM offers several advantages:
- 🚀 **Lightweight & Efficient**: Minimal overhead and bundle size
- 🛠️ **Type-safe**: Full TypeScript support with automated type inference
- 📈 **High Performance**: Optimized query building and execution
- 💻 **Developer Friendly**: Intuitive API and excellent DX

## Migration Steps

### 1. Initial Setup

Install required packages:
```bash
npm i drizzle-orm
npm i -D drizzle-kit
npm i dotenv
npm i postgres
```

Create a `.env` file in your project root:
```env
DATABASE_URL="postgres://user:password@host:port/database"
```

### 2. Database Configuration

Create `drizzle.config.ts` in your project root:
```typescript
import { config } from 'dotenv';
import { defineConfig } from 'drizzle-kit';
config({ path: '.env' });

export default defineConfig({
  out: './drizzle',
  schema: './src/db/schema.ts',
  dialect: 'postgresql',
  dbCredentials: {
    connectionString: process.env.DATABASE_URL!,
  },
});
```

Create `src/db/index.ts` for database connection:
```typescript
import { config } from 'dotenv';
import { drizzle } from 'drizzle-orm/postgres-js';
import postgres from 'postgres';

config({ path: '.env' }); // or .env.local
const client = postgres(process.env.DATABASE_URL!);
export const db = drizzle({ client });
```

### 3. Schema Definition

Create `src/db/schema.ts` to define your database schema:
```typescript
import { integer, pgTable, varchar, text } from "drizzle-orm/pg-core";

export const users = pgTable("users", {
  id: integer("id").primaryKey().notNull(),
  name: varchar("name", { length: 255 }).notNull(),
  email: text("email").notNull().unique(),
});
```

### 4. Database Migrations

You have two options for managing your database schema:

#### Option A: Direct Push (Development)
For quick development iterations, use push:
```bash
npx drizzle-kit push
```

#### Option B: Migration Files (Recommended for Production)
Generate and apply migrations:
```bash
# Generate migration files
npx drizzle-kit generate

# Apply migrations
npx drizzle-kit migrate
```

### 5. Query Migration

Update your existing Supabase queries to use Drizzle:

```typescript
// Before (Supabase)
const { data: users, error } = await supabase
  .from('users')
  .select('*');

// After (Drizzle)
import { db } from '@/db';
import { users } from '@/db/schema';

const allUsers = await db.select().from(users);
```

More complex query examples:

```typescript
// Insert
const newUser = await db.insert(users).values({
  name: 'John Doe',
  email: 'john@example.com',
}).returning();

// Update
const updated = await db
  .update(users)
  .set({ name: 'Jane Doe' })
  .where(eq(users.id, 1))
  .returning();

// Delete
const deleted = await db
  .delete(users)
  .where(eq(users.id, 1))
  .returning();
```

### References and Documentation 📚

To explore more about Drizzle ORM, refer to the official documentation:

- [PostgreSQL Column Types](https://orm.drizzle.team/docs/column-types/pg): Comprehensive guide to all supported PostgreSQL data types in Drizzle ORM. Use this to define your schema accurately.
- [Drizzle Query Builder (RQB)](https://orm.drizzle.team/docs/rqb): Detailed documentation for building queries with Drizzle ORM, including advanced querying techniques.

These resources will help you understand the specifics of column types and query construction, making your migration process smoother.
