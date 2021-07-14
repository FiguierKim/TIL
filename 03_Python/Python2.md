## 파이썬 데이터 유형

### 내장 데이터

텍스트 유형 - `str`

숫자 유형 - `int` (정수 or 길이가 무제한인 양수 또는 음수),`float`(소수를 포함한 양수나 음수), `complex`(복소수)

시퀀스 유형 - `list`, `tuple`, `range`

매핑 유형 - `dict`

세트 유형 - `set`, `frozenset`

바이너리 유형 - `bytes`, `bytearray`, `memoryview`



## 캐스팅

### 변수 유형 지정

- int()
- float()
- str()



## 슬라이싱

문자열의 일부를 반환하려면 시작 인덱스와 끝 인덱스를 `:` 으로 구분

```python
s = 'This is Python'

print(s[1:4])
> his

# 시작 인덱스 생략 가능
print(s[:1])
> T

# 끝 인덱스 생략 가능
print(s[11:])
> hon

```



## 문자열 수정

`upper()` - 문자열을 대문자로 반환

`lower()` - 문자열을 소문자로 반환

`strip()` - 문자열 시작부분이나 마지막 부분의 공백 제거

`replace()` - 문자열 변환

`split()` - 지정한 구분 기호를 기준으로 문자열 분할



