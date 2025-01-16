---
{"dg-publish":true,"permalink":"/docs/Bidirectional relationships using inverse relation {typeorm}/","title":"Bidirectional relationships using inverse relation {typeorm}"}
---


> Bidirectional relationships using *inverse relation*

```ts
// entity/PhotoMetadata.ts

@Entity()
export class PhotoMetadata {
	...
	@OneToOne(type => Photo, (photo) => photo.metadata)
	@JoinColumn()
	photo: Photo;
}

// entity/Photo.ts

@Entity()
export class Photo {
	...
	@OneToOne(type => PhotoMetadata, (photoMetadata) => photoMetadata.photo)
	metadata: PhotoMetadata;
}
```
