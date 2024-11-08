---
title: 미디어 요소
---

`<audio>`와 `<video>` 요소의 속성에 바인딩할 수 있어서 `AudioPlayer.svelte`와 같은 사용자 정의 플레이어 UI를 쉽게 만들 수 있습니다.

먼저 바인딩과 함께 `<audio>` 요소를 추가합니다(`src`, `duration`, `paused`에 대해서는 축약형을 사용합니다):

```svelte
/// file: AudioPlayer.svelte
<div class="player" class:paused>
+++	<audio
		{src}
		bind:currentTime={time}
		bind:duration
		bind:paused
	></audio>+++

	<button
		class="play"
		aria-label={paused ? 'play' : 'pause'}
	></button>
```

다음으로, `paused`를 토글하는 `<button>`에 이벤트 핸들러를 추가합니다:

```svelte
/// file: AudioPlayer.svelte
<button
	class="play"
	aria-label={paused ? 'play' : 'pause'}
	+++onclick={() => paused = !paused}+++
></button>
```

이제 오디오 플레이어가 기본 기능을 갖추게 되었습니다. 슬라이더를 드래그하여 트랙의 특정 부분으로 이동할 수 있는 기능을 추가해봅시다. 슬라이더의 `pointerdown` 핸들러 안에 `time`을 업데이트하는 `seek` 함수가 있습니다:

```js
/// file: AudioPlayer.svelte
function seek(e) {
	const { left, width } = div.getBoundingClientRect();

	let p = (e.clientX - left) / width;
	if (p < 0) p = 0;
	if (p > 1) p = 1;

	+++time = p * duration;+++
}
```

트랙이 끝나면 친절하게 되감기를 해줍시다:

```svelte
/// file: AudioPlayer.svelte
<audio
	{src}
	bind:currentTime={time}
	bind:duration
	bind:paused
+++	onended={() => {
		time = 0;
	}}+++
></audio>
```

`<audio>`와 `<video>`에 대한 전체 바인딩 목록은 다음과 같습니다 - 일곱 개의 _읽기 전용_ 바인딩...

- `duration` — 총 재생 시간(초)
- `buffered` — `{start, end}` 객체의 배열
- `seekable` — 위와 동일
- `played` — 위와 동일
- `seeking` — 불리언
- `ended` — 불리언
- `readyState` — 0에서 4 사이의 숫자

...그리고 다섯 개의 _양방향_ 바인딩:

- `currentTime` — 재생 헤드의 현재 위치(초)
- `playbackRate` — 재생 속도 조절(1이 '정상')
- `paused` — 설명이 필요 없을 것 같습니다
- `volume` — 0과 1 사이의 값
- `muted` — true가 음소거인 불리언 값

비디오는 추가로 읽기 전용 `videoWidth`와 `videoHeight` 바인딩을 가집니다.