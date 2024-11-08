---
title: 컴포넌트 스타일
---

종종 자식 컴포넌트 내부의 스타일에 영향을 주어야 할 때가 있습니다. 이 박스들을 빨강, 초록, 파랑으로 만들고 싶다고 가정해봅시다.

한 가지 방법은 `:global` CSS 수정자를 사용하는 것입니다. 이를 통해 다른 컴포넌트 내부의 요소를 무차별적으로 대상으로 지정할 수 있습니다:

```svelte
/// file: App.svelte
<style>
	.boxes :global(.box:nth-child(1)) {
		background-color: red;
	}

	.boxes :global(.box:nth-child(2)) {
		background-color: green;
	}

	.boxes :global(.box:nth-child(3)) {
		background-color: blue;
	}
</style>
```

하지만 이렇게 하지 않는 것이 좋습니다. 우선 매우 장황합니다. 또한 깨지기 쉽습니다 — `Box.svelte`의 구현 세부사항이 변경되면 선택자가 깨질 수 있습니다.

무엇보다도, 이는 예의 없는 방법입니다. 컴포넌트는 변수를 props로 노출하는 것과 같은 방식으로 어떤 스타일이 '외부'에서 제어될 수 있는지 스스로 결정할 수 있어야 합니다. `:global`은 마지막 수단으로 사용되어야 합니다.

`Box.svelte` 내부에서 `background-color`를 [CSS 커스텀 속성](https://developer.mozilla.org/en-US/docs/Web/CSS/--*)으로 결정되도록 변경하세요:

```svelte
/// file: Box.svelte
<style>
	.box {
		width: 5em;
		height: 5em;
		border-radius: 0.5em;
		margin: 0 0 1em 0;
		background-color: +++var(--color, #ddd)+++;
	}
</style>
```

모든 부모 요소(예: `<div class="boxes">`)가 `--color` 값을 설정할 수 있지만, 개별 컴포넌트에도 설정할 수 있습니다:

```svelte
/// file: App.svelte
<div class="boxes">
	<Box +++--color="red"+++ />
	<Box +++--color="green"+++ />
	<Box +++--color="blue"+++ />
</div>
```

값은 다른 속성처럼 동적일 수 있습니다.

> [!NOTE] 이 기능은 필요한 경우 각 컴포넌트를 `display: contents`를 가진 요소로 감싸고 여기에 커스텀 속성을 적용하는 방식으로 작동합니다. 요소를 검사해보면 다음과 같은 마크업을 볼 수 있습니다:
>
> ```svelte
> <svelte-css-wrapper style="display: contents; --color: red;">
> 	<!-- 내용 -->
> </svelte-css-wrapper>
> ```
>
> `display: contents` 때문에 레이아웃에는 영향을 주지 않지만, 추가 요소는 `.parent > .child`와 같은 선택자에 영향을 줄 수 있습니다.
