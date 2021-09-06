## Comparison with TypeORM

### Annotations on top of class attributes

<div grid="~ cols-2 gap-6" class="mt-4">

<div>

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

<div class="flex items-center">
<div>
<div class="mb-3">
"Object–relational impedance mismatch"? 🤯
</div>

<a href="https://www.prisma.io/docs/concepts/overview/prisma-in-your-stack/is-prisma-an-orm" target="_blank">
  https://www.prisma.io/docs/ ... /is-prisma-an-orm
</a>
</div>
</div>

</div>
