#### DATA STRUCTURE 

> 데이터는 컴퓨터에 어떻게 저장될까?

- storegy
  - 데이터가 영구히 저장됨
  - HDD, SDD, USB, CD
  - 용량 크지만 속도 느림
- memory
  - 데이터가 저장되는 위치가 random
  - RAM
  - 각 칸마다 주소값이 지정되어 있음

---

#### DATA TYPE

>데이터를 0과 1로 표현해서 메모리에 저장하는 방법

's' 	= char		
'sas' 	= string	=> Memory
12.5 	= float		
10 		= int		

- data type없이 저장하게되면 cost가 많이 든다.

- data type의 한계
  -> user-defined data type
  - class를 이용해 나만의 데이터 타입 선언

1. 선형자료구조

  - list
  - stack 
  - linked list   (동적연결리스트)
  - queue

2. 비선형자료구조

  - graph
  - tree (나무를 뒤집어 놓은 모양)

---

#### 추상데이터타입(ADT-abstract data type)


>추상: 여러 가지 사물이나 개념에서 공통되는 특성이나 속성 따위를 추출하여 파악하는 작용.
>structured data + operation

- 데이터가 가지고 있는 공통점
  - 데이터가 가지고 있는 구조
  - 데이터가 가지고 있는 연산
- 스마트폰에서 자주 쓰이는 데이터 구조
  - 개별적인 특징을 지우고 데이터 구조의 특징을 도출
  - factorial
  - 재귀 구현 위해 만들어짐
  - 최대 5000