## Prisma : Le schéma

<div class="grid mt-4 gap-6 -ml-8 -mr-8" style="grid-template-columns: 0.8fr 1.1fr; overflow: auto">

```js {all|all|13}
# schema.prisma

generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  user_id        String         @id
  email          String         @unique
  full_name      String
  bank_accounts  BankAccount[]
  created_at     DateTime       @default(now())
  updated_at     DateTime       @updatedAt

  @@map(name: "users") // Nom de la table en base
}
```

<div v-if="$slidev.nav.clicks >= 1">
```js {all|10-11}







model BankAccount {
  account_id String   @id @default(uuid())
  user_id    String
  user       User     @relation(fields: [user_id], references: [user_id])
  number     Int      @default(1)
  name       String
  balance    Int
  created_at DateTime @default(now())
  updated_at DateTime @updatedAt

  @@unique([user_id, number])

  @@map(name: "bank_accounts")
}
```
</div>

</div>

<!--
#### Allez on va rentrer un peu dans le dur du sujet. Et la première chose sur laquelle on tombe avec Prisma, c'est cette syntaxe de schéma.

#### On retrouve au début des petites infos de configuration, notamment avec l'URL de connexion qui viendra d'une variable d'environnment.

#### Puis ici on a un premier exemple de mapping de table. Bon rien de compliqué c'est un syntaxe qui est assez explicite.

#### Une deuxième table ici 'BankAccount'

#### Petite astuce ici : nommer le champ de la même façon dans les deux tables.

#### C'est un exemple ici de one-to-many, le many-to-many est aussi faisable, via une table de relation.
-->
