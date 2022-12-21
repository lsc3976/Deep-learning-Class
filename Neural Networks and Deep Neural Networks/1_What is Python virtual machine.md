

# 파이썬의 가상머신


---
<br>

## 1. 가상 머신이란? (Virtual Machine)

> 물리적 머신을 에뮬레이트하는 기본 운영 체제 위에 있는 높은 수준의 추상화 머신

프로그램을 작성할때는 대표적으로 컴파일러 방식과 인터프리터 방식이 있다.

<br>

__컴파일 언어__ 

1. 소스 코드 전체를 실행가능한 target CPU의 기계어로 컴파일 한다.
2. 링커는 필요한 라이브러리를 가져오고 여러개의 Object 파일을 묶어 실행 파일을 생성한다.
3. 프로그램을 실행하고 데이터를 입력하면 결과 값을 도출한다.


__인터프리터 언어__

1. 소스코드를 중간 코드(intermediate code)/바이트 코드(byte code)로 변환한다.
2. 이 바이트 코드를 가상머신 소프트웨어로 각 행마다 실행할 때 interpret한다.

![image1.jpg](https://velog.velcdn.com/images%2Fandthensome%2Fpost%2Fbdd46076-fd22-4911-8ca1-361244b1dbd1%2FCompilervrsinterpreter.jpg)




| 컴파일러 방식 | 인터프리터 방식 |
|----|----|
| 프로그램 전체 번역 | 실행하는 행 단위 번역 |
| object프로그램 생성 메모리사용 | 실행 결과만을 표시 |
| 실행 속도 빠름 | 실행 속도 느림|
| 프로그램 일부 수정시 전체 컴파일 | 큰 기억 장치가 필요없고 실행이 간단함 |


<br>
이러한 인터프리터 언어에서 중간코드(바이트코드)를 해석하고 실행시키는것이 바로 가상머신 이다.


<br><br>
 

## 2. 가상 머신을 사용하는 이유

* 여러 작은 워크로드를 하나의 물리적 컴퓨터로 통합하여 효율성을 높이고 비용을 절감한다.
* 새로운 운영 체제로 마이그레이션 하지 않고도 동일한 플랫폼을 여러 운영 체제 및 하드웨어 아키텍처에서 실행할 수 있다.
* 휴대성이 뛰어나 네트워크 내의 물리적 컴퓨터와 온프레미스 및 클라우드 환경 사이를 자유롭게 이동할 수 있다.
* 하드웨어를 더 적게 유지 관리하고 리소스를 더 빠르게 프로비저닝하며 다운타임을 줄여 시간을 절약할 수 있다.




<br><br>

## 3. 가상 머신의 유형

가상 머신(VM)은 물리적인 CPU에 의해 처리되는 동작을 흉내낼 수 있어야 한다.

따라서 일반적으로 VM은 아래의 개념들을 구현(포함)해야 한다.

* 소스 코드를 VM이 실행할 수 있는 바이트 코드로 변환
* 명령어와 피연산자를 포함하는 데이터구조
* 함수를 실행하기 위한 콜스택
* 다음 실행할 명령어를 가리키는 IP(Instruction Pointer)
* 가상 CPU
* Fetch
* Decode
* Execution

위 개념을 구현하는 방법은 크게 2종류가 있다

<br>

### __스택 기반의 VM__


![image2.webp](https://www.korecmblog.com/static/8e043c869194a515a101e1a79ffb0cf6/d00b9/image-20210424161514958.webp)

예를 들어 ```13 + 20 + 7 ```을 계산한다고 하자.<br>
CPU의 덧셈 연산은 2개의 피연산자를 다루므로 20 + 7 를 계산한 결과를 13 과 더해야만 한다.<br>
스택 기반의 VM은 이 결과를 바로 스택에 저장한다.<br>

위 그림을 보면, 20과 7을 더하기 위해서 두 피연산자를 스택에서 꺼낸다.<br>
꺼낸 결과를 가지고 계산한 뒤에 다시 결과를 스택에 넣는 것을 알 수 있다.

이와 같이 값을 가져오고, 계산하고, 저장하고, 반환하는 과정에서 스택을 활용하는 것을 알 수 있다. <br>
그 덕분에 명령어들은 매우 간단하지만 간단한 코드를 수행하기 위해 꽤나 많은 Byte Code가 필요한 것을 알 수 있다. <br>

<br>

| 장점 | 단점 |
|-----|------|
| 하드웨어에서 직접 다루지않으므로 덜 의존적이다 | 스택 오버헤드가 존재 |
| 명령어의 길이가 짧다 | 명령어의 수가 많고 최적화를 할수 없다. |

<br>


### __레지스터 기반의 VM__


![image3.webp](https://www.korecmblog.com/static/ad5c2b19156429c2e12c0f0cdf1b1e46/d00b9/image-20210424161523287.webp)


예를 들어 ``` 5 + 30 + 40``` 을 계산한다고 하자. <br>
레지스터 기반의 VM은 그림처럼 피연산자를 레지스터에서 가져와서 계산하고, 결과를 다시 레지스터에 저장한다.

| 장점 | 단점 |
|-----|------|
| 스택을 사용하지않아 스택에 대한 오버헤드가 없다 |  |
| 명령어의 수가 적다  | 명령어의 길이가 길어진다. |



<br>
<br>


## 4. 마치며

<br>

현대의 많은 사람들이 소스 코드 작성의 편의성과 상황에 구애받지않고 <br>
범용성높은 프로그래밍환경을 위해 가상머신을 활용하는 인터프리터 언어를 사용한다. <br>
사실 [논문](https://www.usenix.org/legacy/events/vee05/full_papers/p153-yunhe.pdf)(Virtual Machine Showdown: Stack Versus Registers)에 따르면, <br>
레지스터 기반의 VM이 스택 기반 VM보다 명령어 사이즈는 25% 크지만 명령어 수는 47% 적다고 한다. <br>
더 적은 명령어를 가져옴으로써 실제 컴퓨터 부하를 줄일수 있다면 <br>
코드 사이즈를 조금 늘리더라도 명령어를 줄이는 것이 더 효율적이라고 할수있겠다. <br>

그럼에도 스택 기반의 VM을 사용하는 이유는 레지스터 기반 VM보다 하드웨어(레지스터 개수,사이즈,CPU)에 적게 의존하기 때문이다. <br>
파이썬 또한 스택을 기반으로 연산을 수행하는 스택 가상머신을 채택함으로써 가장 높은 프로그래밍 언어 점유율을 보여주며 유용성을 입증하고있다. <br>



---


사진 출처 : [1](https://velog.io/@andthensome/%EC%BB%B4%ED%8C%8C%EC%9D%BC%EB%9F%AC-%EC%9D%B8%ED%84%B0%ED%94%84%EB%A6%AC%ED%84%B0#%EC%BB%B4%ED%8C%8C%EC%9D%BC%EB%9F%AC--%EC%9D%B8%ED%84%B0%ED%94%84%EB%A6%AC%ED%84%B0) [2](https://www.korecmblog.com/jvm-stack-and-register/) <br>