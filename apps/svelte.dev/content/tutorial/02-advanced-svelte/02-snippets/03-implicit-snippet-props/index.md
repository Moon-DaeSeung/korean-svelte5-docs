---
title: 암시적 스니펫 props
---

작성의 편의를 위해, 컴포넌트 내부에 직접 선언된 스니펫은 해당 컴포넌트의 props가 됩니다. `header`와 `row` 스니펫을 `<FilteredList>` 안으로 옮겨봅시다:

```svelte
/// file: App.svelte
<FilteredList
	data={colors}
	field="name"
	{header}
	{row}
>
	+++{#snippet header()}...{/snippet}+++

	+++{#snippet row(d)}...{/snippet}+++
</FilteredList>

---{#snippet header()}...{/snippet}---

---{#snippet row(d)}...{/snippet}---
```

이제 명시적 props에서 이들을 제거할 수 있습니다:

```svelte
/// file: App.svelte
<FilteredList data={colors} field="name" ---{header} {row}--->
	{#snippet header()}...{/snippet}

	{#snippet row(d)}...{/snippet}
</FilteredList>
```

선언된 스니펫의 일부가 아닌 컴포넌트 내부의 모든 콘텐츠는 특별한 `children` 스니펫이 됩니다. `header`는 매개변수가 없으므로 블록 태그를 제거하여 `children`으로 만들 수 있습니다...

```svelte
/// file: App.svelte
---{#snippet header()}---
<header>
	<span class="color"></span>
	<span class="name">name</span>
	<span class="hex">hex</span>
	<span class="rgb">rgb</span>
	<span class="hsl">hsl</span>
</header>
---{/snippet}---
```

...그리고 다른 쪽에서 `header` prop을 `children`으로 이름을 바꿉니다:

```svelte
/// file: FilteredList.svelte
<script>
	let { data, field, +++children+++, row } = $props();

	// ...
</script>
```

```svelte
/// file: FilteredList.svelte
<div class="header">
	+++{@render children()}+++
</div>
```