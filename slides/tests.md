## Des tests ?

<div class="mt-8"></div>
<mdi-numeric-1-box class="inline text-orange-300 text-2xl -mt-1" />
En mockant complètement le client Prisma.

<div class="text-sm mt-2 ml-8">
👉 &nbsp;
<a href="https://www.prisma.io/docs/guides/testing/unit-testing" target="_blank">
https://www.prisma.io/docs/guides/testing/unit-testing
</a>
</div>

<div class="mt-12"></div>

<mdi-numeric-2-box class="inline text-orange-300 text-2xl -mt-1" />
En ayant un base de données de test.

<div class="text-sm mt-2 ml-8 mb-4">
👉 &nbsp;
<a href="https://www.prisma.io/docs/guides/testing/integration-testing" target="_blank">
https://www.prisma.io/docs/guides/testing/integration-testing
</a>
</div>

 - Injecter l'URL de la base de données de test :

`DATABASE_URL=postgresql://test-user:plop@localhost:5432/freely-test`

 - Réinitialiser la base de données entre chaque test.

`TRUNCATE TABLE \"${dbSchemaName}\".\"${tablename}\" CASCADE;`


<!--
📍 Problème : ça bloque le run des tests en parallèle...

💡 La technique de passer le test dans une transaction et de ne rien commiter à la fin ?

💡 Créer un schéma par test ?
-->
