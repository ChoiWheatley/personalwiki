---
{"dg-publish":true,"permalink":"/docs/Column Types {typeorm}/","title":"Column Types {typeorm}"}
---

- [[docs/0018.4 TypeORM 💾\|0018.4 TypeORM 💾]]
- [공식문서](https://typeorm.io/entities#column-types)
___

```ts
import { Entity, PrimaryGeneratedColumn, Column } from "typeorm"

@Entity()
export class User {
	@PrimaryGeneratedColumn()
	id: number

	@Column()
	firstName: string

	@Column()
	lastName: string

	@Column()
	age: number
}
```
