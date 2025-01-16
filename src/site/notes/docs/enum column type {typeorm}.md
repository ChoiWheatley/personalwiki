---
{"dg-publish":true,"permalink":"/docs/enum column type {typeorm}/","title":"enum column type {typeorm}"}
---

- <https://typeorm.io/entities#enum-column-type>

```typescript
export enum UserRole {
    ADMIN = "admin",
    EDITOR = "editor",
    GHOST = "ghost",
}

@Entity()
export class User {
    @PrimaryGeneratedColumn()
    id: number

    @Column({
        type: "enum",
        enum: UserRole,
        default: UserRole.GHOST,
    })
    role: UserRole
}
```
