## Chez TypeORM

### Annotations au-dessus d'attributs de classe

<div class="mt-4">

```typescript
// User.ts

@Entity()
export class User {

  @PrimaryGeneratedColumn("uuid")
  user_id: number;

  @Column()
  firstName: string;

  @Column()
  lastName: string;

  @Column()
  age: number;

}
```

</div>

<!--
### Exemple avec d'autres outils comme TypeORM où on va définir une classe JS / TS dans laquelle on va annoter / décorer les propriétés.

### Ça s'inspire d'autres ORM dans d'autres technos, si certains ont connu Java avec *Hibernate*...️
-->
