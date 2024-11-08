---
title: 스토어 소개
---

Svelte 5에서 룬이 도입되기 전에는 스토어가 컴포넌트 외부의 반응형 상태를 다루는 관용적인 방법이었습니다. 이제는 더 이상 그렇지 않지만, Svelte를 사용할 때 여전히 스토어를 접하게 될 것입니다(현재로서는 SvelteKit에서도 포함), 따라서 사용 방법을 아는 것이 좋습니다.

> [!NOTE] 여기서는 사용자 정의 스토어를 만드는 방법은 다루지 않습니다 - 그것에 대해서는 [문서를 참조](/docs/svelte/stores)하세요.

[보편적 반응성](universal-reactivity) 연습에서 다룬 예제를 다시 살펴보되, 이번에는 공유 상태를 스토어를 사용하여 구현해보겠습니다.

`shared.js`에서 현재 숫자인 `count`를 내보내고 있습니다. 이것을 쓰기 가능한 스토어로 바꿔봅시다:

```js
/// file: shared.js
+++import { writable } from 'svelte/store';+++

export const count = +++writable(0)+++;
```

스토어의 값을 참조하려면 `$` 기호를 앞에 붙입니다. `Counter.svelte`에서 `<button>` 안의 텍스트를 업데이트하여 더 이상 `[object Object]`를 표시하지 않도록 합니다:

```svelte
/// file: Counter.svelte
<button onclick={() => {}}>
	clicks: {+++$count+++}
</button>
```

마지막으로, 이벤트 핸들러를 추가합니다. 이것이 쓰기 가능한 스토어이므로 `set` 또는 `update` 메서드를 사용하여 프로그래밍 방식으로 값을 업데이트할 수 있습니다...

```js
count.update((n) => n + 1);
```

...하지만 컴포넌트 내에 있으므로 계속해서 `$` 접두사를 사용할 수 있습니다:

```svelte
/// file: Counter.svelte
<button onclick={() => +++$count += 1+++}>
	clicks: {$count}
</button>
```
