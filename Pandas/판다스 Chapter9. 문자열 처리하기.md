## 문자열 처리하기

### 문자열 메서드

|   메서드   | 설명                                                      |
| :--------: | --------------------------------------------------------- |
| capitalize | 첫문자를 대문자로 변경                                    |
|   count    | 문자열 개수 반환                                          |
| startswith | 문자열이 특정 문자로 시작하면 참                          |
|  endswith  | 문자열이 특정 문자로 끝나면 참                            |
|    find    | 찾을 문자열의 첫 번째 인덱스 반환, 실패시 -1반환          |
|   index    | 찾을 문자열의 첫 번째 인덱스 반환, 실패시 ValueError 반환 |
|  isalpha   | 모든 문자가 알파벳이면 참                                 |
| isdecimal  | 모든 문자가 숫자이면 참                                   |
|  isalnum   | 모든 문자가 알파벳이거나 숫자면 참                        |
|   lower    | 소문자로 변경                                             |
|   upper    | 대문자로 변경                                             |
|  replace   | 문자열의 문자를 다른 문자로 교체                          |
|   strip    | 문자열의 맨앞, 맨뒤 빈칸 제거                             |
|   split    | 구분자를 지정해 문자열 나누고, 나눈 값들의 리스트 반환    |
| partition  | split 메서드와 비슷한 역할, 구분자도 반환                 |
|   zfill    | 문자열의 빈 칸을 '0'으로 채우기                           |



파이썬 문자열 메서드 - 실습코드

| 'black Knight'.capitalize()                     | 'Black Knight'            |
| ----------------------------------------------- | ------------------------- |
| 'It's just  a flesh wound!'.count('u')          | 2                         |
| 'Halt! Who goes there? '.startswith('Halt')     | True                      |
| 'coconut'.endswith('b')                         | false                     |
| 'it's just a flesh wound!'.find('u')            | 7                         |
| 'It's just a flesh wound!'.index('scratch')     | ValueError                |
| 'old woman'.isalpha()                           | True                      |
| '37'.isdecimal( )                               | True                      |
| 'I'm 37'.isalnum()                              | False                     |
| 'Black Knight'.lower()                          | 'black knight'            |
| 'Black Knight'.upper()                          | 'BLACK KNIGHT'            |
| 'flesh wound!'.replace('flesh wound','scratch') | 'scratch!'                |
| ' I'm not dead ''.strip()                       | 'I'm not dead'            |
| 'NI! NI! NI! NI!'.split(sep=' ')                | ['NI!','NI!','NI!','NI!'] |
| '3,4'.partition(',')                            | ('3', ',' ,'4')           |
| 'nine'.center(10)                               | ' nine '                  |
| '9'.zfill(with=5)                               | '00009'                   |



#### Join 메서드

: 문자열을 연결해 새로운 문자열을 반환하는 메서드

```python
a = 'Hello'
b = 'Jane'

greetings = ' '.join(a,b)
print(greetings)
```

#### Splitlines 메서드

:여러 행을 가진 문자열을 분리한 다음 리스트로 반환

```python
multi_str = '''Guard: What? Ridden on a horse?
King Arthur: Yes!
Guard : You're using coconuts!
King Arthur: What?
Guard: You've got ... coconuts[s] and you're bangin' 'em together.'''

multi_str_split = multi_str.splitlines()
```

```python
# 인덱스 슬라이싱으로 Guard의 대사만 가져오기

guard = multi_str_split[::2]
print(guard)
```

#### Replace 메서드

```python
guard = multi_str.replace('Guard', '').splitlines[::2]
```



### 정규식 표현

#### 기본 정규식 문법

| 문법  | 실습코드             | 설명                                                     |
| ----- | -------------------- | -------------------------------------------------------- |
| .     | .a                   | 문자(a) 앞에 문자가 1개가 있는 패턴 찾기                 |
| ^     | ^I like              | 문자열의 처음부터 일치하는 패턴찾기                      |
| $     | on$                  | 문자열의 끝부분부터 일치하는 패턴찾기                    |
| *     | n\d*                 | n이후  숫자가 (\d)가  0개 이상인 패턴 찾기               |
| +     | n\d+                 | n이후 숫자가(\d)가 1개 이상인 패턴찾기                   |
| ?     | apple?               | ? 앞의 문자가 있거나 없는 패턴 찾기                      |
| {m}   | n\d{2}               | n 이후 숫자가(\d) 2({2})개있는 패턴찾기                  |
| {m,n} | n\d{2, 4}            | n 이후 숫자가 2개{2} 이상 4개{4} 이하인 패턴 찾기        |
| \     | \* , \?, \+          | *,?,+ 와 같은 특수 문자를 검색할 때 이스케이프 문자 사용 |
| []    | [cfh]all             | c,f,h 중 1개를 포함하고 나머지 문자열이 all인 패턴찾기   |
| \|    | apple \| application | apple 이나 application 중 하나만 있는 패턴 찾기          |
| ()    | (\d+)-(\d+)-(\d+)    | ()에 지정한 패턴 찾기                                    |
|       |                      |                                                          |

 #### 정규표현식 특수문자

| \d   | 숫자 1개 ([0-9])               |
| ---- | ------------------------------ |
| \D   | 숫자 이외의 문자 1개           |
| \s   | 공백이나 탭 1개를 의미         |
| \S   | 공백 문자 이회의 문자 1개 의미 |
| \w   | 알파벳 1개를 의미              |
| \W   | 알파벳 이외의 문자 1개를 의미  |



#### 정규식 표현 - 메서드

| 함수        | 실습 코드                            | 설명                                                       |
| ----------- | ------------------------------------ | ---------------------------------------------------------- |
| search()    | m = re.search('\d{4}',test)          | 첫번째로 찾은 패턴의 양끝 인덱스 반환                      |
| match()     | m = re.match('\d{4}', test)          | 문자열의 처음부터 검색하여 찾아낸 패턴의 양 끝 인덱스 반환 |
| fullmatch() | m.= re.fullmatch('\d+\s\d+\d+',test) | 전체 문자열이 일치하는 지 검사                             |
| split()     | m=re.split('\s',test)                | 지정한 패턴으로 잘라낸 문자를 리스트로 반환                |
| findall()   | m=re.findall('\d{4}', test)          | 지정한 패턴을 찾아 리스트로 반환                           |
| finditer()  | m=re.finditer('\d{4}', test)         | 지정한 패턴을 찾아 iterator를 반환                         |
| sub()       | print(re.sub('\s','-',test))         | 첫번째 인자로 전달한 값을 두번째 인자로 전달한 값으로 교체 |



###### 정규표현식으로 전화번호 패턴 찾기

```python
import re

tele_num = '1234567890'

m = re.match(patter='\d{10}',string=tele_num)

if m:
	print('match')
else:
	print('no match')
```

```
tele_num_spaces ='123 456 7890'
p = '\d{3}\s?\d{3}\s?\d{4}'
m = re.match(pattern=p, string=tele_num_spaces)
```

