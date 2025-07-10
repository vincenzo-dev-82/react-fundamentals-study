# 0.2 CSS란 무엇인가?

## CSS 소개

CSS(Cascading Style Sheets)는 HTML 문서의 스타일과 레이아웃을 정의하는 스타일시트 언어입니다. HTML이 웹 페이지의 구조를 담당한다면, CSS는 그 구조를 시각적으로 아름답게 표현하는 역할을 합니다.

## CSS의 기본 문법

```css
선택자 {
    속성: 값;
    속성: 값;
}
```

### 예시

```css
h1 {
    color: blue;
    font-size: 24px;
    text-align: center;
}
```

## CSS를 적용하는 방법

### 1. 인라인 스타일

```html
<p style="color: red; font-size: 16px;">빨간색 텍스트</p>
```

### 2. 내부 스타일시트

```html
<head>
    <style>
        p {
            color: blue;
            font-size: 16px;
        }
    </style>
</head>
```

### 3. 외부 스타일시트 (권장)

```html
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```

## CSS 선택자

### 기본 선택자

```css
/* 요소 선택자 */
p {
    color: black;
}

/* 클래스 선택자 */
.my-class {
    background-color: yellow;
}

/* ID 선택자 */
#my-id {
    border: 1px solid black;
}

/* 전체 선택자 */
* {
    margin: 0;
    padding: 0;
}
```

### 복합 선택자

```css
/* 자손 선택자 */
div p {
    color: blue;
}

/* 자식 선택자 */
div > p {
    color: red;
}

/* 인접 형제 선택자 */
h1 + p {
    margin-top: 0;
}

/* 일반 형제 선택자 */
h1 ~ p {
    color: gray;
}
```

### 가상 클래스와 가상 요소

```css
/* 가상 클래스 */
a:hover {
    color: red;
}

button:active {
    background-color: darkblue;
}

input:focus {
    border-color: blue;
}

/* 가상 요소 */
p::first-line {
    font-weight: bold;
}

p::before {
    content: "→ ";
}
```

## 박스 모델

CSS의 모든 요소는 박스 모델을 따릅니다:

```css
.box {
    width: 300px;
    height: 200px;
    padding: 20px;      /* 내부 여백 */
    border: 5px solid black;  /* 테두리 */
    margin: 30px;       /* 외부 여백 */
}
```

### box-sizing

```css
/* 기본값: content-box */
.box1 {
    box-sizing: content-box;
    width: 300px;  /* 콘텐츠 영역만 300px */
}

/* border-box (권장) */
.box2 {
    box-sizing: border-box;
    width: 300px;  /* padding과 border 포함해서 300px */
}
```

## 레이아웃

### Display 속성

```css
.block {
    display: block;      /* 블록 요소 */
}

.inline {
    display: inline;     /* 인라인 요소 */
}

.inline-block {
    display: inline-block;  /* 인라인-블록 요소 */
}

.none {
    display: none;       /* 요소 숨기기 */
}
```

### Position 속성

```css
.static {
    position: static;    /* 기본값 */
}

.relative {
    position: relative;  /* 상대 위치 */
    top: 10px;
    left: 20px;
}

.absolute {
    position: absolute;  /* 절대 위치 */
    top: 0;
    right: 0;
}

.fixed {
    position: fixed;     /* 고정 위치 */
    bottom: 0;
    left: 0;
}
```

### Flexbox

```css
.container {
    display: flex;
    justify-content: center;    /* 주축 정렬 */
    align-items: center;        /* 교차축 정렬 */
    flex-direction: row;        /* 방향 설정 */
    flex-wrap: wrap;           /* 줄바꿈 설정 */
}

.item {
    flex: 1;                   /* 유연한 크기 */
}
```

### Grid

```css
.grid-container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;  /* 3개 열 */
    grid-gap: 10px;                      /* 간격 */
}

.grid-item {
    grid-column: span 2;                 /* 2개 열 차지 */
}
```

## 반응형 디자인

### 미디어 쿼리

```css
/* 기본 스타일 */
.container {
    width: 100%;
    padding: 20px;
}

/* 태블릿 */
@media (min-width: 768px) {
    .container {
        width: 750px;
        margin: 0 auto;
    }
}

/* 데스크톱 */
@media (min-width: 1024px) {
    .container {
        width: 960px;
    }
}
```

## CSS 변수 (사용자 정의 속성)

```css
:root {
    --primary-color: #007bff;
    --secondary-color: #6c757d;
    --font-size-base: 16px;
}

.button {
    background-color: var(--primary-color);
    font-size: var(--font-size-base);
}
```

## 애니메이션과 트랜지션

### 트랜지션

```css
.button {
    background-color: blue;
    transition: background-color 0.3s ease;
}

.button:hover {
    background-color: darkblue;
}
```

### 애니메이션

```css
@keyframes slide-in {
    from {
        transform: translateX(-100%);
    }
    to {
        transform: translateX(0);
    }
}

.animated {
    animation: slide-in 1s ease-out;
}
```

## React에서 CSS 사용하기

React에서는 여러 방법으로 CSS를 적용할 수 있습니다:

1. **일반 CSS 파일**: `import './styles.css'`
2. **CSS Modules**: `import styles from './styles.module.css'`
3. **CSS-in-JS**: styled-components, emotion 등
4. **인라인 스타일**: `style={{ color: 'red' }}`

## 요약

- CSS는 웹 페이지의 시각적 표현을 담당
- 선택자를 통해 HTML 요소를 선택하고 스타일 적용
- 박스 모델, 레이아웃, 반응형 디자인 등 다양한 개념 포함
- React에서도 CSS는 필수적인 요소

다음 장에서는 웹 개발의 핵심 언어인 자바스크립트에 대해 알아보겠습니다.