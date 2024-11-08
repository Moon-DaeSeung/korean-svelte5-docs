---
title: props 전개
---

이 예제에서는 `PackageInfo.svelte`가 기대하는 `name` prop을 전달하는 것을 잊었기 때문에, `<code>` 요소가 비어있고 npm 링크가 깨져있습니다.

prop을 추가하여 수정할 수 있습니다...

```svelte
/// file: App.svelte
<PackageInfo
	name={pkg.name}
	version={pkg.version}
	description={pkg.description}
	website={pkg.website}
/>
```

...하지만 `pkg`의 속성들이 컴포넌트가 기대하는 props와 일치하므로, 대신 컴포넌트에 전개 연산자를 사용할 수 있습니다:

```svelte
/// file: App.svelte
<PackageInfo {...pkg} />
```

> [!NOTE] 반대로, 나머지 속성을 사용하여 컴포넌트에 전달된 모든 props를 포함하는 객체를 얻을 수 있습니다...
>
> ```js
> let { name, ...stuff } = $props();
> ```
>
> ...또는 [구조 분해](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)를 완전히 건너뛸 수 있습니다:
>
> ```js
> let stuff = $props();
> ```
