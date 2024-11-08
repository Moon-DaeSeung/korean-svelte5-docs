---
title: 코드 공유하기
---

지금까지 본 모든 예제에서 `<script>` 블록은 각 컴포넌트 인스턴스가 초기화될 때 실행되는 코드를 포함하고 있습니다. 대부분의 컴포넌트에서는 이것이 필요한 전부입니다.

매우 드물게, 개별 컴포넌트 인스턴스 외부에서 일부 코드를 실행해야 할 필요가 있습니다. 예를 들어: [이전 연습](media-elements)의 커스텀 오디오 플레이어로 돌아가서, 네 개의 트랙을 동시에 재생할 수 있습니다. 하나를 재생하면 다른 모든 트랙이 멈추는 것이 더 좋을 것입니다.

`<script module>` 블록을 선언하여 이를 구현할 수 있습니다. 그 안에 포함된 코드는 컴포넌트가 인스턴스화될 때가 아니라 모듈이 처음 평가될 때 한 번만 실행됩니다. AudioPlayer.svelte의 맨 위에 이것을 배치하세요(이것은 _별도의_ script 태그임에 주의하세요):

```svelte
/// file: AudioPlayer.svelte
+++<script module>
	let current;
</script>+++
```

이제 컴포넌트들이 상태 관리 없이도 서로 '대화'할 수 있게 되었습니다:

```svelte
/// file: AudioPlayer.svelte
<audio
	src={src}
	bind:currentTime={time}
	bind:duration
	bind:paused
+++	onplay={(e) => {
		const audio = e.currentTarget;

		if (audio !== current) {
			current?.pause();
			current = audio;
		}
	}}+++
	onended={() => {
		time = 0;
	}}
/>
```
