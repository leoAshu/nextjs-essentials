<img src='./images/cover.png'>

# Nextjs Essentials

## Introduction

Next.js is a React framework for building server-rendered React applications with ease. It simplifies the process of setting up and deploying React applications by providing a range of features out of the box.
In short, Next.js is a framework for building fast and search engine friendly web sites.

### Why Next.js?

Next.js offers several advantages, including:

- **Server-Side Rendering (SSR):** Improved SEO and faster initial page loads.
- **Automatic Code Splitting:** Efficient loading of only the code needed for a particular page.
- **Simplified Routing:** Page-based routing based on the file system structure.
- **Built-in CSS Support:** Support for various styling approaches.


### Client-side vs Server-side Rendering

|  Client-side Rendering  |  Server-side Rendering  |
|-------------------------|-------------------------|
|      Large bundles      |     Smaller bundles     |
|   Resource intensive    |    Resource efficient   |
|         No SEO          |           SEO           |
|       Less secure       |        More secure      |

> Note:
>
> - All components under `app` folder are server components by default.
> - Server components cannot
>   - Listen to browser events like click, change, etc
>   - Access browser APIs
>   - Maintain state
>   - Use effects

<br>
<p align="center">
    <image src="./images/csr-vs-ssr.png">
</p>
<p align="center">
    <b>Client-side vs Server-side Components</b>
</p>
<br>

## Getting Started

### Setting up a Next.js Project

To create a new Next.js project, you can use the create-next-app command-line tool:

```
npx create-next-app my-nextjs-app
cd my-nextjs-ap
```

### Project Structure

This is a sample project structure taken from the tutorial at [Learn Next.js: Getting Started](https://nextjs.org/learn/dashboard-app/getting-started)

<img src='./images/folder-structure.png'>

- `/app`: Contains all the routes, components, and logic for the application.
- `/app/lib`: Contains functions used in the application, such as reusable utility functions and data fetching functions.
- `/app/ui`: Contains all the UI components for the application, such as cards, tables, and forms.
- `/public`: Contains all the static assets for the application, such as images.
- `/scripts`: Contains utility scripts, for example a seeding script to populate the database.


## Routing in Next.js

### File-based Routing

Next.js uses a file-system-based router. For example, creating a file named `about.js` in the `pages` directory automatically creates the `/about` route.
This is a relatively obsolete approach to implement routing using the `Pages Router`.

In newer versions of Next.js, `App Router` has been introduced which requires each route to be defined as a folder with a `page.tsx` file inside the `app` folder.

> Note:
> - Any folder inside `app` folder is not publicly accessible unless a `page.tsx` file is placed inside it.
> - Pages router does not support server components
> - All components under the app folder are server components by default

### Dynamic Routes

Dynamic routes allow for the creation of pages with dynamic content. For instance, `[id].js` in the `pages` directory corresponds to `/posts/[id]`.

### Linking Between Pages

The `Link` component in Next.js enables client-side navigation between pages reducing the need for full-page reloads.

## Server-Side Rendering (SSR)

Server-side rendering involves rendering pages on the server rather than the client. This improves performance and SEO.

### Pages with `getServerSideProps`

The `getServerSideProps` function allows fetching data on each request, enabling dynamic content for SSR pages.


## Static Site Generation (SSG)

Static site generation generates HTML pages at build time, resulting in faster page loads.

### Pages with `getStaticProps`

Using `getStaticProps`, Next.js can pre-render pages at build time, fetching data to be injected into the page.

### Incremental Static Regeneration (ISR)

ISR allows regeneration of static pages on-demand, enhancing flexibility in content updates.

<br>
<p align="center">
    <image src="./images/rendering.png">
</p>
<p align="center">
    <b>Static and Dynamic Rendering in Next.js</b>
</p>
<br>

## Data Fetching

### Fetching Data on Client side

Use React hooks such as `useState` and `useEffect` to fetch data on the client side.

### SWR (Stale-While-Revalidate)

The SWR library simplifies data fetching with a focus on real-time updates and caching.

> Note:
>
> - Use server components to fetch data.
> - Fetching in server components has an extra benefit: Caching.
> - Next.js comes with a built-in data cache.
>   - Stores response in the cache automatically when using `fetch`.
>   - Pass `{ cache: 'no-store' }` as options to disable caching.
>   - Pass `{ next: { revalidate: 10 } }` as options to make Next.js refresh the response in cache after 10ms.


## API Routes

### Creating API Routes

API routes in the `pages/api` directory allow for the creation of backend APIs within the Next.js project.

### Handling API Requests

Handle HTTP requests within API routes using standard Node.js HTTP request handling.
