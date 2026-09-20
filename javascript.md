# JavaScript 문법 정리

> 모아모아 픽에서는 **바닐라 JavaScript를 우선**해서 사용한다.  
> 회사에서는 **jQuery를 많이 사용**하므로, 같은 기능이 jQuery에서는 어떻게 작성되는지도 함께 정리한다.

---

# 1. 요소 찾기

## id로 찾기

### JavaScript

```javascript
document.getElementById('@@@');
```

예:

```javascript
var navbar = document.getElementById('navbar');
```

### jQuery

```javascript
$('#@@@');
```

예:

```javascript
var $navbar = $('#navbar');
```

---

## CSS 선택자로 하나 찾기

### JavaScript

```javascript
document.querySelector('.@@@');
```

예:

```javascript
var modal = document.querySelector('.cmn-modal');
```

`querySelector()`는 조건에 맞는 **첫 번째 요소 하나만** 가져온다.

### jQuery

```javascript
$('.@@@');
```

jQuery의 `$()`는 조건에 맞는 요소를 모두 담을 수 있다.

첫 번째 요소만 사용하려면:

```javascript
$('.@@@').first();
```

---

## CSS 선택자로 전부 찾기

### JavaScript

```javascript
document.querySelectorAll('.@@@');
```

예:

```javascript
var buttons = document.querySelectorAll('.btn');
```

여러 개의 요소가 반환된다.

### jQuery

```javascript
$('.@@@');
```

예:

```javascript
var $buttons = $('.btn');
```

---

## 태그명으로 찾기

### JavaScript

```javascript
document.getElementsByTagName('@@@');
```

예:

```javascript
document.getElementsByTagName('button');
```

### jQuery

```javascript
$('button');
```

---

# 2. 스타일 제어

요소의 CSS 스타일을 JavaScript에서 직접 변경할 때 사용한다.

### JavaScript

```javascript
element.style.스타일속성 = '값';
```

예:

```javascript
body.style.display = 'none';
body.style.overflow = 'hidden';
```

### jQuery

```javascript
$('요소').css('display', 'none');
```

여러 스타일을 한 번에 변경:

```javascript
$('요소').css({
    display: 'none',
    position: 'fixed'
});
```

```text
JavaScript → element.style
jQuery     → .css()
```

---

# 3. JavaScript CSS 속성명 표기

CSS 속성 이름에 `-`가 있으면 JavaScript의 `style`에서는 **camelCase**로 작성한다.

### JavaScript

```text
background-color → backgroundColor
font-size        → fontSize
margin-top       → marginTop
z-index          → zIndex
pointer-events   → pointerEvents
```

예:

```javascript
element.style.marginTop = '20px';
element.style.backgroundColor = '#fff';
```

### jQuery

jQuery의 `.css()`는 CSS에서 쓰는 속성명 그대로 작성할 수 있다.

```javascript
$('.box').css('margin-top', '20px');
$('.box').css('background-color', '#fff');
```

객체 형태에서는 camelCase도 사용할 수 있다.

```javascript
$('.box').css({
    marginTop: '20px',
    backgroundColor: '#fff'
});
```

---

# 4. hidden

HTML 요소를 숨기거나 보여줄 때 사용할 수 있다.

HTML:

```html
<div hidden></div>
```

### JavaScript

숨김:

```javascript
element.hidden = true;
```

보여줌:

```javascript
element.hidden = false;
```

### jQuery

보통 jQuery에서는 `.hide()` / `.show()`를 많이 사용한다.

숨김:

```javascript
$(element).hide();
```

보여줌:

```javascript
$(element).show();
```

`hidden` 속성 자체를 변경하려면:

```javascript
$(element).prop('hidden', true);
$(element).prop('hidden', false);
```

```text
JavaScript → element.hidden
jQuery     → .hide() / .show()
          또는 .prop('hidden', true / false)
```

---

# 5. dataset

HTML의 `data-*` 속성을 JavaScript에서 읽거나 수정할 때 사용한다.

HTML:

```html
<div data-modal-type="agency"></div>
```

### JavaScript

값 읽기:

```javascript
modal.dataset.modalType;
```

결과:

```text
agency
```

값 변경:

```javascript
modal.dataset.modalType = 'filter';
```

변환 규칙:

```text
data-modal-type
↓
dataset.modalType
```

```text
data-product-id
↓
dataset.productId
```

### jQuery

값 읽기:

```javascript
$(modal).data('modal-type');
```

또는:

```javascript
$(modal).data('modalType');
```

값 저장:

```javascript
$(modal).data('modal-type', 'filter');
```

주의:

jQuery의 `.data()`는 jQuery 내부에 값을 저장해서 사용할 수 있기 때문에, 실제 HTML의 `data-*` 속성값까지 직접 바꾸고 싶다면 `.attr()`을 사용한다.

```javascript
$(modal).attr('data-modal-type', 'filter');
```

```text
JavaScript → dataset
jQuery     → .data()
HTML 속성 직접 변경 → .attr('data-...', 값)
```

---

# 6. textContent

요소 안의 **텍스트를 가져오거나 변경할 때** 사용한다.

### JavaScript

텍스트 넣기:

```javascript
element.textContent = '메시지';
```

텍스트 비우기:

```javascript
element.textContent = '';
```

현재 텍스트 읽기:

```javascript
var text = element.textContent;
```

### jQuery

텍스트 넣기:

```javascript
$(element).text('메시지');
```

텍스트 비우기:

```javascript
$(element).text('');
```

현재 텍스트 읽기:

```javascript
var text = $(element).text();
```

`textContent`와 `.text()`는 HTML 태그를 넣는 용도가 아니라 **텍스트 자체를 넣거나 읽는 용도**다.

```text
JavaScript → textContent
jQuery     → .text()
```

---

# 7. class 제어

## class 추가

### JavaScript

```javascript
element.classList.add('active');
```

### jQuery

```javascript
$(element).addClass('active');
```

---

## class 제거

### JavaScript

```javascript
element.classList.remove('active');
```

### jQuery

```javascript
$(element).removeClass('active');
```

---

## class가 있는지 확인

### JavaScript

```javascript
element.classList.contains('active');
```

### jQuery

```javascript
$(element).hasClass('active');
```

---

## 있으면 제거 / 없으면 추가

### JavaScript

```javascript
element.classList.toggle('active');
```

### jQuery

```javascript
$(element).toggleClass('active');
```

```text
JavaScript → classList.add()
             classList.remove()
             classList.contains()
             classList.toggle()

jQuery     → .addClass()
             .removeClass()
             .hasClass()
             .toggleClass()
```

---

# 8. `||` OR 연산자

OR = 또는.

왼쪽 값이 **truthy**이면 왼쪽 값을 사용하고,  
왼쪽 값이 **falsy**이면 오른쪽 값을 사용한다.

### JavaScript · jQuery 공통

jQuery를 사용하고 있어도 JavaScript 연산자는 그대로 사용한다.

```javascript
scrollLockY = window.scrollY || document.documentElement.scrollTop;
```

의미:

```text
window.scrollY 값이 있으면 사용
↓
없거나 0 등 falsy이면
↓
document.documentElement.scrollTop 사용
```

또 다른 예:

```javascript
mode = mode || 'default';
```

`mode`가 없으면 `'default'`를 사용한다.

---

# 9. `&&` AND 연산자

AND = 그리고.

두 조건이 모두 true여야 true가 된다.

### JavaScript · jQuery 공통

```javascript
if (isMobile && isAndroid) {
    console.log('안드로이드 모바일');
}
```

jQuery 코드 안에서도 `&&`는 똑같이 사용한다.

```javascript
if ($('.popup').length && isMobile) {
}
```

---

# 10. `!` 부정 연산자

`!`는 true / false를 반대로 만든다.

### JavaScript · jQuery 공통

```javascript
if (!deviceOs) {
}
```

의미:

```text
deviceOs가 없으면
```

예:

```javascript
var deviceOs = '';

if (!deviceOs) {
    console.log('OS 정보 없음');
}
```

jQuery에서도 동일하다.

```javascript
if (!$('.popup').length) {
}
```

의미:

```text
.popup 요소가 없으면
```

---

# 11. `===` 일치 연산자

값과 타입이 모두 같은지 확인한다.

### JavaScript · jQuery 공통

```javascript
deviceOs === 'ANDROID'
```

예:

```javascript
var deviceOs = 'ANDROID';

if (deviceOs === 'ANDROID') {
    console.log('안드로이드');
}
```

jQuery를 사용해도 비교 연산자는 동일하다.

```javascript
if ($(element).text() === '완료') {
}
```

가능하면 `==`보다 `===`를 사용한다.

---

# 12. `!==` 불일치 연산자

값 또는 타입이 다르면 true가 된다.

### JavaScript · jQuery 공통

```javascript
if (deviceOs !== 'ANDROID') {
}
```

의미:

```text
deviceOs가 ANDROID가 아니면
```

jQuery에서도 동일하다.

```javascript
if ($(element).text() !== '완료') {
}
```

---

# 13. 삼항 연산자

간단한 조건문을 한 줄로 작성할 때 사용한다.

기본 구조:

```javascript
조건 ? true일 때 값 : false일 때 값
```

### JavaScript · jQuery 공통

```javascript
var text = isAndroid ? '안드로이드' : '아이폰';
```

의미:

```text
isAndroid가 true
→ '안드로이드'

isAndroid가 false
→ '아이폰'
```

회사에서 사용했던 예:

```javascript
freeMode: isAndroid ? {
    enabled: true,
    momentum: true,
    momentumRatio: 0.2
} : true
```

의미:

```text
안드로이드
→ 옵션 객체 사용

안드로이드가 아니면
→ freeMode: true
```

삼항 연산자는 jQuery 전용 문법이 아니라 **JavaScript 문법**이므로 jQuery 코드 안에서도 그대로 사용한다.

---

# 14. if / else

조건에 따라 실행할 코드를 나눌 때 사용한다.

### JavaScript · jQuery 공통

```javascript
if (조건) {

} else {

}
```

예:

```javascript
if (isAndroid) {
    console.log('Android');
} else {
    console.log('iOS 또는 기타 OS');
}
```

jQuery 요소를 조건으로 사용할 수도 있다.

```javascript
if ($('.popup').length) {
    $('.popup').show();
} else {
    console.log('popup 없음');
}
```

`if / else` 자체는 JavaScript 문법이므로 jQuery에서도 동일하다.

---

# 15. 함수

반복해서 사용하는 동작을 하나로 묶는다.

### JavaScript · jQuery 공통

```javascript
function 함수명() {

}
```

예:

```javascript
function openModal() {
    modal.hidden = false;
}
```

실행:

```javascript
openModal();
```

jQuery를 사용하는 함수도 같은 방식으로 만든다.

```javascript
function openModal() {
    $('.modal').show();
}
```

---

## 매개변수

함수 실행할 때 값을 전달할 수 있다.

### JavaScript · jQuery 공통

```javascript
function openModal(type) {
    console.log(type);
}
```

실행:

```javascript
openModal('agency');
```

`type`에는 `'agency'`가 들어간다.

jQuery를 사용하는 함수에서도 동일하다.

```javascript
function openModal(type) {
    $('[data-modal-type="' + type + '"]').show();
}
```

---

# 16. return

함수를 종료하거나 값을 돌려준다.

### JavaScript · jQuery 공통

함수 종료:

```javascript
return;
```

예:

```javascript
if (!modal) {
    return;
}
```

의미:

```text
modal이 없으면
이 아래 코드를 실행하지 않고 함수 종료
```

값을 반환할 수도 있다.

```javascript
function getNumber() {
    return 10;
}
```

jQuery 코드에서도 동일하다.

```javascript
function getPopup() {
    return $('.popup');
}
```

---

# 17. 이벤트 등록

사용자가 클릭하거나 스크롤하거나 키를 누르는 등의 행동을 감지한다.

### JavaScript

```javascript
element.addEventListener('click', function () {

});
```

예:

```javascript
button.addEventListener('click', function () {
    console.log('클릭');
});
```

### jQuery

```javascript
$('.btn').on('click', function () {

});
```

예:

```javascript
$('.btn').on('click', function () {
    console.log('클릭');
});
```

```text
JavaScript → addEventListener()
jQuery     → .on()
```

---

# 18. 이벤트 객체 `event`, `e`

이벤트가 발생하면 해당 이벤트의 정보를 받을 수 있다.

`event`와 `e`는 변수 이름만 다를 뿐 같은 용도로 사용한다.

### JavaScript

```javascript
button.addEventListener('click', function (event) {
    console.log(event);
});
```

짧게 `e`라고 많이 작성한다.

```javascript
button.addEventListener('click', function (e) {
    console.log(e);
});
```

### jQuery

```javascript
$('.btn').on('click', function (event) {
    console.log(event);
});
```

또는:

```javascript
$('.btn').on('click', function (e) {
    console.log(e);
});
```

```text
JavaScript → event / e
jQuery     → event / e
```

jQuery도 이벤트 객체를 함수의 첫 번째 인자로 받는다.

---

# 19. `e.target`

실제로 이벤트가 발생한 요소를 가리킨다.

### JavaScript · jQuery 공통

JavaScript:

```javascript
modal.addEventListener('click', function (e) {
    console.log(e.target);
});
```

jQuery:

```javascript
$('.modal').on('click', function (e) {
    console.log(e.target);
});
```

모달 내부 버튼을 클릭했다면 `e.target`은 그 버튼이 될 수 있다.

회사에서 사용했던 형태:

```javascript
$('#showpopupReview .popup-backdrop').mouseup(function (e) {
    if (e.target === this) {
        $('#showpopupReview').hide();
        bodyScrollUnlock();
    }
});
```

의미:

```text
실제로 클릭한 곳(e.target)이
이벤트를 걸어둔 backdrop(this) 자체일 때만
팝업을 닫는다.
```

즉 팝업 내용 영역을 클릭했을 때는 닫히지 않는다.

`e.target`은 JavaScript 이벤트의 개념이므로 jQuery에서도 그대로 사용한다.

---

# 20. `this`

현재 이벤트가 연결되어 있는 요소를 의미할 때 많이 사용한다.

### JavaScript

```javascript
button.addEventListener('click', function () {
    console.log(this);
});
```

현재 이벤트가 연결된 `button` 요소가 들어온다.

### jQuery

```javascript
$('.btn').on('click', function () {
    console.log(this);
});
```

현재 클릭된 `.btn`의 실제 DOM 요소가 들어온다.

jQuery 기능을 사용하려면 `$()`로 감싼다.

```javascript
$(this)
```

예:

```javascript
$('.btn').on('click', function () {
    $(this).addClass('active');
});
```

```text
this    → 실제 DOM 요소
$(this) → jQuery 객체
```

---

# 21. closest()

현재 요소부터 부모 방향으로 올라가면서 조건에 맞는 가장 가까운 요소를 찾는다.

### JavaScript

```javascript
element.closest('.popup-wrap');
```

예:

```javascript
e.target.closest('.popup-wrap');
```

### jQuery

```javascript
$(e.target).closest('.popup-wrap');
```

회사에서 사용했던 코드:

```javascript
$('#PopupReport').on('click', function (e) {
    if ($(e.target).closest('.popup-wrap').length) {
        return;
    }

    popClose();
});
```

의미:

```text
클릭한 곳이 .popup-wrap 내부
→ 아무것도 하지 않음

.popup-wrap 바깥
→ 팝업 닫음
```

```text
JavaScript → .closest()
jQuery     → .closest()
```

이름은 같지만 JavaScript에서는 DOM 요소에 사용하고, jQuery에서는 jQuery 객체에 사용한다.

---

# 22. length

찾은 요소의 개수를 확인할 때 사용한다.

### JavaScript

`querySelectorAll()` 결과에도 `.length`를 사용할 수 있다.

```javascript
document.querySelectorAll('.popup-wrap').length
```

요소가 있는지 확인:

```javascript
if (document.querySelectorAll('.popup-wrap').length) {
}
```

### jQuery

```javascript
$('.popup-wrap').length
```

요소가 있으면:

```text
1 이상
```

없으면:

```text
0
```

예:

```javascript
if ($('.popup-wrap').length) {
}
```

의미:

```text
.popup-wrap 요소가 존재하면
```

`.length`는 jQuery 전용 문법이 아니다.  
JavaScript의 배열, NodeList, 문자열 등에서도 개수를 확인할 때 사용한다.

---

# 23. keydown

키보드를 누를 때 발생하는 이벤트.

### JavaScript

```javascript
input.addEventListener('keydown', function (event) {

});
```

Enter 확인:

```javascript
input.addEventListener('keydown', function (event) {
    if (event.key === 'Enter') {
    }
});
```

### jQuery

```javascript
$('.boardEntersearch').on('keydown', function (event) {

});
```

Enter 확인:

```javascript
$('.boardEntersearch').on('keydown', function (event) {
    if (event.key === 'Enter') {
    }
});
```

기존 회사 코드에서 볼 수 있는 형태:

```javascript
if (event.which == 13) {
}
```

`13`은 Enter 키 코드.

가능하면 새 코드에서는:

```javascript
event.key === 'Enter'
```

형태가 더 읽기 쉽다.

```text
JavaScript → addEventListener('keydown', ...)
jQuery     → .on('keydown', ...)
Enter 확인 → event.key === 'Enter'
```

---

# 24. preventDefault()

요소가 원래 가지고 있는 기본 행동을 막는다.

예를 들어 `<a>`의 링크 이동이나 `<form>`의 제출 같은 기본 동작을 막을 수 있다.

### JavaScript

```javascript
link.addEventListener('click', function (e) {
    e.preventDefault();
});
```

### jQuery

```javascript
$('a').on('click', function (e) {
    e.preventDefault();
});
```

`preventDefault()`는 이벤트 객체의 메서드이므로 JavaScript와 jQuery에서 사용 방법이 거의 같다.

```text
JavaScript → e.preventDefault()
jQuery     → e.preventDefault()
```

---

25. setTimeout() / clearTimeout() / setInterval() / clearInterval()

시간과 관련된 JavaScript 기본 함수.

시간 단위는 ms(밀리초).

1000ms = 1초
100ms  = 0.1초
setTimeout()

일정 시간이 지난 뒤 한 번 실행한다.

JavaScript · jQuery 공통
setTimeout(function () {

}, 시간);

예:

setTimeout(function () {
    console.log('1초 뒤 실행');
}, 1000);

의미:

1초 기다림
↓
코드 한 번 실행
↓
종료
clearTimeout()

실행 예정인 setTimeout()을 취소할 때 사용한다.

var timer = setTimeout(function () {
    console.log('1초 뒤 실행');
}, 1000);

clearTimeout(timer);

의미:

setTimeout 실행 예약
↓
timer 변수에 해당 타이머 저장
↓
clearTimeout(timer)
↓
예약된 실행 취소
setTimeout()   → 일정 시간 뒤 한 번 실행
clearTimeout() → setTimeout 실행 취소
회사에서 사용했던 setTimeout() 예
if (tabWidth === 0) {
    if ((retry || 0) < 10) {
        setTimeout(function () {
            setCategoryTabAlign((retry || 0) + 1);
        }, 100);
    }

    return;
}

의미:

categoryTab 너비가 아직 0이면
↓
0.1초 기다린다
↓
다시 확인한다
↓
최대 10번 반복

앱 재실행 직후 DOM 크기 계산이 끝나지 않은 문제를 보완하기 위해 사용했다.

이 코드는 setTimeout() 자체가 반복하는 것이 아니라,

setCategoryTabAlign()

함수 안에서 다시 setTimeout()을 실행하는 방식으로 재시도하고 있다.

setInterval()

일정 시간마다 계속 반복 실행한다.

JavaScript · jQuery 공통
setInterval(function () {

}, 시간);

예:

setInterval(function () {
    console.log('1초마다 실행');
}, 1000);

의미:

1초 기다림
↓
실행
↓
1초 기다림
↓
실행
↓
계속 반복
clearInterval()

실행 중인 setInterval() 반복을 중지한다.

var timer = setInterval(function () {
    console.log('1초마다 실행');
}, 1000);

clearInterval(timer);

의미:

setInterval 반복 시작
↓
timer 변수에 타이머 저장
↓
clearInterval(timer)
↓
반복 중지
setInterval()   → 일정 시간마다 계속 반복
clearInterval() → setInterval 반복 중지
한 번에 비교
setTimeout()
→ 일정 시간 뒤 한 번 실행

clearTimeout()
→ setTimeout 실행 취소


setInterval()
→ 일정 시간마다 반복 실행

clearInterval()
→ setInterval 반복 중지

짝으로 외우면:

setTimeout    ↔ clearTimeout
setInterval   ↔ clearInterval

setTimeout(), clearTimeout(), setInterval(), clearInterval()은 모두 jQuery 함수가 아니라 JavaScript 기본 함수다.

따라서 jQuery 코드 안에서도 똑같이 사용한다.
---

# 26. innerWidth()

요소의 내부 너비를 확인할 때 사용한다.

## JavaScript

jQuery의 `.innerWidth()`와 비슷한 용도로 `clientWidth`를 사용할 수 있다.

```javascript
var width = document.getElementById('categoryTab').clientWidth;
```

`clientWidth`는 기본적으로 요소의 **content + padding 영역**을 기준으로 너비를 가져온다.

## jQuery

```javascript
var width = $('#categoryTab').innerWidth();
```

`padding`을 포함한 요소 너비를 가져온다.

회사에서 사용했던 형태:

```javascript
var tabWidth = $tab.innerWidth();

if (tabWidth === 0) {
}
```

요소가 아직 렌더링되지 않아 너비가 `0`인지 확인할 때 사용했다.

```text
JavaScript → element.clientWidth
jQuery     → .innerWidth()
```

---

# 27. window.innerWidth

현재 브라우저 화면의 너비를 확인한다.

### JavaScript

```javascript
window.innerWidth
```

예:

```javascript
if (window.innerWidth <= 768) {
    console.log('모바일');
}
```

### jQuery

```javascript
$(window).width()
```

예:

```javascript
if ($(window).width() <= 768) {
    console.log('모바일');
}
```

```text
JavaScript → window.innerWidth
jQuery     → $(window).width()
```

둘은 스크롤바 처리 방식 등에서 값이 약간 다를 수 있으므로, 같은 기능 안에서는 한 방식을 정해서 사용하는 것이 좋다.

---

# 28. scrollY

현재 페이지가 세로로 얼마나 스크롤되었는지 확인한다.

### JavaScript

```javascript
window.scrollY
```

예:

```javascript
var scrollTop = window.scrollY;
```

브라우저 호환 등을 고려해서 다음처럼 사용할 수도 있다.

```javascript
var scrollTop = window.scrollY || document.documentElement.scrollTop;
```

### jQuery

```javascript
$(window).scrollTop()
```

예:

```javascript
var scrollTop = $(window).scrollTop();
```

```text
JavaScript → window.scrollY
jQuery     → $(window).scrollTop()
```

---

# JavaScript / jQuery 빠른 비교

```text
요소 찾기
JavaScript → document.querySelector('.btn')
jQuery     → $('.btn')

스타일 변경
JavaScript → element.style.display = 'none'
jQuery     → $(element).css('display', 'none')

숨기기
JavaScript → element.hidden = true
jQuery     → $(element).hide()

텍스트 변경
JavaScript → element.textContent = '메시지'
jQuery     → $(element).text('메시지')

class 추가
JavaScript → element.classList.add('active')
jQuery     → $(element).addClass('active')

class 제거
JavaScript → element.classList.remove('active')
jQuery     → $(element).removeClass('active')

class 확인
JavaScript → element.classList.contains('active')
jQuery     → $(element).hasClass('active')

class 토글
JavaScript → element.classList.toggle('active')
jQuery     → $(element).toggleClass('active')

클릭 이벤트
JavaScript → element.addEventListener('click', function () {})
jQuery     → $(element).on('click', function () {})

가장 가까운 부모 찾기
JavaScript → element.closest('.wrap')
jQuery     → $(element).closest('.wrap')

요소 개수
JavaScript → document.querySelectorAll('.item').length
jQuery     → $('.item').length

화면 너비
JavaScript → window.innerWidth
jQuery     → $(window).width()

스크롤 위치
JavaScript → window.scrollY
jQuery     → $(window).scrollTop()
```

---

# JavaScript 문법이라 jQuery에서도 그대로 사용하는 것

아래는 **jQuery 전용 대체 문법이 따로 있는 것이 아니라 JavaScript 문법 자체**이므로 둘 다 동일하게 사용한다.

```text
||              OR
&&              AND
!               부정
===             일치
!==             불일치
? :             삼항 연산자
if / else       조건문
function        함수
return          함수 종료 / 값 반환
event / e       이벤트 객체
e.target        실제 이벤트 발생 요소
e.preventDefault()
setTimeout()
```

jQuery는 JavaScript를 대신하는 별개의 언어가 아니라 **JavaScript 라이브러리**이기 때문에, 기본 JavaScript 문법 위에서 jQuery 기능을 함께 사용한다.
