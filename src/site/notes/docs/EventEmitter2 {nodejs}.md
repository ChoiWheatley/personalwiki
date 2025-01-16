---
{"dg-publish":true,"permalink":"/docs/EventEmitter2 {nodejs}/","title":"EventEmitter2 {nodejs}"}
---

<https://github.com/EventEmitter2/EventEmitter2>

## [emitter.on](https://github.com/EventEmitter2/EventEmitter2?tab=readme-ov-file#emitteronevent-listener-options-objectboolean) OnOptions

- `async: boolean = false`: nodejs의 `setImmediate`를 사용하여 리스너를 호출한다. [[nodejs의 event loop에 대해서 설명해 주세요#2.2 `setImmediate`]] 참고.
- `nextTick: boolean = false`: nodejs의 `process.nextTick()`을 사용하여 리스너를 호출한다. [[nodejs의 event loop에 대해서 설명해 주세요#3.1 `process.nextTick`]] 참고. `setImmediate`보다 빨리 호출될 수 있다.
- `promisify: boolean`: 리스너를 Promise로 감싼다. 이벤트 발행시 `emitAsync`와 함께 사용해야한다.

## [emitter.emitAsync](https://github.com/EventEmitter2/EventEmitter2?tab=readme-ov-file#emitteremitasyncevent--eventns-arg1-arg2-)

위에서 언급했던 emitter.on `promisfy` 옵션과 맞물린다. [[docs/Promise.all\|Promise.all]] 을 사용하여 모든 리스너를 기다린다. 
