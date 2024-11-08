---
title: 반응성 선언
---

Svelte의 핵심 기능 중 하나는 _반응성_ 입니다 - 즉, DOM이 데이터의 변경 사항에 자동으로 업데이트된다는 것입니다.

반응성을 보여주기 위해, 먼저 이벤트 핸들러가 필요합니다. `on:click` 디렉티브를 사용하여 버튼에 클릭 이벤트 핸들러를 추가해보세요:

```svelte
/// file: App.svelte
<button on:click={increment}>
	Clicked {count} {count === 1 ? 'time' : 'times'}
</button>

<script>
	let count = 0;

	function increment() {
		count += 1;
	}
</script>
```

내부의 `{count === 1 ? 'time' : 'times'}` 표현식은 단수형과 복수형을 적절히 처리합니다. 버튼을 클릭해보세요.

Svelte는 컴포넌트의 상태(여기서는 `count`)가 변경될 때 DOM을 자동으로 업데이트합니다. 변수에 영향을 미치는 상태 변경은 해당 변수가 사용되는 곳마다 반응성을 트리거합니다.
