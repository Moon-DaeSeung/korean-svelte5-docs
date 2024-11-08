---
title: 매개변수 추가하기
---

트랜지션 함수는 매개변수를 받을 수 있습니다. `fade` 트랜지션을 `fly`로 교체해보겠습니다...

```svelte
/// file: App.svelte
<script>
	import { +++fly+++ } from 'svelte/transition';

	let visible = $state(true);
</script>
```

...그리고 `<p>`에 몇 가지 옵션과 함께 적용합니다:

```svelte
/// file: App.svelte
<p transition:+++fly={{ y: 200, duration: 2000 }}+++>
	+++날아+++ 들어오고 나갑니다
</p>
```

트랜지션이 _가역적_이라는 점에 주목하세요 - 트랜지션이 진행되는 동안 체크박스를 토글하면, 처음이나 끝이 아닌 현재 지점에서부터 트랜지션이 시작됩니다.
