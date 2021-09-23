# *틱택토 게임*



#### 🎯 *실행 화면*


![Sep-24-2021 01-50-34](https://user-images.githubusercontent.com/86669143/134550377-42544b72-e952-498e-931c-13c54cfa1a56.gif)





---
#### 🧩 *배운 내용 정리하기*

    1. 이차원 배열
    => 배열 안에 배열이 있을 때 이차원 배열이라고 한다. 배열이 몇 번 중첩됐느냐에 따라 몇 차원 배열인지 정해진다.
       표와 비슷한 모양이어서 실무에서 많이 사용된다.

    2. 구조분해 할당
    => 객체 내부의 속성과 할당하는 변수명이 같을 때 다음과 같이 줄여서 쓸 수 있다.
   
    ex) const { body } = document;
        const body = document.body;

    - 여러 속성을 한번에 변수에 할당할 수도 있다.
    ex) const obj = {a: 1, b: 2};
        const { a,b } = obj; // 다음 두 줄을 이렇게 한줄로 표현 가능
        const a = obj.a;
        const b = obj.b;

    - 배열을 줄여서 쓸 수 있다.
    ex) const array = [1,2,5];
        const [one, two, five] = array; // 다음 세 줄을 이렇게 한 줄로 표현 가능
        const one = array[0];
        const two = array[1];
        const five = array[2];

    3. 이벤트 버블링
    => 이벤트 버블링(event bubbling)은 이벤트가 발생할 때 부모 태그에도 동일한 이벤트가 발생하는 
       현상을 말한다. td의 부모 태그는 tr이고 , tr의 부모 태그는 table 이다.
       td 태그를 클릭하면 td 태그에 click 이벤트가 발생하고, td 태그의 부모인 tr 태그와 tr 태그의 부모인
       table 태그에도 발생한다. 즉 , td 태그에서 발생한 click 이벤트가 table 태그까지 전달된다.  

       이벤트 버블링 현상이 일어나면 이벤트 리스너 콜백함수의 event.target은 이벤트가 발생한 태그로 바꿔주므로
       주의해야 한다. 이벤트가 발생한 태그가 아닌 이벤트를 연결한 태그에 접근하고 싶다면 event.currentTarget을 
       사용해야한다.

    4. parentNode와 children
    => 현재 태그의 부모 태그를 찾고 싶을 때는 parentNode를 사용한다. 
        아래와 같은 HTML이 있다고 가정해보자.
    ex) <table>
          <tr>
            <td id = 'td00'></td>
            <td id = 'td01'>X</td>
            <td id = 'td02'></td>
          </tr>
        </table>
    -  tr 태그의 부모는 table 이다.
    ex) document.querySelector('tr').parentNode; // table 태그
    
    -  자식 태그를 찾으려면 children 속성을 사용한다. 자식 태그는 여러 개일 수 있으므로 
       children 속성은 배열 모양의 값이 된다.
       단, 진짜 배열은 아니고 배열모양의 객체이다.
    ex) document.querySelector('tr').children; // {0: td, 1: td, 2: td }

    5. rowIndex와 cellIndex
    => tr 태그는 몇 번째 줄인지 알려주는 rowIndex라는 속성을 제공하고, td 태그는 몇 번째 칸인지를
      알려 주는 cellIndex 라는 속성을 제공한다.
    ex) const rowIndex = $tr.rowIndex;
        const cellIndex = $td.cellIndex;

    6. 유사 배열 객체와 Array.from
    =>  4번에 나온 children 속성 같은, 배열 모양의 객체를 유사 배열 객체 (array-like object) 라고
        한다.배열이 아니므로 배열 메서드를 사용할 수없다. 배열 메서드를 사용하고 싶다면 Array.from 메서드로
        유사 배열 객체를 배열로 바꾼다.
    ex) Array.from($tr.children).indexOf($td);

    - 문자열도 Array.from 메서드를 사용해 배열로 바꿀 수 있다.
    ex) Array.from('123'); // ['1','2','3']

    7. every와 some
    => 배열에서 모든 값이 조건에 해당하는지 판단하려면 every 메서드를 사용하고, 하나라도 조건에 해당하는지
       판단하려면 some 메서드를 사용한다.
    
    형식) 배열.every(조건함수);
         배열.some(조건함수);

    - 일반 반복문을 사용하면 끝까지 탐색하지만 , every와 some 메서드는 조건이 충족 또는 불충족되면 멈추므로
      일반 반복문 보다 효율적인 경우가 많다. 
      every는 하나라도 조건을 만족하지 않는 요소 (조건 함수가 false 를 return)를 찾으면 반복을 중단하고,
      some은 하나라도 조건을 만족하는 요소 (조건 함수가 true를 return)를 찾으면 반복을 중단한다.
 
    8. flat
    => flat은 배열의 차원을 한 단계 낮추는 메서드로 , n차원 배열을 n-1차원 배열로 낮춘다. 
       이차원 배열이라면 일차원 배열로 바꾼다. 차원을 낮추는 게 배열을 평평하게 만드는 것 처럼 보여서 flat이라는 
       이름이 붙었다. 일차원 배열은 flat을 적용해도 그대로 일차원 배열이 된다. 
    ex) const array = [[1,2,3],[4,5,6],[7,8,9]];
        array.flat(); // [1,2,3,4,5,6,7,8,9]
        const array2 = [1,2,3,[[4,5,6],[7,8,9]]];
        array2.flat(); // [1,2,3,[4,5,6],[7,8,9]];