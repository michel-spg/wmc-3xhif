---
title: "Routing"
description: "Routing in Next.js"
nav_order: 2
layout: default
parent: Nextjs & React
---

![bg left:50% 80%](../../assets/imgs/spg_logo.png)

# Routing
## What is Routing?
Routing is the process of determining what content to display based on the URL. In a web application, different URLs can be used to display different content. For example, a URL like /about might display information about a company, while a URL like /contact might display a contact form.

## Routing (in Next.js)
Next.js uses **file-system based routing**, meaning you can use folders and files to define routes. This makes Next.js very easy to use and understand.

## Add a new folder about and page.tsx file
Link: https://nextjs.org/docs/app/getting-started/layouts-and-pages

NOTE: Using App Router

Create a new folder `about` in the `app` directory and add a new file `page.tsx` with the following content:

/app/about/page.tsx
```js
export default function AboutPage() {
  return (
    <div className="max-w-2xl mx-auto p-6 text-center">
      <h1 className="text-3xl font-bold mb-4">About Us</h1>
      <p className="text-lg text-gray-700">
        Welcome to our recipe collection! Our goal is to share delicious and
        easy-to-follow recipes for every occasion. Whether you are a beginner or
        an experienced cook, you'll find something to inspire your next meal.
        Enjoy cooking and happy eating!
      </p>
    </div>
  );
}
```	

Browser: http://localhost:3000/about

## Edit root layout.tsx and add component Header
Components are reusable pieces of code that can be used in multiple places in your application. In this step, you will create a new component called Header and add it to the root `layout.tsx` file, so it appears on every page.

Header.tsx
```js
export default function Header({ title }: { title: string }) {
  return (
    <div className="bg-emerald-50 rounded-lg p-4 text-4xl font-bold">
      <h1 className="text-center">{title}</h1>
      <p className="text-center text-lg">Fetch Recipes from an API</p>
    </div>
  );
}
```	

Delete the same content (from Header) from `page.tsx`.

Add the Header component to the `layout.tsx` file:

```tsx
import Header from "./components/Header";

// ...

  return (
    <html lang="en">
      <body
        className={`${geistSans.variable} ${geistMono.variable} antialiased`}
      >
        <div className="md:container md:mx-auto my-5">
          <Header title="Recipe App" />
          {children}
        </div>
      </body>
    </html>
  );
```	

Delete the div from above in the `page.tsx` file.

=== Add a Navbar component to the root `layout.tsx` file
Create a new component called Navbar and add it to the root `layout.tsx` file, so it appears on every page.

Navbar.tsx
```tsx
import Link from "next/link";

export default function Navbar() {
  return (
    // sticky
    <div className="header rounded-lg mb-3 top-0 bg-white flex items-center justify-center px-8 py-2">
      <nav className="nav text-lg text-center">
        <ul className="flex items-center space-x-6">
          <li className="p-3 border-b-2 border-emerald-50 border-opacity-0 hover:border-opacity-100 hover:text-emerald-50 duration-200 cursor-pointer">
            <Link key="Recipes" href="/">
              Recipes
            </Link>
          </li>
          <li className="p-3 border-b-2 border-emerald-50 border-opacity-0 hover:border-opacity-100 hover:text-emerald-50 duration-200 cursor-pointer">
            <Link key="About" href="/about">
              About
            </Link>
          </li>
        </ul>
      </nav>
    </div>
  );
}
```	

layout.tsx
```tsx
import Navbar from "./components/Navbar";

// ...

  return (
    <html lang="en">
      <body
        className={`${geistSans.variable} ${geistMono.variable} antialiased`}
      >
        <div className="md:container md:mx-auto my-5">
          <Navbar />
          <Header title="Recipe App" />
          {children}
        </div>
      </body>
    </html>
  );
```	

## Dynamic Routes
A Dynamic Segment can be created by wrapping a folder's name in square brackets: [folderName]. For example, [id]. This allows you to create a route that can match any value for that segment of the URL.

Create a new folder called `recipes` in the `app` directory. Inside the `recipes` folder, create a new folder called `[id]` and add to this folder a new file `page.tsx` with the following content:

/app/recipes/[id]/page.tsx
```tsx	
import { notFound } from "next/navigation";
import { Recipe } from "../../types/Recipe";

// kann auch ausgelagert werden in eine API Datei in einem Ordner lib oder service
async function getRecipe(id: string): Promise<Recipe | null> {
  const res = await fetch(`https://dummyjson.com/recipes/${id}`);
  if (!res.ok) return null;
  return res.json();
}

export default async function RecipeDetailPage({
  params,
}: {
  params: Promise<{ id: string }>;
}) {
  const { id } = await params;  // extracts the id from the params object.
  const recipe = await getRecipe(id);

  if (!recipe) {
    return notFound();
  }

  return (
    <>
      TODO
    </>
  );
}
```

* params: Promise<{ id: string }> is a dynamic route parameter that Next.js will automatically * pass to the page component.
* notFound() is a helper function that returns a default 404 page.

RecipeList.tsx
```tsx
  // ...
  <p>Preparation Time: {recipe.prepTimeMinutes} minutes</p>
  <p>Cooking Time: {recipe.cookTimeMinutes} minutes</p>
  <Link href={`/recipes/${recipe.id}`}>
    <button className="px-4 py-2 bg-emerald-50 rounded-lg shadow-md">
      Details
    </button>
  </Link>
```

Browser: http://localhost:3000/recipes/1 OR http://localhost:3000/recipes/2