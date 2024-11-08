---
title: 진입과 퇴장
---

`transition` 디렉티브 대신, 요소는 `in` 또는 `out` 디렉티브를 가질 수 있으며, 둘 다 함께 사용할 수도 있습니다. `fly`와 함께 `fade`를 가져옵니다...

```js
/// file: App.svelte
import { +++fade+++, fly } from 'svelte/transition';
```

...그런 다음 `transition` 디렉티브를 별도의 `in`과 `out` 디렉티브로 교체합니다:

```svelte
/// file: App.svelte
<p +++in+++:fly={{ y: 200, duration: 2000 }} +++out:fade+++>
	날아서 들어오고, +++페이드아웃됩니다+++
</p>
```

이 경우에는 트랜지션이 _가역적이지 않습니다_.
