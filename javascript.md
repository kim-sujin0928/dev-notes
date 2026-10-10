**# JavaScript 문법 정리**



\> 모아모아 픽에서는 **\*\*바닐라 JavaScript를 우선\*\***&#xD574;서 사용한다.  

\> 회사에서는 **\*\*jQuery를 많이 사용\*\***&#xD558;므로, 같은 기능이 jQuery에서는 어떻게 작성되는지도 함께 정리한다.



\---



**# 1. 요소 찾기**



**## id로 찾기**



**### JavaScript**



\`\`\`javascript

document.getElementById('@@@');

\`\`\`



예:



\`\`\`javascript

var navbar = document.getElementById('navbar');

\`\`\`



**### jQuery**



\`\`\`javascript

$('#@@@');

\`\`\`



예:



\`\`\`javascript

var $navbar = $('#navbar');

\`\`\`



\---



**## CSS 선택자로 하나 찾기**



**### JavaScript**



\`\`\`javascript

document.querySelector('.@@@');

\`\`\`



예:



\`\`\`javascript

var modal = document.querySelector('.cmn-modal');

\`\`\`



\`querySelector()\`는 조건에 맞는 **\*\*첫 번째 요소 하나만\*\*** 가져온다.



**### jQuery**



\`\`\`javascript

$('.@@@');

\`\`\`



jQuery의 \`$()\`는 조건에 맞는 요소를 모두 담을 수 있다.



첫 번째 요소만 사용하려면:



\`\`\`javascript

$('.@@@').first();

\`\`\`



\---



**## CSS 선택자로 전부 찾기**



**### JavaScript**



\`\`\`javascript

document.querySelectorAll('.@@@');

\`\`\`



예:



\`\`\`javascript

var buttons = document.querySelectorAll('.btn');

\`\`\`



여러 개의 요소가 반환된다.



**### jQuery**



\`\`\`javascript

$('.@@@');

\`\`\`



예:



\`\`\`javascript

var $buttons = $('.btn');

\`\`\`



\---



**## 태그명으로 찾기**



**### JavaScript**



\`\`\`javascript

document.getElementsByTagName('@@@');

\`\`\`



예:



\`\`\`javascript

document.getElementsByTagName('button');

\`\`\`



**### jQuery**



\`\`\`javascript

$('button');

\`\`\`



\---



**# 2. 스타일 제어**



요소의 CSS 스타일을 JavaScript에서 직접 변경할 때 사용한다.



**### JavaScript**



\`\`\`javascript

element.style.스타일속성 = '값';

\`\`\`



예:



\`\`\`javascript

body.style.display = 'none';

body.style.overflow = 'hidden';

\`\`\`



**### jQuery**



\`\`\`javascript

$('요소').css('display', 'none');

\`\`\`



여러 스타일을 한 번에 변경:



\`\`\`javascript

$('요소').css({

    display: 'none',

    position: 'fixed'

});

\`\`\`



\`\`\`text

JavaScript → element.style

jQuery     → .css()

\`\`\`



\---



**# 3. JavaScript CSS 속성명 표기**



CSS 속성 이름에 \`-\`가 있으면 JavaScript의 \`style\`에서는 **\*\*camelCase\*\***&#xB85C; 작성한다.



**### JavaScript**



\`\`\`text

background-color → backgroundColor

font-size        → fontSize

margin-top       → marginTop

z-index          → zIndex

pointer-events   → pointerEvents

\`\`\`



예:



\`\`\`javascript

element.style.marginTop = '20px';

element.style.backgroundColor = '#fff';

\`\`\`



**### jQuery**



jQuery의 \`.css()\`는 CSS에서 쓰는 속성명 그대로 작성할 수 있다.



\`\`\`javascript

$('.box').css('margin-top', '20px');

$('.box').css('background-color', '#fff');

\`\`\`



객체 형태에서는 camelCase도 사용할 수 있다.



\`\`\`javascript

$('.box').css({

    marginTop: '20px',

    backgroundColor: '#fff'

});

\`\`\`



\---



**# 4. hidden**



HTML 요소를 숨기거나 보여줄 때 사용할 수 있다.



HTML:



\`\`\`html

\<div hidden>\</div>

\`\`\`



**### JavaScript**



숨김:



\`\`\`javascript

element.hidden = true;

\`\`\`



보여줌:



\`\`\`javascript

element.hidden = false;

\`\`\`



**### jQuery**



보통 jQuery에서는 \`.hide()\` / \`.show()\`를 많이 사용한다.



숨김:



\`\`\`javascript

$(element).hide();

\`\`\`



보여줌:



\`\`\`javascript

$(element).show();

\`\`\`



\`hidden\` 속성 자체를 변경하려면:



\`\`\`javascript

$(element).prop('hidden', true);

$(element).prop('hidden', false);

\`\`\`



\`\`\`text

JavaScript → element.hidden

jQuery     → .hide() / .show()

          또는 .prop('hidden', true / false)

\`\`\`



\---



**# 5. dataset**



HTML의 \`data-\*\` 속성을 JavaScript에서 읽거나 수정할 때 사용한다.



HTML:



\`\`\`html

\<div data-modal-type="agency">\</div>

\`\`\`



**### JavaScript**



값 읽기:



\`\`\`javascript

modal.dataset.modalType;

\`\`\`



결과:



\`\`\`text

agency

\`\`\`



값 변경:



\`\`\`javascript

modal.dataset.modalType = 'filter';

\`\`\`



변환 규칙:



\`\`\`text

data-modal-type

↓

dataset.modalType

\`\`\`



\`\`\`text

data-product-id

↓

dataset.productId

\`\`\`



**### jQuery**



값 읽기:



\`\`\`javascript

$(modal).data('modal-type');

\`\`\`



또는:



\`\`\`javascript

$(modal).data('modalType');

\`\`\`



값 저장:



\`\`\`javascript

$(modal).data('modal-type', 'filter');

\`\`\`



주의:



jQuery의 \`.data()\`는 jQuery 내부에 값을 저장해서 사용할 수 있기 때문에, 실제 HTML의 \`data-\*\` 속성값까지 직접 바꾸고 싶다면 \`.attr()\`을 사용한다.



\`\`\`javascript

$(modal).attr('data-modal-type', 'filter');

\`\`\`



\`\`\`text

JavaScript → dataset

jQuery     → .data()

HTML 속성 직접 변경 → .attr('data-...', 값)

\`\`\`



\---



**# 6. textContent**



요소 안의 **\*\*텍스트를 가져오거나 변경할 때\*\*** 사용한다.



**### JavaScript**



텍스트 넣기:



\`\`\`javascript

element.textContent = '메시지';

\`\`\`



텍스트 비우기:



\`\`\`javascript

element.textContent = '';

\`\`\`



현재 텍스트 읽기:



\`\`\`javascript

var text = element.textContent;

\`\`\`



**### jQuery**



텍스트 넣기:



\`\`\`javascript

$(element).text('메시지');

\`\`\`



텍스트 비우기:



\`\`\`javascript

$(element).text('');

\`\`\`



현재 텍스트 읽기:



\`\`\`javascript

var text = $(element).text();

\`\`\`



\`textContent\`와 \`.text()\`는 HTML 태그를 넣는 용도가 아니라 **\*\*텍스트 자체를 넣거나 읽는 용도\*\***&#xB2E4;.



\`\`\`text

JavaScript → textContent

jQuery     → .text()

\`\`\`



\---



**# 7. class 제어**



**## class 추가**



**### JavaScript**



\`\`\`javascript

element.classList.add('active');

\`\`\`



**### jQuery**



\`\`\`javascript

$(element).addClass('active');

\`\`\`



\---



**## class 제거**



**### JavaScript**



\`\`\`javascript

element.classList.remove('active');

\`\`\`



**### jQuery**



\`\`\`javascript

$(element).removeClass('active');

\`\`\`



\---



**## class가 있는지 확인**



**### JavaScript**



\`\`\`javascript

element.classList.contains('active');

\`\`\`



**### jQuery**



\`\`\`javascript

$(element).hasClass('active');

\`\`\`



\---



**## 있으면 제거 / 없으면 추가**



**### JavaScript**



\`\`\`javascript

element.classList.toggle('active');

\`\`\`



**### jQuery**



\`\`\`javascript

$(element).toggleClass('active');

\`\`\`



\`\`\`text

JavaScript → classList.add()

             classList.remove()

             classList.contains()

             classList.toggle()



jQuery     → .addClass()

             .removeClass()

             .hasClass()

             .toggleClass()

\`\`\`



\---



**# 8. \`||\` OR 연산자**



OR = 또는.



왼쪽 값이 **\*\*truthy\*\***&#xC774;면 왼쪽 값을 사용하고,  

왼쪽 값이 **\*\*falsy\*\***&#xC774;면 오른쪽 값을 사용한다.



**### JavaScript · jQuery 공통**



jQuery를 사용하고 있어도 JavaScript 연산자는 그대로 사용한다.



\`\`\`javascript

scrollLockY = window\.scrollY || document.documentElement.scrollTop;

\`\`\`



의미:



\`\`\`text

window\.scrollY 값이 있으면 사용

↓

없거나 0 등 falsy이면

↓

document.documentElement.scrollTop 사용

\`\`\`



또 다른 예:



\`\`\`javascript

mode = mode || 'default';

\`\`\`



\`mode\`가 없으면 \`'default'\`를 사용한다.



\---



**# 9. \`&&\` AND 연산자**



AND = 그리고.



두 조건이 모두 true여야 true가 된다.



**### JavaScript · jQuery 공통**



\`\`\`javascript

if (isMobile && isAndroid) {

    console.log('안드로이드 모바일');

}

\`\`\`



jQuery 코드 안에서도 \`&&\`는 똑같이 사용한다.



\`\`\`javascript

if ($('.popup').length && isMobile) {

}

\`\`\`



\---



**# 10. \`!\` 부정 연산자**



\`!\`는 true / false를 반대로 만든다.



**### JavaScript · jQuery 공통**



\`\`\`javascript

if (!deviceOs) {

}

\`\`\`



의미:



\`\`\`text

deviceOs가 없으면

\`\`\`



예:



\`\`\`javascript

var deviceOs = '';



if (!deviceOs) {

    console.log('OS 정보 없음');

}

\`\`\`



jQuery에서도 동일하다.



\`\`\`javascript

if (!$('.popup').length) {

}

\`\`\`



의미:



\`\`\`text

.popup 요소가 없으면

\`\`\`



\---



**# 11. \`===\` 일치 연산자**



값과 타입이 모두 같은지 확인한다.



**### JavaScript · jQuery 공통**



\`\`\`javascript

deviceOs === 'ANDROID'

\`\`\`



예:



\`\`\`javascript

var deviceOs = 'ANDROID';



if (deviceOs === 'ANDROID') {

    console.log('안드로이드');

}

\`\`\`



jQuery를 사용해도 비교 연산자는 동일하다.



\`\`\`javascript

if ($(element).text() === '완료') {

}

\`\`\`



가능하면 \`==\`보다 \`===\`를 사용한다.



\---



**# 12. \`!==\` 불일치 연산자**



값 또는 타입이 다르면 true가 된다.



**### JavaScript · jQuery 공통**



\`\`\`javascript

if (deviceOs !== 'ANDROID') {

}

\`\`\`



의미:



\`\`\`text

deviceOs가 ANDROID가 아니면

\`\`\`



jQuery에서도 동일하다.



\`\`\`javascript

if ($(element).text() !== '완료') {

}

\`\`\`



\---



**# 13. 삼항 연산자**



간단한 조건문을 한 줄로 작성할 때 사용한다.



기본 구조:



\`\`\`javascript

조건 ? true일 때 값 : false일 때 값

\`\`\`



**### JavaScript · jQuery 공통**



\`\`\`javascript

var text = isAndroid ? '안드로이드' : '아이폰';

\`\`\`



의미:



\`\`\`text

isAndroid가 true

→ '안드로이드'



isAndroid가 false

→ '아이폰'

\`\`\`



회사에서 사용했던 예:



\`\`\`javascript

freeMode: isAndroid ? {

    enabled: true,

    momentum: true,

    momentumRatio: 0.2

} : true

\`\`\`



의미:



\`\`\`text

안드로이드

→ 옵션 객체 사용



안드로이드가 아니면

→ freeMode: true

\`\`\`



삼항 연산자는 jQuery 전용 문법이 아니라 **\*\*JavaScript 문법\*\***&#xC774;므로 jQuery 코드 안에서도 그대로 사용한다.



\---



**# 14. if / else**



조건에 따라 실행할 코드를 나눌 때 사용한다.



**### JavaScript · jQuery 공통**



\`\`\`javascript

if (조건) {



} else {



}

\`\`\`



예:



\`\`\`javascript

if (isAndroid) {

    console.log('Android');

} else {

    console.log('iOS 또는 기타 OS');

}

\`\`\`



jQuery 요소를 조건으로 사용할 수도 있다.



\`\`\`javascript

if ($('.popup').length) {

    $('.popup').show();

} else {

    console.log('popup 없음');

}

\`\`\`



\`if / else\` 자체는 JavaScript 문법이므로 jQuery에서도 동일하다.



\---



**# 15. 함수**



반복해서 사용하는 동작을 하나로 묶는다.



**### JavaScript · jQuery 공통**



\`\`\`javascript

function 함수명() {



}

\`\`\`



예:



\`\`\`javascript

function openModal() {

    modal.hidden = false;

}

\`\`\`



실행:



\`\`\`javascript

openModal();

\`\`\`



jQuery를 사용하는 함수도 같은 방식으로 만든다.



\`\`\`javascript

function openModal() {

    $('.modal').show();

}

\`\`\`



\---



**## 매개변수**



함수 실행할 때 값을 전달할 수 있다.



**### JavaScript · jQuery 공통**



\`\`\`javascript

function openModal(type) {

    console.log(type);

}

\`\`\`



실행:



\`\`\`javascript

openModal('agency');

\`\`\`



\`type\`에는 \`'agency'\`가 들어간다.



jQuery를 사용하는 함수에서도 동일하다.



\`\`\`javascript

function openModal(type) {

    $('[data-modal-type="' + type + '"]').show();

}

\`\`\`



\---



**# 16. return**



함수를 종료하거나 값을 돌려준다.



**### JavaScript · jQuery 공통**



함수 종료:



\`\`\`javascript

return;

\`\`\`



예:



\`\`\`javascript

if (!modal) {

    return;

}

\`\`\`



의미:



\`\`\`text

modal이 없으면

이 아래 코드를 실행하지 않고 함수 종료

\`\`\`



값을 반환할 수도 있다.



\`\`\`javascript

function getNumber() {

    return 10;

}

\`\`\`



jQuery 코드에서도 동일하다.



\`\`\`javascript

function getPopup() {

    return $('.popup');

}

\`\`\`



\---



**# 17. 이벤트 등록**



사용자가 클릭하거나 스크롤하거나 키를 누르는 등의 행동을 감지한다.



**### JavaScript**



\`\`\`javascript

element.addEventListener('click', function () {



});

\`\`\`



예:



\`\`\`javascript

button.addEventListener('click', function () {

    console.log('클릭');

});

\`\`\`



**### jQuery**



\`\`\`javascript

$('.btn').on('click', function () {



});

\`\`\`



예:



\`\`\`javascript

$('.btn').on('click', function () {

    console.log('클릭');

});

\`\`\`



\`\`\`text

JavaScript → addEventListener()

jQuery     → .on()

\`\`\`



\---



**# 18. 이벤트 객체 \`event\`, \`e\`**



이벤트가 발생하면 해당 이벤트의 정보를 받을 수 있다.



\`event\`와 \`e\`는 변수 이름만 다를 뿐 같은 용도로 사용한다.



**### JavaScript**



\`\`\`javascript

button.addEventListener('click', function (event) {

    console.log(event);

});

\`\`\`



짧게 \`e\`라고 많이 작성한다.



\`\`\`javascript

button.addEventListener('click', function (e) {

    console.log(e);

});

\`\`\`



**### jQuery**



\`\`\`javascript

$('.btn').on('click', function (event) {

    console.log(event);

});

\`\`\`



또는:



\`\`\`javascript

$('.btn').on('click', function (e) {

    console.log(e);

});

\`\`\`



\`\`\`text

JavaScript → event / e

jQuery     → event / e

\`\`\`



jQuery도 이벤트 객체를 함수의 첫 번째 인자로 받는다.



\---



**# 19. \`e.target\`**



실제로 이벤트가 발생한 요소를 가리킨다.



**### JavaScript · jQuery 공통**



JavaScript:



\`\`\`javascript

modal.addEventListener('click', function (e) {

    console.log(e.target);

});

\`\`\`



jQuery:



\`\`\`javascript

$('.modal').on('click', function (e) {

    console.log(e.target);

});

\`\`\`



모달 내부 버튼을 클릭했다면 \`e.target\`은 그 버튼이 될 수 있다.



회사에서 사용했던 형태:



\`\`\`javascript

$('#showpopupReview .popup-backdrop').mouseup(function (e) {

    if (e.target === this) {

        $('#showpopupReview').hide();

        bodyScrollUnlock();

    }

});

\`\`\`



의미:



\`\`\`text

실제로 클릭한 곳(e.target)이

이벤트를 걸어둔 backdrop(this) 자체일 때만

팝업을 닫는다.

\`\`\`



즉 팝업 내용 영역을 클릭했을 때는 닫히지 않는다.



\`e.target\`은 JavaScript 이벤트의 개념이므로 jQuery에서도 그대로 사용한다.



\---



**# 20. \`this\`**



현재 이벤트가 연결되어 있는 요소를 의미할 때 많이 사용한다.



**### JavaScript**



\`\`\`javascript

button.addEventListener('click', function () {

    console.log(this);

});

\`\`\`



현재 이벤트가 연결된 \`button\` 요소가 들어온다.



**### jQuery**



\`\`\`javascript

$('.btn').on('click', function () {

    console.log(this);

});

\`\`\`



현재 클릭된 \`.btn\`의 실제 DOM 요소가 들어온다.



jQuery 기능을 사용하려면 \`$()\`로 감싼다.



\`\`\`javascript

$(this)

\`\`\`



예:



\`\`\`javascript

$('.btn').on('click', function () {

    $(this).addClass('active');

});

\`\`\`



\`\`\`text

this    → 실제 DOM 요소

$(this) → jQuery 객체

\`\`\`



\---



**# 21. closest()**



현재 요소부터 부모 방향으로 올라가면서 조건에 맞는 가장 가까운 요소를 찾는다.



**### JavaScript**



\`\`\`javascript

element.closest('.popup-wrap');

\`\`\`



예:



\`\`\`javascript

e.target.closest('.popup-wrap');

\`\`\`



**### jQuery**



\`\`\`javascript

$(e.target).closest('.popup-wrap');

\`\`\`



회사에서 사용했던 코드:



\`\`\`javascript

$('#PopupReport').on('click', function (e) {

    if ($(e.target).closest('.popup-wrap').length) {

        return;

    }



    popClose();

});

\`\`\`



의미:



\`\`\`text

클릭한 곳이 .popup-wrap 내부

→ 아무것도 하지 않음



.popup-wrap 바깥

→ 팝업 닫음

\`\`\`



\`\`\`text

JavaScript → .closest()

jQuery     → .closest()

\`\`\`



이름은 같지만 JavaScript에서는 DOM 요소에 사용하고, jQuery에서는 jQuery 객체에 사용한다.



\---



**# 22. length**



찾은 요소의 개수를 확인할 때 사용한다.



**### JavaScript**



\`querySelectorAll()\` 결과에도 \`.length\`를 사용할 수 있다.



\`\`\`javascript

document.querySelectorAll('.popup-wrap').length

\`\`\`



요소가 있는지 확인:



\`\`\`javascript

if (document.querySelectorAll('.popup-wrap').length) {

}

\`\`\`



**### jQuery**



\`\`\`javascript

$('.popup-wrap').length

\`\`\`



요소가 있으면:



\`\`\`text

1 이상

\`\`\`



없으면:



\`\`\`text

0

\`\`\`



예:



\`\`\`javascript

if ($('.popup-wrap').length) {

}

\`\`\`



의미:



\`\`\`text

.popup-wrap 요소가 존재하면

\`\`\`



\`.length\`는 jQuery 전용 문법이 아니다.  

JavaScript의 배열, NodeList, 문자열 등에서도 개수를 확인할 때 사용한다.



\---



**# 23. keydown**



키보드를 누를 때 발생하는 이벤트.



**### JavaScript**



\`\`\`javascript

input.addEventListener('keydown', function (event) {



});

\`\`\`



Enter 확인:



\`\`\`javascript

input.addEventListener('keydown', function (event) {

    if (event.key === 'Enter') {

    }

});

\`\`\`



**### jQuery**



\`\`\`javascript

$('.boardEntersearch').on('keydown', function (event) {



});

\`\`\`



Enter 확인:



\`\`\`javascript

$('.boardEntersearch').on('keydown', function (event) {

    if (event.key === 'Enter') {

    }

});

\`\`\`



기존 회사 코드에서 볼 수 있는 형태:



\`\`\`javascript

if (event.which == 13) {

}

\`\`\`



\`13\`은 Enter 키 코드.



가능하면 새 코드에서는:



\`\`\`javascript

event.key === 'Enter'

\`\`\`



형태가 더 읽기 쉽다.



\`\`\`text

JavaScript → addEventListener('keydown', ...)

jQuery     → .on('keydown', ...)

Enter 확인 → event.key === 'Enter'

\`\`\`



\---



**# 24. preventDefault()**



요소가 원래 가지고 있는 기본 행동을 막는다.



예를 들어 \`\<a>\`의 링크 이동이나 \`\<form>\`의 제출 같은 기본 동작을 막을 수 있다.



**### JavaScript**



\`\`\`javascript

link.addEventListener('click', function (e) {

    e.preventDefault();

});

\`\`\`



**### jQuery**



\`\`\`javascript

$('a').on('click', function (e) {

    e.preventDefault();

});

\`\`\`



\`preventDefault()\`는 이벤트 객체의 메서드이므로 JavaScript와 jQuery에서 사용 방법이 거의 같다.



\`\`\`text

JavaScript → e.preventDefault()

jQuery     → e.preventDefault()

\`\`\`



\---



**# 25. setTimeout() / clearTimeout() / setInterval() / clearInterval()**



시간과 관련된 JavaScript 기본 함수다.



시간 단위는 **\*\*ms(밀리초)\*\*** 를 사용한다.



\`\`\`text

1000ms = 1초

100ms  = 0.1초

\`\`\`



**## setTimeout()**



일정 시간이 지난 뒤 **\*\*한 번 실행\*\***&#xD55C;다.



**### JavaScript · jQuery 공통**



\`\`\`javascript

setTimeout(function () {



}, 시간);

\`\`\`



예:



\`\`\`javascript

setTimeout(function () {

    console.log('1초 뒤 실행');

}, 1000);

\`\`\`



의미:



\`\`\`text

1초 기다림

↓

코드 한 번 실행

↓

종료

\`\`\`



\---



**## clearTimeout()**



실행 예정인 \`setTimeout()\`을 취소할 때 사용한다.



\`\`\`javascript

var timer = setTimeout(function () {

    console.log('1초 뒤 실행');

}, 1000);



clearTimeout(timer);

\`\`\`



의미:



\`\`\`text

setTimeout 실행 예약

↓

timer 변수에 해당 타이머 저장

↓

clearTimeout(timer)

↓

예약된 실행 취소

\`\`\`



\`\`\`text

setTimeout()   → 일정 시간 뒤 한 번 실행

clearTimeout() → setTimeout 실행 취소

\`\`\`



**### 회사에서 사용했던 setTimeout() 예**



\`\`\`javascript

if (tabWidth === 0) {

    if ((retry || 0) < 10) {

        setTimeout(function () {

            setCategoryTabAlign((retry || 0) + 1);

        }, 100);

    }



    return;

}

\`\`\`



의미:



\`\`\`text

categoryTab 너비가 아직 0이면

↓

0.1초 기다린다

↓

다시 확인한다

↓

최대 10번 반복

\`\`\`



앱 재실행 직후 DOM 크기 계산이 끝나지 않은 문제를 보완하기 위해 사용했다.



이 코드는 \`setTimeout()\` 자체가 반복하는 것이 아니라, \`setCategoryTabAlign()\` 함수 안에서 다시 \`setTimeout()\`을 실행하는 방식으로 재시도하고 있다.



\---



**## setInterval()**



일정 시간마다 **\*\*계속 반복 실행\*\***&#xD55C;다.



**### JavaScript · jQuery 공통**



\`\`\`javascript

setInterval(function () {



}, 시간);

\`\`\`



예:



\`\`\`javascript

setInterval(function () {

    console.log('1초마다 실행');

}, 1000);

\`\`\`



의미:



\`\`\`text

1초 기다림

↓

실행

↓

1초 기다림

↓

실행

↓

계속 반복

\`\`\`



\---



**## clearInterval()**



실행 중인 \`setInterval()\` 반복을 중지한다.



\`\`\`javascript

var timer = setInterval(function () {

    console.log('1초마다 실행');

}, 1000);



clearInterval(timer);

\`\`\`



의미:



\`\`\`text

setInterval 반복 시작

↓

timer 변수에 타이머 저장

↓

clearInterval(timer)

↓

반복 중지

\`\`\`



\`\`\`text

setInterval()   → 일정 시간마다 계속 반복

clearInterval() → setInterval 반복 중지

\`\`\`



**## 한 번에 비교**



\`\`\`text

setTimeout()

→ 일정 시간 뒤 한 번 실행



clearTimeout()

→ setTimeout 실행 취소



setInterval()

→ 일정 시간마다 반복 실행



clearInterval()

→ setInterval 반복 중지

\`\`\`



짝으로 외우면:



\`\`\`text

setTimeout  ↔ clearTimeout

setInterval ↔ clearInterval

\`\`\`



\`setTimeout()\`, \`clearTimeout()\`, \`setInterval()\`, \`clearInterval()\`은 모두 jQuery 함수가 아니라 **\*\*JavaScript 기본 함수\*\***&#xB2E4;.



따라서 jQuery 코드 안에서도 똑같이 사용한다.



\---



**# 26. innerWidth()**



요소의 내부 너비를 확인할 때 사용한다.



**## JavaScript**



jQuery의 \`.innerWidth()\`와 비슷한 용도로 \`clientWidth\`를 사용할 수 있다.



\`\`\`javascript

var width = document.getElementById('categoryTab').clientWidth;

\`\`\`



\`clientWidth\`는 기본적으로 요소의 **\*\*content + padding 영역\*\***&#xC744; 기준으로 너비를 가져온다.



**## jQuery**



\`\`\`javascript

var width = $('#categoryTab').innerWidth();

\`\`\`



\`padding\`을 포함한 요소 너비를 가져온다.



회사에서 사용했던 형태:



\`\`\`javascript

var tabWidth = $tab.innerWidth();



if (tabWidth === 0) {

}

\`\`\`



요소가 아직 렌더링되지 않아 너비가 \`0\`인지 확인할 때 사용했다.



\`\`\`text

JavaScript → element.clientWidth

jQuery     → .innerWidth()

\`\`\`



\---



**# 27. window\.innerWidth**



현재 브라우저 화면의 너비를 확인한다.



**### JavaScript**



\`\`\`javascript

window\.innerWidth

\`\`\`



예:



\`\`\`javascript

if (window\.innerWidth <= 768) {

    console.log('모바일');

}

\`\`\`



**### jQuery**



\`\`\`javascript

$(window).width()

\`\`\`



예:



\`\`\`javascript

if ($(window).width() <= 768) {

    console.log('모바일');

}

\`\`\`



\`\`\`text

JavaScript → window\.innerWidth

jQuery     → $(window).width()

\`\`\`



둘은 스크롤바 처리 방식 등에서 값이 약간 다를 수 있으므로, 같은 기능 안에서는 한 방식을 정해서 사용하는 것이 좋다.



\---



**# 28. scrollY**



현재 페이지가 세로로 얼마나 스크롤되었는지 확인한다.



**### JavaScript**



\`\`\`javascript

window\.scrollY

\`\`\`



예:



\`\`\`javascript

var scrollTop = window\.scrollY;

\`\`\`



브라우저 호환 등을 고려해서 다음처럼 사용할 수도 있다.



\`\`\`javascript

var scrollTop = window\.scrollY || document.documentElement.scrollTop;

\`\`\`



**### jQuery**



\`\`\`javascript

$(window).scrollTop()

\`\`\`



예:



\`\`\`javascript

var scrollTop = $(window).scrollTop();

\`\`\`



\`\`\`text

JavaScript → window\.scrollY

jQuery     → $(window).scrollTop()

\`\`\`



\---



**# 29. siblings()**



현재 요소와 **\*\*같은 부모를 가진 형제 요소\*\***&#xB97C; 찾을 때 사용한다.



회사 코드에서는 파일 선택 버튼 옆의 \`.filehidden\`, \`.filename\`처럼 **\*\*같은 줄에 있는 요소를 찾을 때\*\*** 자주 사용했다.



**### JavaScript**



JavaScript에는 jQuery의 \`.siblings()\`와 완전히 같은 단일 메서드는 없다.

부모의 자식들을 가져온 뒤 현재 요소를 제외하는 방식으로 만들 수 있다.



\`\`\`javascript

var siblings = Array.from(element.parentElement.children).filter(function (item) {

    return item !== element;

});

\`\`\`



특정 형제 요소 하나만 필요하다면 부모에서 다시 찾는 방법이 더 간단할 때도 있다.



\`\`\`javascript

var fileInput = element.parentElement.querySelector('.filehidden');

\`\`\`



**### jQuery**



\`\`\`javascript

$(this).siblings('.filehidden');

\`\`\`



회사에서 사용했던 형태:



\`\`\`javascript

$(document).on('click', '.btn-file-select', function () {

    $(this).siblings('.filehidden').click();

});

\`\`\`



의미:



\`\`\`text

this

→ 현재 클릭한 .btn-file-select



siblings('.filehidden')

→ 같은 부모 안에 있는 .filehidden 형제 요소 찾기



.click()

→ 파일 input 클릭 실행

\`\`\`



\`\`\`text

JavaScript → parentElement.children / querySelector()

jQuery     → .siblings()

\`\`\`



\---



**# 30. empty()**



요소 **\*\*자체는 남겨두고 안쪽의 자식 요소만 전부 제거\*\***&#xD560; 때 사용한다.



**### JavaScript**



권장 방식:



\`\`\`javascript

element.replaceChildren();

\`\`\`



또는:



\`\`\`javascript

element.innerHTML = '';

\`\`\`



텍스트와 자식 노드를 모두 비울 때는 다음도 가능하다.



\`\`\`javascript

element.textContent = '';

\`\`\`



**### jQuery**



\`\`\`javascript

$(element).empty();

\`\`\`



회사에서 사용했던 형태:



\`\`\`javascript

$('.setting-list').empty().hide();

\`\`\`



의미:



\`\`\`text

.setting-list 안의 항목 전부 제거

→ 영역 자체는 DOM에 남아 있음

→ hide()로 화면에서 숨김

\`\`\`



\`.empty()\`와 \`.remove()\` 차이:



\`\`\`text

.empty()  → 선택한 요소는 남기고 내부만 삭제

.remove() → 선택한 요소 자체를 삭제

\`\`\`



\`\`\`text

JavaScript → replaceChildren() / innerHTML = ''

jQuery     → .empty()

\`\`\`



\---



**# 31. find()**



현재 요소 **\*\*안쪽의 자식·후손 요소 중에서 조건에 맞는 요소를 찾을 때\*\*** 사용한다.



**### JavaScript**



하나 찾기:



\`\`\`javascript

var filename = admin.querySelector('.filename');

\`\`\`



여러 개 찾기:



\`\`\`javascript

var inputs = admin.querySelectorAll('input');

\`\`\`



**### jQuery**



\`\`\`javascript

$admin.find('.filename');

\`\`\`



회사에서 자주 사용했던 형태:



\`\`\`javascript

var $admin = $(this).closest('.admin-cmn');

var $switch = $admin.find('.switch-input');

\`\`\`



의미:



\`\`\`text

closest()

→ 바깥 부모 방향으로 찾기



find()

→ 안쪽 자식 방향으로 찾기

\`\`\`



\`\`\`text

JavaScript → querySelector() / querySelectorAll()

jQuery     → .find()

\`\`\`



\---



**# 32. eq()**



jQuery로 여러 요소를 찾았을 때 **\*\*몇 번째 요소 하나를 선택\*\***&#xD560; 때 사용한다.



순서는 \`0\`부터 시작한다.



\`\`\`text

0 → 첫 번째

1 → 두 번째

2 → 세 번째

\`\`\`



**### JavaScript**



\`\`\`javascript

var colorpickers = document.querySelectorAll('.colorpicker');

var first = colorpickers[0];

var second = colorpickers[1];

\`\`\`



**### jQuery**



\`\`\`javascript

var $first = $('.colorpicker').eq(0);

var $second = $('.colorpicker').eq(1);

\`\`\`



회사에서 링크 블록의 컬러피커 두 개를 구분할 때 사용했던 형태:



\`\`\`javascript

var btnColor = $admin.find('.colorpicker').eq(0).val();

var textColor = $admin.find('.colorpicker').eq(1).val();

\`\`\`



\`\`\`text

JavaScript → NodeList[index]

jQuery     → .eq(index)

\`\`\`



\---



**# 33. val()**



\`input\`, \`textarea\`, \`select\` 등의 **\*\*값을 읽거나 변경\*\***&#xD560; 때 사용한다.



**### JavaScript**



값 읽기:



\`\`\`javascript

var value = input.value;

\`\`\`



값 변경:



\`\`\`javascript

input.value = '내용';

\`\`\`



값 비우기:



\`\`\`javascript

input.value = '';

\`\`\`



**### jQuery**



값 읽기:



\`\`\`javascript

var value = $('input').val();

\`\`\`



값 변경:



\`\`\`javascript

$('input').val('내용');

\`\`\`



값 비우기:



\`\`\`javascript

$('input').val('');

\`\`\`



회사 초기화 코드에서 사용했던 형태:



\`\`\`javascript

$('.filehidden').val('');

$('.admin-subtitle input[type="text"]').val('');

\`\`\`



\`\`\`text

JavaScript → element.value

jQuery     → .val()

\`\`\`



\---



**# 34. prop()**



체크박스의 \`checked\`, 비활성화의 \`disabled\`처럼 **\*\*현재 DOM 상태값(property)\*\***&#xC744; 읽거나 변경할 때 사용한다.



**### JavaScript**



\`\`\`javascript

checkbox.checked = true;

checkbox.checked = false;

\`\`\`



확인:



\`\`\`javascript

if (checkbox.checked) {

}

\`\`\`



**### jQuery**



\`\`\`javascript

$('.switch-input').prop('checked', true);

$('.switch-input').prop('checked', false);

\`\`\`



값 읽기:



\`\`\`javascript

var checked = $('.switch-input').prop('checked');

\`\`\`



\`attr()\`과 구분:



\`\`\`text

.prop() → 현재 DOM 상태

.attr() → HTML 속성값

\`\`\`



체크박스 상태처럼 사용자가 동작하면서 바뀌는 값은 보통 \`.prop()\`을 사용한다.



\`\`\`text

JavaScript → element.checked

jQuery     → .prop('checked', ...)

\`\`\`



\---



**# 35. is(':checked')**



체크박스나 라디오가 **\*\*현재 체크되어 있는지 확인\*\***&#xD560; 때 자주 사용한다.



**### JavaScript**



\`\`\`javascript

if (checkbox.checked) {

}

\`\`\`



**### jQuery**



\`\`\`javascript

if ($('.switch-input').is(':checked')) {

}

\`\`\`



회사에서 사용했던 형태:



\`\`\`javascript

if ($admin.find('.switch-input').is(':checked')) {

    updatePreview($admin);

}

\`\`\`



의미:



\`\`\`text

해당 관리자 영역의 스위치가 ON이면

→ 프리뷰 업데이트 실행

\`\`\`



\`\`\`text

JavaScript → element.checked

jQuery     → .is(':checked')

\`\`\`



\---



**# 36. not()**



선택한 요소들 중에서 **\*\*특정 조건에 맞는 요소만 제외\*\***&#xD560; 때 사용한다.



**### JavaScript**



\`\`\`javascript

var inputs = Array.from(document.querySelectorAll('input')).filter(function (input) {

    return !input.matches('.colorpicker');

});

\`\`\`



**### jQuery**



\`\`\`javascript

$('input').not('.colorpicker');

\`\`\`



회사에서 새 블록 초기화 시 사용했던 형태:



\`\`\`javascript

$newBlock.find('input[type="text"]').not('.colorpicker').val('');

\`\`\`



의미:



\`\`\`text

새 블록 안의 text input을 찾음

→ .colorpicker는 제외

→ 나머지 input 값만 비움

\`\`\`



\`\`\`text

JavaScript → filter() + matches()

jQuery     → .not()

\`\`\`



\---



**# 37. 이벤트 위임 .on()**



나중에 JavaScript로 새로 만들어지는 요소처럼 **\*\*페이지 로드 시점에는 아직 없는 요소에도 이벤트가 동작하도록\*\*** 할 때 사용한다.



**### JavaScript**



상위 요소에 이벤트를 걸고 실제 클릭된 요소를 확인한다.



\`\`\`javascript

document.addEventListener('click', function (e) {

    var button = e.target.closest('.btn-file-select');



    if (!button) {

        return;

    }



    console.log('파일 선택 버튼 클릭');

});

\`\`\`



**### jQuery**



\`\`\`javascript

$(document).on('click', '.btn-file-select', function () {

    console.log('파일 선택 버튼 클릭');

});

\`\`\`



직접 이벤트와 비교:



\`\`\`javascript

$('.btn-file-select').on('click', function () {

});

\`\`\`



위 코드는 **\*\*현재 DOM에 이미 존재하는 \`.btn-file-select\`\*\***&#xC5D0; 이벤트를 연결한다.



\`\`\`javascript

$(document).on('click', '.btn-file-select', function () {

});

\`\`\`



위 코드는 이벤트를 \`document\`에 걸고, 클릭이 올라왔을 때 \`.btn-file-select\`인지 확인하므로 **\*\*나중에 동적으로 만들어진 버튼에도 동작한다.\*\***



\`\`\`text

기존 요소만 대상 → $('.btn').on(...)

동적 요소 포함     → $(document).on('event', '.btn', ...)

\`\`\`



\---



**# 38. click / input / change 이벤트 차이**



회사 관리자 화면에서 자주 사용한 이벤트들이다.



**### click**



버튼이나 요소를 **\*\*클릭했을 때\*\*** 실행한다.



\`\`\`javascript

$(document).on('click', '.btn-file-select', function () {

});

\`\`\`



**### input**



텍스트 입력값이 **\*\*입력되는 즉시\*\*** 실행된다.



\`\`\`javascript

$(document).on('input', '.admin-subtitle input[type="text"]', function () {

});

\`\`\`



한 글자를 입력하거나 지울 때마다 바로 반응해야 하는 프리뷰에 적합하다.



**### change**



값이 **\*\*변경된 것이 확정될 때\*\*** 실행된다.



\`\`\`javascript

$(document).on('change', '.filehidden', function () {

});

\`\`\`



파일 input, checkbox, radio, select 등에 자주 사용한다.



\`\`\`text

click  → 클릭했을 때

input  → 입력하는 즉시

change → 값 변경이 확정됐을 때

\`\`\`



이벤트 이름은 jQuery 전용이 아니라 브라우저의 JavaScript 이벤트를 jQuery의 \`.on()\`으로 연결해서 사용하는 것이다.



\---



**# 39. files[0]**



\`\<input type="file">\`에서 사용자가 선택한 파일을 가져올 때 사용한다.



\`files\`는 선택된 파일들을 담고 있는 \`FileList\`이고, \`[0]\`은 첫 번째 파일을 의미한다.



**### JavaScript**



\`\`\`javascript

var file = fileInput.files[0];

\`\`\`



**### jQuery 이벤트 안에서**



\`\`\`javascript

$(document).on('change', '.filehidden', function () {

    var file = this.files[0];



    if (!file) {

        return;

    }

});

\`\`\`



여기서 \`this\`는 실제 DOM 요소이므로 \`this.files\`를 바로 사용할 수 있다.



\`\`\`text

this         → 실제 file input DOM 요소

this.files   → 선택된 파일 목록

this.files[0]→ 첫 번째 선택 파일

\`\`\`



\---



**# 40. FileReader**



브라우저에서 사용자가 선택한 파일의 내용을 **\*\*JavaScript로 읽을 때\*\*** 사용하는 Web API다.



jQuery 기능이 아니라 JavaScript 기능이다.



이미지 파일을 프리뷰할 때 자주 사용한다.



\`\`\`javascript

var file = input.files[0];



if (!file) {

    return;

}



var reader = new FileReader();



reader.onload = function (e) {

    preview\.src = e.target.result;

};



reader.readAsDataURL(file);

\`\`\`



흐름:



\`\`\`text

파일 선택

→ files[0]으로 File 객체 가져오기

→ new FileReader()

→ readAsDataURL(file)로 읽기 시작

→ 읽기가 끝나면 onload 실행

→ e.target.result에 읽은 결과가 들어옴

\`\`\`



이미지 프리뷰에서는 \`e.target.result\`를 \`\<img src>\`에 넣어 사용할 수 있다.



\---



**# 41. remove()**



선택한 **\*\*요소 자체를 DOM에서 삭제\*\***&#xD560; 때 사용한다.



**### JavaScript**



\`\`\`javascript

element.remove();

\`\`\`



**### jQuery**



\`\`\`javascript

$(element).remove();

\`\`\`



회사에서 리스트나 자유 블록 삭제 시 사용한 형태:



\`\`\`javascript

$row\.remove();

\`\`\`



\`.empty()\`와 다시 비교:



\`\`\`text

.empty()  → 요소 내부만 비움

.remove() → 요소 자체를 삭제

\`\`\`



\---



**# 42. before() / append()**



동적으로 만든 요소를 **\*\*DOM의 특정 위치에 넣을 때\*\*** 사용한다.



**## before()**



현재 요소의 **\*\*바로 앞 형제 위치\*\***&#xC5D0; 삽입한다.



**### JavaScript**



\`\`\`javascript

footer.before(previewList);

\`\`\`



**### jQuery**



\`\`\`javascript

$('.footer').before('\<div class="preview-add-list">\</div>');

\`\`\`



회사에서 프리뷰 자유블록 영역이 없을 때 생성할 때 사용했던 형태다.



**## append()**



선택한 요소의 **\*\*마지막 자식으로 추가\*\***&#xD55C;다.



**### JavaScript**



\`\`\`javascript

parent.append(child);

\`\`\`



**### jQuery**



\`\`\`javascript

$('.setting-list').append($row);

\`\`\`



\`\`\`text

before() → 선택 요소 앞에 형제로 삽입

append() → 선택 요소 안쪽 마지막 자식으로 삽입

\`\`\`



\---



**# 이번 복습: 회사 코드 한 번에 읽기**



아래 형태에는 이번에 정리한 문법이 여러 개 같이 들어 있다.



\`\`\`javascript

$(document).on('change', '.filehidden', function () {

    var file = this.files[0];

    var $admin = $(this).closest('.admin-cmn');



    if (!file) {

        return;

    }



    $(this).siblings('.filename').text(file.name);



    if ($admin.find('.switch-input').is(':checked')) {

        updatePreview($admin);

    }

});

\`\`\`



위에서부터 읽으면:



\`\`\`text

$(document).on(...)

→ 동적으로 생긴 .filehidden까지 change 이벤트 감지



this.files[0]

→ 현재 file input에서 선택한 첫 번째 파일



$(this).closest('.admin-cmn')

→ 현재 input을 감싸는 가장 가까운 관리자 블록 찾기



if (!file) return;

→ 파일이 없으면 함수 종료



$(this).siblings('.filename')

→ 같은 부모에 있는 filename 형제 요소 찾기



.text(file.name)

→ 선택한 파일 이름 표시



$admin.find('.switch-input')

→ 해당 관리자 블록 내부의 스위치 찾기



.is(':checked')

→ 스위치가 켜져 있는지 확인



updatePreview($admin)

→ 켜져 있으면 해당 관리자 영역 기준으로 프리뷰 업데이트

\`\`\`



이번 복습에서 묶어서 기억할 핵심:



\`\`\`text

밖으로 올라가기 → closest()

안으로 내려가기 → find()

옆 형제 찾기    → siblings()

몇 번째 고르기  → eq()

입력값           → val()

체크 상태 변경   → prop()

체크 상태 확인   → is(':checked')

내부 비우기      → empty()

요소 자체 삭제   → remove()

동적 이벤트      → $(document).on(...)

파일 가져오기    → this.files[0]

파일 읽기        → FileReader

\`\`\`



\---



**# JavaScript / jQuery 빠른 비교**



\`\`\`text

요소 찾기

JavaScript → document.querySelector('.btn')

jQuery     → $('.btn')



스타일 변경

JavaScript → element.style.display = 'none'

jQuery     → $(element).css('display', 'none')



숨기기

JavaScript → element.hidden = true

jQuery     → $(element).hide()



텍스트 변경

JavaScript → element.textContent = '메시지'

jQuery     → $(element).text('메시지')



class 추가

JavaScript → element.classList.add('active')

jQuery     → $(element).addClass('active')



class 제거

JavaScript → element.classList.remove('active')

jQuery     → $(element).removeClass('active')



class 확인

JavaScript → element.classList.contains('active')

jQuery     → $(element).hasClass('active')



class 토글

JavaScript → element.classList.toggle('active')

jQuery     → $(element).toggleClass('active')



클릭 이벤트

JavaScript → element.addEventListener('click', function () {})

jQuery     → $(element).on('click', function () {})



가장 가까운 부모 찾기

JavaScript → element.closest('.wrap')

jQuery     → $(element).closest('.wrap')



요소 개수

JavaScript → document.querySelectorAll('.item').length

jQuery     → $('.item').length



화면 너비

JavaScript → window\.innerWidth

jQuery     → $(window).width()



스크롤 위치

JavaScript → window\.scrollY

jQuery     → $(window).scrollTop()



형제 요소 찾기

JavaScript → parentElement.children / parentElement.querySelector()

jQuery     → .siblings()



자식·후손 찾기

JavaScript → element.querySelector() / querySelectorAll()

jQuery     → .find()



몇 번째 요소

JavaScript → nodeList[index]

jQuery     → .eq(index)



input 값

JavaScript → element.value

jQuery     → .val()



checkbox 상태 변경

JavaScript → element.checked = true / false

jQuery     → .prop('checked', true / false)



checkbox 상태 확인

JavaScript → element.checked

jQuery     → .is(':checked')



내부 자식 전부 제거

JavaScript → element.replaceChildren()

jQuery     → .empty()



요소 자체 삭제

JavaScript → element.remove()

jQuery     → .remove()



특정 요소 제외

JavaScript → filter() + matches()

jQuery     → .not()



동적 요소 이벤트

JavaScript → 상위 요소 addEventListener() + e.target.closest()

jQuery     → $(document).on('event', 'selector', handler)



파일 첫 번째 항목

JavaScript → input.files[0]

jQuery     → this.files[0]  // this는 실제 DOM 요소




forEach / each
JavaScript → nodeList.forEach(function (item) {})
jQuery     → .each(function () {})

체크된 요소 찾기
JavaScript → document.querySelectorAll('.item:checked')
jQuery     → $('.item:checked') / .filter(':checked')

파일 읽기

JavaScript → FileReader

jQuery     → 별도 대체 문법 없음



요소 앞에 삽입

JavaScript → element.before()

jQuery     → .before()



마지막 자식으로 삽입

JavaScript → parent.append()

jQuery     → .append()

\`\`\`



\---



**# JavaScript 문법이라 jQuery에서도 그대로 사용하는 것**



아래는 **\*\*jQuery 전용 대체 문법이 따로 있는 것이 아니라 JavaScript 문법 자체\*\***&#xC774;므로 둘 다 동일하게 사용한다.



\`\`\`text

||              OR

&&              AND

!               부정

\===             일치

!==             불일치

? :             삼항 연산자

if / else       조건문

function        함수

return          함수 종료 / 값 반환

event / e       이벤트 객체

e.target        실제 이벤트 발생 요소

e.preventDefault()

setTimeout()

FileReader          파일 읽기 Web API

\`\`\`



jQuery는 JavaScript를 대신하는 별개의 언어가 아니라 **\*\*JavaScript 라이브러리\*\***&#xC774;기 때문에, 기본 JavaScript 문법 위에서 jQuery 기능을 함께 사용한다.


---

# 43. forEach()

여러 개의 요소나 배열 값을 **하나씩 꺼내서 같은 작업을 반복**할 때 사용한다.

특히 `querySelectorAll()`로 여러 요소를 가져온 뒤 각각 처리할 때 자주 사용한다.

### JavaScript

예:

```javascript
var items = document.querySelectorAll('.item');

items.forEach(function (item) {
    console.log(item);
});
```

의미:

```text
items 안의 요소를 하나씩 꺼냄
↓
현재 꺼낸 요소를 item이라는 매개변수로 받음
↓
각 요소마다 같은 코드 실행
```

예를 들어 `.item`이 3개라면 반복하면서:

```text
item = 첫 번째 .item
item = 두 번째 .item
item = 세 번째 .item
```

처럼 현재 요소가 하나씩 들어온다.

`item`이라는 이름은 정해진 이름이 아니다.

```javascript
items.forEach(function (country) {
    console.log(country);
});
```

처럼 원하는 이름을 사용할 수 있다.

중요:

```text
querySelector()    → 요소 하나
querySelectorAll() → 요소 여러 개(NodeList)

여러 요소에 같은 작업을 반복
→ forEach() 사용 가능
```

체크박스 예:

```javascript
var whereItems = document.querySelectorAll('.item');

whereItems.forEach(function (item) {
    item.addEventListener('change', function () {
        console.log(this.checked);
    });
});
```

의미:

```text
개별 체크박스를 하나씩 꺼냄
↓
각 체크박스에 change 이벤트를 연결
```

### jQuery

jQuery에서는 비슷한 역할로 `.each()`를 사용할 수 있다.

```javascript
$('.item').each(function () {
    console.log(this);
});
```

또는 jQuery의 `.on()`은 선택된 여러 요소에 이벤트를 한 번에 연결할 수 있어서, 단순히 이벤트만 붙일 때는 `.each()`가 필요하지 않을 수도 있다.

```javascript
$('.item').on('change', function () {
    console.log($(this).prop('checked'));
});
```

```text
JavaScript → forEach()
jQuery     → .each()

여러 요소에 이벤트만 연결
JavaScript → forEach() + addEventListener()
jQuery     → 여러 요소 선택 후 .on()으로 한 번에 가능
```

---

# 44. 체크박스 전체 선택 / 전체 해제

여러 개의 개별 체크박스와 `전체` 체크박스를 서로 연동할 때 자주 사용한다.

HTML 예:

```html
<label>
    <input type="checkbox" value="all">
    전체
</label>

<label>
    <input type="checkbox" class="item" value="uk">
    영국
</label>

<label>
    <input type="checkbox" class="item" value="france">
    프랑스
</label>
```

## 개별 체크박스가 전부 체크되면 전체 체크

### JavaScript - forEach() 방식

```javascript
var whereAll = where.querySelector('input[value="all"]'); // 전체 체크박스
var whereItems = where.querySelectorAll('.item'); // 개별 체크박스들

whereItems.forEach(function (item) {

    // 개별 체크박스 하나의 상태가 바뀔 때 실행
    item.addEventListener('change', function () {

        // 일단 개별 체크박스가 모두 체크됐다고 가정
        var allChk = true;

        // 개별 체크박스를 다시 하나씩 확인
        whereItems.forEach(function (chk) {

            // 하나라도 체크 안 된 것이 있으면
            if (!chk.checked) {
                allChk = false;
            }
        });

        // 최종 결과를 전체 체크박스에 반영
        whereAll.checked = allChk;
    });

});
```

핵심:

```text
첫 번째 forEach()
→ 개별 체크박스마다 change 이벤트 연결

두 번째 forEach()
→ 개별 체크박스가 전부 체크됐는지 검사
```

`allChk`:

```javascript
var allChk = true;
```

의 의미:

```text
일단 "전부 체크됐다"고 가정
↓
하나라도 체크 안 된 항목 발견
↓
allChk = false
```

## 전체 개수와 체크된 개수 비교 방식

`forEach()` 없이 전체 개수와 체크된 개수를 비교할 수도 있다.

```javascript
var whereAll = where.querySelector('input[value="all"]');
var whereItems = where.querySelectorAll('.item');

where.addEventListener('change', function () {

    var checkedItems = where.querySelectorAll('.item:checked');

    if (whereItems.length === checkedItems.length) {
        whereAll.checked = true;
    } else {
        whereAll.checked = false;
    }
});
```

의미:

```text
whereItems.length
→ 개별 체크박스 전체 개수

checkedItems.length
→ 현재 체크된 개별 체크박스 개수

두 개수가 같음
→ 전부 체크됨
→ 전체 체크박스 체크
```

### jQuery

```javascript
var $whereAll = $('.search-where input[value="all"]');
var $whereItems = $('.search-where .item');

$whereItems.on('change', function () {

    if ($whereItems.length === $whereItems.filter(':checked').length) {
        $whereAll.prop('checked', true);
    } else {
        $whereAll.prop('checked', false);
    }

});
```

```text
JavaScript
→ querySelectorAll('.item:checked').length

jQuery
→ $items.filter(':checked').length
```

## 전체 체크박스 클릭 시 개별 전체 선택 / 해제

### JavaScript

```javascript
whereAll.addEventListener('change', function () {

    whereItems.forEach(function (item) {
        item.checked = whereAll.checked;
    });

});
```

의미:

```text
전체 체크박스가 체크됨
→ whereAll.checked = true
→ 모든 item.checked = true

전체 체크박스가 해제됨
→ whereAll.checked = false
→ 모든 item.checked = false
```

### jQuery

```javascript
$whereAll.on('change', function () {
    $whereItems.prop('checked', $(this).prop('checked'));
});
```

```text
JavaScript → element.checked
jQuery     → .prop('checked', ...)
```

---

# 45. :checked 선택자

현재 체크된 `checkbox` 또는 `radio`만 선택할 때 사용한다.

### JavaScript

```javascript
var checkedItems = document.querySelectorAll('.item:checked');
```

현재 체크된 `.item`만 가져온다.

개수 확인:

```javascript
var checkedCount = document.querySelectorAll('.item:checked').length;
```

### jQuery

```javascript
$('.item:checked');
```

또는 이미 선택해둔 jQuery 객체에서 체크된 요소만 걸러낼 수 있다.

```javascript
var $items = $('.item');
var $checkedItems = $items.filter(':checked');
```

```text
JavaScript → querySelectorAll('.item:checked')
jQuery     → $('.item:checked')
           또는 .filter(':checked')
```

---

# 46. NodeList

`querySelectorAll()`을 사용하면 여러 요소가 **NodeList 형태**로 반환된다.

```javascript
var items = document.querySelectorAll('.item');
```

`items`는 요소 하나가 아니라 여러 요소가 들어 있는 목록이다.

예:

```text
items[0] → 첫 번째 .item
items[1] → 두 번째 .item
items[2] → 세 번째 .item
```

개수:

```javascript
items.length
```

여러 요소를 각각 처리하려면:

```javascript
items.forEach(function (item) {

});
```

처럼 반복해서 사용한다.

중요:

```text
querySelector()
→ 요소 하나
→ 바로 addEventListener() 사용 가능

querySelectorAll()
→ 여러 요소(NodeList)
→ NodeList 자체에 addEventListener()를 바로 사용할 수 없음
→ 각각의 요소에 이벤트를 연결해야 함
```

잘못된 예:

```javascript
var items = document.querySelectorAll('.item');

items.addEventListener('change', function () {
});
```

올바른 예:

```javascript
var items = document.querySelectorAll('.item');

items.forEach(function (item) {
    item.addEventListener('change', function () {
    });
});
```

---

# 47. hidden과 display:none 차이

`hidden`은 HTML 기본 속성이고, `display:none`은 CSS로 요소를 숨기는 방식이다.

HTML:

```html
<div class="search-where" hidden>
    여행지
</div>
```

### JavaScript

```javascript
where.hidden = true;  // 숨김
where.hidden = false; // 보여줌
```

날짜 값이 있을 때만 보여주는 예:

```javascript
date.addEventListener('change', function () {
    where.hidden = !this.value;
});
```

의미:

```text
this.value 있음
→ !this.value = false
→ hidden = false
→ 보여줌

this.value 없음
→ !this.value = true
→ hidden = true
→ 숨김
```

주의:

HTML에 다음처럼 `display:none`을 직접 넣어둔 상태에서:

```html
<div class="search-where" style="display:none;">
```

JavaScript에서:

```javascript
where.hidden = false;
```

만 실행해도 `style="display:none;"`은 그대로 남아 있기 때문에 화면에 보이지 않는다.

따라서 한 기능에서는 숨김 방식을 되도록 통일한다.

```text
hidden 방식
→ HTML: hidden
→ JavaScript: element.hidden = true / false

display 방식
→ CSS 또는 style.display 사용
```

jQuery에서는 보통:

```javascript
$(element).hide();
$(element).show();
```

또는:

```javascript
$(element).prop('hidden', true);
$(element).prop('hidden', false);
```

를 사용한다.

