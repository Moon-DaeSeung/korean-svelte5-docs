<script>
  const benefits = [
    {
      title: "이제 스벨트5를 시작할 때! 🎯",
      description: "룬($) 문법으로 전역 상태 관리가 더욱 쉬워졌어요"
    },
    {
      title: "지금이 가장 완벽한 시기! ⭐",
      description: "기존 문법 배우고 또 새로 배울 필요 없음"
    },
    {
      title: "스벨트5를 하면 생기는 일 ✨",
      items: [
        "입맛이 싹 돌아옴",
        "와이파이가 잘 터짐",
        "맥북 배터리 수명이 2배 증가",
        "버그가 절반으로 줄어듦",
        "코드가 저절로 이쁘게 정렬됨"
      ]
    }
  ];
</script>

<style>
  .container {
    max-width: 800px;
    margin: 20px auto;
    padding: 20px;
  }

  .title {
    font-size: 24px;
    font-weight: bold;
    padding: 15px 0;
    margin-bottom: 20px;
    color: #333;
  }

  .section {
    padding: 15px 0;
    margin-bottom: 20px;
  }

  .section-title {
    font-size: 18px;
    font-weight: bold;
    margin-bottom: 10px;
    color: #2c3e50;
  }

  .description {
    color: #666;
    margin-bottom: 10px;
    line-height: 1.5;
  }

  .magic-list {
    list-style-type: none;
    padding: 0;
    margin: 0;
  }

  .magic-item {
    padding: 8px 0;
    color: #555;
    display: flex;
    align-items: center;
  }

  .magic-item:before {
    content: "•";
    margin-right: 10px;
    color: #2c3e50;
    font-size: 1.2em;
  }

  /* 구분선 추가 */
  .section + .section {
    border-top: 1px solid #eee;
  }
</style>

<div class="container">
  <div class="title">🚀 왜 지금 스벨트5인가?</div>
  
  {#each benefits as benefit}
    <div class="section">
      <div class="section-title">{benefit.title}</div>
      {#if benefit.description}
        <div class="description">{benefit.description}</div>
      {/if}
      {#if benefit.items}
        <ul class="magic-list">
          {#each benefit.items as item}
            <li class="magic-item">{item}</li>
          {/each}
        </ul>
      {/if}
    </div>
  {/each}
</div>