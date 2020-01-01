# pytest

python 기반 테스트 프레임워크. 작은 테스트를 쉽게 만들 수 있다!  클래스 기반인 __unittest__ 보다 간결하게 사용할 수 있다. 이 장점으로 python 알고리즘 테스트에 쓰는게 유닛테스트보다 좋을 것 같아서 찾아봄!



## getting started

```python
$ pip install -U pytest
```

바로 깔림. 파일 이름은 `test` 여야한다.  `pytest` 를 치면 테스트 코드가 실행된다. 여러 파일을 테스트하고싶다면 파일에 `test_*.py` 또는 `*_test.py` 로 작성하면 된다. 



```python
$ pip install pytest-watch
```

`ptw` 명령어를 치면 시작하는데, 테스트 파일이 바뀌면 자동으로 테스트를 실행해준다. 



## example

알고리즘 짠 코드 

```python
input = []
output = 2

def test_simple():
    assert solution(input) == expected


def solution(nums):
    """code"""
    return 11

if __name__ == "__main__":
    solution(input)
```



 여러 테스트 케이스를 하고싶을때는 아래와 같이 사용한다

```python
def solution(numbers):
    ans = 0
    for i in range(len(numbers)):
        temp = 1
        for j in range(len(numbers)):
            if i == j:
                temp *= numbers[j] + 1
            else:
                temp *= numbers[j]
        print(temp)
        ans = max(ans, temp)
    return ans
```

