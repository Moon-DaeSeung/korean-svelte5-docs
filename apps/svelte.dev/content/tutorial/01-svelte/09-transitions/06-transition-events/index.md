---
title: 트랜지션 이벤트
---

트랜지션이 시작되고 끝나는 시점을 아는 것이 유용할 수 있습니다. Svelte는 다른 DOM 이벤트처럼 감지할 수 있는 이벤트를 발생시킵니다:

```svelte
/// file: App.svelte
<p
	transition:fly={{ y: 200, duration: 2000 }}
+++	onintrostart={() => status = '진입 시작됨'}
	onoutrostart={() => status = '퇴장 시작됨'}
	onintroend={() => status = '진입 종료됨'}
	onoutroend={() => status = '퇴장 종료됨'}+++
>
	날아 들어오고 나갑니다
</p>
```
