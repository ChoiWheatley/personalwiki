---
{"dg-publish":true,"permalink":"/docs/cascade option {typeorm}/","title":"cascade option {typeorm}"}
---


> `cascade` 옵션을 주어 부모 테이블에 일어난 변화를 자식 테이블도 같이 수정되도록 만들 수 있다.

```ts
export class Photo {
	...
	@OneToOne(type => PhotoMetadata, (metadata) => metadata.photo, {
		cascade: true,
	})
	metadata: PhotoMetadata;
}

///

const photo = new Photo();
const metadata = new PhotoMetadata();
...
photo.metadata = metadata; // this way we CONNECT them

await photoRepository.save(photo);
```
