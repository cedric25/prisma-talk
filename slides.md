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
src: ./slides/prismaTitle.md
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

## Chez TypeORM

### Annotations au-dessus d'attributs de classe

<div class="mt-4">

```typescript
// User.ts

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

Des fonctions 'helpers' :
 - Formuler des requêtes de base de données,
 - Nous renvoient toujours des objets JavaScript simples.

<div class="text-sm mt-10">
(On peut toujours faire du SQL natif si Prisma ne contient pas la méthode qu'on souhaite : `prismaClient.$queryRaw`)
</div>

</div>
<div>

### index.d.ts

Les types TypeScript correspondant à nos modèles.  

<div class="text-sm mb-2">
8 tables = 13 000 lignes de TS...
</div>

```typescript
async getAccountingSumInCents({
  userId, firstDate, lastDate
}: {
  userId: string; firstDate: Date; lastDate: Date
}): Promise<
  Prisma.GetAccountingLineAggregateType<{
    sum: { amount_in_cents: true }
  }>
> {
    return this.#accountingLine.aggregate({
      sum: { amount_in_cents: true },
      where: {
        user_id: userId,
        date: { gte: firstDate, lte: lastDate },
      },
    })
}
```

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







---

## Les tests ?





---

## Prisma migrate

1. On travaille sur sa feature :

Modifications dans le schema.prisma.
`prisma db push` && `prisma generate`

2. On est prêt à valider notre feature :
`prisma migrate dev --name "Ajout de la table authors"`

 -> Nous génère un script de migration :
```
server
 > dist
 > node_modules
 > prisma
     > migrations
         > 20210715144607_ajout_de_la_table_authors
             migration.sql
     schema.prisma
 > src
 > test
   ...
```

Et pour mettre à jour la base de données de préprod :

`prisma migrate deploy`

```json
scripts: {
  "db-preprod-up": "dotenv -e .env.preprod -- npx prisma migrate deploy",
}
```

(Insertion d'une ligne dans la table _prisma_migrations)






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

## Pourquoi ça m'a plu ?

➕➕ <strong>TypeScript-first.</strong>  

➕➕ <strong>La doc qui balaye large.</strong>  
On retrouve par exemple un article qui donne les solutions de hosting cloud d'une DB.

➕➕ <strong>Le dynamisme du projet.</strong>  
Une levée de fonds en 2018, les releases régulières, le Slack de 46,000 personnes, la récente conf' Prisma Day.  
<span class="text-sm">
  (Disclaimer: Comme tout outil on ne sait pas si ça sera encore aussi dynamique dans quelques années !)
</span>

<Tweet id="1400893865196879873" scale="0.65" class="mt-7" />

<!--
### Et pourtant je ne suis pas un fan de la première de TS, mais là il faut bien reconnaître que c'est hyper agréable de bosser avec ça dans l'IDE.
-->





---

## En vrac

👉 Au début l'outil s'appelait Graphcool.

👉 Le "Prisma Query Engine" est codé en Rust.

👉 La roadmap de l'équipe Prisma est partagée ici :
<a href="https://www.notion.so/Prisma-Roadmap-50766227b779464ab98899accb98295f" target="_blank">notion.so/Pris...</a>





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





---

## Un ROTI ?

