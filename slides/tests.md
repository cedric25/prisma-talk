## Les tests

1. En mockant complètement le prisma client.

2. En ayant un base de données de test.

2.1. Injecter l'URL de la bdd de test :

`DATABASE_URL=postgresql://test-user:plop@localhost:5432/freely-test`

2.2. Reset de la base entre chaque test.

📍 Problème : ça bloque le run des tests en parallèle...

<div>
💡 La technique de passer le test dans une transaction et de ne rien commiter à la fin est à priori déconseillé par Prisma.
</div>

<div>
💡 Créer un schéma par test ?
</div>

<!--
#### Alors je n'ai pas trop creusé la première option.


-->
