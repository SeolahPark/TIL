# 3. Python
**:book: Contents**

- [3. Python](#2-network)
    - [변수와 데이터 타입](#변수와-데이터-타입)
    - [리스트 VS 튜플](#리스트-VS-튜플)
    - [함수 VS 람다 함수](#함수-VS-람다-함수)
    - [GIL(Global Interpreter Lock)](#GIL(Global Interpreter Lock))
    - [제너레이터(generator) VS 이터레이터(iterator)](#제너레이터(generator)-VS-이터레이터(iterator))
    - [메모리 관리](#메모리-관리)
    - [데코레이터(decorator)](#데코레이터(decorator))
    - [예외 처리](#예외-처리)
    - [모듈 VS 패키지](#모듈-VS-패키지)
    - [리스트 컴프리헨션(list comprehension)](#리스트-컴프리헨션(list-comprehension))
    - [가상 환경(virtual environment)](#가상-환경(virtual-environment))
    - [다중 상속(Multiple Inheritance)](#다중-상속(Multiple-Inheritance))
  - [:house: Home](#house-home)
---

### 변수와 데이터 타입
* Python은 동적 타이핑(dynamic typing)을 사용하는 언어로, 변수의 타입을 명시적으로 선언하지 않아도 됩니다. Python의 주요 데이터 타입에는 int, float, str, list, tuple, dict, set 등이 있으며, 각 타입은 고유의 메서드와 속성을 가지고 있습니다.

### 리스트 VS 튜플
* 리스트(List): 가변적(mutable)이며, 요소를 추가, 삭제, 변경할 수 있습니다. 대괄호 []로 정의합니다.
* 튜플(Tuple): 불변적(immutable)이며, 정의 후에는 요소를 변경할 수 없습니다. 소괄호 ()로 정의합니다. 불변성 덕분에 튜플은 더 안전하고 성능이 향상될 수 있습니다.

### 함수 VS 람다 함수
* 함수: def 키워드를 사용하여 정의하며, 여러 줄의 코드를 포함할 수 있습니다.
* 람다 함수: lambda 키워드를 사용하여 정의하며, 한 줄로 작성되는 익명 함수입니다. 간단한 연산이나 기능을 빠르게 정의할 때 유용합니다.

```
def add(x, y):
    return x + y

add_lambda = lambda x, y: x + y
```

### GIL(Global Interpreter Lock)
* GIL은 Python의 메모리 관리와 쓰레드 안정성을 보장하기 위해 존재하는 락입니다. GIL은 한 번에 하나의 쓰레드만 Python 바이트코드를 실행할 수 있도록 제한합니다. 이로 인해 멀티쓰레딩의 성능 이점이 제한될 수 있으며, I/O 바운드 작업에 유리하지만, CPU 바운드 작업에는 적합하지 않습니다.

### 제너레이터(generator) VS 이터레이터(iterator)
* 이터레이터: __iter__()와 __next__() 메서드를 구현한 객체로, 한 번에 하나의 요소를 반환할 수 있습니다.
* 제너레이터: 함수 내에서 yield 키워드를 사용하여 값을 반환하는 특수한 이터레이터입니다. 제너레이터는 일시적으로 실행 상태를 유지하며, 호출될 때마다 이전 상태로부터 재개됩니다.
  
```
def my_generator():
    yield 1
    yield 2
    yield 3

gen = my_generator()
```

### 메모리 관리
* 참조 카운팅: 각 객체에 대한 참조 수를 추적하여, 참조 수가 0이 되면 메모리를 해제합니다.
* 가비지 컬렉터: 순환 참조(circular references)를 처리하기 위해 주기적으로 메모리를 스캔하여 사용할 수 없는 객체들을 해제합니다.

### 데코레이터(decorator)
* 데코레이터는 다른 함수를 수정하거나 확장할 수 있는 고차 함수입니다. 주로 함수의 전후에 코드를 실행하거나, 기존 함수를 감싸는(wrapping) 방식으로 사용됩니다. @ 기호를 사용하여 데코레이터를 적용합니다.
  
```
def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
```

### 예외 처리
* Python은 try, except, else, finally 블록을 사용하여 예외 처리를 수행합니다. try 블록 내에서 예외가 발생하면, 해당 예외에 맞는 except 블록이 실행됩니다. 예외가 발생하지 않으면 else 블록이 실행되며, finally 블록은 예외 발생 여부와 상관없이 항상 실행됩니다.

```
try:
    result = 10 / 0
except ZeroDivisionError:
    print("You can't divide by zero!")
else:
    print("Division successful!")
finally:
    print("This will always execute.")
```

### 모듈 VS 패키지
* 모듈(Module): 하나의 .py 파일로, 관련된 함수, 클래스, 변수 등을 정의하고 포함할 수 있습니다.
* 패키지(Package): 여러 모듈을 포함하는 디렉토리로, __init__.py 파일을 포함하여 Python 패키지로 인식되도록 합니다. 패키지는 모듈을 구조적으로 관리할 수 있는 단위를 제공합니다.

### 리스트 컴프리헨션(list comprehension)
* 리스트 컴프리헨션은 리스트를 간결하게 생성할 수 있는 구문입니다. 일반적인 for 루프보다 더 읽기 쉽고 간결하게 리스트를 생성할 수 있습니다.

```
squares = [x**2 for x in range(10)]
```

### 가상 환경(virtual environment)
* 가상 환경은 Python 프로젝트별로 독립된 패키지와 종속성을 관리할 수 있는 격리된 환경을 제공합니다. 이를 통해 프로젝트 간의 패키지 버전 충돌을 방지할 수 있으며, 개발 환경과 배포 환경을 일치시킬 수 있습니다. venv 모듈을 사용하여 가상 환경을 생성할 수 있습니다.

```
python -m venv myenv
source myenv/bin/activate  # Unix/MacOS
myenv\Scripts\activate  # Windows
```

### 다중 상속(Multiple Inheritance)
* Python은 다중 상속을 지원하며, 하나의 클래스가 여러 부모 클래스로부터 속성과 메서드를 상속받을 수 있습니다. 다중 상속 시, MRO(Method Resolution Order)를 사용하여 메서드 호출 순서를 결정합니다. super() 함수는 다중 상속에서 MRO에 따라 부모 클래스의 메서드를 호출할 때 사용됩니다.
