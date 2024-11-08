---
title: Tween 값
---

`writable`과 `readable` 스토어 외에도, Svelte는 사용자 인터페이스에 모션을 추가하기 위한 스토어를 제공합니다.

먼저 `progress` 스토어를 `tweened` 스토어로 변경해봅시다:

```svelte
/// file: App.svelte
<script>
	import { +++tweened+++ } from 'svelte/+++motion+++';

	const progress = +++tweened+++(0);
</script>
```

버튼을 클릭하면 진행 막대가 새로운 값으로 애니메이션됩니다. 하지만 약간 로봇 같고 만족스럽지 않습니다. easing 함수를 추가해야 합니다:

```svelte
/// file: App.svelte
<script>
	import { tweened } from 'svelte/motion';
	+++import { cubicOut } from 'svelte/easing';+++

	const progress = tweened(0, +++{
		duration: 400,
		easing: cubicOut
	}+++);
</script>
```

> [!NOTE] `svelte/easing` 모듈은 [Penner easing 방정식](https://web.archive.org/web/20190805215728/http://robertpenner.com/easing/)을 포함하고 있으며, 또는 `p`와 `t`가 모두 0과 1 사이의 값인 자신만의 `p => t` 함수를 제공할 수도 있습니다.

`tweened`에서 사용할 수 있는 전체 옵션 목록:

- `delay` — tween이 시작되기 전 밀리초 단위 지연
- `duration` — tween의 지속 시간(밀리초) 또는 더 큰 값 변화에 대해 더 긴 tween을 지정할 수 있는 `(from, to) => milliseconds` 함수
- `easing` — `p => t` 함수
- `interpolate` — 임의의 값 사이를 보간하기 위한 사용자 정의 `(from, to) => t => value` 함수. 기본적으로 Svelte는 숫자, 날짜, 그리고 동일한 형태의 배열과 객체(숫자와 날짜 또는 다른 유효한 배열과 객체만 포함하는 경우) 사이를 보간합니다. 색상 문자열이나 변환 행렬과 같은 것을 보간하려면 사용자 정의 보간자를 제공하세요.

이러한 옵션들은 두 번째 인수로 `progress.set`과 `progress.update`에도 전달할 수 있으며, 이 경우 기본값을 재정의합니다. `set`과 `update` 메서드는 모두 tween이 완료될 때 해결되는 프로미스를 반환합니다.