## Prisma migrate

<div grid="~ cols-2 gap-6" class="relative">

<div v-click class="mt-6">
<div class="mb-3">
<mdi-numeric-1-box class="inline text-orange-300 text-2xl -mt-1" />
I'm working on a new feature, I make changes to my `schema.prisma` file:
</div>

- `prisma format` > formats + runs some checks
- `prisma db push` > updates local database structure + updates Prisma client
</div>

<div v-click class="-mt-14">
<mdi-numeric-2-box class="inline text-orange-300 text-2xl -mt-1" />
I'm ready to ship my new feature:

- `prisma migrate dev --name "Adding bank_accounts table"`

```js {4-7}
server
 > dist
 > node_modules
 > prisma
   > migrations
     > 20210715144607_adding_bank_accounts_table
         migration.sql
   schema.prisma
 > src
   ...
```
</div>

</div>

<div v-click class="mt-4">
<div class="mb-1">
<mdi-numeric-3-box class="inline text-orange-300 text-2xl -mt-1" />
I replicate database structure changes to other environments:
</div>

```json
scripts: {
  "db-preprod-up": "dotenv -e .env.preprod -- npx prisma migrate deploy",
}
```

<div class="mt-2">
👉 &nbsp;Runs the SQL migration script + inserts a new row to `_prisma_migrations` table.
</div>
</div>


<!--
#### Prisma intègre de la gestion de migrations. (qu'on peut utiliser, ou pas !)

#### Le workflow sur lequel je commence à me caler.

#### On peut aller vérifier les scripts SQL générés par 'prisma migrate'. Dans mon cas rien de bien compliqué donc c'était ok.
#### On peut toujours aller modifier ces scripts (garder la main), mais attention aux modifs il faut que ça reste compatible avec le client Prisma.

### Alors ça, ça marche dans les cas "simples". Typiquement si on renomme une colonne, prisma bloquera pour éviter de perdre des données...
-> <a href="https://www.prisma.io/dataguide/types/relational/expand-and-contract-pattern" target="_blank">Expand and contract pattern</a>
-->
