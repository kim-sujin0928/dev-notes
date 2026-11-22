# HTML 정리

> 작업하면서 요청한 태그 · 속성만 정리한다.

- 항목 형식: 설명 → 사용법 → 예 → 주의(접근성 등) → 한 줄 요약
- 번호 읽는 법: `2-3` = 2번 분류의 3번째 항목

## 목차

- [1. 폼](#1-폼)
  - [1-1. fieldset / legend — 폼 요소 묶기](#1-1-fieldset--legend--폼-요소-묶기)

---

## 1. 폼

### 1-1. fieldset / legend — 폼 요소 묶기

체크박스 · 라디오 · input 여러 개를 **"같은 그룹"으로 묶는 상자**. `legend`는 그 상자의 이름표다.

**사용법**

```html
<fieldset>
    <legend>그룹 이름</legend>
    <!-- 같은 그룹의 폼 요소들 -->
</fieldset>
```

fieldset이 해주는 일:

```text
1. 그룹으로 묶기    → 이 요소들이 같은 질문에 대한 선택지라는 의미
2. 이름표(legend)   → 스크린리더가 "여행지, 프랑스 체크박스"처럼 그룹 이름까지 읽어줌
3. 한 번에 비활성화 → fieldset에 disabled를 걸면 안의 폼 요소가 전부 비활성화
```

`div`로 묶어도 화면은 똑같이 만들 수 있지만, 1 · 2 · 3은 `div`로는 안 된다.

**예**

체크박스 칩 그룹:

```html
<fieldset class="search-where">
    <legend class="sr-only">여행지 선택</legend>
    <label class="chip">
        <input type="checkbox" name="searchwhere" value="all">
        <span>전체</span>
    </label>
    <label class="chip">
        <input type="checkbox" name="searchwhere" value="france" class="item">
        <span>프랑스</span>
    </label>
</fieldset>
```

화면에 제목을 따로 보여주고 있으면, `legend`는 `sr-only`(화면에서만 숨기고 스크린리더는 읽는 클래스)로 숨겨도 된다.

그룹 전체 비활성화:

```html
<fieldset disabled>
    <!-- 안의 input, button이 전부 비활성화됨 -->
</fieldset>
```

```javascript
where.disabled = true;               // JavaScript
$('.search-where').prop('disabled', true); // jQuery
```

JavaScript에서 그룹 구분하기 (이벤트 위임):

```javascript
search.addEventListener('change', function (e) {
    var group = e.target.closest('fieldset'); // 바뀐 체크박스를 감싼 그룹
});
```

`closest('fieldset')`은 "나를 감싸고 있는 가장 가까운 fieldset 찾아줘"라는 뜻이다. jQuery는 `$(e.target).closest('fieldset')`. (javascript.md 1-4, 11-2 참고)

**주의**

- `legend`는 `fieldset`의 **첫 번째 자식**이어야 한다.
- 브라우저 기본 스타일로 테두리 · 안쪽 여백 · `min-width: min-content`가 들어 있다. 레이아웃이 안 줄어들면 `min-width: 0`, 테두리는 `border: 0; padding: 0; margin: 0;`으로 초기화한다.
- `legend`를 `display: none`이나 `hidden`으로 숨기면 스크린리더도 못 읽는다. 숨길 때는 `sr-only`를 쓴다.
- 질문이 하나뿐인 단일 input(예: 출발일 하나)은 `label`만으로 충분하다. 선택지가 여러 개인 체크박스 · 라디오 묶음에 쓰는 게 기본이다.

```text
여러 선택지를 한 그룹으로 → fieldset + legend
그룹 전체 비활성화        → fieldset disabled
JS에서 어느 그룹인지      → e.target.closest('fieldset')
```

<!--
새 항목 템플릿

---

## N. 분류명

### N-1. 태그 / 속성 이름

무엇을 할 때 쓰는지 한두 줄.

**사용법**

```html
```

**예**

```html
```

**주의**

접근성 · 브라우저 기본 동작 · 자주 하는 실수

```text
한 줄 요약
```
-->
