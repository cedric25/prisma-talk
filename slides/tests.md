## Des tests ?

<div class="mt-8"></div>
<mdi-numeric-1-box class="inline text-orange-300 text-2xl -mt-1" />
En mockant complètement le client Prisma.

👉 https://www.prisma.io/docs/guides/testing/unit-testing

<div class="mt-12"></div>

<mdi-numeric-2-box class="inline text-orange-300 text-2xl -mt-1" />
En ayant un base de données de test.

👉 https://www.prisma.io/docs/guides/testing/integration-testing

 - Injecter l'URL de la base de données de test :

`DATABASE_URL=postgresql://test-user:plop@localhost:5432/freely-test`

 - Réinitialiser la base de données entre chaque test.

`TRUNCATE TABLE \"${dbSchemaName}\".\"${tablename}\" CASCADE;`


<!--
📍 Problème : ça bloque le run des tests en parallèle...

💡 La technique de passer le test dans une transaction et de ne rien commiter à la fin ?

💡 Créer un schéma par test ?
-->
