## Express, body parser

Express, as you know, is a web framework that we’ll be using for building the REST APIs, and body-parser is a module that parses the request (of various content types) and creates a req.body object that we can access in our routes.

## Express

Express is one of the most popular web frameworks for node.js. It is built on top of node.js http module, and adds support for routing, middleware, view system etc. It is very simple and minimal, unlike other frameworks that try do way to much, thereby reducing the flexibility for developers to have their own design choices.

## Mongoose

Mongoose is an ODM (Object Document Mapping) tool for Node.js and MongoDB. It helps you convert the objects in your code to documents in the database and vice versa.

## Middleware

A middleware is a function that has access to the request and response objects. It can execute any code, transform the request object, or return a response.

## Node.js

Node.js는 브라우저 밖에서도 자바스크립트를 실행할 수 있는 환경을 의미합니다. Node.js가 나오기 전까지는 자바스크립트가 브라우저의 동작을 제어하는데 사용되었고 브라우저에서만 실행할 수 있었지만 이제는 Node.js로 자바스크립트를 브라우저 밖에서도 실행할 수 있게 되었습니다.

Webpack 과 Babel 같은 도구들이 자바스크립트 런타임인 Node.js 를 기반으로 만들어져있습니다. 그렇기에 해당 도구들을 사용하기 위해서 Node.js 를 설치합니다.

## Yarn

Yarn 은 조금 개선된 버전의 npm 이라고 생각하시면 됩니다. npm 은 Node.js 를 설치하게 될 때 같이 딸려오는 패키지 매니저 도구입니다. 프로젝트에서 사용되는 라이브러리를 설치하고 해당 라이브러리들의 버전 관리를 하게 될 때 사용하죠. 우리가 Yarn 을 사용하는 이유는, 더 나은 속도, 더 나은 캐싱 시스템을 사용하기 위함입니다.
