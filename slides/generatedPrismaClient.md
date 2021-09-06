## Two generated files

<div grid="~ cols-2 gap-6" class="relative">

<div class="pr-3 border-r">

### index.js

👉 &nbsp;findFirst()  
👉 &nbsp;findMany()  
👉 &nbsp;updateOne()  
👉 &nbsp;etc..

'helper' functions:
- To write your queries,
- Will always return simple JavaScript objects (POJOs).

<div class="text-sm mt-10">
<div class="-mb-3">
We can still write SQL if necessary:
</div>

`prismaClient.$queryRaw('<SQL>')`
</div>

</div>
<div v-click>

### index.d.ts

All TypeScript types corresponding to our entities.

👉 `BankAccount` :
> A row in our table.

<br>

👉 `BankAccountCreateInput` :
> What we have to set when creating a bank_account.

<br>

👉 `BankAccountWhereInput`
> What we can use in a 'where' condition.

</div>
</div>
