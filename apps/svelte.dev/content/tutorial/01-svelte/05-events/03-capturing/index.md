---
title: 캡처링
---

일반적으로 이벤트 핸들러는 [_버블링_](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Event_bubbling) 단계에서 실행됩니다. 이 예제에서 `<input>`에 무언가를 입력하면 어떤 일이 일어나는지 보세요 - 이벤트가 대상으로부터 문서까지 '버블링'되면서 내부 핸들러가 먼저 실행되고, 그 다음 외부 핸들러가 실행됩니다.

때로는 핸들러가 _캡처_ 단계에서 실행되기를 원할 수 있습니다. 이벤트 이름 끝에 `capture`를 추가하세요:

```svelte
/// file: App.svelte
<div onkeydown+++capture+++={(e) => alert(`<div> ${e.key}`)} role="presentation">
	<input onkeydown+++capture+++={(e) => alert(`<input> ${e.key}`)} />
</div>
```

이제 실행 순서가 반대가 됩니다. 주어진 이벤트에 대해 캡처링과 비캡처링 핸들러가 모두 존재하는 경우, 캡처링 핸들러가 먼저 실행됩니다.
