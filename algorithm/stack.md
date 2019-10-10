## 스택이란?

Last In Out First 방식을 가지고 있는 데이터 저장 방법. 자료가 순서대로 저장되며, 마지막에 들어온 데이터가 먼저 나가는 방법을 말한다. 일상 생활에서 책을 꺼내거나, 웹서핑 후 뒤로가기를 누를 때 스택이 사용된다.

![Stack Structure](https://miro.medium.com/max/1760/1*S2ujFRrOU_GJQOhhQD8LyA.png)



## 기능

- `push`: 데이터를 넣는 기능. 가장 위 (`top`) 에서 데이터를 추가한다.
- `pop`: 데이터를 뽑는 기능. 가장 위 (`top`) 에서 데이터를 제거한다.
- `top`: 제일 위를 가르키고 있는 포인터. `push` `top` 둘 다 `top` 에 있는 데이터만 뽑을 수 있다.
- `peek`: 스택의 가장 위 데이터의 내용을 반환한다.
- `is empty`: 스택이 비어있을 경우 `true` 를 반환한다. 

## 특징

- 가장 위 데이터만 알 수 있다. 
- 문제의 종류에 따라 배열보다 스택에 데이터를 저장하는 것이 더 적합한 방법일 수 있다.

## 사용 사례

- 재귀 알고리즘
- 웹 브라우저 방문 기록
- 실행취소
- 역순 문자열 만들기
- 수식 괄호 검사
- 후위 표기법 계산 

## 스택 구현

python docs 에서는 __리스트__ 를 이용해 스택을 구현한다. python 의 리스트는 __동적 배열__ 이기 때문에 새로운 원소를 _삽입_, _삭제_ 할 수 있다. List 변수에는 첫번째 원소값 주소가 저장되기 때문에, 마지막 원소의 데이터 또한 불러올 수 있다. 

```python
class Stack():
    def __init__(self):
        self.stack = list()

    def push(self, e):
        self.stack.append(e)
    
    def pop(self):
        if self.stack: return self.stack.pop() 

    def isEmpty(self):
        return self.stack if True else False

    def peek(self):
        if self.stack: return self.stack[-1]

```



## 과제

#### valid-parentheses

> 처음에는 좌측괄호 / 우측 괄호 관련 스택을 이용해서 유효성 검사를 하려다, 한쪽 괄호만 사용할 수 있을 것 같아서 아래처럼 짜봄.
>
> 1. 짝 맞을 경우 ->  lstack 값 x > true
> 2. 짝이 안맞을경우 > lstack 값 o > false 
> 3. 오른쪽 짝만 남을 경우 > else 
>
> 교훈: 경우의수를 잘 짜자 

```python
class Solution:
    def isValid(self, s: str) -> bool:
        left = list()
        peek = []
        for i in s:
            if left: 
                peek = left[-1] 
            if (i == "(" or i == "[" or i == "{"):
                left.append(i)
            elif (i == ")"and peek == "(") or (i == "}" and peek == "{") or (i=="]" and peek =="["):
                left.pop()
            else:
                return False
        if (left):
            return False
        else:
            return True
```

고쳐보기

```python
class Solution:
    def isValid(self, s: str) -> bool:
        left = list()
        valid = ""
        for i in s:
            # empty check 
            if left: 
                valid = left[-1] + i
            if (i in "([{"): 
                left.append(i)
            elif (valid =="()" or valid == "{}" or valid == "[]"):
                left.pop()
                valid = ""
            else:
                return False
        if (left):
            return False
        else:
            return True
```

#### climbing-stairs

recursive 코드로 짰으나, 35에서 time exceed 발생

```python
# time exceed code 
class Solution:
    def climbStairs(self, n: int) -> int:
        return self.recursive(n)
        
    def recursive(self, n):
    	if(n == 0 or n == 1):
        	return 1
    	return self.recursive(n-1) + self.recursive(n-2)
```

##### 제출 보고 짠 문제...

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        if (n == 1):
            return 1
        
        first = 1
        second = 2
        
        # python 은 n까지 > n+1 
        for i in range(3,n+1):
            third = first + second
            first, second = second, third 
        
        return second
```



## 알게된 점

삼항 연산자 파이썬 사용법 

```ruby
result = condition ? when True : when False;
```

원래 보통 이런식으로 c, java 는 작성하나 파이썬은 달랐다

```python
result = (a-b) if a == b else (a+b)    # 결과는 a+b = 30
```



## 생각해 봐야 할 점

- stack 에 고정관념이 생기는듯 