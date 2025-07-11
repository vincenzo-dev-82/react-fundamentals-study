# 1.1 리액트는 무엇인가?

## React 소개

React는 Facebook(현재 Meta)에서 개발한 사용자 인터페이스(UI)를 만들기 위한 자바스크립트 라이브러리입니다. 2013년에 처음 공개되었으며, 현재 가장 인기 있는 프론트엔드 프레임워크 중 하나입니다.

### React의 핵심 개념

1. **컴포넌트 기반**: UI를 재사용 가능한 컴포넌트로 나누어 개발
2. **선언적 프로그래밍**: UI가 어떻게 보여야 하는지 선언
3. **Virtual DOM**: 효율적인 DOM 업데이트
4. **단방향 데이터 흐름**: 예측 가능한 데이터 흐름

## React의 탄생 배경

### 기존 웹 개발의 문제점

1. **복잡한 DOM 조작**: jQuery 등으로 직접 DOM을 조작하는 방식의 한계
2. **코드 재사용성 부족**: 비슷한 UI를 반복적으로 작성
3. **상태 관리의 어려움**: 애플리케이션이 커질수록 상태 관리가 복잡

### React의 해결책

```javascript
// 기존 방식 (명령형)
document.getElementById('myDiv').innerHTML = '<h1>Hello</h1>';
document.getElementById('myDiv').style.color = 'red';

// React 방식 (선언형)
function MyComponent() {
    return <h1 style={{color: 'red'}}>Hello</h1>;
}
```

## React의 주요 특징

### 1. 컴포넌트 (Component)

컴포넌트는 React의 기본 빌딩 블록입니다. 각 컴포넌트는 독립적이고 재사용 가능합니다.

```javascript
// 함수 컴포넌트 예시
function Welcome(props) {
    return <h1>안녕하세요, {props.name}님!</h1>;
}

// 컴포넌트 사용
<Welcome name="홍길동" />
```

### 2. JSX (JavaScript XML)

JSX는 JavaScript의 확장 문법으로, HTML과 유사한 문법을 사용하여 UI를 표현합니다.

```javascript
// JSX 예시
const element = (
    <div>
        <h1>Hello, World!</h1>
        <p>React를 배워봅시다.</p>
    </div>
);
```

### 3. Virtual DOM

Virtual DOM은 실제 DOM의 가상 표현입니다. React는 Virtual DOM을 사용하여 효율적으로 UI를 업데이트합니다.

```
1. 상태 변경 발생
2. 새로운 Virtual DOM 생성
3. 이전 Virtual DOM과 비교 (Diffing)
4. 변경된 부분만 실제 DOM에 반영
```

### 4. 단방향 데이터 바인딩

데이터가 부모에서 자식으로 한 방향으로만 흐릅니다.

```javascript
function Parent() {
    const [data, setData] = useState('Hello');
    
    return <Child message={data} />;
}

function Child(props) {
    return <p>{props.message}</p>;
}
```

## React의 생태계

### 주요 라이브러리와 도구

1. **React Router**: 라우팅 관리
2. **Redux/MobX**: 상태 관리
3. **Next.js**: 서버 사이드 렌더링
4. **Create React App**: 프로젝트 시작 도구
5. **React Native**: 모바일 앱 개발

### 커뮤니티와 지원

- 활발한 오픈소스 커뮤니티
- 풍부한 학습 자료와 문서
- 대기업들의 적극적인 사용과 지원

## React를 사용하는 이유

### 1. 생산성 향상

- 컴포넌트 재사용으로 개발 속도 향상
- 명확한 구조로 유지보수 용이

### 2. 성능 최적화

- Virtual DOM을 통한 효율적인 렌더링
- 필요한 부분만 업데이트

### 3. 풍부한 생태계

- 다양한 라이브러리와 도구
- 활발한 커뮤니티 지원

### 4. 학습 곡선

- JavaScript 기반으로 진입 장벽이 낮음
- 점진적으로 학습 가능

## React vs 다른 프레임워크

### React vs Angular

- React: 라이브러리, 유연함, 학습 곡선이 완만
- Angular: 풀 프레임워크, 많은 기능 내장, 학습 곡선이 가파름

### React vs Vue

- React: 더 큰 생태계, 더 많은 일자리
- Vue: 더 쉬운 학습, 템플릿 기반

## 요약

- React는 UI를 만들기 위한 JavaScript 라이브러리
- 컴포넌트 기반의 선언적 프로그래밍 방식
- Virtual DOM을 통한 효율적인 렌더링
- 풍부한 생태계와 커뮤니티 지원
- 현대 웹 개발의 핵심 기술 중 하나

다음 장에서는 React의 구체적인 장점들에 대해 더 자세히 알아보겠습니다.