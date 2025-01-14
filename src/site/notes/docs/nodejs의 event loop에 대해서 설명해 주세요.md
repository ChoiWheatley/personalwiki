---
{"aliases":null,"tags":null,"description":null,"links":["https://nodejs.org/en/learn/asynchronous-work/understanding-setimmediate","https://nodejs.org/en/learn/asynchronous-work/event-loop-timers-and-nexttick"],"status":null,"title":"nodejs의 event loop에 대해서 설명해 주세요","created":"2024-11-08T21:42:42","updated":"2025-01-10T22:25:02","dg-publish":true,"permalink":"/docs/nodejs의 event loop에 대해서 설명해 주세요/","dgPassFrontmatter":true}
---



Node.js의 이벤트 루프는 비동기 작업을 처리하기 위한 중요한 구조입니다. 이를 이해하기 위해서는 **Microtask**, **Macrotask**(또는 Task Queue), 그리고 Node.js에서 제공하는 **특수 API**(`setImmediate`, `setTimeout`, `process.nextTick`)의 동작 방식을 파악해야 합니다. 이 문서에서는 `setImmediate`와 `setTimeout`의 차이를 중심으로, 이를 Microtask와 Macrotask의 관점에서 비교합니다.

---

### 1. 이벤트 루프의 기본 구조

Node.js 이벤트 루프는 다음과 같은 단계로 이루어져 있습니다:

1. **Timers**: `setTimeout` 및 `setInterval` 콜백 처리.
2. **I/O Callbacks**: I/O 작업 완료 시 실행되는 콜백 처리.
3. **Idle, Prepare**: 내부적으로 사용되는 단계.
4. **Poll**: 새로운 I/O 이벤트를 가져오고, 필요한 경우 콜백을 실행.
5. **Check**: `setImmediate` 콜백 처리.
6. **Close Callbacks**: 닫기 이벤트의 콜백 처리. 예: `socket.on('close', ...)`

```
   ┌───────────────────────────┐
┌─>│        timers        │
│  └─────────────┬─────────────┘
│  ┌─────────────┴─────────────┐
│  │  pending callbacks   │
│  └─────────────┬─────────────┘
│  ┌─────────────┴─────────────┐
│  │    idle, prepare     │
│  └─────────────┬─────────────┘      ┌────────────────┐
│  ┌─────────────┴─────────────┐      │ incoming:   │
│  │         poll         │<─────┤ connections: │
│  └─────────────┬─────────────┘      │ data, etc.  │
│  ┌─────────────┴─────────────┐      └────────────────┘
│  │        check         │
│  └─────────────┬─────────────┘
│  ┌─────────────┴─────────────┐
└──┤    close callbacks   │
   └───────────────────────────┘
```

[출처](https://nodejs.org/en/learn/asynchronous-work/event-loop-timers-and-nexttick)

#### Microtask와 Macrotask

- **Microtask**: Promises의 `.then`이나 `process.nextTick`과 같은 작업은 현재 실행 중인 작업이 완료된 후 **즉시** 실행됩니다.
- **Macrotask**: `setTimeout`, `setImmediate` 등은 이벤트 루프의 다음 단계에서 실행됩니다.

---

### 2. `setImmediate` vs `setTimeout`

#### 2.1 `setTimeout`

- 특정 시간(기본값 0ms) 후에 실행되는 Macrotask입니다.
- **Timers 단계**에서 실행됩니다.
- 최소 지연 시간이 적용되므로, 타이머의 값이 0일지라도 다른 작업의 영향을 받을 수 있습니다.

```javascript
setTimeout(() => {
  console.log('setTimeout');
}, 0);
```

#### 2.2 `setImmediate`

- [poll](https://nodejs.org/en/learn/asynchronous-work/event-loop-timers-and-nexttick#poll) If the *poll* queue is *empty*, one of two more things will happen:
	- If scripts have been scheduled by `setImmediate()`, the event loop will end the **poll** phase and continue the **check** phase to execute those scheduled scripts.
	- If scripts *have not* been scheduled by `setImmediate()`, the event loop will wait for callbacks to be added to the queue, then execute them immediately

- 이벤트 루프의 **Check 단계**에서 실행됩니다.
- I/O 작업 이후 즉시 실행되므로, 일반적으로 `setTimeout`보다 먼저 실행됩니다.
- Node.js 환경에서 비동기 I/O와 결합할 때 유용합니다.

```javascript
setImmediate(() => {
  console.log('setImmediate');
});
```

#### 실행 순서 비교

|**코드**|**결과**|
|---|---|
|`setTimeout(() => console.log('Timeout'), 0); setImmediate(() => console.log('Immediate'));`|`Immediate`, `Timeout`|
|`fs.readFile('file.txt', () => { setTimeout(...); setImmediate(...); });`|`Immediate`, `Timeout`|

`setImmediate`가 `setTimeout`보다 항상 먼저 실행되는 것은 아니며, I/O 작업 여부에 따라 달라질 수 있습니다.

---

### 3. `process.nextTick`와 Promises

#### 3.1 `process.nextTick`

- **Microtask**로 분류됩니다.
- 현재 실행 중인 작업이 완료되기 전에 실행됩니다. 이벤트 루프 단계에 관계없이 우선적으로 실행됩니다.

```javascript
process.nextTick(() => {
  console.log('nextTick');
});
```

#### 3.2 Promises

- `.then`, `.catch`, `.finally`는 **Microtask**로 실행됩니다.
- `process.nextTick`보다는 **뒤**에 실행됩니다.

```javascript
Promise.resolve().then(() => {
  console.log('Promise');
});
```

#### 실행 순서 비교

|**코드**|**결과**|
|---|---|
|`process.nextTick(() => console.log('nextTick')); Promise.resolve().then(() => console.log('Promise'));`|`nextTick`, `Promise`|
|`setTimeout(() => console.log('Timeout'), 0); setImmediate(() => console.log('Immediate'));`|`Immediate`, `Timeout`|

---

### 4. 전체 비교 표

|**API**|**분류**|**실행 시점**|**우선 순위**|
|---|---|---|---|
|`process.nextTick`|Microtask|현재 작업 완료 후, 이벤트 루프 이전|가장 높음|
|Promises|Microtask|현재 작업 완료 후, Microtask Queue에서 처리|`process.nextTick`보다 낮음|
|`setTimeout`|Macrotask|Timers 단계에서 실행|낮음|
|`setImmediate`|Macrotask|Check 단계에서 실행|`setTimeout`보다 높음|

---

### 5. 실습 예제

#### 코드

```javascript
setTimeout(() => console.log('setTimeout'), 0);
setImmediate(() => console.log('setImmediate'));
Promise.resolve().then(() => console.log('Promise'));
process.nextTick(() => console.log('nextTick'));
```

#### 예상 결과

1. `process.nextTick` → Microtask로 즉시 실행.
2. `Promise` → 다음 Microtask Queue에서 실행.
3. `setImmediate` → Check 단계에서 실행.
4. `setTimeout` → Timers 단계에서 실행.

#### 출력

```
nextTick
Promise
setImmediate
setTimeout
```

---

### 6. 결론

- **Microtask**는 Macrotask보다 항상 먼저 실행됩니다.
- `process.nextTick`은 가장 높은 우선 순위를 가지며, 이벤트 루프에 관계없이 실행됩니다.
- `setImmediate`는 I/O 작업 이후 Check 단계에서 실행되므로, 특정 상황에서는 `setTimeout`보다 먼저 실행됩니다.
- `setTimeout`은 지정된 시간 이후에 실행되지만, 최소 지연 시간과 이벤트 루프 단계에 따라 순서가 달라질 수 있습니다.
