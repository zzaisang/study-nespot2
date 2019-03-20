## 세션6 Creating a Prouction-Grade Workflow

- user (push) => feature (pull request to merge with master) =>  master  => Travis CI => test run => (deploy) => AWS 

- npm install -g create-react-app

- create-react-app frentend

- 우선 react를 설치하자
    - 이 실습은 컨테이너에 사용되는 code를 집중적으로 배우지 않을 것이다. 오직 container 사용에만 포커스를 맞출 것이다.
    - project는 java든 javascript는 php든 상관이 없다.
    - 이 강의는 react를 예제로 사용하였다.
- create-react-app 에 사용되는 기본 명령어
    - npm run start
    - npm run test
    - npm run build 

- Dockerfile.dev 생성

```
FROM node:alpine

WORKDIR '/app'

COPY package.json .
RUN npm install

COPY . .

CMD ["npm","run","start"]

```

- docker 명령어 실행

```javascript
docker build -f Dockerfile.dev . 

docker run -p 3000:3000 {이미지ID}
```

- 만약 react에 있는 App.js를 수정할때 즉시 container에도 반영을 할 수 있을까?? 어떤 방법을 써야 할까??
