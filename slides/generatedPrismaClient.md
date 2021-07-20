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

👉 `BankAccount` :
> Une ligne dans notre table.

<br>
 
👉 `BankAccountCreateInput` :
> Ce qu'on a le droit de mettre quand on crée un bank_account.

<br>

👉 `BankAccountWhereInput`
> Ce qu'on a le droit de mettre dans une condition 'where'.

</div>
</div>

<!--
#### Des POJOs, contrairement à d'autres ORMs qui ont tendance à renvoyer des instances de modèles.

### $queryRaw : Je l'ai utilisé pour une requête de recherche de texte pour enlever les caractères accentués via un plugin de Postgres...
#### Mais attention ici on perdra les vérifications de syntaxe.
-->
