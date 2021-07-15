
## Prisma : Focus sur ce 'schema.prisma'

<div grid="~ cols-2 gap-6" class="relative">

<div
  class="absolute -top-1 left-70 px-4 py-3 border rounded-full text-white bg-orange-300 shadow"
  style="z-index: 1;"
>
  1
</div>

```js {all|4-5}
server
 > dist
 > node_modules
 > prisma
     schema.prisma
 > src
 > test
   .env
   .env.local
   .gitignore
   .npmrc
   .nvmrc
   .prettierrc.yml
   package.json
   package-lock.json
   README.md
   tsconfig.json
```

<div
  v-if="$slidev.nav.clicks >= 2"
  class="absolute top-19 left-190 px-4 py-3 border rounded-full text-white bg-orange-300 shadow"
  style="z-index: 1;"
>
  2
</div>

<div>
<div v-click class="mt-5 border p-2 rounded-xl">
Génère-moi le client Prisma pour ce schéma :

`prisma generate`
</div>

<div
  v-if="$slidev.nav.clicks >= 3"
  class="absolute top-80 left-190 px-4 py-3 border rounded-full text-white bg-orange-300 shadow"
  style="z-index: 1;"
>
  3
</div>

<div v-click class="mt-8">
```js {3,5-8}
server
 > dist
 > node_modules
   > .bin
   > .prisma
     > client
         index.d.ts
         index.js
         ...
   > ...
 > prisma
     schema.prisma
 > src
 > test
   ...
```
</div>
</div>

</div>
