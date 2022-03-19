2022.03.19 Sat

Availy를 준비하면서 최대한 간결하면서 확장성이 용이하게 프로덕트를 만들고 싶었다.
특히 신경쓰고 있는 부분은 Test Coverage를 위해 어떻게 깔끔하게 관심사 분리를 할 것인가,
그리고 비동기 데이터 처리였다. 여러 선택지를 고민하면서 결론적으로는 React Query를 도입하기로 결정했다.
그 이유들은 아래와 같다.

- client state와 server state를 분리해 server state를 더욱 간결하게 관리할 수 있다.(client state의 전역 상태관리는 recoil로 잠정 결론내렸다)
- mutation 관리 시 optimistic UI 관리가 편하다. 기존에는 server state를 useState에 저장한 뒤, post하고 나서 직접 setState로 mutation을 관리했다. 매우 불편했음😅
- 미래에 캐싱 전략을 적용할 수 있으므로 확장성에 용이하다고 판단했다.
- Next.js에도 쉽게 도입할 수 있다.

React Query에 대한 학습과 적용은 실제 구현 시 더욱 깊게 살펴보고자 한다.

<!-- 자세한 내용은 적용하면서 TIL에 추가할 것임. 다만 공식문서를 통해 업데이트하자.->
