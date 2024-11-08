---
title: 내보내기
---

`module` 스크립트 블록에서 내보낸 모든 것은 모듈 자체의 내보내기가 됩니다. `stopAll` 함수를 내보내봅시다:

```svelte
/// file: AudioPlayer.svelte
<script module>
	let current;

+++	export function stopAll() {
		current?.pause();
	}+++
</script>
```

이제 `App.svelte`에서 `stopAll`을 가져올 수 있습니다...

```svelte
/// file: App.svelte
<script>
	import AudioPlayer, +++{ stopAll }+++ from './AudioPlayer.svelte';
	import { tracks } from './tracks.js';
</script>
```

...그리고 이벤트 핸들러에서 사용할 수 있습니다:

```svelte
/// file: App.svelte
<div class="centered">
	{#each tracks as track}
		<AudioPlayer {...track} />
	{/each}

+++	<button onclick={stopAll}>
		모두 정지
	</button>+++
</div>
```

> [!NOTE] 기본 내보내기는 사용할 수 없습니다. 컴포넌트 자체가 기본 내보내기이기 때문입니다.
