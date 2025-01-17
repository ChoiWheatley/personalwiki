---
{"dg-publish":true,"permalink":"/docs/JS {basic} {types} {for in, for of} {spread} {destructuring}/","title":"20230530 JS {basic} {types} {for in, for of} {spread} {destructuring}"}
---

[JS DeepDive 4000줄이나 되는 복습용 총체](https://github.com/weniv/BackendOrmi/blob/main/JavaScript/%EB%B3%B5%EC%8A%B5.md)
- 웹의 ~~3~~ 4대 요소
	- HTML
	- CSS
	- JS
	- WASM
- JS 삽입위치는 주로 head, body의 맨 끝 | 내부 스크립트는 `<script>` 태그 안에 코드가 있고 | 외부 스크립트는 `<script src="____"></script>` 로 링크함.
- 세미콜론 안 붙여도 돌아감. 근데 걍 붙여주는 에디터 있음.
- 엄격모드 | `"use strict"`를 사용하면 ES5부터 나오는 변경사항과의 충돌을 막을 수 있다.
	- class는 ES6때 나왔기 때문에 엄격모드가 기본이다.
- 변수 이름규칙 | `$`는 주로 도큐먼트 원소를 지칭할 때 prefix로 쓰고, `_`는 for문에서 안쓰는 변수일 때 단일 underscore로 사용.
- `var, let, const` | `var`: 함수레벨 스코프, shadowing 🙆 | `let`: 블록레벨 스코프, shadowing 🙅 | `const` : 블록레벨 스코프, shadowing 🙅, constant
- 연산자
	- `??`: nullish 병합 연산자: 값이 없으면 그 뒤에 오는 값을 집어넣어.
	- `typeof`: 현업에서는 별도의 타입체크 함수를 만들어 쓴다는거. 왜냐면 별에별게 다 `Object`로 튀어나와서...
	- 관계 연산자 `in`: 키만 가지고 판단한다는거 주의
- Types
	- 원시타입, 참조타입
	- `Number` | `toString`, `parseInt`
		- `Math`
		- `NaN`
		- `Infinity`, `-Infinity`
	- `String` | ``length, indexOf, includes, slice, splice, split, substring, toLoserCase, toUpperCase, trim, replace, concat, repeat``
	- `Boolean` | `true, false`
	- `undefined`타입의 유일한 값인 `undefined`
	- `null`을 오브젝트로 만든 건 실수였다고...
	- `Array`는 `typeof`로 확인해보면 오브젝트로 나온다...
		- forEach: 도큐먼트원소를 순회할 때 쓰지 말 것 => `NodeList`의 forEach이라서 호환성이 안 좋음 => `...` 전개문법을 사용하여 Array로 변환 후 forEach할 것.
		- length, map, filter, push, pop, slice, reduce, join, indexOf, includes, find,  every, some, fill, shift, unshift, reverse, sort
		- concat: `[10].concat([10])`
		- reduce를 사용하여 sum 구하기: `[1,2,3,4,5].reduce((a,b) => a + b, 0)`
		- sort는 디폴트로 lexicographical order이기 때문에 `[1,11,2,22,3,33].sort((a, b) => a - b)` 식으로 작성해야함.
	- `Object` 
		- 객체 자체는 iterable하지 않다. 그러니까 파이썬처럼 `of` 문법을 사용하여 작성하는게 불가. `in` 문법을 사용하여 키값을 순회한다면 가능. 

		```js
		myObject = {
		  지역이름: "전국", // key : value(2개의 집합을 가리켜 객체 프로퍼티)
		  확진자수: 24889,
		  격리해제수: 23030,
		  사망자수: 438,
		  십만명당발생율: 48.0,
		};
		
		for (const k in myObject) {
		  console.log(`(${k}: ${myObject[k]})`);
		}
		```

	- Map: object
		- set, get, has, delete, size, keys, values, entries
	- Set: object
		- add, delete, has, size
- LOOPS
	- 구글 컨벤션에서는 `for in` 보다는 `for of`를 권고하고 있다.
- Functions
- Classes
	- 원래 클래스는 없었다. ES6 전까지는 생성자(`constructor`)만 있었다.
	- 상속은 자바와 똑같이 `extends`를 사용함.
- 예외처리
	- try - catch - finally 도 자바와 똑같
- 전개구문 (spread)

	```js
	function f(...x){
	    return x;
	}
	
	f(1, 2, 3, 4, 5)
	```

	```js
	let arr1 = [1, 2, 3, 4];
	let arr2 = [10, 20, 30, 40];
	let arr3 = [100, ...arr1, 200, ...arr2, 300]
	let arr4 = [100, arr1, 200, arr2, 300]
	console.log(arr3)
	Math.max(...arr3);
	let [a, b, c, ...d] = [10, 20, 30, 40, 50, 60, 70]
	```

- 구조분해할당 (destructuring, unpacking)

	```js
	for (let [[i, j], k] of [[[1, 2], 2], [[1, 2], 4]]) {
	    console.log(i, j);
	}
	```

- Fetch
	- 비동기 네트워크 통신을 구현하기 위해 사용하는 Web API
	- `fetch(<URL>).then(<callback_response>)`
	- `response.json()`, `response.text()`, `response.blob()`
	- then then then... 구문을 사용하기 싫으면 fetch 앞에 `await`를 사용하면 response를 가져올 수 있다.

	```js
	async function printjson() {
	  const response = await fetch(`http://test.api.weniv.co.kr/mall`);
	  const json = await response.json();
	
	  console.log(json);
	}
	printjson();
	```

- DOM
	- Document Object Model API | DOM과 JS는 별개임. 
	- `document.getElementById`
