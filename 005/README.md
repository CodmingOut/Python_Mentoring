# 5. 함수

이 문서에서는 파이썬의 문법 중 하나인 함수에 대하여 다룬다.

## 5.1. 서론

우리가 프로그램을 만들 때, 리스트의 내용들을 여러번 출력해야한다고 생각해보자.

```python
l = list()

# ...

for i in l:
    print(i)
  
# ...

for i in l:
    print(i)
    
# .....

```

코드가 반복되고있다. 우리 프로그래머들은 코드의 반복을 용납하지 못한다.

가독성도 떨어지고, 코드의 길이도 쓸데없이 길어지기 때문이다.

이러한 경우 '함수(메서드)'를 통해 반복을 제거하고, 코드의 재사용성을 높일 수 있다.

<br>

## 5.2. 파이썬에서의 함수

특정 값 X를 인수로 받으면, 특정 값 Y를 결과로 반환하는 것. 수학의 함수와 유사하다고 보면 된다.

다만 파이썬에서는 반환하는 값이 없을 수도 있다.

하나의 특정 작업을 수행하기 위해 독립적으로 설계된 프로그램 코드의 집합이다.

> 인수 : 함수를 호출할 때 함수 내부에서 사용할 수 있도록 전달하는 데이터

<br>

## 5.3. 우리는 이미 함수를 쓰고 있었다.

우리가 자연스럽게 사용하고 있던 `print()`나 `input()`도 파이썬에서 미리 만들어 제공해 주는 '함수'이다.

이를 내장 함수라고 한다.

<br>

## 5.4. 함수 선언

```python
def 함수명([매개변수1], [매개변수2], [...]):
    함수의 공간
```

파이썬에서 함수는 위와 같이 선언한다.

`def`를 앞에 꼭 적어주어야 한다. 함수를 선언하겠다고 알리는 것이라 이해하면 될 듯하다.

`함수명`은 말 그대로 함수의 이름이다. 호출할 때 사용된다.

`[매개변수1], [매개변수2], [...]`는 함수를 호출할 때 전달되는 인수의 값을 함수 내부에서 사용할 때 쓰일 이름들이다.

`함수의 공간`은 함수가 호출되었을 때 실행될 코드들을 적는다.

> def 로 시작되는 함수를 선언하는 줄 맨 끝에는 무조건 콜론(:)을 붙여주어야 한다!

<br>

## 5.5. 함수 호출

```python
함수명([인수1], [인수2], [...])
```

파이썬에서는 함수를 위와 같이 호출한다.

`함수명`은 선언한 함수의 이름을 그대로 써야한다. 대소문자를 구분한다.

`[인수1], [인수2], [...]`는 함수를 호출할 때 필요한 인수들이다.

함수에 선언된 대로 인수를 넘겨주어야 한다. 선언된 개수와 넘겨준 인수의 개수가 다를 경우 오류가 발생한다.

<br>

## 5.6. 값 반환

```python
def 함수명([매개변수1], [...]):
    # ...
    return 값
```

파이썬에서는 위와 같이 `return`키워드를 사용하여 값을 반환할 수 있다.

```python
변수명 = 함수명([인수1], [...])
```

이렇게 함수에서 반환 된 값은 상수 혹은 변수처럼 사용할 수 있다.

그렇기 때문에 위와 같이 곧바로 변수에 대입하여 사용할 수 있다.

<br>

## 5.7. 예시(1)

```python
def sum(a, b):
    print("- 함수 시작 -")
    result = a + b
    print("- 함수 끝 -")
    return result

c = sum(1, 2)
print(c)

print(sum(3, 4))
```

```python
def multiplicationTablePrint(val):
    for i in range(1, 10):
        print(val, '×', i, '=', val * i)

def multiplicationTableList(val):
    result_list = list()
    for i in range(1, 10):
        result_list.append(val * i)
    return result_list

multiplicationTablePrint(5)

print(multiplicationTableList(7))
```

위의 코드들을 보며 결과가 어떨지 예상해보자.

<br>

## 5.8. 매개변수 지정

함수에 넘겨주는 인수는 선언된 함수의 매개변수 순서에 따라 순서대로 들어간다.

만약 인수가 저장되는 매개변수를 직접 지정하고 싶다면, 인수를 넘겨줄 때 '=' 를 사용하여 직접 지정하면 된다.

```python
def sub(a, b):
    print(a - b)
    
sub(1, 2) # -1
sub(a = 1, b = 2) # -1
sub(b = 1, a = 2) # 1
```

이렇게 매개변수를 지정해주면 무슨 매개변수에 무슨 값이 들어가는지 알 수 있으므로, 가독성이 높아진다.

<br>

## 5.9. 매개변수 기본값 설정

[앞에서 선언된 함수의 매개변수의 개수와 넘겨준 인수의 개수가 다르면 오류가 발생한다고 했다.](#55-함수-호출)

하지만 매개변수에 기본값을 설정해 놓을 경우, 전달하지 않은 인수는 기본값으로 초기화할 수 있다.

```python
def total(a, b = 5, c = 10):
    print(a + b + c)
total(1) # 16
total(1, 2) # 13
total(1, 2, 3) # 6
total(1, c = 3) # 9
```

다만, 매개변수의 기본값 설정은 항상 오른쪽부터 차례대로 명시되어야 한다.

```python
def total(a = 1, b, c = 10):
    print(a + b + c)
total(1) # 1 은 어디로 들어가야 하는가.
```

이렇게는 안 된다는 말이다.

함수에 전달되는 인수는 매개변수의 순서에 따라 순서대로 저장된다.

그래서 인수로 넘겨준 1은 `a`에 저장되며, `b`에 들어간 인수가 없기 때문에, 오류가 발생한다.

<br>

## 5.10. 가변 매개변수

```python
def 함수명(*매개변수):
    # ...
```

함수를 호출할 때, 몇 개의 인자가 전달될지 미리 알 수 없다면, 호출할 때 매개변수의 개수를 정할 수 있도록 선언할 수 있다.

위와 같이 매개변수명 앞에 별 기호를 추가하여 선언한다.

이렇게 들어온 모든 인수는 튜플의 형태로 매개변수에 들어가게 된다.

<br>

```python
def 함수명(**매개변수):
    # ...
```

별 기호를 2개 붙여주면 딕셔너리의 형태로 가변 매개변수를 사용할 수 있다.

<br>

## 5.11. 여러 개의 반환값

```python
def arith(a, b):
    add = a + b
    sub = a - b
    mul = a * b
    div = a / b
    return add, sub, mul, div

a, s, m, d = arith(5, 7)
print(a)
print(s)
print(m)
print(d)
```

우리는 앞에서 결과를 반환할 때, 단 하나의 결과만을 반환했다.

하지만 여러 개의 값을 반환할 수도 있는데, 위와 같이 `return`에서 여러 개의 변수를 콤마(',')로 구분하여 넣으면 된다.

이를 '언패킹(Unpacking)'이라고 한다.

<br>

## 5.12. 리스트 언패킹, 튜플 언패킹

```python
def print_numbers(a, b, c):
    print(a)
    print(b)
    print(c)

print_numbers(10, 20, 30) # 일반적인 사용법

param_list = [10, 20, 30]
print_numbers(*param_list) # 리스트 언패킹

param_tuple = (10, 20, 30) # 'param_tuple = 10, 20, 30' 도 가능
print_numbers(*param_list) # 튜플 언패킹
```

리스트나 튜플의 값 순서대로 각 매개변수에 들어간다고 보면 된다.

그러므로 매개변수의 개수와 리스트나 튜플의 값의 개수가 다를 경우, 오류가 발생한다.

<br>

## 5.13. 딕셔너리 언패킹

```python
def student_info(number, name, grade):
    print('학번:', number)
    print('이름:', name)
    print('학년:', grade)

student_dict = {'number': '10101', 'name' : '누구누구', 'grade' : '3'}
student_info(**student_dict)
```

딕셔너리의 키 값과 같은 이름을 가진 매개변수에 값이 들어간다고 보면 된다.

그러므로 매개변수의 개수와 딕셔너리의 키의 개수도 같아야하고, 매개변수의 이름과 키의 이름도 같아야 한다.

<br>

## 5.14. 람다

```python
def add(a, b):
    return a + b

print(add(1, 2))
print((lambda a, b: a + b)(1, 2))
```

람다는 간단한 함수의 선언과 호출을 하나의 식으로 간략히 표현한 것이다.

람다는 일반 함수와 달리 이름을 가지지 않고, 일반적으로 함수 자체를 인수로 전달받는 함수에서 자주 사용된다.

파이썬에서는 lambda 키워드로 다음과 같이 람다를 정의한다.

```python
lambda 매개변수1, 매개변수2, ...: 매개변수를 이용한 표현식
```

람다는 일반적인 함수와 달리 선언한 그 때에만 사용할 수 있다.

<br>

## 5.15. 예시(2)

```python
person_list = []

def register(name, age, gender = '기타', description = '없음', **features):
    person_dict = {}
    person_dict['name'] = name
    if age is not int:
        person_dict['age'] = int(age)
    else:
        person_dict['age'] = age
    person_dict['description'] = description
    person_dict['features'] = features
    person_list.append(person_dict)

def person_print(name, age, description, features):
    print('name :', name)
    print('age :', age)
    print('description :', description)
    for feature in features.items():
        print(feature[0], ':', feature[1])

register('동그라미', 17, '여자', '평범하다.', 성격 = '조용하다', 좋아하는것 = '초코')
register('세모', 19, '남자', 성격 = '모르겠다', 좋아하는것 = '딱히 쓸말이 없다')
register('네모', 18, description = '항상 보면 누워 있다.', 성격 = '잘 심심해 한다.', 싫어하는것 = '시끄러운 곳')

for person in person_list:
    person_print(**person)
    print()
```

먼저 스스로 이해하려 노력하고, 모르는 것이 있을 경우 멘토에게 물어보자!

<br>

## References

http://tcpschool.com/python2018/python_function_function

https://dojang.io/course/view.php?id=7

https://www.tutorialspoint.com/python3/index.htm
