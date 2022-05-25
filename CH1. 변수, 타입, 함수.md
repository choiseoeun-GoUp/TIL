
## 앞선 기초지식!

자바스크립트의 선언에는 3가지 방법이 있습니다.

> 1\. var : 변수를 선언. 추가로 동시에 값을 초기화  
> 2\. let : 블록 스코프 지역변수를 선언. 추가로 동시에 값을 초기화  
> 3\. const : 블록 스코프 읽기 전용 상수를 선언.

이제부터 오늘의 코드스테이츠 2일 차 TIL정리 시작합니다.

## CH1. 변수 (Variable)💁🏻

#### **1\. 변수란?**

> **변수**란 **어떤 값(데이터)을 담는 저장소(메모리)의 이름**입니다. 


#### **2\. 변수의 사용방법**

 ㄱ. 변수의 선언

-   변수를 선언한다는 것은 데이터 보관함에 데이터를 넣을 **공간을 확보**하는 것을 의미합니다.
-   예를 들어 let age; 를 age변수를 선언했다고 합니다.

ㄴ. 변수의 할당 

-   변수의 할당은 데이터가 들어있는 보관함에 **데이터를 저장**하는 것입니다.
-   age=25;
-   **지정된 초기 값 없이** var 혹은 let 문을 사용해서 선언된 변수는 **undefined** **값**을 갖습니다.

> 변수를 선언하고 할당하는 가장 큰 이유는 **반복적으로 사용하는 값을 데이터 보관함에 넣어 두었다가 편하게 꺼내서 사용**하기 위함입니다. 즉 , **재사용**을 위함

여기서 포인트!

```
let favoriteFruit = '사과'
```

**let으로 favorite을 선언하고, '사과'를 할당합니다.**

여기서 = 은 할당 연산자입니다. 같다는 의미의 산술연산자는 ===입니다.  (기술면접 시 이러한 사소한 것도 논리적으로 설명할 것)

## CH2. 타입 (Type)💁🏻

대표적인 데이터 타입 8가지

1.  **Boolean** : 논리 요소를 나타내며 true와 false를 반환하는 객체입니다. 
2.  **Null** : null하나의 값만 가질 수 있습니다. **어떤 값이 의도적으로 비어있음**을 표현하며 **boolean 연산에서는 거짓**으로 취급합니다. 
3.  **Undefined** : **선언한 후 값을 할당하지 않은** **변수** 혹은 값이 **주어지지 않은 인수**에 자동으로 할당됩니다. 메서드와 선언도 평가할 변수가 값을 할당받지 않는 경우에 undefined를 반환합니다.
4.  **Number** : 3과 -30 등의 **정수**를 다룰 때 사용하는 객체입니다.
5.  **BigInt** : number객체가 안정적으로 표현할 수 있는 2^53 -1보다 큰 정수를 표현할 때 사용하는 객체입니다.
6.  **String** : t문자열(문자의 나열)의 생성자입니다.
7.  **Symbol** : 원시 타입의 값의 일종입니다. 주로 이름의 충동 위험이 없는 유일한 **객체의 프로퍼티 키( property key)를** 만들기 위해 사용합니다. **new연산자**를 이용한 래퍼 객체의 생성이 **불가능합니다.**
8.  **Object** : 자바스크립트는 객체 기반의 프로그래밍 언어입니다. 자바스크립트를 구성하는 거의 **'모든 것'**이 객체입니다. 즉, **object는 키(key)와 값(value)으로 구성된 프로퍼티들의 집합**입니다.

#### Typeof연산자

> typeof는 **변수의 데이터 타입을 반환**하는 연산자입니다.

## CH3. 함수 (function)💁🏻

#### **1\. 함수란?**

> 함수는 JavaScript에서 기본적인 구성 **블록** 중의 하나입니다. 함수는 작업을 수행하거나 값을 계산하는 문장 집합 같은 자바스크립트 절차입니다. 함수를 사용하려면 함수를 호출하고자 하는 범위 내에서 함수를 정의해야만 합니다. 즉, 간단히 정의하자면 **어떠한 목적을 가진 작업들을 수해하는 코드들이 모인 블록입니다.**

```
function square(number) {
  return number * number;
}
```

함수 square은 number라는 하나의 **매개변수**를 가집니다. 이 함수는 **인수** (즉, number) 자체를 곱하여 반환하는 하나의 문장으로 구성되어 있습니다. return문은 함수에 의해 반환된 값을 지정합니다. 함수 내부에서 return을 반환하지 않는다면 출력 값이 undefined로 나옵니다. 

여기서, 매개변수 값을 바꾸더라도 전역적으로 또는 **함수를 호출하는 곳에 반영되지 않습니다.**

**매개변수(인자) : parameter / 인수 : argument**

#### **2\. 함수 선언 방법**

**함수 선언식**

```
function getTriangleArea(base, height){
let triangleArea = (base * height) / 2;
return triangleArea;
}
```

**함수 표현식**

```
const getTriangleArea = function(base, height){
let triangleArea = (base * height) / 2;
return triangleArea;
}
```

**화살표 함수**

```
const getTriangleArea = (base, height) =>{
let triangleArea = (base * height) / 2;
return triangleArea;
}
```

\-> 만약 함수의 본문에 return문 만 있는 경우, return과 {} 중괄호를 생략할 수 있습니다. 

```
const getTriangleArea = (base, height) => base * height /2; //0, 정상작동
const getTriangleArea = (base, height) => {base * height /2}; //x, undefined 리턴
const getTriangleArea = (base, height) => (base * height /2); // 하지만 소괄호 사용은 가능합니다.
```

이 3가지의 차이점은 따로 자바스크립트 페이지에서 다루겠습니다. 

## **오늘의 추가 공부**💁🏻

1.  let과 const 키워드의 차이를 비교해보자
2.  함수 선언식 vs 함수 표현식 vs 화살표 함수의 차이점 
3.  undefined vs null / not defined vs undefined
