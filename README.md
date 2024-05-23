<h1> Web_LLM_tutorial </h1>
<h3> Secret-llama와 web-llm를 사용하는 방법을 기술 </h3>

- Reference
- https://github.com/abi/secret-llama (Secret LLAMA)
- https://github.com/mlc-ai/web-llm (Web LLM)

## About
- Web LLM과 Secret LLama를 사용하는 방법을 한국어로 정리한 내용
- 어떻게 시도해볼지 모르는 사람을 위해 따라가기만 해도 해볼 수 있도록 정리

## 환경

- OS : Windows
- Web : Next.js Node.js
- Infra : Docker

## Start

- web-llm을 사용하기 위해 Node.js를 설치
- 기존에 Node.js가 설치되어 있다면 넘어가도 되지만 Docker를 통해 node.js를 쉽게 관리할 수 있도록 작업 수행

### Docker Install
- Docker Install
- 자신의 환경에 맞는 Docker 설치 : https://docs.docker.com/engine/install/
- cmd 창을 열어 ```docker --verision ``` 입력시 버전 정보가 나온다면 설치 완료

### Docker Image 설치
- 웹에서 node.js에서 docker image를 설치하는 코드를 복사
- https://nodejs.org/en/download/package-manager (v20.13.1(LTS) 사용)
- cmd 창을 열고 ```docker pull node:20-alpine ``` 입력 후 설치
- cmd 창에 ``` docker run node:20-alpine node -v ``` 입력후 ``` `v20.13.1` ``` 버전 정보가 나오는지 확인
- cmd 창에 ``` docker run node:20-alpine npm -v ``` 입력후 ``` `10.5.2` ``` 버전 정보가 나오는지 확인

### Docker node.js container 설치
- cmd 창에서 ``` docker run -d -it -p 8888:3000 --name [container_name] -v [container와 연결할 local folder 경로]:/app node:20-alpine ``` 입력 후 container 생성
- ex) ``` docker run -d -it -p 8888:3000 --name next-web-llm -v C:\Users\unmun\node-app:/app node:20-alpine ```
- cmd 창에서 ``` docker ps ``` 후 container가 올라왔는지 확인

### Web-llm 실행
- cmd 창에서 ``` docker exec -it [container_name] /bin/sh ``` 를 실행하여 container Repo에 접근
- Window에서 container와 연결한 local folder에 web-llm 파일을 옮기기
- cmd 창에서 ``` ls ./app/web-llm ```을 통해 파일이 잘 옮겨졌는지 확인
- cmd 창에서 ``` cd ./app/web-llm ```으로 해당 폴더로 이동
- (ISSUE) ``` npm install autoprefixer@latest ``` autoprefixer와 관련된 오류가 발생한다면 미리 설치
- cmd 창에서 ``` npm run dev ```으로 해당 폴더 실행
- 윈도우에서 Browser를 통해 ```localhost:8888```을 입력하면 간단하게 Secret llama를 사용해볼 수 있음.