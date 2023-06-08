# DOM의 기초

## 1. DOM과 DOM 트리

### 1) DOM(문서 객체 모델)

- **자바스크립트**를 이용하여 웹문서에 접근하고 제어할 수 있도록 객체를 사용해 웹문서를 체계적으로 정리하는 방법
- 웹문서를 구조화한 **DOM 트리**(DOM tree)와 **이벤트** 등을 정리해놓은 표준

### 2) DOM 트리

- **웹 문서에 있는 요소**들 간의 부모, 자식 관계를 계층구조로 표시한 것이다.
  - 루트노드: html
- 문서의 요소 뿐만 아니라 **각 요소의 속성**도 자식으로 나타낸다.

## 2. 웹 요소에 접근하기(access)

### 1) 웹 요소에 접근하기

※ chrome에서 f12 누르고 콘솔에서 실험해볼 수 있다.

- `querySelector(선택자)`, `querySelectorAll(선택자)` 함수

  ```javascript
  document.querySelector("#id");
  document.querySelector(".class");
  document.querySelector("tag");
  ```

- `getElement~()` 함수

  ```javascript
  document.getElementById("id");
  document.getElementsByClassName("class");
  document.getElementsByTagName("tag");
  ```

- getElement~() 와querySelector()의 차이
  - querySelector()를 사용하면 둘 이상의 선택자를 조합해서 접근할 수 있다.
    - ex: #detail > p

### 2) 웹 요소 내용 가져오기 및 수정하기

- 접근한 요소의 텍스트 내용을 가져오거나 지정할 때
  - `innerText`
    - 순수 텍스트 가져오기
    - 해당 요소에 텍스트 지정
  - `innerHTML`
    - 태그와 함께 텍스트 가져오기
    - 해당 요소에 태그와 함께 텍스트 지정
  - `textContent`
    - 소스에 있는대로 텍스트 가져오기(화면에 보이는 대로 아님)
      - 화면에서 감춘 요소에서 내용 가져오기
      - 소스에 공백이 여러 개일 경우 그 공백도 모두

## 3. 자바스크립트로 스타일 수정하기

### 1) CSS 속성에 접근하기

```javascript
// css에서는 속성 이름이 background-color
// camelCase
요소.style.backgroundColor;
```

### 2) `classList` 프로퍼티

두 개 이상의 class 스타일이 적용되었을 경우 **class 스타일 정보**를 담아두는 프로퍼티

```javascript
요소.classList;
```

- 클래스 스타일 **추가**하기 및 **삭제**하기

  ```javascript
  요소.classList.add("className"); // 추가(추가할 클래스 스타일이 미리 지정되어있으면 적용)
  요소.classList.remove("className"); // 삭제
  ```

- contains() – 특정 클래스 스타일 있는지 **확인**

  ```javascript
  // 보통 클래스 스타일을 삭제하기 전 확인할 때 사용
  요소.classList.contains("className"); // T/F 반환
  ```

- toggle() – 특정 스타일 토글

  - 특정 클래스를 추가하거나 삭제하기를 반복할 때

  ```javascript
  요소.onclick = () => {
    // 요소를 클릭할 때마다 알아서 className 스타일이 추가되고 삭제됨
    요소.classList.toggle("className");
  };
  ```

## 4. DOM에서 폼 다루기

### 1) 폼 요소에 접근하기

```html
<form name="order">
  <input type="text" name="box" id="input-box" />
</form>
```

- id로 접근해서 입력값 알아보기
  ```javascript
  document.querySelector("#input-box").value;
  ```
- **name** 속성 값을 사용해 접근하기

  ```javascript
  // form, form 태그 안 요소에도 name 속성이 있어야 한다.
  document.order.box.value;
  ```

- **폼 배열**을 사용해 접근하기(**id, class, name 속성도 없을 때**)

  - DOM에서는 웹 문서 안에 있는 **모든 요소**를 **배열** 형태로 저장한다.

  ```javascript
  document.forms; // 모든 form 태그 정보를 배열로 저장하는 프로퍼티
  document.forms[0].elements;
  document.forms[0].elements[0]; // 폼 안의 요소 역시 elements 속성에 배열로 저장된다.
  ```

  - 배열에 저장되는 **순서**(아래 인덱스 참고)

  ```html
  <form>
    <!-- 0: fieldset -->
    <fieldset>
      <!-- 1: input -->
      <input type="text" />
      <!-- 2: input -->
      <input type="text" />
    </fieldset>
    <!-- 3: fieldset -->
    <fieldset>
      <!-- 4: input -->
      <input type="text" />
      <!-- 5: input -->
      <input type="text" />
    </fieldset>
  </form>
  ```

### 2) 선택 목록과 항목에 접근하기

```html
<select id="select">
  <option>0</option>
  <option>1</option>
  <option>2</option>
  <option>3</option>
  <option>4</option>
</select>
```

- 선택목록 항목에 접근하기

  ```javascript
  document.querySelector("#select").options;
  ```

- 선택된 항목 알아보기

  ```javascript
  document.querySelector("#select").options[selectMenu.selectedIndex]; // html요소 반환
  document.querySelector("#select").options[selectMenu.selectedIndex].innerText; // 텍스트 반환

  document.querySelector("#select").options.selectedIndex; // 인덱스 반환
  document.querySelector("#select").selectedIndex; // 인덱스 반환
  ```

### 3) 라디오 버튼과 체크박스에 접근하기

```html
<form name="test">
  <!-- radio -->
  <label> <input type="radio" name="radios" /> radio 1 </label>
  <label> <input type="radio" name="radios" /> radio 2 </label>
  <!-- checkbox -->
  <label> <input type="checkbox" name="checkboxes" /> check 1 </label>
  <label> <input type="checkbox" name="checkboxes" /> check 2 </label>
</form>
```

- 특징

  - **name** 속성을 이용해 버튼을 그룹으로 묶는다.
    - name 값을 이용해 접근한다.
  - **RadioNodeList**라는 노드 리스트 형태로 저장된다.(배열과 비슷)
  - 선택한 요소는 **checked** 속성으로 확인한다.

- 라디오 버튼, 체크박스에 접근하기

  ```javascript
  document.test.radios; // RadioNodeList 반환
  document.test.checkboxes; // RadioNodeList 반환
  ```

- checked 속성 사용하기(선택한 요소 확인)
  ```javascript
  // 항목을 선택하면 그 항목 요소에 checked 속성이 (true 값으로) 추가된다.
  document.querySelector("input[name='radios']:checked"); // 라디오 선택된 요소
  document.querySelectorAll("input[name='checkboxes']:checked"); // 체크박스 선택된 요소(2개 이상 선택 가능)
  ```
