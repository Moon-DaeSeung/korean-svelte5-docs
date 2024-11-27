<script>
  const projects = [
    {
      title: 'NotionPresso',
      description: '노션 콘텐츠를 웹사이트로 렌더링하트 라이브러리',
      status: 'in-progress',
      statusText: '진행 중',
      features: [
        'React 버전 완료, Svelte 5 버전 개발 중',
        '노션 API와 스벨트의 강력한 기능 결합'
      ],
      url: 'https://notionpresso.com',
      icon: '📚'
    },
    {
      title: 'SSGOI',
      description: '크로스 브라우저 페이지 전환 애니메이션 라이브러리',
      status: 'completed',
      statusText: '완료',
      features: [
        '모든 브라우저 호환 페이지 전환',
        'SvelteKit 최적화'
      ],
      url: 'https://ssgoi.dev',
      icon: '🚀'
    },
    {
      title: 'EasyRD',
      description: '실시간 협업 다이어그램 서비스',
      status: 'active',
      statusText: '운영 중',
      features: [
        '실시간 협업 기능',
        'dbml 포맷 지원'
      ],
      url: 'https://easyrd.dev',
      icon: '📊'
    }
  ];

  let hoveredProject = null;
</script>

<style>
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 1.5rem;
    padding: 1rem;
  }

  @media (min-width: 768px) {
    .projects-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (min-width: 1024px) {
    .projects-grid {
      grid-template-columns: repeat(3, 1fr);
    }
  }

  .project-card {
    background-color: white;
    border-radius: 0.5rem;
    padding: 1.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    transition: box-shadow 0.3s ease;
  }

  .project-card:hover {
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  }

  .card-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 1rem;
  }

  .project-icon {
    font-size: 2rem;
  }

  .status-badge {
    padding: 0.25rem 0.75rem;
    border-radius: 9999px;
    font-size: 0.875rem;
  }

  .status-badge.in-progress {
    background-color: #dbeafe;
    color: #1e40af;
  }

  .status-badge.completed {
    background-color: #dcfce7;
    color: #166534;
  }

  .status-badge.active {
    background-color: #f3e8ff;
    color: #6b21a8;
  }

  .project-title {
    font-size: 1.25rem;
    font-weight: bold;
    margin-bottom: 0.5rem;
  }

  .project-description {
    color: #4b5563;
    margin-bottom: 1rem;
  }

  .features-list {
    margin-bottom: 1rem;
  }

  .feature-item {
    display: flex;
    align-items: center;
    color: #4b5563;
    font-size: 0.875rem;
    margin-bottom: 0.5rem;
  }

  .feature-item::before {
    content: "•";
    margin-right: 0.5rem;
  }

  .project-link {
    display: inline-flex;
    align-items: center;
    color: #2563eb;
    text-decoration: none;
  }

  .project-link:hover {
    color: #1e40af;
  }

  .link-icon {
    margin-left: 0.25rem;
    width: 1rem;
    height: 1rem;
  }
</style>

<div class="projects-grid">
  {#each projects as project}
    <div class="project-card">
      <div class="card-header">
        <span class="project-icon">{project.icon}</span>
        <span class="status-badge {project.status}">{project.statusText}</span>
      </div>
      
      <h3 class="project-title">{project.title}</h3>
      <p class="project-description">{project.description}</p>
      
      <ul class="features-list">
        {#each project.features as feature}
          <li class="feature-item">{feature}</li>
        {/each}
      </ul>
      
      <a href={project.url} class="project-link" target="_blank" rel="noopener noreferrer">
        둘러보기
        <svg class="link-icon" viewBox="0 0 20 20" fill="currentColor">
          <path fill-rule="evenodd" d="M10.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L12.586 11H5a1 1 0 110-2h7.586l-2.293-2.293a1 1 0 010-1.414z" clip-rule="evenodd" />
        </svg>
      </a>
    </div>
  {/each}
</div>