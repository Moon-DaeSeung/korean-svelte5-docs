---
title: 매개변수 추가하기
---

트랜지션과 애니메이션처럼 액션도 매개변수를 받을 수 있으며, 이 매개변수는 액션이 속한 엘리먼트와 함께 액션 함수에 전달됩니다.

이 예제에서는 [`Tippy.js`](https://atomiks.github.io/tippyjs/) 라이브러리를 사용하여 `<button>`에 툴팁을 추가하려고 합니다. 액션은 이미 `use:tooltip`으로 연결되어 있지만, 버튼 위에 마우스를 올리거나(또는 키보드로 포커스하면) 툴팁에 내용이 없습니다.

먼저 액션이 Tippy에 전달할 옵션을 반환하는 함수를 받아야 합니다:

```js
/// file: App.svelte
function tooltip(node, +++fn+++) {
	$effect(() => {
		const tooltip = tippy(node, +++fn()+++);

		return tooltip.destroy;
	});
}
```

> [!NOTE] 옵션 자체가 아닌 함수를 전달하는 이유는 옵션이 변경될 때 `tooltip` 함수가 다시 실행되지 않기 때문입니다.

그런 다음 액션에 옵션을 전달해야 합니다:

```svelte
/// file: App.svelte
<button use:tooltip+++={() => ({ content })}+++>
	Hover me
</button>
```

> [!NOTE] Svelte 4에서는 액션이 `update`와 `destroy` 메서드가 있는 객체를 반환했습니다. 이 방식도 여전히 작동하지만 더 많은 유연성과 세분성을 제공하는 `$effect`를 사용하는 것을 추천합니다.
