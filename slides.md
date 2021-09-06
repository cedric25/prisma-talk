---
theme: seriph

background: https://images.unsplash.com/photo-1588153191435-c890d9adbb99?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1650&q=80

# apply any windi css classes to the current slide
class: 'text-center'

# https://sli.dev/custom/highlighters.html
highlighter: shiki

# some information about the slides, markdown enabled
info: |
  ## LyonJS - Prisma Talk 
  July 21st, 2021

  By [Cédric Nicoloso](https://cedric.nicoloso.me/)

layout: cover
---

# Welcome to LyonJS #68

<div class="flex justify-center">
  <img
    class="w-80 opacity-90"
    src="https://secure-content.meetupstatic.com/images/https%3A%2F%2Fsecure.meetupstatic.com%2Fphotos%2Fevent%2F9%2F2%2F9%2F7%2Fhighres_496537527.jpeg/600x337.jpg"
  />
</div>

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Talk #1: Prisma as my ORM for PostgreSQL <carbon:arrow-right class="inline"/>
  </span>
</div>




---
src: ./slides/prismaTitle.md
---


---
src: ./slides/myContext.md
---


---
src: ./slides/prismaWhatIsIt.md
---


---
src: ./slides/competitors.md
---


---
src: ./slides/prismaSchema.md
---


---

## Both ways

<div class="mt-15">
I've got my <span class="base-chip green">Prisma schema</span>
<heroicons-outline:arrow-narrow-right class="text-3xl inline mx-4" />
I want my structure in my <span class="base-chip orange">database</span>

`prisma db push` &nbsp;&nbsp;&nbsp;✅
</div>

<div class="mt-14">
I've got my structure in my <span class="base-chip orange">database</span>
<heroicons-outline:arrow-narrow-right class="text-3xl inline mx-4" />
I want my <span class="base-chip green">Prisma schema</span>

`prisma db pull` &nbsp;&nbsp;&nbsp;✅
</div>


---
src: ./slides/typeOrmComparison.md
---


---
src: ./slides/prismaSchema2.md
---


---
src: ./slides/generatedPrismaClient.md
---



---

## Use Prisma client in your app

<div class="mt-8">

```javascript
import express from 'express'
// 1- Import it
import { PrismaClient } from '@prisma/client' // = import from '.prisma/client

// 2- Instantiate it
const prisma = new PrismaClient()

const app = express()

app.get('/bank-accounts', async (req, res) => {
  // 3- Use it
  const bankAccounts = await prisma.bankAccount.findMany({
    where: { active: true },
    include: { user: true },
    orderBy: { created_at: 'desc' },
  })
  res.json(bankAccounts)
})
```

</div>



---
src: ./slides/tests.md
---


---
src: ./slides/prismaMigrate.md
---



---

## Prisma studio

`prisma studio`

A minimalist admin UI to navigate throughout your data.

<img src="/images/prisma-studio.png" class="mt-10" style="max-width: 650px;">

<div class="mt-10 text-sm">
→ Other option: <a href="https://tableplus.com/" target="_blank">TablePlus</a>
</div>

<style>
.ced-link {
  border-radius: 1.5rem;
  display: inline-block;
  transition-property: background-color,border-color,color,fill,stroke;
  transition-timing-function: cubic-bezier(.4,0,.2,1);
  transition-duration: 150ms;
  padding: .7em .9em .7em .9em;
  border-bottom-width: 0 !important;
}
.ced-link:hover {
  cursor: pointer;
  background-color: rgba(16,135,117,.1);
}
</style>




---

## What I like about Prisma

➕➕ &nbsp;<strong>TypeScript-first.</strong>

➕➕ &nbsp;<strong>Dynamic project.</strong>  
A real team behind it, regular releases, huge community on Slack (~46,000 people), Prisma Day conference.  
<span class="text-sm">
  (Disclaimer: Like any other tool, we don't know if it will still be that dynamic in a few years!)
</span>

➕➕ &nbsp;<strong>A wide and well-written documentation.</strong>  

<Tweet id="1400893865196879873" scale="0.65" class="mt-7" />




---

## Miscellaneous

<ul>
<li class="list-none mt-7">
👉 &nbsp;<u>May 2017:</u> The tool was initially known as <span class="base-chip">Graphcool</span>.
</li>

<li class="list-none mt-7">
👉 &nbsp;<u>May 2018:</u> $4.5M seed round + rebranding to Prisma.
</li>

<li class="list-none mt-7">
👉 &nbsp;<u>Early 2019:</u> <span class="base-chip">Prisma 2</span> release with wider support than just GraphQL.
</li>

<li class="list-none mt-12">
👉 &nbsp;The "Prisma Query Engine" is implemented in <span class="base-chip">Rust</span>.
</li>

<li class="list-none mt-7">
👉 &nbsp;High level Prisma roadmap is shared here:
<a href="https://www.notion.so/Prisma-Roadmap-50766227b779464ab98899accb98295f" target="_blank">notion.so/Prisma-Roadmap...</a>
</li>
</ul>




---

## Some more resources

<ul class="mt-8">
  <li>
    <div>Getting started with Prisma:</div>
    👉 <a href="https://www.prisma.io/docs/getting-started" target="_blank" class="ml-1">
      https://www.prisma.io/docs/getting-started
    </a>
  </li>
  <li>
    <div>Comparing SQL, query builders, and ORMs:</div>
    👉 <a href="https://www.prisma.io/dataguide/types/relational/comparing-sql-query-builders-and-orms" target="_blank" class="ml-1">
      https://www.prisma.io/dataguide/types/relational/comparing-sql-query-builders-and-orms
    </a>
  </li>
  <li>
    <div>9 Best JS and TS ORMs: <span class="ml-2 text-sm text-gray-400">(mars 2021)</span></div>
    👉 <a href="https://www.sitepoint.com/javascript-typescript-orms/" target="_blank" class="ml-1">
      https://www.sitepoint.com/javascript-typescript-orms/
    </a>
  </li>
</ul>

<style>
ul li {
  @apply mb-5;

  div {
    @apply -mb-2;
  }
  a {
    @apply text-sm;
  }
}
</style>




---
src: ./slides/roti.md
---

