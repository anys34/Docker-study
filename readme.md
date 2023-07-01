## Dockerfile 내용정리

# FROM node:16-alpine
- FROM : 제일 처음에는 FROM baseimage로 시작해야함
- node : 미리 만들어 둔 이미지 사용
- 16 : 노드 버전
- alpine : 최소 버전

# WORKDIR /app
- WORKDIR /app : root 경로에 있는 app이라는 폴더 안에 프로젝트 관련 파일을 복사

# COPY package.json package-lock.json ./
- app 폴더에 package.json과 package-lock.json을 저장

# RUN npm ci
- package-lock.json에 저장되어있는 버전을 설치
- 만약 RUN npm install을 한다면 package.json에 있는 내용을 모두 최신 버전으로 설치(이 경우 개발한 버전과 달라 에러가 날 수 있음)

# COPY index.js .
// app 폴더에 index.js을 저장

# ENTRYPOINT [ "node", "index.js" ]
- 마지막으로 node와 index.js를 실행