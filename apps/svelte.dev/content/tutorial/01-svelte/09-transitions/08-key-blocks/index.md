---
title: key 블록
---

key 블록은 표현식의 값이 변경될 때 그 내용을 파괴하고 재생성합니다. 이는 요소가 DOM에 들어오거나 나갈 때만이 아니라 값이 변경될 때마다 트랜지션을 실행하고 싶을 때 유용합니다.

예를 들어, 여기서는 로딩 메시지, 즉 `i`가 변경될 때마다 `transition.js`의 `typewriter` 트랜지션을 실행하고 싶습니다. `<p>` 요소를 key 블록으로 감싸보세요:

```svelte
/// file: App.svelte
+++{#key i}+++
	<p in:typewriter={{ speed: 10 }}>
		{messages[i] || ''}
	</p>
+++{/key}+++
```
