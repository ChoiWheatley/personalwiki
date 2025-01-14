---
{"aliases":null,"tags":null,"description":null,"links":["[[0018.1.1 NestJS Troubleshooting]]"],"status":null,"title":"NestJS DI 컨테이너의 스코프 분리 문제","created":"2025-01-13T14:18:17","updated":"2025-01-13T14:18:27","dg-publish":true,"permalink":"/docs/NestJS DI 컨테이너의 스코프 분리 문제/","dgPassFrontmatter":true}
---


> 두 군데에서 주입받은 같은 타입의 객체가 알고보니 서로 다른 인스턴스인 경우

### 재연

다음 테스트 코드를 작성하면서 발견한 문제이다:

```typescript
  beforeEach(async () => {
    const module: TestingModule = await Test.createTestingModule({
      imports: [EventEmitterModule.forRoot()],
      providers: [
        MatchDepositUseCase,
        EventEmitter2,
      ],
    }).compile();
    eventEmitter = module.get(EventEmitter2);
    matchDepositUseCase = module.get(MatchDepositUseCase);
  });
```

이때 MatchDepositUseCase는 `eventEmitter: EventEmitter2` 를 주입받고 있기 때문에 아래와 같은 테스트에서 두 eventEmitter의 동등성을 비교했다:

```typescript
  it('should have same identity', () => {
    expect(matchDepositUseCase['eventEmitter']).toBe(eventEmitter);
  });
```

하지만 놀랍게도 위의 테스트는 실패한다. jest가 NestJS 테스트 모듈을 생성하면서 mock 객체를 만들어 주입한걸까?

### 문제의 원인

`imports` 에서 `EventEmitterModule.forRoot()`가 `EventEmitter2` 객체를 전역범위에서 사용할 수 있도록 DI 컨테이너에 등록한다. 하지만 `providers: [EventEmitter2]`가 **재정의** 되었기 때문에 새로 정의된 인스턴스를 사용하게 된다. 따라서 `eventEmitter` 변수는 재정의된 객체를, `matchDepositUseCase['eventEmitter']`는 전역 객체를 사용하게 되어 위의 테스트 코드가 실패하게 된다.

### 문제의 해결방법

둘 중 하나만 사용하면 문제가 해결이 된다. 그동안 모듈 임포트와 프로바이더 주입을 항상 같이 해왔음에도 문제가 없던 이유는, 프로바이더들이 전부 무상태였기 때문에 서로 다른 인스턴스를 가지더라도 문제가 되지 않았던 것이다. 하지만 하나의 인스턴스로 충분히 해낼 수 있는 일을 굳이 여러개를 만들어 메모리 공간을 낭비할 필요는 없으니까 임포트를 하여 모듈의 모든 프로바이더를 주입받을 건지, 하나의 프로바이더만 구체적으로 지목할 것인지를 똑똑하게 결정해야 할 것이다.
