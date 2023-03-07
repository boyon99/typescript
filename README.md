# typescript

- [TS 공식문서](https://www.typescriptlang.org/ko/)
- [REPL](https://www.typescriptlang.org/play/index.html)
  - 작성한 내용이 컴파일러 옵션에 따라 어떻게 자바스크립트로 변환되는지 바로 확인할 수 있다.
- [Repl.it](https://replit.com/languages/typescript)
  - 파일과 디렉터리로 관리되는 타입스크립트 프로젝트를 손쉽게 구성할 수 있다.
  - 간단한 프로젝트로 타입스크립트를 테스트하기 좋다.
- [transform tool](https://transform.tools/json-to-typescript)

<br/>

### 설치하기

- 전역 설치하기
  `npm i typescript -g`
  > mac에서 전역으로 설치할 때의 오류 : 맨 앞에 sudo를 붙인 후 암호를 입력한다. 전역으로 설치하는 이유는 명령어를 사용하기 위함이다. (ts의 경우 tsc의 명령어)
- 단일 프로젝트에서만 사용하기
  `npm install -D typescript`
  > 이런 경우 명령어를 사용하기 위해서는 `npx tsc`명령어를 입력해야 한다.

<br/>

### 컴파일을 위한 다양한 옵션

1. 터미널에서 직접 컴파일하기

```console
tsc [파일이름].ts
tsc ./src/index.ts --watch --strict true --target ES6 --lib ES2015,DOM --module CommonJS
tsc --watch // 변경사항이 저장할 때 마다 자동으로 변환, -w로 단축하여 작성할 수도 있다.
```

2. `tsconfig.json` 파일을 통해 옵션을 지정할 수 있다.

```console
tsc --init // 초기화하면 `tsconfig.json` 파일이 추가된다.
```

> [컴파일을 위한 다양한 옵션을 확인할 수 있는 공식문서](https://www.typescriptlang.org/docs/handbook/compiler-options.html)

```json
{
  "compilerOptions": {
    "strict": true,
    "target": "ES6",
    "lib": ["ES2015", "DOM"],
    "module": "CommonJS"
  }
}
```

<br/>

### Parcel

타입스크립트를 로컬 환경에서 빠르게 테스트하고 싶은 경우 Parcel 번들러를 선택할 수 있다.

#### 설치하기

```console
npm init -y
npm install -D typescript parcel-bundler
```

1. `tsconfig.json`에 작성하기

```json
{
  "compilerOptions": {
    "strict": true
  },
  "exclude": ["node_modules"]
}
```

2. main.ts 파일 생성 후 ts 작성하기

3. index.html 파일 생성 후 .ts파일 연결하기

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>TypeScript Test</title>
  </head>
  <body>
    <script src="main.ts"></script>
  </body>
</html>
```

4. 실행하기
```console
npx parcel index.html
```

<br/>

### TS Node
NodeJS 환경에서 테스트하고 싶은 경우 TS Node를 사용한다.

#### 설치하기
```console
npm init -y
npm install -D typescript @types/node ts-node // @types/node는 Node.js API를 위한 타입 선언 모듈이다.
```

1. `tsconfig.json`에 작성하기
```json
{
  "compilerOptions": {
    "strict": true,
    "module": "CommonJS"
  },
  "exclude": [
    "node_modules"
  ]
}
```

2. main.ts 파일 생성 후 작성하기
```js
console.log('TypeScript on NodeJS!');
```

3. TS Node를 사용해 main.ts를 실행하기
```shell
npx ts-node main.js
```

<br/>



