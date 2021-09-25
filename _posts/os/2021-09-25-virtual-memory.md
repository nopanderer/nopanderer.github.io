---
layout: post
title: "[OS] 가상 메모리"
categories: os
---

* this unordered seed list will be replaced by toc as unordered list
{:toc}

## 가상 메모리

- 실제 메모리 크기와 상관없이 메모리를 이용할 수 있도록 가상의 메모리 주소를 사용하는 것
- 페이징(고정 분할) 혹은 세그멘테이션(가변 분할) 기법이 있음

### 이점

- 실제 메모리 크기보다 더 큰 공간을 사용할 수 있음(보조 저장장치 사용)
- 가상의 주소 공간을 이용해 논리적인 연속성을 제공
- 물리 메모리 주소 공간을 알 필요가 없음

### 페이징

- 고정 크기로 분할된 페이지를 통해 가상 메모리를 관리하는 기법
  - 페이지: 가상 메모리를 고정 크기로 나눈 블록
  - 프레임: 실제 메모리를 페이지와 같은 크기로 나눈 블록(=페이지 프레임)
- 가상 메모리의 페이지가 하나의 프레임을 할당받으면 물리 메모리에 위치하게 됨
- 프레임을 할당받지 못한 페이지는 외부 저장장치에 저장

#### 페이지 테이블

- 프로세스의 페이지 정보를 저장하고 있는 테이블
- 페이지에 매핑되는 프레임을 찾을 때 참조
- Demand Paging: 요청할 때 해당 페이지를 메모리로 가져오는 것
- Page Fault: 요청한 페이지가 메모리에 존재하지 않는 경우

![Page Table](/assets/img/page-table.png)


## 참고

- <https://gamedevlog.tistory.com/85>