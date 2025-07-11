# 1.3 리액트의 단점

## 개요

모든 기술에는 장단점이 있듯이, React도 완벽하지 않습니다. React를 제대로 활용하기 위해서는 장점뿐만 아니라 단점도 이해하고 있어야 합니다. 이번 장에서는 React의 주요 단점들과 그에 대한 대응 방안을 살펴보겠습니다.

## 1. 가파른 초기 학습 곡선

### JSX 문법의 생소함

JSX는 처음 보는 개발자에게는 혼란스러울 수 있습니다.

```javascript
// HTML도 아니고 JavaScript도 아닌 것 같은 문법
function App() {
    const isLoggedIn = true;
    
    return (
        <div className="app">  {/* HTML의 class가 아닌 className */}
            {isLoggedIn ? <UserDashboard /> : <LoginForm />}
            <button onClick={() => console.log('clicked')}>
                클릭
            </button>
        </div>
    );
}
```

### 새로운 개념들

- Virtual DOM
- 단방향 데이터 바인딩
- 상태(State)와 속성(Props)
- 생명주기 메서드
- Hooks

## 2. 방대한 생태계로 인한 선택 장애

### 너무 많은 선택지

```javascript
// 상태 관리만 해도...
// Redux, MobX, Recoil, Zustand, Context API, Jotai...

// 스타일링도...
// CSS Modules, styled-components, emotion, Tailwind CSS...

// 라우팅도...
// React Router, Reach Router, TanStack Router...
```

### 빠르게 변하는 베스트 프랙티스

```javascript
// 2018년: 클래스 컴포넌트가 표준
class MyComponent extends React.Component {
    state = { count: 0 };
    
    render() {
        return <div>{this.state.count}</div>;
    }
}

// 2019년 이후: 함수 컴포넌트 + Hooks가 표준
function MyComponent() {
    const [count, setCount] = useState(0);
    return <div>{count}</div>;
}
```

## 3. 보일러플레이트 코드

### 간단한 기능에도 많은 코드 필요

```javascript
// 간단한 폼 하나 만드는데도...
function ContactForm() {
    const [formData, setFormData] = useState({
        name: '',
        email: '',
        message: ''
    });
    
    const [errors, setErrors] = useState({});
    const [isSubmitting, setIsSubmitting] = useState(false);
    
    const handleChange = (e) => {
        const { name, value } = e.target;
        setFormData(prev => ({
            ...prev,
            [name]: value
        }));
    };
    
    const validate = () => {
        const newErrors = {};
        if (!formData.name) newErrors.name = '이름은 필수입니다';
        if (!formData.email) newErrors.email = '이메일은 필수입니다';
        // ... 더 많은 검증
        return newErrors;
    };
    
    const handleSubmit = async (e) => {
        e.preventDefault();
        const newErrors = validate();
        if (Object.keys(newErrors).length > 0) {
            setErrors(newErrors);
            return;
        }
        
        setIsSubmitting(true);
        try {
            // API 호출
        } finally {
            setIsSubmitting(false);
        }
    };
    
    // ... 렌더링 코드
}
```

## 4. SEO 문제

### 클라이언트 사이드 렌더링의 한계

```javascript
// 기본 React 앱은 초기 HTML이 비어있음
// index.html
<div id="root"></div>

// 검색 엔진이 JavaScript를 실행하기 전까지는
// 콘텐츠를 볼 수 없음
```

### 해결책의 복잡성

- Server Side Rendering (SSR) 구현 복잡
- Next.js 같은 프레임워크 학습 필요
- 서버 인프라 고려사항 증가

## 5. 번들 크기 문제

### 기본 번들 크기가 큼

```bash
# Create React App의 기본 프로덕션 빌드
# React + React-DOM ≈ 45KB (gzipped)
# 추가 라이브러리들이 계속 더해짐
```

### 의존성 관리의 어려움

```json
// package.json
{
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.8.0",
    "axios": "^1.3.0",
    "redux": "^4.2.0",
    "react-redux": "^8.0.5",
    // ... 계속 늘어나는 의존성들
  }
}
```

## 6. 과도한 리렌더링

### 성능 문제 발생 가능성

```javascript
// 잘못된 예시 - 모든 자식이 리렌더링됨
function Parent() {
    const [count, setCount] = useState(0);
    
    // 이 객체는 매번 새로 생성됨
    const childProps = {
        data: { value: 'constant' }
    };
    
    return (
        <div>
            <button onClick={() => setCount(count + 1)}>증가</button>
            <ExpensiveChild props={childProps} />
        </div>
    );
}
```

### 최적화의 복잡성

```javascript
// React.memo, useMemo, useCallback 등을 적절히 사용해야 함
const ExpensiveChild = React.memo(({ props }) => {
    // 복잡한 계산
    return <div>{/* ... */}</div>
});

function Parent() {
    const [count, setCount] = useState(0);
    
    // 메모이제이션 필요
    const childProps = useMemo(() => ({
        data: { value: 'constant' }
    }), []);
    
    return (
        <div>
            <button onClick={() => setCount(count + 1)}>증가</button>
            <ExpensiveChild props={childProps} />
        </div>
    );
}
```

## 7. 디버깅의 어려움

### 복잡한 에러 메시지

```
// React 에러 메시지 예시
Warning: Can't perform a React state update on an unmounted component. 
This is a no-op, but it indicates a memory leak in your application. 
To fix, cancel all subscriptions and asynchronous tasks in a useEffect cleanup function.
    at UserProfile (http://localhost:3000/static/js/bundle.js:1234:5)
    at div
    at App
```

### 비동기 처리의 복잡성

```javascript
function UserProfile({ userId }) {
    const [user, setUser] = useState(null);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState(null);
    
    useEffect(() => {
        let cancelled = false;
        
        async function fetchUser() {
            try {
                setLoading(true);
                const response = await api.getUser(userId);
                if (!cancelled) {
                    setUser(response.data);
                }
            } catch (err) {
                if (!cancelled) {
                    setError(err.message);
                }
            } finally {
                if (!cancelled) {
                    setLoading(false);
                }
            }
        }
        
        fetchUser();
        
        return () => {
            cancelled = true;
        };
    }, [userId]);
    
    // ... 렌더링 로직
}
```

## 8. 테스팅의 복잡성

### 환경 설정의 복잡함

```javascript
// jest.config.js, setupTests.js, 각종 mock 설정...
// 테스트 환경 구성이 복잡함
```

### 비동기 테스트의 어려움

```javascript
test('사용자 데이터를 로드한다', async () => {
    const { getByText, findByText } = render(<UserProfile userId={1} />);
    
    // 로딩 상태 확인
    expect(getByText('Loading...')).toBeInTheDocument();
    
    // 데이터 로드 대기
    const userName = await findByText('John Doe');
    expect(userName).toBeInTheDocument();
});
```

## 9. 타입 안정성 부족

### JavaScript의 동적 타이핑

```javascript
// props의 타입을 실수로 잘못 전달해도 런타임에만 발견
function UserCard({ user }) {
    // user가 undefined일 수도 있음
    return <div>{user.name}</div>;  // 에러 발생 가능
}

// 어디선가...
<UserCard user={null} />  // 런타임 에러!
```

### PropTypes의 한계

```javascript
// PropTypes는 런타임 검사만 제공
UserCard.propTypes = {
    user: PropTypes.shape({
        name: PropTypes.string.isRequired,
        email: PropTypes.string.isRequired
    }).isRequired
};
```

## 10. 상태 관리의 복잡성

### Props Drilling

```javascript
// 깊은 컴포넌트 트리에서 props 전달이 복잡해짐
function App() {
    const [user, setUser] = useState(null);
    
    return <Dashboard user={user} />;
}

function Dashboard({ user }) {
    return <Header user={user} />;
}

function Header({ user }) {
    return <UserMenu user={user} />;
}

function UserMenu({ user }) {
    return <div>{user?.name}</div>;
}
```

## 대응 방안

### 1. 학습 곡선 완화
- 단계별 학습 계획 수립
- 공식 문서와 튜토리얼 활용
- 작은 프로젝트부터 시작

### 2. 도구 선택
- 프로젝트 요구사항에 맞는 최소한의 도구 선택
- 팀 내 표준 정립

### 3. 코드 품질
- ESLint, Prettier 등 도구 활용
- 컴포넌트 라이브러리 구축
- 코드 리뷰 문화

### 4. 성능 최적화
- React DevTools Profiler 활용
- 필요한 곳에만 최적화 적용
- 번들 크기 모니터링

### 5. TypeScript 도입
```typescript
interface UserCardProps {
    user: {
        name: string;
        email: string;
    };
}

function UserCard({ user }: UserCardProps) {
    return <div>{user.name}</div>;
}
```

## 요약

React의 주요 단점들:

1. **가파른 초기 학습 곡선**: 새로운 개념과 문법
2. **방대한 생태계**: 선택 장애와 결정 피로
3. **보일러플레이트**: 간단한 기능에도 많은 코드 필요
4. **SEO 문제**: CSR의 한계
5. **번들 크기**: 기본 크기가 크고 쉽게 증가
6. **리렌더링 이슈**: 성능 최적화의 복잡성
7. **디버깅 어려움**: 복잡한 에러와 비동기 처리
8. **테스팅 복잡성**: 환경 설정과 비동기 테스트
9. **타입 안정성**: JavaScript의 한계
10. **상태 관리**: Props drilling과 복잡성

이러한 단점들에도 불구하고 React는 여전히 훌륭한 선택입니다. 중요한 것은 이러한 단점들을 인지하고, 적절한 대응 방안을 마련하여 프로젝트에 적용하는 것입니다.

다음 장부터는 React를 실제로 사용하는 방법에 대해 알아보겠습니다!