CH1. 반복문 💁🏻
1. for : 고전적인 for문
2. for in : 객체의 프로퍼티 키 열거 전용
3. for of : 이터러블 순회 전용
4. forEach(): 배열 순회 전용 메서드
5. while : 고전적인 while문
6. do while : 고전적인 do...while문
7. Object 객체 메서드: 객체 순회 전용
8. Array.prototye 메서드 : 배열 전용
이렇게 8가지 종류가 있다고 합니다. 솔직히 아직까진 어디에 어떻게쓰는지 잘모르겠어서 정리는 따로 안하려고합니다. 나중에 객체와 배열 등을 제대로 공부하고나서 정리하면 더 좋은 예제로 할 수 있을 것 같습니다.!

CH2. 반복문 예제 💁🏻
문제1.  문자열을 입력받아 버그('#')의 인덱스를 리턴해야 합니다. 
입력 : word는 string 타입의 단어
출력 : number 타입을 리턴해야 합니다.
1. for문을 사용한 정답

function findTheBug(word) {
  for (let i = 0; i < word.length; i++) {
    if (word[i] === '#') {
      return i;
    }
  }

  return undefined;
}
2. for of 문을 사용한 정답

function findTheBug(word) {
  let sum=0;
  for(const element of word){
    if(element==="#") return sum;
    sum++;
  }
  return undefined;
}
-> 그냥 word에 들어오는 값중 #이있으면 그값의 인덱스 번호를 출력해주면 되는 문제였습니다. 솔직히 처음에는 word라는 한단어가 왜 배열처럼 들어오는 지가 이해가안됬는데 내가 이해한바로는 string은 문자의 나열 이니까 하나하나 인식이 가능한게 아닌지...? 사실 그냥 그런가보다 그런더가 하고 넘어갔어요. 그리고! for of로 쓰면 좀 더 간결하게 표현이 가능한거같습니다. 모든 값을 다돌아야한다면 for of로 되도록 써보려고합니다.

문제2. 수를 입력받아 홀수인지 여부를 리턴해야 합니다.
입력 : number 타입의 정수
출력 : boolean 타입을 리턴해야 합니다.
주의사항 : 반복문(while)문을 사용해야 합니다. for문 사용은 금지됩니다. 나눗셈(/), 나머지(%) 연산자 사용은 금지됩니다. 0은 짝수로 간주합니다. 
1. 내가 푼 풀이

function isOdd(num) {
  let result = 0;
  let i = 1;
  while(i <= num){
    if(i > num){
      result = i - num;
      if(result === 1) return true;
      else return false;
    }
    i+=2;
  } 
}
2. 정답

function isOdd(num) {
  if (num < 0) {
    num = -num;
  }

  while (num >= 0) {
    if (num === 0) {
      return false;
    } else if (num === 1) {
      return true;
    }

    num = num - 2;
  }
}
문제3. 수(num)를 입력받아 1부터 num까지의 정수로 구성된 문자열을 리턴해야 합니다.
입력 : number 타입의 정수 (num >= 1)
출력 : string 타입을 리턴해야 합니다.
주의사항 : 반복문(while)문을 사용해야 합니다. for문 사용은 금지됩니다. 숫자(number string) 사이를 '-'로 구분합니다.
('1-2-3-4-5')
수도코드의 중요성을 실시간 줌시간에 인지했어요. 나같은 초보들은 수도코드로 내머릿속에서 정리하는 단계를 거치면 코드로 실현이 가능했습니다. 그래서 몇문제는 수도코드, 즉 의사코드를 추가해보려고 합니다~

👀 수도코드

1부터 num까지 모든수를 문자열로 리턴
1 - 2
1 - 2 - 3
1 - 2 - 3 - 4 이런식으로 빈문자열에 계속해서 값을 쌓아줘야함
function makeDigits2(num) {
  let result = '1';
  let i = 2;  //위의 결과값을 넣을 변수인 result가 문자열 1부터 시작했으니까 반복문을 돌면서 값이 커질 i는 2부터 시작해도 무방하다고 생각함
  while(i <= num){
    result = result + '-' +String(i);
    i++;
  }
  return result;
}
문제3. 두 개의 수를 입력받아 두 수를 포함해 두 수 사이의 수 중 2의 배수의 개수를 리턴해야 합니다.
입력 : number 타입의 정수 (num1 >= 0)
출력 : number 타입을 리턴해야 합니다.
주의사항 : 반복문(for)문을 사용해야 합니다. num1이 num2보다 작지 않을 수도 있습니다. 0은 2의 배수가 아니라고 가정합니다.
👀 수도코드

num1 이 num2보다 클경우, 그 반대의 경우를 생각한다
만약 num1 과 num2가 같다면 1을 출력, 두수가 다 0이라면 0을 리턴한다. 
그 수 사이에서 반복문을 돌면서 2로 나누었을때 나머지가 0이되는 수의 개수를 센다. 
function makeMultiplesOfDigit2(num1, num2) {
  let count = 0;
  let start = num1;
  let end = num2;

  if (num1 > num2) {
    start = num2;
    end = num1;
  }

  if (start === 0) {
    start = 1;
  }

  for (let i = start; i <= end; i++) {
    if (i % 2 === 0) {
      count += 1;
    }
  }

  return count;
}
-> 수도코드에서 적었듯이 나는 num1이 num2보다 작을 경우도 조건문으로 넣어줘야한다고 생각했다. 하지만 위의 정답코드처럼 num1이 num2보다 클때만 서로를 바꿔주면 모두 같은 조건이 되기때문에 굳이 두가지 조건문을 써서 코드를 길게 할 필요가 없는것이다. 

문제4. 수를 입력받아 약수(factor)의 합을 리턴해야 합니다.
입력 : number 타입의 수
출력 : number 타입을 리턴해야 합니다.
👀 수도코드

약수란 어떤수를 나눌 수 있는 1과 어떤 수 사이의 모든 수 
num을 i로 나누었을때 나머지가 0인수를 결과값에 넣어준다.
function getSumOfFactors(num) {
  let result = 0;
  for(let i = 0; i <= num ; i++){
    if(num % i === 0) result = result + i;
  }
  return result;
}
문제5. 1 이상의 자연수를 입력받아 소수(prime number)인지 여부를 리턴해야 합니다.
입력 : number 타입의 수
출력 : boolean 타입을 리턴해야 합니다.

👀 수도코드

소수란 1과 자기자신만 나눌 수 있는 수 
num을 i로 나누었을때 나머지가 0인 수를 찾아 새로운 변수에 카운팅하듯이 넣는다.
만약 count수가 1보다 크다면 자기자신이외에 수도 나누어지는 수 이므로 소수가 아님
function getSumOfFactors(num) {
  let count = 0;

  for(let i = 0; i <= num ; i++){
    if(num % i === 0) count++;
  }
  if(count>1) return false;
  return true;
}
 하지만 내답과 다른 정답코드

function isPrime(num) {
  let sqrt = parseInt(Math.sqrt(num));

  if (num === 1) {
    return false;
  }

  if (num === 2) {
    return true;
  }

  if (num % 2 === 0) {
    return false;
  }

  for (let i = 3; i <= sqrt; i += 2) {
    if (num % i === 0) {
      return false;
    }
  }

  return true;
}
-> 정답 코드는 Math.sqrt함수를 썻더라구요. Math.sqrt함수는 숫자의 제곱근을 반환합니다. 왜....이걸 쓴거죠? 왜죠? 이해가안됩니다. 수업시간에 나왔던 코드를 굳이 제곱근을 사용하지 않아도되었는데 말이죠! 

수업 중 나온 또 다른 정답코드

function isPrime(num) {

  if (num === 1) {
    return false;
  }

  if (num === 2) {
    return true;
  }

  if (num % 2 === 0) {
    return false;
  }

  for (let i = 3; i <= num; i++) {
  //num을 ( 3과 num사이에 있는 수) 로 나눠서 나머지가 0인게 하나라도 있으면, 그건 소수가 아님.
    if (num % i === 0) {
      return false;
    }
   return true;
  }
이외에도 어려웠던 문제들은 많았습니다.....예...뭐....멘탈이 조금 나갔구요... 그치만 복습 철저히 해서 좀 더 빠르게 머릿속에서 계산이됬으면 좋겟습니다.ㅎㅎㅎㅎ일단 오늘은 자고 내일은 html이더라구요 공부를 미리했었던 부분이라 빠르게 듣고 반복문을 좀 더 추가해서 정리 할 생각입니다. 앞서 들었던 강의의 추가적으로 정리 못했던 것도 추가할 예정입니다.

오늘의 추가 공부💁🏻
문자열은 배열과 비슷한 속성을 가지고 있습니다. 레퍼런스(MDN - Array)를 살펴보면서 문자열과 배열의 공통점이 무엇인지 확인해보겠습니다.
반복문을 이용한 코딩테스트 문제를 조금 더 풀어볼 생각입니다.
더불어서 Math함수를 한번 정리해서 짚고 넘어가야겠더라구요. 기억을 다 할진 모르겠지만 그래도 한번 본다면 나중에 검색해서 사용할 수 있겠죵?
