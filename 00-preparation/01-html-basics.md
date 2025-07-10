# 0.1 HTML 살펴보기

## HTML이란?

HTML(HyperText Markup Language)은 웹 페이지의 구조와 내용을 정의하는 마크업 언어입니다. 웹 브라우저는 HTML 문서를 해석하여 사용자에게 시각적으로 표현합니다.

## HTML의 기본 구조

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>문서 제목</title>
</head>
<body>
    <h1>안녕하세요!</h1>
    <p>이것은 단락입니다.</p>
</body>
</html>
```

### 주요 구성 요소

1. **`<!DOCTYPE html>`**: HTML5 문서임을 선언
2. **`<html>`**: HTML 문서의 루트 요소
3. **`<head>`**: 문서의 메타데이터를 포함
4. **`<body>`**: 실제 표시되는 콘텐츠를 포함

## 주요 HTML 태그들

### 텍스트 관련 태그

```html
<h1>제목 1</h1>
<h2>제목 2</h2>
<h3>제목 3</h3>
<p>단락</p>
<span>인라인 텍스트</span>
<strong>굵은 글씨(중요)</strong>
<em>기울임 글씨(강조)</em>
```

### 링크와 이미지

```html
<a href="https://www.example.com">링크 텍스트</a>
<img src="image.jpg" alt="이미지 설명">
```

### 목록

```html
<!-- 순서 없는 목록 -->
<ul>
    <li>항목 1</li>
    <li>항목 2</li>
</ul>

<!-- 순서 있는 목록 -->
<ol>
    <li>첫 번째</li>
    <li>두 번째</li>
</ol>
```

### 컨테이너 요소

```html
<div>블록 레벨 컨테이너</div>
<section>의미론적 섹션</section>
<article>독립적인 콘텐츠</article>
<header>헤더 영역</header>
<footer>푸터 영역</footer>
<nav>네비게이션</nav>
```

## 폼 요소

```html
<form>
    <label for="name">이름:</label>
    <input type="text" id="name" name="name">
    
    <label for="email">이메일:</label>
    <input type="email" id="email" name="email">
    
    <button type="submit">제출</button>
</form>
```

## HTML 속성

모든 HTML 요소는 속성을 가질 수 있습니다:

- **`class`**: CSS 스타일링을 위한 클래스 지정
- **`id`**: 요소의 고유 식별자
- **`style`**: 인라인 스타일 지정
- **`data-*`**: 사용자 정의 데이터 속성

```html
<div class="container" id="main-container" data-value="123">
    콘텐츠
</div>
```

## 시맨틱 HTML

시맨틱(Semantic) HTML은 의미를 가진 태그를 사용하여 문서 구조를 명확히 하는 것입니다:

```html
<main>
    <article>
        <header>
            <h1>기사 제목</h1>
            <time datetime="2024-01-01">2024년 1월 1일</time>
        </header>
        <section>
            <p>기사 내용...</p>
        </section>
        <footer>
            <p>작성자: 홍길동</p>
        </footer>
    </article>
</main>
```

## React에서 HTML의 역할

React 애플리케이션에서도 HTML은 여전히 중요합니다:

1. **루트 요소**: React 앱이 마운트될 HTML 요소가 필요
2. **SEO**: 초기 HTML 구조는 검색 엔진 최적화에 중요
3. **접근성**: 올바른 HTML 사용은 웹 접근성 향상에 필수

## 요약

- HTML은 웹 페이지의 구조와 내용을 정의하는 마크업 언어
- 다양한 태그를 통해 콘텐츠를 구조화
- 시맨틱 HTML 사용으로 의미 있는 문서 구조 생성
- React 개발에서도 HTML의 기초는 매우 중요

다음 장에서는 HTML을 꾸미는 CSS에 대해 알아보겠습니다.