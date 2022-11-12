https://roseline.oopy.io/dev/translation-why-cjs-and-esm-cannot-get-along

ESM와 CJS 은 완전히 다른 동물이다.
CommonJS에서 require()는 동기적으로 동작한다. require() 는 promise를 리턴하거나 callback을 호출하지 않는다. require()는 디스크에서(또는 네트워크로부터) 데이터를 읽어온 후, 그 자체로 I/O를 하거나 사이드 이펙트가 있을 수 있는 스크립트를 즉시 실행시킨다. 그런 다음 어떤 값이건 module.exports에 할당된 값을 반환한다.
ESM에서는 비동기적인 단계들을 거쳐 모듈 로더가 실행된다. 첫 단계에서는 import한 스크립트를 실행시키지 않고 import와 export하는 구문이 있는지 스크립트를 파싱한다. 파싱 단계에서 ESM 로더는 즉시 named imports에서 오타를 감지하여 import한 스크립트를 실행시키지 않고 에러를 발생시킨다.
ESM 모듈 로더는 import한 스크립트를 비동기적으로 다운로드하고 파싱한 후 dependency들의 "module graph"를 빌드한다. import하는 게 아무것도 없는 스크립트를 찾을 때까지 이 과정을 반복한다. 마지막으로 스크립트는 실행을 허락하고 dependency 스크립트 또한 실행을 허락한다.
ESM - module graph 참고 이미지
ES 모듈 그래프에서 모든 "형제(siblings)" 스크립트(같은 레벨의 스크립트)는 병렬적으로 다운로드되지만, 실행은 로더 스펙에 정의된 순서대로 실행한다.
