---
{"dg-publish":true,"permalink":"/docs/object literal to class object using Object.assign {js}/","title":"object literal to class object using Object.assign {js}"}
---

예제:

```typescript
const {userImg, userAcc, defaultImgId, ...userInfo} = userDto;
const user = new User();

// TODO 중복값에 대한 예외 처리 (userPhone, userNick)
Object.assign(user, userInfo);
```
