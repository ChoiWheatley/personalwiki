---
{"dg-publish":true,"permalink":"/docs/Repository {typeorm}/","title":"Repository {typeorm}"}
---

- [[docs/0018.4 TypeORM 💾\|0018.4 TypeORM 💾]]
- [공식문서](https://typeorm.io/working-with-repository#)
___

모든 엔티티는 해당 테이블에 접근하고 수정할 권한을 가지고 있는 리포지토리 객체에 책임을 전가한다.

```ts
const photoRepository = AppDataSource.getRepository(Photo);
await photoRepository.save(photo);
const savedPhotos = await photoRepository.find()
```
