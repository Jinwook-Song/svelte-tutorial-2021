[Svelte](https://svelte.dev/)

[Svelte.js 완벽 가이드(Renew)](https://heropy.blog/2019/09/29/svelte/)

- Core concept
  - Write less code
    - 높은 가독성 유지
    - 개발 시간 단축
    - 쉬운 리팩토링
    - 쉬운 디버깅
    - 더 작은 번들(SPA 최적화)
    - 낮은 러닝 커브
  - No virtual DOM
    - No Diffing
      - Diffing이란 Virtual DOM에서 서로 비교하여 차이가 있는 부분만 업데이트 하는 방식
      - 비교를 위해서는 새로운 Virtual DOM을 생성해야하고, 그 결과를 실제 DOM에 갱신
      - Svelte의 경우 갱신만 해주면 된다
    - No Overhead
      - 어떤 처리를 위해 들어가는, 간접적인 시간이나 메모리
      - VIrtual DOM을 통한 추가적인 loss가 발생하지 않음
    - 빠른 성능(퍼포먼스)
      - 예시) Result of memory usage
        - React: 30 ~ 110 MB
        - Svelt: 15 ~ 30 MB
  - Truly reactive
    - Framework-less VanillaJS, Only use ‘devDependencies’
      - Svelte가 어플리케이션을 VanillaJS로 컴파일하고 그 결과만 동작하기 때문에, Svelte는 브라우저(런타임)에서 동작하지 않는 컴파일러라고 할 수 있다.
  - 명시석 설계(창의적 작업)
- 단점 (2019. 4 기준)
  낮은 성숙도(작은 커뮤니티)
  CDN 미제공 (런타임에서 동작하지 않기 때문에)
  IE 미지원

# 시작하기

```bash
npx degit sveltejs/template my-svelte-project
cd my-svelte-project
npm install
npm run dev
```
