# 202130235 최한솔
<hr>  

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











