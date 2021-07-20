---
# try also 'default' to start simple
theme: seriph

# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
#background: https://source.unsplash.com/collection/94734566/1920x1080
background: https://images.unsplash.com/photo-1588153191435-c890d9adbb99?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1650&q=80

# apply any windi css classes to the current slide
class: 'text-center'

# https://sli.dev/custom/highlighters.html
highlighter: shiki

# some information about the slides, markdown enabled
info: |
  ## LyonJS - Talk sur Prisma 
  Mercredi 21 juillet 2021

  Par [Cédric Nicoloso](https://cedric.nicoloso.me/)

layout: cover
---

# Bienvenue au LyonJS #68

<div class="flex justify-center">
  <img
    class="w-80 opacity-90"
    src="https://secure-content.meetupstatic.com/images/https%3A%2F%2Fsecure.meetupstatic.com%2Fphotos%2Fevent%2F9%2F2%2F9%2F7%2Fhighres_496537527.jpeg/600x337.jpg"
  />
</div>

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Talk #1 : Prisma comme ORM pour PostgreSQL <carbon:arrow-right class="inline"/>
  </span>
</div>

<!--
## Et ben, bienvenue à toutes et à tous.  

### On est ravi de pouvoir vous accueillir ici chez Indy pour ce nouveau LyonJS.

### On va attaquer le premier talk...
### Et je vais prendre une vingtaine de minutes pour vous parler de Prisma.
-->





---
src: ./slides/prismaTitle.md
layout: prisma-title
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

## Dans les deux sens

<div class="mt-15">
<span class="base-chip green">Schéma Prisma</span>
<heroicons-outline:arrow-narrow-right class="inline mx-4" />
<span class="base-chip orange">Base de données</span>

`prisma db push`

`prisma migrate dev`
</div>

<div class="mt-20">
<span class="base-chip orange">Base de données</span>
<heroicons-outline:arrow-narrow-right class="inline mx-4" />
<span class="base-chip green">Schéma Prisma</span>

  `prisma introspect`
</div>

<!--
#### Ah oui et si vous avez déjà une base de données, vous pouvez demander à Prisma de vous générer ce fichier. (Commande 'introspect')
-->


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

## Intégration du client Prisma

```javascript
import express from 'express'
import { PrismaClient } from '@prisma/client' // = import from '.prisma/client

const prisma = new PrismaClient()

const app = express()

app.get('/posts', async (req, res) => {
  const posts = await prisma.post.findMany({
    where: { published: true },
    include: { author: true },
  })
  res.json(posts)
})
```

<!--
### Exemple classique, tiré de la doc de Prisma.

#### Bon, c'est un exemple...
#### On préfèrera faire par exemple de l'injection de dépendance pour accéder à notre client Prisma. 
-->




---
src: ./slides/tests.md
---


---
src: ./slides/prismaMigrate.md
---



---

## Prisma studio

`prisma studio`

Une UI "minimaliste" pour explorer la base.

<img src="/images/prisma-studio.png" class="mt-10" style="max-width: 650px;">

<div class="mt-10 text-sm">
→ Autre option : <a href="https://tableplus.com/" target="_blank">TablePlus</a>
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

<!--
#### Bon je le mentionne quand même, ça a le mérite d'exister !
#### Mais pour être un peu plus sérieux je vous conseille TablePlus.
-->





---

## Avantages de l'outil

➕➕ <strong>TypeScript-first.</strong>

➕➕ <strong>Le dynamisme du projet.</strong>  
Une vraie équipe derrière, des releases régulières, le Slack de 46,000 personnes, la récente conf' Prisma Day.  
<span class="text-sm">
  (Disclaimer: Comme tout outil on ne sait pas si ça sera encore aussi dynamique dans quelques années !)
</span>

➕➕ <strong>La doc qui balaye large.</strong>  
On retrouve par exemple un article qui donne <a href="https://www.prisma.io/dataguide/postgresql/5-ways-to-host-postgresql" target="_blank">des solutions de hosting cloud d'un PostgreSQL</a>.

<Tweet id="1400893865196879873" scale="0.65" class="mt-7" />

<!--
### Je suis pas un fan de la première heure de TS, mais là il faut bien reconnaître que c'est hyper agréable de bosser avec ça dans l'IDE.
-->




---

## Dans mon contexte

<ul>
<li class="list-none mt-7">
👉 &nbsp;Un nouveau projet.
</li>

<li class="list-none mt-7">
👉 &nbsp;Seul développeur au début.
</li>

<li class="list-none mt-7">
👉 &nbsp;Expérience précédente sur <strong>MongoDB</strong> et <strong>Mongoose</strong>.
</li>
</ul>

<div class="mt-18">

<div class="uppercase mb-5 text-gray-400">
"Est-ce je devrais utiliser Prisma ?" 🤔
</div>
<a href="https://www.prisma.io/docs/concepts/overview/should-you-use-prisma" target="_blank">
https://www.prisma.io/docs/concepts/overview/should-you-use-prisma
</a>
</div>

<!--
#### 3. Donc l'idée c'était aussi de pas partir à l'opposé de ça.

#### Bref pour l'instant, dans mon contexte, plus d'avantages que d'inconvénients.

#### Et de toute façon, un ORM ne vous empêchera de tomber sur des problématiques plus larges de base de données, de SQL, etc.
-->




---

## En vrac

<ul>
<li class="list-none mt-7">
👉 &nbsp;Mai 2017 : Au début l'outil s'appelait <strong>Graphcool</strong>.
</li>

<li class="list-none mt-7">
👉 &nbsp;Mai 2018 : Seed de $4.5M et renommage en Prisma.
</li>

<li class="list-none mt-7">
👉 &nbsp;Début 2019 : Sortie de Prisma 2 et décorrélation de GraphQL.
</li>

<li class="list-none mt-12">
👉 &nbsp;Le "Prisma Query Engine" est codé en <strong>Rust</strong>.
</li>

<li class="list-none mt-7">
👉 &nbsp;La roadmap de l'équipe Prisma est partagée ici :
<a href="https://www.notion.so/Prisma-Roadmap-50766227b779464ab98899accb98295f" target="_blank">notion.so/Prisma-Roadmap...</a>
</li>
</ul>




---

## Quelques liens utiles

<ul>
  <li>
    <div>Commencer avec Prisma :</div>
    👉 <a href="https://www.prisma.io/docs/getting-started" target="_blank" class="ml-1">
      https://www.prisma.io/docs/getting-started
    </a>
  </li>
  <li>
    <div>Comparaison de différents ORMs JS / TS : <span class="ml-2 text-sm text-gray-400">(mars 2021)</span></div>
    👉 <a href="https://www.sitepoint.com/javascript-typescript-orms/" target="_blank" class="ml-1">
      https://www.sitepoint.com/javascript-typescript-orms/
    </a>
  </li>
  <li>
    <div>Un article qui compare Prisma à TypeORM : <span class="ml-2 text-sm text-gray-400">(avril 2021)</span></div>
    👉 <a href="https://javascript.developpez.com/actu/314513/Prisma-un-ORM-de-nouvelle-generation-pour-Node-js-et-TypeScript-pour-concurrencer-TypeORM-et-Sequelize-et-devenir-la-norme-de-l-industrie/" target="_blank" class="ml-1">
      https://javascript.developpez.com/actu/314513/Prisma-un-ORM-de-nouv...
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

