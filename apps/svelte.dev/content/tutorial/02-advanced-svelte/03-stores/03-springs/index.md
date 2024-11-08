---
title: 스프링
---

`spring` 함수는 `tweened`의 대안으로, 자주 변경되는 값에 대해 더 나은 동작을 제공하는 경우가 많습니다.

이 예제에서는 두 개의 스토어가 있습니다 - 하나는 원의 좌표를 나타내고, 다른 하나는 크기를 나타냅니다. 이들을 스프링으로 변환해봅시다:

```svelte
/// file: App.svelte
<script>
	import { +++spring+++ } from 'svelte/+++motion+++';

	let coords = +++spring+++({ x: 50, y: 50 });
	let size = +++spring+++(10);
</script>
```

두 스프링 모두 기본 `stiffness`와 `damping` 값을 가지고 있으며, 이는 스프링의... 음, 탄성을 제어합니다. 우리만의 초기값을 지정할 수 있습니다:

```js
/// file: App.svelte
let coords = spring({ x: 50, y: 50 }, +++{
	stiffness: 0.1,
	damping: 0.25
}+++);
```

마우스를 움직여보고, 슬라이더를 드래그해서 스프링의 동작에 어떤 영향을 미치는지 느껴보세요. 스프링이 여전히 움직이는 동안에도 값을 조정할 수 있다는 점을 주목하세요.
