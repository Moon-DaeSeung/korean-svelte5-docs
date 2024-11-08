---
title: 커스텀 CSS 트랜지션
---

`svelte/transition` 모듈에는 몇 가지 내장 트랜지션이 있지만, 자신만의 트랜지션을 만드는 것도 매우 쉽습니다. 예를 들어, 다음은 `fade` 트랜지션의 소스 코드입니다:

```js
function fade(node, { delay = 0, duration = 400 }) {
	const o = +getComputedStyle(node).opacity;

	return {
		delay,
		duration,
		css: (t) => `opacity: ${t * o}`
	};
}
```

이 함수는 두 개의 인자를 받습니다 — 트랜지션이 적용될 노드와 전달된 매개변수들 — 그리고 다음과 같은 속성을 가질 수 있는 트랜지션 객체를 반환합니다:

- `delay` — 트랜지션이 시작되기 전 대기 시간(밀리초)
- `duration` — 트랜지션의 지속 시간(밀리초)
- `easing` — `p => t` 이징 함수 ([tweening](/tutorial/svelte/tweens) 챕터 참조)
- `css` — `(t, u) => css` 함수, 여기서 `u === 1 - t`
- `tick` — 노드에 영향을 주는 `(t, u) => {...}` 함수

`t` 값은 진입 트랜지션의 시작 또는 퇴장 트랜지션의 끝에서 `0`이며, 진입 트랜지션의 끝 또는 퇴장 트랜지션의 시작에서 `1`입니다.

대부분의 경우 `tick` 속성이 아닌 `css` 속성을 반환해야 합니다. CSS 애니메이션은 가능한 한 성능 저하를 방지하기 위해 메인 스레드 외부에서 실행됩니다. Svelte는 트랜지션을 '시뮬레이션'하고 CSS 애니메이션을 구성한 다음 실행되도록 합니다.

예를 들어, `fade` 트랜지션은 다음과 같은 CSS 애니메이션을 생성합니다:

<!-- prettier-ignore-start -->
```css
0% { opacity: 0 }
10% { opacity: 0.1 }
20% { opacity: 0.2 }
/* ... */
100% { opacity: 1 }
```
<!-- prettier-ignore-end -->

하지만 우리는 더 창의적으로 만들 수 있습니다. 정말 과감한 것을 만들어봅시다:

```svelte
/// file: App.svelte
<script>
	import { fade } from 'svelte/transition';
	+++import { elasticOut } from 'svelte/easing';+++

	let visible = $state(true);

	function spin(node, { duration }) {
		return {
			duration,
			css: t => +++{
				const eased = elasticOut(t);

				return `
					transform: scale(${eased}) rotate(${eased * 1080}deg);
					color: hsl(
						${Math.trunc(t * 360)},
						${Math.min(100, 1000 * (1 - t))}%,
						${Math.min(50, 500 * (1 - t))}%
					);`
			}+++
		};
	}
</script>
```

기억하세요: 큰 힘에는 큰 책임이 따릅니다.
