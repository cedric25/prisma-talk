## Prisma migrate

1. On travaille sur sa feature :

Modifications dans le schema.prisma.
`prisma format` && `prisma db push` && `prisma generate`

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
