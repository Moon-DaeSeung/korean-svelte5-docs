---
title: 스타일링
---

HTML에서처럼 컴포넌트에 `<style>` 태그를 추가할 수 있습니다. `<p>` 요소에 몇 가지 스타일을 추가해봅시다:

```svelte
/// file: App.svelte
<p>이것은 문단입니다.</p>

<style>
+++	p {
		color: goldenrod;
		font-family: 'Comic Sans MS', cursive;
		font-size: 2em;
	}+++
</style>
```

중요한 점은 이러한 규칙들이 _컴포넌트에 범위가 한정된다는 것_ 입니다. 다음 단계에서 보시겠지만, 앱의 다른 곳에 있는 `<p>` 요소의 스타일이 실수로 변경되는 일은 없을 것입니다.
