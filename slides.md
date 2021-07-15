---
# try also 'default' to start simple
theme: seriph

# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080

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
    class="w-80 opacity-75"
    src="https://secure-content.meetupstatic.com/images/https%3A%2F%2Fsecure.meetupstatic.com%2Fphotos%2Fevent%2F9%2F2%2F9%2F7%2Fhighres_496537527.jpeg/600x337.jpg"
  />
</div>

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<!--
## Et ben, bienvenue à toutes et à tous.  

### On est ravi de pouvoir vous accueillir ici chez Indy pour ce nouveau LyonJS.

### On va attaquer le premier talk...
### Et je vais prendre une vingtaine de minutes pour vous parler de Prisma.
-->





---
layout: prisma-title
src: ./slides/prismaTitle.md
---





---

## Prisma, qu'est-ce que c'est ?

<div class="text-xl mt-8">
  Prisma fait partie de <strong>la famille des ORMs</strong>.
</div>

<div class="mt-12">
  <img src="/images/prisma_diagram.svg">
</div>

<div v-click class="absolute top-95 left-100">
  <ul>
    <li>REST</li>
    <li>GraphQL</li>
  </ul>
</div>

<div v-click class="absolute top-95 left-190">
  <ul>
    <li>SQLite</li>
    <li>MySQL</li>
    <li>PostgreSQL</li>
    <li>
      SQL Server <span class="chip">Preview</span>
    </li>
    <li>
      MongoDB <span class="chip">Early Access</span>
    </li>
  </ul>
</div>

<style>
.chip {
  color: rgb(160, 174, 192);
  font-size: 0.875rem;
  font-style: normal;
  font-weight: 600;
  background: rgb(237, 242, 247);
  border-radius: 5px;
  padding: 2px 5px;
}
.chip.chip-light {
  color: rgba(160, 174, 192, 0.5);
  background: rgba(237, 242, 247, 0.2   );
}
</style>

<!--
#### En gros il va se placer entre notre code serveur et la base de données, et son rôle ça va être de nous :  
### → faciliter la vie dans ces interactions avec la base de données.
-->





---

## Autres candidats

### Contexte : PostgreSQL

<div grid="~ cols-4 gap-2" class='h-full pt-10 pb-20'>

<div class="flex items-center justify-center border-r">
  <div>
    <a href="https://github.com/brianc/node-postgres" target="_blank" class="text-3xl">
      pg
    </a>
    <div class="mt-3">
      → Le driver natif JS pour PostgreSQL
    </div>
  </div>
</div>

<div class="flex items-center justify-center border-r">
  <div>
    <a href="https://github.com/knex/knex" target="_blank" class="text-3xl">
      knex
      <img src="https://knexjs.org/assets/favicons/favicon-32x32.png" class="inline-block" style="width: 25px;" />
    </a>
    <div class="mt-3">
      → Un query builder
    </div>
    <div class="mt-3">
      <GithubStars count="14.4k" />
    </div>
  </div>
</div>

<div class="flex flex-col content-center items-end">
  <div style="width: 150px;">
    <a href="https://github.com/sequelize/sequelize" target="_blank" class="text-2xl">
      Sequelize
      <img src="https://sequelize.org/master/image/brand_logo.png" class="inline-block -mt-2" style="width: 25px;" />
    </a>
    <div class="mt-4">
      <GithubStars count="24.6k" />
    </div>
  </div>
  <div class="mt-10" style="width: 150px;">
    <a href="https://github.com/typeorm/typeorm" target="_blank" class="text-2xl">
      TypeORM
      <img src="/images/github-repos/typeorm-logo.png" class="inline-block -mt-1" style="width: 30px;" />
    </a>
    <div class="mt-4">
      <GithubStars count="24.9k" />
    </div>
  </div>
  <div class="mt-10" style="width: 150px;">
    <a href="https://github.com/mikro-orm/mikro-orm" target="_blank" class="text-2xl">
      MikroORM
      <img src="https://mikro-orm.io/img/favicon.ico" class="inline-block -mt-1" style="width: 22px;" />
    </a>
    <div class="mt-4">
      <GithubStars count="3.3k" />
    </div>
  </div>
</div>

<div class="flex flex-col content-center items-center">
  <div class="mt-10">
    <a href="https://github.com/bookshelf/bookshelf" target="_blank">
      Bookshelf.js
      <img src="https://avatars.githubusercontent.com/u/4448260?s=200&v=4" class="inline-block -mt-3" style="width: 22px;" />
    </a>
    <div class="mt-4">
      <GithubStars count="6.2k" />
    </div>
  </div>
  <div class="mt-10">
    <a href="https://github.com/Vincit/objection.js" target="_blank">
      Objection.js
    </a>
    <div class="mt-4">
      <GithubStars count="6.2k" />
    </div>
  </div>
</div>

</div>

<!--
### pg : On est au plus proche de la bdd, c'est top, en terme de perfs, etc. Mais on est un peu à poil, à écrire nos requêtes SQL sans auto-complétion dans l'IDE, sans type-checking, etc.

#### knex, l'entre-deux. Des méthodes helpers pour écrire nos requêtes, on se sent un peu plus en sécurité.

#### knex est parfois la base de l'ORM : Objection.js, MikroORM, Bookshelf.js, etc.
-->





---
src: ./slides/prismaSchema.md
---





---

## Chez TypeORM

### Annotations au-dessus d'attributs de classe

<div class="mt-4">

```js
@Entity()
export class User {

  @PrimaryGeneratedColumn("uuid")
  user_id: number;

  @Column()
  firstName: string;

  @Column()
  lastName: string;

  @Column()
  age: number;

}
```

</div>

<!--
### Exemple avec d'autres outils comme TypeORM où on va définir une classe JS / TS dans laquelle on va annoter / décorer les propriétés.

### C'est un peu subjectif mais j'accroche pas trop avec cette notation, les décorateurs en JS ce n'est pas une syntaxe native (il faut se tirer `reflect-metadata` si je me souviens bien), et ça me rappelle peut-être trop Java avec *Hibernate*... 🤷‍♂️
-->





---
src: ./slides/prismaSchema2.md
---





---

## Les deux fichiers générés

<div grid="~ cols-2 gap-6" class="relative">

<div class="pr-3 border-r">

### index.js

👉 findFirst()  
👉 findMany()  
👉 updateOne()  
👉 etc..

Des fonctions 'helpers' pour formuler des requêtes de base de données qui renvoient toujours des objets JavaScript simples.

(On peut toujours faire du SQL natif si Prisma ne contient pas la méthode qu'on souhaite : `prismaClient.$queryRaw` |

</div>
<div>

### index.d.ts

Les types TypeScript correspondant à nos modèles.  
8 tables → 13 000 lignes de TS 🤯

</div>
</div>

<!--
#### Des POJOs, contrairement à d'autres ORMs qui ont tendance à renvoyer des instances de modèles.

### $queryRaw : Je l'ai utilisé pour une requête de recherche de texte pour enlever les caractères accentués via un plugin de Postgres...
#### Mais attention ici on perdra les vérifications de syntaxe.
-->





---

## Intégration du client Prisma

```javascript
import express from 'express'
import { PrismaClient } from '@prisma/client'

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

#### Bon je comprends que c'est un exemple mais personnellement quand je vois ça j'ai mal aux yeux.
#### Non on n'interagît pas avec la base depuis un handler de route 🙀
-->





---

## On essaye plus propre ?



<!--
### Exemple classique, tiré de la doc de Prisma.

#### Bon je comprends que c'est un exemple mais personnellement quand je vois ça j'ai mal aux yeux.
#### Non on n'interagît pas avec la base depuis un handler de route 🙀
-->





---

## Les tests ?





---

## Prisma migrate

plop





---

## Prisma studio

plop






---

## Pourquoi ça m'a plu ?

➕➕ <strong>TypeScript-first.</strong>  

➕➕ <strong>La doc qui balaye large.</strong>  
On retrouve par exemple un article qui donne les solutions de hosting cloud d'une DB.

➕➕ <strong>Le dynamisme du projet.</strong>  
Les releases régulières, le Slack de 46,000 personnes, la récente conf' Prisma Day.  
<span class="text-sm">
  (Disclaimer: Comme tout outil on ne sait pas si ça sera encore vivant dans 2-3 ans !)
</span>

<Tweet id="1400893865196879873" scale="0.65" class="mt-7" />

<!--
### Et pourtant je ne suis pas un fan de la première de TS, mais là il faut bien reconnaître que c'est hyper agréable de bosser avec ça dans l'IDE.
-->





---

## Et ?

<img src="/images/frameworks-using-prisma.png">

👉 &nbsp;https://www.prisma.io/blog/prisma-the-complete-orm-inw24qjeawmb





---

## Pour aller plus loin

<ul>
  <li>
    <div>Commencer avec Prisma :</div>
    👉 <a href="https://www.prisma.io/docs/getting-started" target="_blank" class="ml-1">
      https://www.prisma.io/docs/getting-started
    </a>
  </li>
  <li>
    <div>(mars 2021) Comparaison de différents ORMs JS / TS :</div>
    👉 <a href="https://www.sitepoint.com/javascript-typescript-orms/" target="_blank" class="ml-1">
      https://www.sitepoint.com/javascript-typescript-orms/
    </a>
  </li>
  <li>
    <div>(avril 2021) Un article qui compare Prisma à TypeORM :</div>
    👉 <a href="https://javascript.developpez.com/actu/314513/Prisma-un-ORM-de-nouvelle-generation-pour-Node-js-et-TypeScript-pour-concurrencer-TypeORM-et-Sequelize-et-devenir-la-norme-de-l-industrie/" target="_blank" class="ml-1">
      https://javascript.developpez.com/actu/314513/Prisma-un-ORM-de-nouv...
    </a>
  </li>
  <li>
    <div>Chaîne Youtube avec présentations des releases</div>
    👉 <a href="https://www.youtube.com/c/PrismaData" target="_blank" class="ml-1">
      https://www.youtube.com/c/PrismaData
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
class: text-center
---

## Cédric Nicoloso

<br>

<div class="flex justify-center">
  <img src="https://avatars.githubusercontent.com/u/4280765" class="w-40 h-40 rounded-full">
</div>

<br>

https://cedric.nicoloso.me/

<br>
<br>

Retrouvez ces slides : https://cedric.nicoloso.me/2021-07/prisma-talk
