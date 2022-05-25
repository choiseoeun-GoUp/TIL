## CH1. 조건문 (conditional express)💁🏻

우리는 둘 중 하나를 선택하는 일에 매우 익숙합니다. 배가 고프면 밥을 먹고 그러지 않다면 밥을 먹지 않습니다. 하지만 컴퓨터는 매일 아침, 점심, 저녁을 먹도록 프로그래밍해놓았다면 배가 부르더라고 무조건 정해진 시간에 식사를 합니다. 배가 고프지 않을 때 식사를 하지 못하도록 하기 위해서는 조건문이 필요합니다.

#### **1\. 조건문이란?**

> 조건문은 주어진 조건식의 결과에 따라 명령을 수행하도록 제어하는 명령문입니다.

**ㄱ. ' if ' 문**

대표적인 조건문의 형태는 **if문**입니다. if문은 괄호 안에 들어가는 조건을 평가하는데, 그 결과가 **true**이면 코드블록이 실행됩니다.

```
if(조건1) {
//조건1이 통과할 경우
} else if (조건2){
//조건1이 통과하지않고 
//조건2가 통과할 경우
} else {
//모든 조건이 통과하지 않는경우
}
```

**ㄱ. 조건부 연산자 '?'**

조건에 따라 다른 값을 변수에 할당해줘야 할 때 사용합니다. 

```
let result = condition ? value1 : value2;
```

#### **2\. 비교연산자**(comparison operator)****

조건문에는 반드시 **비교연산자(comparison operator)**가 필요합니다. 비교의 결과는 늘 boolean, 즉 **true혹은 false**입니다. 

| **비교연산자(comparison operator)** |  |
| --- | --- |
| \> | 초과 |
| < | 미만 |
| \>= | 이상 |
| <= | 이하 |
| \=== | 같다 |
| !== | 다르다 |

#### **3\. 논리 연산자(Logic Operator)**

| 논리 연산자(Logic Operator) |  |
| --- | --- |
| && | AND연산자 |
| \|\| | OR연산자 |
| ! | NOT연산자 |

#### **4\. 기억해야할 6가지 falsy값**

1.  if ( false )
2.  if ( null )
3.  if ( undefined )
4.  if ( 0 )
5.  if ( NaN )
6.  if ( ' ' )

```
//falsy 예제 : 임의의 값을 입력받아 falsy 값인지 여부를 리턴하세요

function isFalsy(anything) {
 return !Boolean(anything);
}
```

**여기서 조건문 팁! 맨 위에 제일 어려운 조건을 걸어서 거르고 세세하게 나눈다!**

## **CH2. 문자열 (string)**💁🏻

#### **1\. 문자열이란?**

> **string** 전역객체는 문자열(문자의 나열)의 생성자입니다. 문자열은 read only입니다. 새로 할당하지 않는 한 그 값이 바뀌지 않습니다.

연산자를 string타입과 다른 타입사이에 쓰면 string 형식으로 변환됩니다. (toString)

```
var str1 = 'code';
var str2 = 'states';
var str3 = '1';
console.log(str1 + str2 ); //'codestates'
console.log(str3 + 7 ); //'17'
```

#### **2\. length PROPERTY** : 문자열의 전체 길이를 반환합니다. 

```
var str1 = 'codestates';
console.log(str.length); //10
```

#### **3\. 문자열의 메소드**

**1\. 문자열에서의 위치 찾기** 

-   indexOf() : String 인스턴스에서 **특정 문자나 문자열이 처음으로 등장하는 위치의 인덱스**를 반환합니다.
-   lastIndexOf : String 인스턴스에서 특정 문자나 문자열이 **마지막으로 등장**하는 위치의 인덱스를 반환합니다.

```
'Blue Whale'.indexOf('Blue'); //0
'Blue Whale'.indexOf('blue'); //-1
'Blue Whale'.indexOf('Whale'); //5
'Blue Whale Whale'.indexOf('Whale'); //5

'canal'.lastIndexOf('a'); //3
```

-   str.includes ( searchValue) : 포함되어있는지를 확인하는 메서드로 true 혹은 false를 반환한다. 

#### **2\. 문자열 분리**

-   split() : String 인스턴스를 구분자(separator)를 기준으로 나눈 후, 나뉜 **문자열을 하나의 배열로 반환**합니다.

```
var str = 'Hello fro, the other side';
console.log(str.split('');
//['Hello', 'from', 'the', 'other', 'side']
```

#### **3\. 문자열 추출**

-   slice() : String 인스턴스에서 전달받은 **시작 인덱스부터 종료 인덱스 바로 앞까지의 문자열을 추출**한 새 문자열을 반환합니다.
-   substring() : String 인스턴스에서 전달받은 **시작 인덱스부터 종료 인덱스 바로 앞까지의 문자열을 추출**한 새 문자열을 반환합니다.
-   substr() : String 인스턴스에서 전달받은 **시작 인덱스부터 길이만큼의 문자열을 추출한 새로운 문자열을 반환**합니다.

#### **4\. 문자열의 대소문자 변환**

-   toUpperCase() : String 인스턴스의 모든 문자를 **대문자**로 변환한 새로운 문자열을 반환합니다.
-   toLowerCase() : String 인스턴스의 모든 문자를 **소****문자**로 변환한 새로운 문자열을 반환합니다.

```
var str = "JavaScript";

str.toUpperCase(); // JAVASCRIPT

str.toLowerCase(); // javascript
```

## **오늘의 추가 공부**💁🏻

-   trim
-   공백 문자: 탭 문자(t), Carrige return 및 return 문자
-   match
-   replace
-   정규표현식

## **오늘의 회고💁🏻**

**다 안다고 생각하고 넘어갔던 기초지식이 생각보다 머리에 남아있지 않았던 것 같다. 검색을 통해서 그때그때 찾아서 쓸 수 있지만 그래도 정리하면서 머릿속에 더 넣어야 할 것 같다.**
