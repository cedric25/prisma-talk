## Prisma : Le schéma

<div grid="~ cols-2 gap-6" class="mt-4">

```js {all|all|11}
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
  first_name     String
  last_name      String
  bank_accounts  BankAccount[]
  roles          String[]
  created_at     DateTime       @default(now())
  updated_at     DateTime       @updatedAt

  @@map(name: "users") // Nom de la table en base
}
```

<div v-if="$slidev.nav.clicks >= 1">
```js {all|11-12}








model BankAccount {
  bank_account_id  String   @id @default(uuid())
  user_id          String
  user             User     @relation(fields: [user_id], references: [user_id])
  number           Int      @default(1)
  name             String
  balance_in_cents Int
  created_at       DateTime @default(now())
  updated_at       DateTime @updatedAt

  @@unique([user_id, number])

  @@map(name: "bank_accounts")
}
```
</div>

</div>
