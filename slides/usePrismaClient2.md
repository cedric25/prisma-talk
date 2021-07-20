## On essaye plus propre ?

<div class="grid gap-6 relative" style="grid-template-columns: 1fr 1fr;">

<div>

<!-- Col 1 -->
<div v-click>
<div
  class="absolute top-1 left-80 px-4 py-3 border rounded-full text-white bg-orange-300 shadow"
  style="z-index: 1;"
>
  1
</div>

<div class="mb-2">
  Au démarrage&nbsp;:
</div>

```typescript
import { PrismaClient } from '@prisma/client'

const prismaClient = new PrismaClient()

// Je décore mon instance de serveur
// avec mon client Prisma
export default plugin(async instance => {
  instance.decorate('db', prismaClient)
})
```
</div>

<div v-click>
<div
  class="absolute top-65 left-85 px-4 py-3 border rounded-full text-white bg-orange-300 shadow"
  style="z-index: 1;"
>
  2
</div>

<div class="mt-5 mb-2">
  Dans le module 'bankAccount' de mon application&nbsp;:
</div>

```typescript
// Je récupère le lien vers la table qui m'intéresse
const { bankAccount } = instance.db

// Je crée un fichier de DAO (Data Access Object)
const bankAccountDao = new BankAccountDao({
  bankAccount,
})
```
</div>
</div>

<!-- Col 2 -->
<div v-click>
<div
  class="absolute top-1 left-180 px-4 py-3 border rounded-full text-white bg-orange-300 shadow"
  style="z-index: 1;"
>
  3
</div>

<div class="mb-2">
  Dans le DAO :
</div>

```typescript
export class BankAccountDao {
  #bankAccount

  constructor({ bankAccount }: { bankAccount: PrismaClient['bankAccount'] }) {
    this.#bankAccount = bankAccount
  }

  async findBankAccounts({
    userId,
  }: {
    userId: string
  }): Promise<BankAccounts> {
    ...
  }
}
```
</div>

</div>
