# 0.4 개발 환경 설정하기

## 개발 환경이란?

개발 환경은 코드를 작성하고, 테스트하고, 실행하는 데 필요한 모든 도구와 설정을 말합니다. React 개발을 위해서는 적절한 개발 환경 구성이 필수적입니다.

## 필수 도구 설치

### 1. Node.js와 npm

Node.js는 자바스크립트를 브라우저 밖에서 실행할 수 있게 해주는 런타임입니다. npm(Node Package Manager)은 Node.js와 함께 설치되는 패키지 관리자입니다.

#### 설치 방법

1. [Node.js 공식 웹사이트](https://nodejs.org)에서 LTS 버전 다운로드
2. 설치 후 터미널에서 확인:

```bash
# Node.js 버전 확인
node --version
# v18.17.0 (예시)

# npm 버전 확인
npm --version
# 9.6.7 (예시)
```

### 2. 코드 에디터 (VS Code)

Visual Studio Code는 가장 인기 있는 코드 에디터 중 하나입니다.

#### VS Code 설치

1. [VS Code 공식 웹사이트](https://code.visualstudio.com)에서 다운로드
2. 설치 후 실행

#### 유용한 VS Code 확장 프로그램

- **ES7+ React/Redux/React-Native snippets**: React 코드 스니펫
- **Prettier**: 코드 포맷터
- **ESLint**: 코드 린터
- **Auto Rename Tag**: HTML/JSX 태그 자동 수정
- **Bracket Pair Colorizer**: 괄호 쌍 색상 구분
- **Live Server**: 라이브 프리뷰

### 3. Git

버전 관리 시스템인 Git은 코드의 변경 사항을 추적하고 협업을 가능하게 합니다.

#### Git 설치

```bash
# macOS (Homebrew 사용)
brew install git

# Windows
# Git 공식 웹사이트에서 다운로드: https://git-scm.com

# 설치 확인
git --version
```

#### Git 기본 설정

```bash
# 사용자 이름 설정
git config --global user.name "Your Name"

# 이메일 설정
git config --global user.email "your.email@example.com"
```

## React 프로젝트 생성

### Create React App 사용하기

Create React App은 React 프로젝트를 쉽게 시작할 수 있게 해주는 도구입니다.

```bash
# 새 React 프로젝트 생성
npx create-react-app my-app

# 프로젝트 디렉토리로 이동
cd my-app

# 개발 서버 시작
npm start
```

### 프로젝트 구조

```
my-app/
├── node_modules/      # 설치된 패키지들
├── public/           # 정적 파일들
│   ├── index.html
│   └── favicon.ico
├── src/              # 소스 코드
│   ├── App.css
│   ├── App.js
│   ├── App.test.js
│   ├── index.css
│   ├── index.js
│   └── logo.svg
├── .gitignore        # Git 무시 파일
├── package.json      # 프로젝트 설정 및 의존성
├── package-lock.json # 의존성 잠금 파일
└── README.md         # 프로젝트 설명
```

## 브라우저 개발자 도구

### Chrome DevTools

1. **Elements**: HTML/CSS 검사 및 수정
2. **Console**: 자바스크립트 디버깅
3. **Network**: 네트워크 요청 모니터링
4. **Sources**: 소스 코드 디버깅
5. **Application**: 로컬 스토리지, 쿠키 등 확인

### React Developer Tools

React 컴포넌트를 검사할 수 있는 브라우저 확장 프로그램입니다.

1. Chrome 웹 스토어에서 "React Developer Tools" 검색
2. 확장 프로그램 설치
3. 개발자 도구에서 "Components"와 "Profiler" 탭 확인

## 터미널/명령 프롬프트 사용법

### 기본 명령어

```bash
# 현재 디렉토리 확인
pwd

# 디렉토리 내용 보기
ls  # macOS/Linux
dir # Windows

# 디렉토리 이동
cd 폴더명
cd ..  # 상위 디렉토리로

# 디렉토리 생성
mkdir 폴더명

# 파일 생성
touch 파일명  # macOS/Linux
type nul > 파일명  # Windows

# 파일/폴더 삭제
rm 파일명
rm -rf 폴더명  # 폴더와 내용 모두 삭제
```

### npm 명령어

```bash
# 패키지 설치
npm install 패키지명
npm install  # package.json의 모든 의존성 설치

# 개발 의존성으로 설치
npm install --save-dev 패키지명

# 전역 설치
npm install -g 패키지명

# 패키지 제거
npm uninstall 패키지명

# 스크립트 실행
npm start
npm run build
npm test
```

## 추가 도구 및 설정

### Prettier 설정

`.prettierrc` 파일 생성:

```json
{
  "semi": true,
  "trailingComma": "es5",
  "singleQuote": true,
  "printWidth": 80,
  "tabWidth": 2
}
```

### ESLint 설정

`.eslintrc.json` 파일:

```json
{
  "extends": [
    "react-app",
    "react-app/jest"
  ],
  "rules": {
    "no-console": "warn",
    "no-unused-vars": "warn"
  }
}
```

### VS Code 설정

`.vscode/settings.json`:

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "emmet.includeLanguages": {
    "javascript": "javascriptreact"
  }
}
```

## 개발 워크플로우

### 1. 프로젝트 시작

```bash
# 프로젝트 생성
npx create-react-app my-project
cd my-project

# Git 초기화 (이미 되어 있음)
git init

# 개발 서버 시작
npm start
```

### 2. 코드 작성

1. VS Code에서 프로젝트 열기
2. 컴포넌트 작성
3. 저장 시 자동 포맷팅 (Prettier)
4. 브라우저에서 실시간 확인 (Hot Reload)

### 3. 버전 관리

```bash
# 변경 사항 확인
git status

# 변경 사항 추가
git add .

# 커밋
git commit -m "Add new feature"

# 원격 저장소에 푸시
git push origin main
```

### 4. 빌드 및 배포

```bash
# 프로덕션 빌드
npm run build

# build 폴더가 생성됨
# 이 폴더의 내용을 웹 서버에 배포
```

## 문제 해결 팁

### 자주 발생하는 문제들

1. **포트 충돌**: 기본 포트(3000)가 사용 중일 때
   ```bash
   # 다른 포트로 실행
   PORT=3001 npm start
   ```

2. **npm 캐시 문제**:
   ```bash
   npm cache clean --force
   ```

3. **node_modules 재설치**:
   ```bash
   rm -rf node_modules package-lock.json
   npm install
   ```

## 요약

- Node.js, VS Code, Git은 React 개발의 필수 도구
- Create React App으로 쉽게 프로젝트 시작 가능
- 개발자 도구와 확장 프로그램 활용으로 생산성 향상
- 터미널 명령어와 npm 사용법 숙지 필요
- 적절한 개발 환경 설정으로 효율적인 개발 가능

이제 개발 환경이 준비되었으니, 다음 장부터 본격적으로 React를 학습해보겠습니다!