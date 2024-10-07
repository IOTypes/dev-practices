# Fetching Data in Next.js
There are multiple ways to handle data fetching depending on your use case, and we’ll highlight the key approaches.

## API Layer
### Why use it?
APIs act as a middle layer between your app and the database, useful when:
 - You’re using third-party services.
 - You want to secure database access by running API logic on the server.
 - In Next.js, you can create API endpoints using [Route Handlers](https://nextjs.org/docs/app/building-your-application/routing/route-handlers).
  
### How?
- In Next.js, create API routes in the /api directory for server-side logic.

## Direct Database Queries
### Why use it?
- When using server components, you can skip APIs and query the database directly.
- This method is secure since the logic runs on the server, hiding database details from the client.
-  For [relational databases](https://aws.amazon.com/relational-database/) like Postgres, you can do this with SQL or with an [ORM](https://vercel.com/docs/storage/vercel-postgres/using-an-orm).
  
## React Server Components
### Why use it?
- These components simplify data fetching by supporting async/await syntax. Fetch data on the server and send only the necessary results to the client, keeping expensive logic hidden.
  
## Using SQL
* Why use it?
- SQL allows for powerful and specific queries when interacting with relational databases.
- It helps you retrieve only the data you need and prevents unnecessary data transfer.
  
## Parallel Data Fetching
### Why use it?
- Avoid performance bottlenecks by fetching data in parallel.
- Use Promise.all() to execute multiple requests simultaneously, improving speed and efficiency.




## Fetching Data with Search & Pagination
Fetching data with search and pagination in Next.js allows users to filter results by search terms and navigate through pages of data dynamically.

**Fetch Data on Every Request:** 
* Use `getServerSideProps` to fetch data from an API every time someone visits the page.

**Pagination:** 
* Use a `page` parameter in the URL to load data for specific pages (e.g, `?page=2` for page 2).

**Search:** 
* Use a `query`parameter (e.g, `?query=searchTerm`) to filter results based on what the user is searching for..

**Display the Results:** 
* Show the search results and allow users to click "Next" or "Previous" to load more pages.

```bash
export async function getServerSideProps(context) {
  const { page = 1, query = '' } = context.query; // Get page and search term
  const res = await fetch(`https://api.example.com/data?page=${page}&query=${query}`); // Fetch data from API
  const data = await res.json(); // Convert to JSON
  
  return { props: { data, page } } // Pass data to the page
}
```
To learn more [Click](https://nextjs.org/learn/dashboard-app/adding-search-and-pagination)