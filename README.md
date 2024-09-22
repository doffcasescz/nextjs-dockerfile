# Next.js app box for EasyPanel

[![StandWithUkraine](https://raw.githubusercontent.com/vshymanskyy/StandWithUkraine/main/badges/StandWithUkraine.svg)](https://github.com/vshymanskyy/StandWithUkraine) &nbsp;
[![Github Badge](https://img.shields.io/github/followers/digitalandyeu?label=@digitalandyeu&style=social)](https://www.github.com/digitalandyeu)

Next.js box starter for EasyPanel. Supports all Next.js features. See also [Next.js with Docker for EasyPanel](https://github.com/digitalandyeu/next-with-docker)

- Supports `public` directory and **images optimization**
- Choose between **node.js server** or `standalone` build

## Node.js Server (Recommended)

Next.js can be deployed to any hosting provider that supports Node.js. Ensure your `package.json` file has the following
scripts:

```json
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start"
  }
}
```

## Standalone setup

To use this box as a standalone app, you need to add a `next.config.js` file to the root of your project with the following content:

```js
/** @type {import('next').NextConfig} */
const nextConfig = {
  output: "standalone"
};

export default nextConfig;
```

Modify the npm scripts in `package.json` to use `node ./.next/standalone/server.js` instead of `next start` and copy the `public` and `static` directories to the `.next/standalone` directory:

```json
{
  "dev": "next dev",
  "build": "next build",
  "lint": "next lint",
  "start": "node ./.next/standalone/server.js",
  "postbuild": "npm-run-all -s export:*",
  "export:public": "cp -r ./public ./.next/standalone",
  "export:static": "cp -r ./.next/static ./.next/standalone/.next"
}
```

---

This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.
