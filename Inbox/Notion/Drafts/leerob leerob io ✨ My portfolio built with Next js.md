# leerob/leerob.io: ✨ My portfolio built with Next.js, MDX, Tailwind CSS, and Vercel.

Source: Notes
Status: Unprocessed
URL: https://github.com/leerob/leerob.io

[https://repository-images.githubusercontent.com/162028712/4a18a100-578f-11eb-91ec-5463f26aae27](https://repository-images.githubusercontent.com/162028712/4a18a100-578f-11eb-91ec-5463f26aae27)

---

[4a18a100-578f-11eb-91ec-5463f26aae27](leerob%20leerob%20io%20%E2%9C%A8%20My%20portfolio%20built%20with%20Next%20js%205e45c61d0aed475c81cae24371dc5644/4a18a100-578f-11eb-91ec-5463f26aae27)

[leerob%20leerob%20io%20%E2%9C%A8%20My%20portfolio%20built%20with%20Next%20js%205e45c61d0aed475c81cae24371dc5644/68747470733a2f2f76657263656c2e636f6d2f627574746f6e](leerob%20leerob%20io%20%E2%9C%A8%20My%20portfolio%20built%20with%20Next%20js%205e45c61d0aed475c81cae24371dc5644/68747470733a2f2f76657263656c2e636f6d2f627574746f6e)

# leerob.io

My portfolio has transformed over the years - from a static HTML site, to Jekyll, to Hugo, and finally to Next.js/React/MDX. My personal slice of the internet provides a platform for my writing and to showcase my latest work.

If you want to understand this repo better, I did a [one-hour live stream](https://www.youtube.com/watch?v=xXQsF0q8KUg) walking through the codebase.

## Overview

- `pages/api/*` - [API routes](https://nextjs.org/docs/api-routes/introduction) powering `[/dashboard](https://leerob.io/dashboard)`, newsletter subscription, and post views.
- `pages/blog/*` - Static pre-rendered blog pages using [MDX](https://github.com/mdx-js/mdx).
- `pages/dashboard` - [Personal dashboard](https://leerob.io/dashboard) containing metrics like sales, views, and subscribers.
- `pages/*` - All other static pages.

## Running Locally

```
$ git clone https://github.com/leerob/leerob.io.git
$ cd leerob.io
$ yarn
$ yarn dev
```

Create a `.env.local` file similar to `[.env.example](https://github.com/leerob/leerob.io/blob/master/.env.example)`.

## Built Using

- [Next.js](https://nextjs.org/)
- [Vercel](https://vercel.com/)
- [MDX](https://github.com/mdx-js/mdx)
- [Tailwind CSS](https://tailwindcss.com/)