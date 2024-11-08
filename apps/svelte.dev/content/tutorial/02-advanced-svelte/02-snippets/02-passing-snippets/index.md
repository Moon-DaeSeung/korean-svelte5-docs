---
title: 컴포넌트에 스니펫 전달하기
---

스니펫은 함수처럼 단순한 값이므로 props로 컴포넌트에 전달할 수 있습니다.

이 `<FilteredList>` 컴포넌트를 보세요. 이 컴포넌트의 역할은 전달받은 `data`를 필터링하는 것이지만, 그 데이터를 어떻게 렌더링할지에 대해서는 관여하지 않습니다 - 그것은 부모 컴포넌트의 책임입니다.

이미 몇 가지 스니펫이 정의되어 있습니다. `<FilteredList>`에 이들을 전달하는 것부터 시작해봅시다:

```svelte
/// file: App.svelte
<FilteredList
	data={colors}
	field="name"
	+++{header}+++
	+++{row}+++
></FilteredList>
```

그런 다음, 다른 쪽에서 `header`와 `row`를 props로 선언합니다:

```svelte
/// file: FilteredList.svelte
<script>
	let { data, field, +++header, row+++ } = $props();

	// ...
</script>
```

마지막으로, 임시 콘텐츠를 렌더 태그로 교체합니다:

```svelte
/// file: FilteredList.svelte
<div class="header">
	+++{@render header()}+++
</div>

<div class="content">
	{#each filtered as d}
		+++{@render row(d)}+++
	{/each}
</div>
```

이제 더 이상 `MistyRose`나 `PeachPuff`의 16진수 코드를 외울 필요가 없습니다.
