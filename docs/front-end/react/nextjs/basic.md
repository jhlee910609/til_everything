# basic

## CSR(Clinet Side Rendering)
- 모든 javascript를 브라우저가 실행시켜 화면을 그림
- 브라우저에서 javascript 실행 off 해버리면 동작을 안함 
- network speed throttle 걸어서 봐도 알 수 있음 
- [Lecture – 노마드 코더 Nomad Coders](https://nomadcoders.co/nextjs-fundamentals/lectures/3439)


## SSR(Server Side Rendering)
- javascript 기반으로 HTML pre-rendering 해둠 
- hydration -> 그려진 html 기반으로 interaction(javascript) 코드를 binding 함 


## next.js
- [GitHub - nomadcoders/nextjs-fundamentals: Learning NextJS by Building a Tiny Movie Website.](https://github.com/nomadcoders/nextjs-fundamentals)

- Server side에서 그는 것과 Client side에서 그리는 걸 분리해서 잘 생각해야함
  - ex) router 관련 동작은 client 내려오기 전까지 브라우저가 제공하는 정보들은 알 수가 없음 -> server side context 꺼내서 쓸 수 있음 