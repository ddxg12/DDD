# 202130235 최한솔
<hr>  

## 10.01 6주차
#### client-side transitions  
- 일반적으로 서버렌더링 페이지로 이동하면 전체 페이지가 업로드 됩니다. 이로 인해 state가 삭제되고, 스크롤 위치가 재설정되며 상호작용이 차단됨  
- next.js는 link 컴포넌트를 사용하는 클라이언트 측 전환을 통해 이를 방지하고 페이지를 다시 로딩하ㅡㄴ 대신  다음과 같은 방법으로 콘텐츠를 동적으로 업데이트합니다.   
- 공유 레이아웃과 UI를 유지  
- 현재 페이지를 미리 가져온 로딩 상태 또는 사용 가능한 경우 새 페이지로 바꿈  
- 클라이언트 측 전환은 서버에서 렌더링된 앱을 클라이언트에서 렌더링된 앱처럼 느껴지게 하는 요소  
- 또한 프리페칭 및 스트리밍과 함께 사용하면 동적 경로에서 빠른 전환 가능  
#### 네비게이션 작동 방식  
- root page 간단히 작성  
- blog 디렉토리 만들고 간단한 page와 로딩 스켙톤  
- rootrayout에 link 컴포넌트를 이용해서 blog네비게이션 만듬  
#### await이 없어도 async를 붙여 두는 이유  
- next.js의 app router에서 page.tsx 같은 server.component는 비동기 렌더링을 전제로 함  
- 즉 page.tsx안에서 데이터를 fetch하는 경우가 많기 때문에 async를 기본으로 붙여도 문제 없음
- 1. 일관성 유지 : 같은 프로젝트 안에서 어떤 페이지는 async, 어떤 페이지는 일반 fucntion이면 혼란스러울 수 있음.  
- 2. 확장성 : 지금은 더미 데이터를 쓰지만, 나중에 DB나 API에서 데이터를 가져올 때 AWAIT FETCH 같은 코드가 들어갈 수 있기 때문에, 미리 ASYNC를 붙여두면 수정할 필요 없음  
- 3. REACT SERVER COMPONENT 호환성: SERVER COMPONENT는 PROMISE를 반환할 수 있어야 하고 NEXT.JS는 내부적으로 ASYNC 함수 패턴에 맞춰 최적화된 렌더링 파이프라인을 갖고 있어서 ASYNC가 붙어 있어도 불필요한 오버헤드가 거의 없음.  
#### Hydration이 완료되지 않음  
- 링크는 클라이언트 컴포넌트이기 때문에 라우팅 페이지를 프리패치하기전에 하이드레이션 해야함  
- 초기 방문시 대용량 자바스크립트 번들로 인해 하이드레이션이 지연되어 프리패칭이 바로 시작되지 않을 수 있음
- react는 선택적 hydration을 통해 이를 완화하며, 다음과 같은 방법으로 이를 더욱 개선할 수 있음
- 플러그인을 사용하면 대규모 종속성을 제거하여, 번들 크기를 식별하고 줄일 수 있음  
- 가능하다면 클라이언트에서 서버로 로직을 이동. 자세한 내용은 서버 및 클라이언트 컴포넌트 문서 참조  
## 09.24 5주차  

#### 왜 동적 렌더링이 되는가?  
- Next.js에서 페이지는 크게 정적 또는 동적으로 렌더링 될 수 있음  
#### Linking beteween pages  
- link 컴포넌트를 사용하여 경로 사이를 탐색 할 수 있음  
- link는 html a 태그를 확장하여 prefetching 및 client-side navigation 기능을 제공하는 next.js으 기본제공 컴포넌트임  
- 블로그 글 목록을 생성하려면 next/link 에서 link를 가져와서 컴포넌트에 href prop를 전달함  
#### Route 방식 비교  
- react vs Next.js 라우팅 방식의 차이  
    - 수동 vs 자동  
    - 외부라이브러리 필요 vs 내장파일 기반  
    - 직접 route정의 vs 라우트 자동 매핑  
- react는 기본적으로 라우팅 기능이 없기 때문에, 직접 라우터 라이브러리를 설치해서 라우팅을 설정해야함  
- next.js는 자체적으로 라우팅 시스템 내장  
#### server 렌더링   
- 서버 렌더링에는 발생 시점에 따라 두가지 유형이 있음.  
- 정적 렌더링은 빌드 시점이나 재검증 중에 발생하며, 결과는 캐시됨  
- 동적 렌더링은 클라이언트 요청에 대한 응답으로 요청 시점에 발생  
- 서버렌더링의 단점은 클라이언트가 새 경로를 표시하기 전에 서버의 응답을 기다려야함  
- nex.js는 사용자가 방문할 가능성이 높은 경로를 미리 가져오고, 클라이언트 측 전환을 수행하여 지연 문제를 해결  


## 09.17 4주차  
#### searchParams란?  
- URL의 쿼리 문자열(Query String)을 읽는 방법  
- 예시 URL : /products?category=shoes&page=2  
- 여기서 category=shoes, page=2가 search parameters 임  
- next.js의 App Router에서 searchParams는 다음과 같이 사용될 수 있음  ( export default function ProductsPage({searchParams}) {
    return <p>카테고리: {searchParams.category}</p>:
})
- searchParms는 컴포넌트의 props로 전달되며, 내부적으로는 URLSearchParams 처럼 작동함  
## 09.10 3주차
#### 용어 정의  
- 원문에는 route라는 단어가 자주 등장하고, 사전적 의미로는 "경로"라고 함  
- route는 경로를 의미하고 routing는 경로를 찾아가는 과정을 의미함.  
- path 또한 경로로 번역하기 때문에 구별을 위해 대부분 routing으로 번역함  
- directory와 folder는 특별한 구분 없이 나오며, 최상위 폴더의 경우 directory로 하위 폴더는 folder로 쓰는 경우가 많지만 반드시 그렇지는 않음.  
- directory와 folder는 os에 따라 구분되는 용어이기 때문에 같은의미로 이해하면 됨.  
- segment는 routing과 관련이 있는 directory의 별칭 정도로 이해하면 편함  
    1. Folder and file conventions(폴더 파일 및 규칙)  
        - 최상위 폴더 (top-level folders)  
            - 최상위 폴더는 애프리케이션의 코드와 정적 자산을 구성하는데 사용.  
            - 최상위 파일은 애플리케이션 구성,종속성 관리,미들웨어 실행, 모니터링 도구 통합,환경 변수 정의에 사용.( 파일들이 프로젝트 생성과 동시에 모두 생성되는 것은 아님.)  
#### Open Graph Protocol  
- 웹사이트나 페이스북,인스타,X,카카오톡 등에 링크를 전달할 때 '미리보기'를 생성하는 프로토콜  
- 페이스북이 주도하는 표준화 규칙으로 대부분의 SNS플랫폼에서 활용되고있음  
- 모든 플랫폼이 동일한 방식으로 오픈 그래프를 처리하는 것은 아님  
- 웹페이티의 메타 태그에 선언함    
- (HEAD)  <BR>
    meta property="og.type" content="website"><BR>
    meta property="og.url" content="https.."><BR>
    meta property="og.title" content="제목"><BR>
    meta property="og.description" content="설명요약"><BR>
    meta property="og.image" content="https."><BR>
    meta property="og.site_name" conten="사이트이름"><BR>
    meta property="og.locale" content="ko_KR">
    <BR>(HEAD)  
#### layout과 template의 차이  
- 마스터 텍스트 스타일 ㅍㄴ집  
    - layout.tsx : 경로별 공유 레이아웃 (유지됨.정적) - 네비게이션,사이드바 등  
    - template.tsx : 메번 새 인스턴스 생성 (초기화됨.동적) - 페이지별로 초기화 필요  
#### 2.Organizing your project(프로젝트 구성)  
##### colocation - 파일 및 폴더를 기능별로 그룹화하여 프로젝트의 구졸르 명확하게 정의  
- app 디렉토리에서 중첩된 폴더는 라우팅 구조를 정의  
- 각 폴더는 URL경로의 해당 세그먼트에 맵핑되는 라우팅 세그먼트를 나타냄  
- 즉 프로젝트 파일을 app 디렉토리의 라우팅 세그먼트 내에 안전하게 배치하여 실수로 라우팅되지 않을 수 있도록 할 수 있음  

## 09.03 2주차
#### IDE 플러그인   
- NEXT.JS에는 사용자 정의 TypeScript 플러그인과 유형 검사기가 포함(다음 작업을 하기 전에 TypeScript reference를 참고해서, next.config.js를 먼저 작성함.) 
- Vs Code에서 플러그인을 활성화하는 방법  
  1. 명령 팔레트 열기 (ctrl + shift + p )  
  2. "TypeScript: TypeScript 버전 선택" 검색  
  3. "Use Workpace Version" 선택  
- ESLint 설정  
    - next.js 에는 ESLint가 내장되어있으며
create-next-app 명령을 사용하여 새 프로젝트를 생성하면 필요한 패키지를 자동으로 설치하고 적절한 설정을 구성
기존 프로젝트에 ESLint를 수동으로 추가하려면 package.json에 next.lint 스크립트를 다음과 같이 추가
다음으로 npm run list를 실행하면 동작  
- 동작하면 다음과 같은 메시지가 추가됨.   
    - strict : next.js의 기본 ESLint구성과 더욱 엄격한 core web vitals 규칙세트 포함
    - base : next.js의 기본 ESLint구성을 포함
    - cancle : 구성을 건너뜀. 사용자 지정 ESLint 구성을 설정하려면 이 옵션 선택
    - strict 또는 base 중 하나가 선택되면, next.js는 자동으로 eslint 와 eslint-config-next 애플리케이션의 의존성으로 설치, 또한 선택한 설정을 포함하는 .eslintrc.json파일을 프로젝트 루트 디렉토리에 생성.이제 next.lint를 실행할 때마다 eslint 가 실행되어 오류를 찾아냄  
- import 및 모듈의 절대 경로 별칭 설정  
    - .next.js에는 tsconfig.json 및 jsconfig.json파일의 "paths" 및 "baseUrl" 옵션에 대한 지원을 내장(이 옵션을 사용하면 프로젝트 디렉터리를 절대 경로로 별칭하여 모듈을 더 쉽고 깔끔하게 가져올 수 있음)  
    - 별칭으로 import를 구성하려면 tsconfig.json 또는 jsconfig.json 파일의 baseurl에 구성 옵션 추가  
    - baseurl 경로를 구성하는것 외에도 paths 옵션을 사용하여 모듈 경로를 별칭으로 사용할 수 있음(ex:예를 들어 다음 구성은 @/components/*를 components/*에 매핑)
    - paths의 각 항목은 baseurl의 경로에 따라 상대적임  
- 자동 생성되는 항목
    - 다음은 프로젝트를 자동 생성할때 자동으로 생성되는 항목
1. package.json 파일에 script 잦동 추가 / public 디렉토리
2. typescript사용(선택):tsconfig.json파일 생성
3. Eslint 설정(선택) eslintrc.json 대신 eslint.config.mjs 파일 생성
4. Tailwind Css 사용 ( 선택)
5. src 디렉토리 사용 (선택)
6. App Router 선택 app/layout.tsx 파일 및 app/page.tsx
7.TurboPack 사용
8.import alias 사용 : tsconfig.json에 paths 자동 생성
- 수동으로 프로젝트를 생성할 때 추가적으로 해야 하는 작업을 자동으로 처리해줌
#### 실습에 사용할 프로젝트 생성  
- 공식 문서에는 기본 패키지 관리자를 pnpm을 사용  
- 원하는 패키지 관리자 탭을 클릭하면 명령을 확인할 수 있음  
- pnpm과 관련한 내용은 뒤에서 설명  
- 다음 명령으로 프로젝트를 사용(실행하면 8개의 선택항목이 나옴)  
    1. 프로젝트 이름입력
    2. ~.4 TypeScript.ESLint,Tailwind를 사용할지 선택 
    5. src/ 디렉토리를 사용할지 선택  
    6. App Router를 사용할지 선택  
    7. import alias 를 사용할지 선택  
    8. alias 문자 지정. 기본은 @/*임    
    
## 08.27 1주차  
#### OT & TypeScript에 대한 설명  











