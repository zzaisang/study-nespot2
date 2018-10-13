# Scala

## Functional Programming Principles in Scala(강좌)


### Functions & Evaluation

- call-by-name vs call by reference

```scala

def loop:Int = loop //현제 버전에서는 컴파일러 error가 발생합니다. 컴파일러에서 무한 재귀를 막습니다...ㅎㅎ
def first(x:Int, y: Int) = x

first(1,loop) //call by name에서는 루프를 돌지 않고 1을 반환합니다. loop를 나중에 실행하기 때문입니다.
first(1,loop) //call by value에서는 무한 루프가 발생합니다. 함수 실행전 모든 인자를 계산하기 때문입니다.

```

- Scala는 call by value를 사용한다.

- Call by name 처럼 쓰고 싶다면 아래 예제 처럼 사용 하면 된다.

```scala
def constOne(x:Int, f:Int => Int) : Int = x //f는 함수이기때문에 call-by-name처럼 사용 가능
```

- 다시 한번 말하지만 scala는 call-by-value이기 때문에 반환하기전 계산을 먼저 한다.

```
val a = (1+1) + (2+2) // 2 + 4 => 6

def constOne = 1
val one = constOne //javascript와는 다르다. javascript에서는 one은 function이 되지만 scala에서는 constOne의 return값이 one에 반환된다.
```
