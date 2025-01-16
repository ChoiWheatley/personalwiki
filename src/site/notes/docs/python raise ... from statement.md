---
{"dg-publish":true,"permalink":"/docs/python raise ... from statement/","title":"python raise ... from statement"}
---


## TL;DR

The "raise from" statement in Python is used to raise a new exception while preserving the context of the original exception. This allows you to provide additional information about the error that occurred, making debugging easier.

```python
try:
    raise ValueError
except Exception as e:
    raise IndexError from e
```

## PEP-3134

<http://legacy.python.org/dev/peps/pep-3134/>

다음 제안에서는 세가지 dunder attributes들이 포함된다:

- `__context__`: 암묵적으로 체이닝된 예외. 예외가 처리되지 않고 새 예외가 발생하면 자동으로 설정되는 attribute
- `__cause__`: 명시적으로 체이닝된 예외, 새로 발생한 예외가 다른 예외로 인해 발생했음을 나타낸다. 
	- `raise IndexError from e` 구문을 사용해 설정할 수 있다.
- `__traceback__`: 백트레이스와 관련한 정보 (예외 발생시 출력될 스택프레임)

이 제안 덕분에 Python 3.0 이후부터 하나의 예외가 다른 예외의 의해 발생했음을 명시적으로 표현할 수 있게된다.

## 예제 1: `raise ... from ...`으로 명시적 예외 체인 설정 (`__cause__`)

```python
try:
    # 첫 번째 예외 발생
    raise ValueError("원래 예외")
except ValueError as e:
    # 두 번째 예외를 발생시키며 원래 예외를 명시적으로 연결
    raise RuntimeError("새로운 예외") from e
```

### 출력 결과:

```
Traceback (most recent call last):
  File "<stdin>", line 3, in <module>
ValueError: 원래 예외

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "<stdin>", line 6, in <module>
RuntimeError: 새로운 예외
```

- **설명**:  
  - `raise RuntimeError("새로운 예외") from e`는 `ValueError`가 `RuntimeError`의 직접적인 원인임을 나타냅니다.
  - 이로 인해 출력에 `The above exception was the direct cause of the following exception:` 메시지가 추가됩니다.
  - 이 관계는 `__cause__` 속성에 저장됩니다.

---

## 예제 2: 암묵적 연결 (`__context__`)

```python
try:
    # 첫 번째 예외 발생
    raise KeyError("첫 번째 예외")
except KeyError:
    # 두 번째 예외 발생 (암묵적으로 연결됨)
    raise TypeError("두 번째 예외")
```

### 출력 결과:

```
Traceback (most recent call last):
  File "<stdin>", line 3, in <module>
KeyError: '첫 번째 예외'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "<stdin>", line 6, in <module>
TypeError: 두 번째 예외
```

- **설명**:  
  - `TypeError`는 `KeyError` 처리 중에 발생했으므로 암묵적으로 연결됩니다.
  - 이 관계는 `__context__` 속성에 저장되며, 출력에 `During handling of the above exception, another exception occurred:` 메시지가 추가됩니다.

---

## 예제 3: `__suppress_context__ = True`로 이전 예외 억제

```python
try:
    # 첫 번째 예외 발생
    raise IndexError("첫 번째 예외")
except IndexError:
    # 이전 예외를 억제하고 새로운 예외 발생
    ex = ValueError("두 번째 예외")
    ex.__suppress_context__ = True
    raise ex
```

### 출력 결과:

```
Traceback (most recent call last):
  File "<stdin>", line 7, in <module>
ValueError: 두 번째 예외
```

- **설명**:  
  - `__suppress_context__ = True`를 설정하면 이전에 발생한 `IndexError`가 출력되지 않습니다.
  - 이는 불필요한 디버깅 정보를 제거하고 새로운 예외만 표시하고 싶을 때 유용합니다.

---

**요약**

- **명시적 연결**: `raise ... from ...` → `__cause__`
- **암묵적 연결**: 처리 중 다른 예외 발생 → `__context__`
- **출력 억제**: `__suppress_context__ = True` → 이전 예외 숨김

이 기능은 디버깅 시 문제의 원인을 더 명확히 파악하는 데 매우 유용합니다! 😊
