---
title: <svelte:self>
---

Svelte는 다양한 내장 요소를 제공합니다. 첫 번째인 `<svelte:self>`는 컴포넌트가 자신을 재귀적으로 포함할 수 있게 해줍니다.

이것은 이 폴더 트리 뷰와 같은 것에 유용합니다. 여기서 폴더는 _다른_ 폴더들을 포함할 수 있습니다. `Folder.svelte`에서 우리는 이렇게 하고 싶습니다...

```svelte
/// file: Folder.svelte
{#if file.files}
	<Folder {...file}/>
{:else}
	<File {...file}/>
{/if}
```

...하지만 모듈이 자신을 가져올 수 없기 때문에 이는 불가능합니다. 대신 `<svelte:self>`를 사용합니다:

```svelte
/// file: Folder.svelte
{#if file.files}
	+++<svelte:self {...file} />+++
{:else}
	<File {...file} />
{/if}
```
