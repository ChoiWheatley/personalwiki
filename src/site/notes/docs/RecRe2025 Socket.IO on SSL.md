---
{"aliases":null,"tags":null,"description":null,"links":null,"status":null,"title":"RecRe2025 Socket.IO on SSL","created":"2025-01-05T15:58:39","updated":"2025-01-06T16:44:43","dg-publish":true,"permalink":"/docs/RecRe2025 Socket.IO on SSL/","dgPassFrontmatter":true}
---

Socket.IO 연결을 SSL 인증서로 암호화하여 HTTPS, WSS 프로토콜로 통신하고자 한다. 하지만 아래와 같은 오류가 계속 발생한다:

```
WebSocket connection to 'wss://socket.recre.store/socket.io/?uuId=bd6bf4b7-d4f6-49e8-9b84-e2b53818289f&EIO=4&transport=websocket' failed:
```

Client Side `connect_error` listen한 결과를 출력하면..

```javascript
{
  description: 400,
  context: {
    UNSENT: 0,
    OPENED: 1,
    HEADERS_RECEIVED: 2,
    LOADING: 3,
    DONE: 4,
    readyState: 4,
    responseText: '{"code":0,"message":"Transport unknown"}',
    responseXML: '',
    status: 400,
    statusText: null
  },
  type: 'TransportError',
  stack: 'Error: xhr poll error\n' +
    '    at Polling.onError (/home/choiwheatley/workspace/recre-frontend/node_modules/engine.io-client/build/cjs/transport.js:47:37)\n' +
    '    at Request.<anonymous> (/home/choiwheatley/workspace/recre-frontend/node_modules/engine.io-client/build/cjs/transports/polling.js:238:18)\n' +
    '    at Request.Emitter.emit (/home/choiwheatley/workspace/recre-frontend/node_modules/@socket.io/component-emitter/index.js:143:20)\n' +
    '    at Request.onError (/home/choiwheatley/workspace/recre-frontend/node_modules/engine.io-client/build/cjs/transports/polling.js:343:14)\n' +
    '    at Timeout._onTimeout (/home/choiwheatley/workspace/recre-frontend/node_modules/engine.io-client/build/cjs/transports/polling.js:316:30)\n' +
    '    at listOnTimeout (node:internal/timers:581:17)\n' +
    '    at processTimers (node:internal/timers:519:7)',
  message: 'xhr poll error'
}
```

---

## 별도의 스크립트에서 실험

```typescript
import { io } from "socket.io-client";
import { v4 as uuidv4 } from "uuid";

const socket = io(`http://recre.store:3002/catch`, {
  withCredentials: true,
  transports: ['websocket'],
  query: {
    uuId: uuidv4(),
  }
});

socket.on("connect", () => {
  console.log("connected!");
  console.log(socket.id);
});

socket.on("connect_error", (err) => {
  console.log(err);
});

socket.on("disconnect", (reason) => {
  console.log("disconnected.");
  console.log("reason:" + reason);
})
```

**stdout**

```
'connected!'
'HVCYEX-7LsWL52_5AAAB'
```

좋아, 일단 http에서 접속이 되는 것은 확인했으니 HTTPS에서 접속이 되는지 실험해본다.

```typescript
const socket = io(`https://socket.recre.store/catch`, {
  withCredentials: true,
  transports: ['websocket'],
  query: {
    uuId: uuidv4(),
  }
});
```

새로운 에러 메시지를 확인했다

```javascript
{
  description: {
    error: {},
    message: "Hostname/IP does not match certificate's altnames: Host: socket.recre.store. is not in the cert's altnames: DNS:recre.store",
    target: {},
    type: 'error',
    '...': '...'
  },
  context: undefined,
  type: 'TransportError',
  message: 'websocket error'
}
```

GPT한테 물어보니 Subject Alternative Name (SAN)이 SSL 인증서에 포함이 되어있지 않아 TransportError가 발생한 것이라고 한다.

그래서 그냥 SSL 인증서를 새로 발급받았다.

![Screenshot 2025-01-06 at 16.33.04.png](/img/user/docs/assets/Screenshot%202025-01-06%20at%2016.33.04.png)

그리고 기존에 SSL을 지워버렸으니 Proxy Hosts에 SSL을 다시 할당해주었다.

![Screenshot 2025-01-06 at 16.42.01.png](/img/user/docs/assets/Screenshot%202025-01-06%20at%2016.42.01.png)

둘 다 새로 진행하니 Connection이 제대로 진행된다!! 🎉

![Screenshot 2025-01-06 at 16.42.23.png](/img/user/docs/assets/Screenshot%202025-01-06%20at%2016.42.23.png)

![Screenshot 2025-01-06 at 16.43.07.png](/img/user/docs/assets/Screenshot%202025-01-06%20at%2016.43.07.png)

그리고 게임도 정상적으로 커넥션이 이루어진다!!!!

![Screenshot 2025-01-06 at 16.44.23.png](/img/user/docs/assets/Screenshot%202025-01-06%20at%2016.44.23.png)
