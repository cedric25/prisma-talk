---

## Autres candidats

### Contexte : PostgreSQL

<div grid="~ cols-4 gap-2" class='h-full pt-10 pb-20'>

<div class="flex items-center justify-center border-r -ml-4">
  <div>
    <a href="https://github.com/brianc/node-postgres" target="_blank" class="text-3xl">
      pg
    </a>
    <div class="mt-3">
      → Le driver natif JS pour PostgreSQL
    </div>
    <div class="mt-3" style="width: 215px;">

```javascript
const user = await client.query(
  'SELECT * FROM users WHERE id = $1',
  ['123']
)
```

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
    <div class="mt-3 code-small">

```typescript
interface User {
  id: number;
  name: string;
  age: number;
}

knex<User>('users')
  .where('id', '123')
  .first();
```

</div>
  </div>
</div>

<div class="flex flex-col content-center items-end -mt-14">
  <div style="width: 150px;">
    <a href="https://github.com/sequelize/sequelize" target="_blank" class="text-2xl">
      Sequelize
      <img src="https://sequelize.org/master/image/brand_logo.png" class="inline-block -mt-2" style="width: 25px;" />
    </a>
    <div class="mt-3 transform scale-90 -ml-2">
      <GithubStars count="24.6k" />
    </div>
    <div class="mt-1">
      <PackageHealth
        score="92"
        snyk-link="https://snyk.io/advisor/npm-package/sequelize"
      />
    </div>
  </div>
  <div class="mt-10" style="width: 150px;">
    <a href="https://github.com/typeorm/typeorm" target="_blank" class="text-2xl">
      TypeORM
      <img src="/images/github-repos/typeorm-logo.png" class="inline-block -mt-1" style="width: 30px;" />
    </a>
    <div class="mt-3 transform scale-90 -ml-2">
      <GithubStars count="24.9k" />
    </div>
    <div class="mt-1">
      <PackageHealth
        score="89"
        snyk-link="https://snyk.io/advisor/npm-package/typeorm"
      />
    </div>
  </div>
  <div class="mt-10" style="width: 150px;">
    <a href="https://github.com/mikro-orm/mikro-orm" target="_blank" class="text-2xl">
      MikroORM
      <img src="https://mikro-orm.io/img/favicon.ico" class="inline-block -mt-1" style="width: 22px;" />
    </a>
    <div class="mt-3 transform scale-90 -ml-2">
      <GithubStars count="3.3k" />
    </div>
    <div class="mt-1">
      <PackageHealth
        score="83"
        snyk-link="https://snyk.io/advisor/npm-package/mikro-orm"
      />
    </div>
  </div>
</div>

<div class="flex flex-col content-center items-center -mt-5">
  <div class="mt-10" style="min-width: 120px">
    <a href="https://github.com/bookshelf/bookshelf" target="_blank">
      Bookshelf.js
      <img src="https://avatars.githubusercontent.com/u/4448260?s=200&v=4" class="inline-block -mt-3" style="width: 22px;" />
    </a>
    <div class="mt-3 transform scale-90 -ml-2">
      <GithubStars count="6.2k" />
    </div>
    <div class="mt-1">
      <PackageHealth
        score="76"
        snyk-link="https://snyk.io/advisor/npm-package/bookshelf"
      />
    </div>
  </div>
  <div class="mt-10" style="min-width: 120px">
    <a href="https://github.com/Vincit/objection.js" target="_blank">
      Objection.js
    </a>
    <div class="mt-3 transform scale-90 -ml-2">
      <GithubStars count="6.2k" />
    </div>
    <div class="mt-1">
      <PackageHealth
        score="86"
        snyk-link="https://snyk.io/advisor/npm-package/objection"
      />
    </div>
  </div>
</div>

</div>

<style>
.code-small pre {
  font-size: 0.7rem !important;
}
</style>

<!--
### pg : On est au plus proche de la bdd, c'est flexible, c'est top en terme de perfs, etc. Mais on est un peu à poil, à écrire nos requêtes SQL sans auto-complétion dans l'IDE, sans type-checking, etc.

#### knex, l'entre-deux. Des méthodes helpers pour écrire nos requêtes, on se sent un peu plus en sécurité.

#### knex est parfois la base de l'ORM : Objection.js, MikroORM, Bookshelf.js, etc.
-->