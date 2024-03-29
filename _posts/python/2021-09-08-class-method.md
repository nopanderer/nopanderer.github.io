---
layout: post
title: "[Python] 클래스 메서드, 정적 메서드"
categories: python
---

* this unordered seed list will be replaced by toc as unordered list
{:toc}

## 클래스 메서드

- `@classmethod` 데코레이터를 사용해서 클래스 메서드로 선언
- 이 때, 첫번째 인자로 클래스 인스턴스가 아닌 클래스 자체가 넘어오게 됨. 관행적으로 `cls` 라는 이름을 붙임
    - 클래스 속성에 접근하거나 다른 클래스 메서드 호출 가능
- 팩토리 메서드를 작성할 때 유용하게 사용

```python
class User:
    def __init__(self, email, password):
        self.email = email
        self.password = password

    @classmethod
    def fromTuple(cls, tup):
        return cls(tup[0], tup[1])

    @classmethod
    def fromDictionary(cls, dic):
        return cls(dic["email"], dic["password"])
```

## 정적 메서드

- `@staticmethod` 데코레이터를 사용해서 정적 메서드로 선언
- 인스턴스 메서드나 클래스 메서드와 달리 첫번째 매개 변수가 할당되지 않음
    - 따라서 정적 메서드 내에서는 인스턴스/클래스 속성에 접근 및 호출이 불가
- 보통 유틸리티 메서드를 구현할 때 많이 사용

```python
class StringUtils:
    @staticmethod
    def toCamelcase(text):
        words = iter(text.split("_"))
        return next(words) + "".join(i.title() for i in words)

    @staticmethod
    def toSnakecase(text):
        letters = ["_" + i.lower() if i.isupper() else i for i in text]
        return "".join(letters).lstrip("_")
```

## 참고

- <https://www.daleseo.com/python-class-methods-vs-static-methods/>
