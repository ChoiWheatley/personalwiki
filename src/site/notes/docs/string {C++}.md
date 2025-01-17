---
{"dg-publish":true,"permalink":"/docs/string {C++}/","title":"string {C++}"}
---

- [[docs/C++\|C++]]
- [[docs/커스텀 타입을 string으로 변환하는 방법 {C++}\|커스텀 타입을 string으로 변환하는 방법 {C++}]]
- [모두의코드 10-4. C++ 문자열의 모든 것 (string과 string_view)](https://modoocode.com/292)
- [std\:\:basic_string](https://en.cppreference.com/w/cpp/string/basic_string) 문자열을 저장하고 수정하는 기능을 정의해놓은 템플릿 클래스 
- [std\:\:char_traits](https://en.cppreference.com/w/cpp/string/char_traits) 문자(열) 연산들에 대한 기본적인 기능을 정의해놓은 템플릿 클래스. 
	- 대소비교, 할당/이동/복사 연산자, find, 변환 등을 정의한다.
- [[docs/string_view {C++17}\|string_view {C++17}]]
- 

## std::string 과 std:;basic_string과의 차이점을 설명해주세요

`std::string`은 `std::basic_string<char>`입니다. 그러니까, char 타입으로 특수화된 객체인거죠.

## basic_string과 char_traits의 차이점을 설명해주세요

- <https://modoocode.com/292#page-heading-0>
- <https://en.cppreference.com/w/cpp/string/basic_string>
- <https://en.cppreference.com/w/cpp/string/char_traits>

`basic_string`템플릿 클래스는 문자열 데이터가 저장하는 C 스타일 배열을 **보관**하는 기능을 다루고 `char_traits`템플릿 클래스는 문자열들을 어떻게 **연산**하는지에 대한 기능을 다룹니다. 

`char_traits`는 `basic_string`이 사용하는 연산들 중 대소, 동등, 길이 등을 제공합니다. 따라서, 사용자가 이를 오버라이드 하여 별도의 정렬규칙을 적용하거나 대소문자를 무시하는 로직을 짤 수 있습니다.

## Short String Optimization(SSO)에 대해서 설명해주세요

- <https://modoocode.com/292#page-heading-2>
- [[docs/overload operator new {C++}\|overload operator new {C++}]]

basic_string이 저장하는 문자열의 길이는 특정할 수는 없지만 많은 경우 길이가 짧은 문자열을 생성하고 소멸합니다. 이 경우 매번 동적할당과 free를 반복하게 되면 굉장히 비효율적입니다. 따라서 길이가 작은 문자열을 생성하게 될 경우 객체 멤버에 저장해 버리는 최적화를 수행합니다.

하지만 모든 라이브러리가 SSO를 하는 것은 아니며, 이는 구현체에 따라 달라질 수 있어 주의를 요하는 부분입니다.

## multi line string in C++

```cpp
string s = R"(#include <iostream>
int main(void) {
	std::cout << "Hello, world" << std::endl;
	return 0;
}
)";
```

## Encoding

- <https://modoocode.com/292#page-heading-6>
- <https://github.com/nemtrif/utfcpp>

> UTF-8, UTF-16, UTF-32의 차이점이 뭔가요?

UTF-8은 유니코드 문자열을 최소 1바이트, 최대 4바이트로 표현하는 방식을 의미하고 UTF-16은 2 또는 4바이트로 표현하는 방식을 의미하며, UTF-32는 모든 유니코드를 4바이트로 표현하는 방식을 뜻합니다. 웹에서는 효율적으로 문자열을 취급하기 위해 UTF-8을 사용합니다.

한 글자 한 글자의 바이트수가 다르기 때문에 단순 인덱싱으로는 원하는 글자가 나오지 않습니다. 따라서 UTF-16 또는 32 문자열을 사용하거나 유니코드 규칙에 따라 비트마스크를 사용하여 글자의 바이트 수를 직접 파악하는 방법이 있습니다.

**2024-01-14 추가**

- [포프TV / UTF8로 쳐바르자](https://youtu.be/qouu3gMJFJY?si=rYjnM4jbuK3sZ_UV)

UTF8 -> 16 또는 32로 변환해서 편하게 인덱싱 & 사이즈 측정하면 좋지 않을까 생각했으나, 생각해보니 그럼 메모리 공간을 두배 + a 사용하게 되는 것이다. 그래서 포프 아조씨는 자기만의 string 라이브러리를 만들어놓고 유니코드로 작업이 필요할때마다 해당 라이브러리를 불러다 쓴다고 했다.

- [Stack Overflow / utf8 문자열의 `length` 구하기](https://stackoverflow.com/questions/4063146/getting-the-actual-length-of-a-utf-8-encoded-stdstring) => count all first-bytes the one that don't match 10xxxxxx.

```cpp
int len = 0;
while (*s) {
	len += (*s++ & 0b11000000) != 0b10000000;
}
```

## string_view (C++17~)

- [[docs/string_view {C++17}\|string_view {C++17}]]
