# Pulling Supabase Schema into Drizzle ORM

## Overview
This guide shows how to pull your existing Supabase database schema into Drizzle ORM, making it easy to migrate your database structure.

## Prerequisites
- Existing Supabase project
- Next.js project with Drizzle ORM installed
- Supabase connection credentials

## Steps

### 1. Get Supabase Connection String
Get your database connection string from Supabase:
1. Go to your Supabase project dashboard
2. Navigate to Project Settings → Database
3. Find the Connection String (URI) under Connection Info
4. Copy the connection string that looks like:
```
postgresql://postgres.[project-ref]:[password]@aws-0-[region].pooler.supabase.com:6543/postgres
```

### 2. Configure Drizzle
Create `drizzle.config.ts` in your project root:

```typescript
import 'dotenv/config';
import { defineConfig } from 'drizzle-kit';

export default defineConfig({
  dialect: 'postgresql',
  out: './drizzle',
  schema: './src/db/schema.ts',
  dbCredentials: {
    connectionString: process.env.DATABASE_URL!,
  },
  // Optionally filter specific tables/schemas
  tablesFilter: ['*'], // or ['users', 'posts'] for specific tables
  schemaFilter: ['public'], // Supabase stores user tables in public schema
  // Exclude Supabase's internal schemas
  schemas: ['public'],
  // Ignore Supabase's internal tables
  tablesFilter: ['!realtime*', '!auth*', '!storage*', '*'],
});
```

### 3. Pull the Schema
Run the pull command to generate your schema file:

```bash
npx drizzle-kit pull
```

This will create a `schema.ts` file with your database structure.

### 4. Review and Customize
Check the generated schema in `src/db/schema.ts`. You might want to:
- Add TypeScript types
- Modify column configurations
- Add indexes or relationships
- Remove any unwanted tables

Example of a generated schema:
```typescript
import { pgTable, serial, text, timestamp } from 'drizzle-orm/pg-core';

export const users = pgTable('users', {
  id: serial('id').primaryKey(),
  email: text('email').notNull(),
  name: text('name'),
  createdAt: timestamp('created_at').defaultNow(),
});

// Other tables will be added here
```

## Tips
- Use `.env` for database credentials
- Exclude Supabase's system tables using filters
- Review the generated schema for accuracy
- Add custom configurations after pulling

## Common Issues

1. **Authentication Error**
```bash
# Make sure your connection string is correct and includes:
- Correct project reference
- Valid database password
- Proper host and port
```

2. **Missing Tables**
```typescript
// Adjust tablesFilter in drizzle.config.ts
tablesFilter: ['*'], // Pull all tables
// or
tablesFilter: ['users', 'posts'], // Pull specific tables
```

3. **System Tables Included**
```typescript
// Add filters to exclude Supabase system tables
tablesFilter: ['!realtime*', '!auth*', '!storage*', '*'],
```

## Next Steps
After pulling your schema:
1. Set up your database connection
2. Migrate existing queries to Drizzle
3. Test your database operations
4. Consider setting up migrations for future changes
