# 202130235 최한솔
<hr>

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











