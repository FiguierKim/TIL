# Day 14

Collection API

> 데이터들을 저장해서 사용할 수 있음
>
> 타입과 갯수의 제한없이 데이터들을 저장 가능
>
> List, Set, Map이 있다

**Set** - 저장되는 값의 중복이 불가능, 저장된 인덱스 번호를 통한 접근 불가능

**List** - 저장되는 값의 중복이 가능, 저장된 인덱스 번호를 통합 접근 가능

**Map** - 데이터의 이름과 값 저장 가능, 이름 중복 불가능, Set 또는 Collection 어느것도 상속안함



## Set

**HashSet** - 동기화 안됨, HashMap보다 느리다

**TreeSet** - 동기화 안됨, 키가 정렬된다



## Map

**HashMap** - 동기화 안됨, 가장 빠르다, `nul`l 값 가능

**HashTable** - 동기화 가능, `null` 값 불가능

**TreeMap** - 동기화 안됨, 키가 정렬된다



## List

**ArrayList** - 동기화 안됨, `null` 값 허용

**LinkedList** - 동기화 안됨

**Vector** - 동기화 가능

**Stack** - 동기화 가능, LIFO 가능

