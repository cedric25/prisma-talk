## Les deux fichiers générés

<div grid="~ cols-2 gap-6" class="relative">

<div class="pr-3 border-r">

### index.js

👉 findFirst()  
👉 findMany()  
👉 updateOne()  
👉 etc..

Des fonctions 'helpers' :
- Formuler des requêtes de base de données,
- Nous renvoient toujours des objets JavaScript simples.

<div class="text-sm mt-10">
(On peut toujours faire du SQL natif si Prisma ne contient pas la méthode qu'on souhaite : `prismaClient.$queryRaw`)
</div>

</div>
<div>

### index.d.ts

Les types TypeScript correspondant à nos modèles.

```typescript
import { Prisma } from '@prisma/client'

async getAccountingSumInCents({
  userId, accountingNumber, firstDate, lastDate
}): Promise<
  Prisma.GetAccountingLineAggregateType<{
    sum: { amount_in_cents: true }
  }>
> {
    return this.#accountingLine.aggregate({
      sum: { amount_in_cents: true },
      where: {
        user_id: userId,
        accounting_number: accountingNumber,
        date: { gte: firstDate, lte: lastDate },
      },
    })
}
```

</div>
</div>

<!--
#### Des POJOs, contrairement à d'autres ORMs qui ont tendance à renvoyer des instances de modèles.

### $queryRaw : Je l'ai utilisé pour une requête de recherche de texte pour enlever les caractères accentués via un plugin de Postgres...
#### Mais attention ici on perdra les vérifications de syntaxe.
-->