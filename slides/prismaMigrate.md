## Prisma migrate

<div grid="~ cols-2 gap-6" class="relative">

<div v-click>
<div class="mb-3">
<mdi-numeric-1-box class="inline text-orange-300 text-2xl -mt-1" />
Je travaille sur ma feature, je fais une modification dans mon `schema.prisma` :
</div>

- `prisma format` > formatage + quelques vérifications
- `prisma db push` > Mise à jour de la structure de la base
- `prisma generate` > Mise à jour du client Prisma
</div>

<div v-click class="-mt-10">
<mdi-numeric-2-box class="inline text-orange-300 text-2xl -mt-1" />
Je suis prêt à valider ma feature :

- `prisma migrate dev --name "Ajout de la table des bank_accounts"`

```js {4-7}
server
 > dist
 > node_modules
 > prisma
   > migrations
     > 20210715144607_ajout_de_la_table_bank_accounts
         migration.sql
   schema.prisma
 > src
   ...
```
</div>

</div>

<div v-click class="-mt-2">
<div class="mb-1">
<mdi-numeric-3-box class="inline text-orange-300 text-2xl -mt-1" />
Je réplique les changements :
</div>

```json
scripts: {
  "db-preprod-up": "dotenv -e .env.preprod -- npx prisma migrate deploy",
}
```

<div class="mt-2">
👉 &nbsp;Joue le script SQL + insère une ligne dans la table `_prisma_migrations`.
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
