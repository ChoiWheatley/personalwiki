---
{"dg-publish":true,"permalink":"/docs/EntityManager {typeorm}/","title":"EntityManager {typeorm}"}
---


> Save data with `EntityManager`

```ts
import {Photo} from './entity/Photo';
import {AppDataSource} from './index';

const photo = new Photo();
await AppDataSource.manager.save(photo);
```
