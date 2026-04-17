<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Alais Barbosa — Coordenadora de TI</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Mono:wght@300;400;500&family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0f1e;
    --surface: #111827;
    --surface2: #1a2235;
    --border: rgba(100,160,255,0.12);
    --accent: #3b82f6;
    --accent2: #06b6d4;
    --accent3: #8b5cf6;
    --text: #e2e8f0;
    --text-muted: #94a3b8;
    --text-dim: #64748b;
    --health: #10b981;
    --glow: rgba(59,130,246,0.15);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Outfit', sans-serif;
    font-weight: 300;
    line-height: 1.7;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── NOISE TEXTURE OVERLAY ── */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
    pointer-events: none; z-index: 0; opacity: 0.4;
  }

  /* ── GRID BG ── */
  .grid-bg {
    position: fixed; inset: 0; z-index: 0;
    background-image:
      linear-gradient(rgba(59,130,246,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(59,130,246,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
  }

  .container {
    position: relative; z-index: 1;
    max-width: 900px;
    margin: 0 auto;
    padding: 60px 24px 100px;
  }

  /* ── HEADER ── */
  header {
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 40px;
    align-items: start;
    margin-bottom: 72px;
    padding-bottom: 48px;
    border-bottom: 1px solid var(--border);
    animation: fadeUp 0.8s ease both;
  }

  .header-left { }

  .badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background: rgba(16,185,129,0.12);
    border: 1px solid rgba(16,185,129,0.3);
    color: var(--health);
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 0.08em;
    padding: 4px 12px;
    border-radius: 100px;
    margin-bottom: 20px;
  }

  .badge::before {
    content: '';
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--health);
    animation: pulse-dot 2s infinite;
  }

  h1 {
    font-family: 'DM Serif Display', serif;
    font-size: clamp(2.4rem, 6vw, 3.8rem);
    font-weight: 400;
    line-height: 1.05;
    letter-spacing: -0.02em;
    color: #f1f5f9;
    margin-bottom: 10px;
  }

  h1 em {
    font-style: italic;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .role-title {
    font-size: 1rem;
    font-weight: 500;
    color: var(--text-muted);
    letter-spacing: 0.04em;
    text-transform: uppercase;
    font-size: 0.8rem;
    margin-bottom: 24px;
  }

  .contact-row {
    display: flex;
    flex-wrap: wrap;
    gap: 16px;
  }

  .contact-item {
    display: flex;
    align-items: center;
    gap: 7px;
    font-family: 'DM Mono', monospace;
    font-size: 12px;
    color: var(--text-muted);
    text-decoration: none;
    transition: color 0.2s;
  }
  .contact-item:hover { color: var(--accent2); }
  .contact-item svg { flex-shrink: 0; }

  .header-right {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    gap: 12px;
    padding-top: 4px;
  }

  .stat-pill {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 12px 20px;
    text-align: right;
    min-width: 130px;
  }

  .stat-pill .num {
    font-family: 'DM Serif Display', serif;
    font-size: 1.8rem;
    color: var(--accent);
    line-height: 1;
    display: block;
  }

  .stat-pill .lbl {
    font-size: 0.68rem;
    color: var(--text-dim);
    text-transform: uppercase;
    letter-spacing: 0.06em;
  }

  /* ── ABOUT ── */
  .about {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 28px 32px;
    margin-bottom: 56px;
    position: relative;
    overflow: hidden;
    animation: fadeUp 0.8s 0.1s ease both;
  }

  .about::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2), var(--accent3));
  }

  .about p {
    font-size: 0.95rem;
    color: var(--text-muted);
    line-height: 1.8;
  }

  .about p strong {
    color: var(--text);
    font-weight: 600;
  }

  /* ── SECTION TITLES ── */
  .section {
    margin-bottom: 52px;
    animation: fadeUp 0.8s ease both;
  }

  .section:nth-child(3) { animation-delay: 0.15s; }
  .section:nth-child(4) { animation-delay: 0.2s; }
  .section:nth-child(5) { animation-delay: 0.25s; }
  .section:nth-child(6) { animation-delay: 0.3s; }

  .section-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 28px;
  }

  .section-icon {
    width: 36px; height: 36px;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    flex-shrink: 0;
  }

  .section-title {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    font-weight: 500;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--text-dim);
  }

  .section-line {
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ── EXPERIENCE CARDS ── */
  .exp-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 28px 32px;
    margin-bottom: 16px;
    position: relative;
    transition: border-color 0.3s, transform 0.3s;
  }

  .exp-card:hover {
    border-color: rgba(59,130,246,0.3);
    transform: translateX(4px);
  }

  .exp-card::before {
    content: '';
    position: absolute;
    left: 0; top: 20%; bottom: 20%;
    width: 2px;
    border-radius: 2px;
    background: linear-gradient(180deg, var(--accent), var(--accent2));
    opacity: 0;
    transition: opacity 0.3s;
  }

  .exp-card:hover::before { opacity: 1; }

  .exp-top {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    gap: 16px;
    margin-bottom: 6px;
    flex-wrap: wrap;
  }

  .exp-company {
    font-size: 0.75rem;
    font-weight: 500;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    color: var(--accent2);
    margin-bottom: 4px;
    font-family: 'DM Mono', monospace;
  }

  .exp-role {
    font-size: 1.05rem;
    font-weight: 600;
    color: var(--text);
  }

  .exp-period {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--text-dim);
    background: var(--surface2);
    padding: 4px 10px;
    border-radius: 6px;
    white-space: nowrap;
    border: 1px solid var(--border);
  }

  .exp-bullets {
    margin-top: 16px;
    display: flex;
    flex-direction: column;
    gap: 6px;
  }

  .exp-bullet {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    font-size: 0.88rem;
    color: var(--text-muted);
    line-height: 1.6;
  }

  .exp-bullet::before {
    content: '';
    width: 5px; height: 5px;
    border-radius: 50%;
    background: var(--accent);
    margin-top: 8px;
    flex-shrink: 0;
    opacity: 0.7;
  }

  /* ── SKILLS ── */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 12px;
  }

  .skill-group {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 18px 20px;
    transition: border-color 0.3s, background 0.3s;
  }

  .skill-group:hover {
    border-color: rgba(59,130,246,0.3);
    background: var(--surface2);
  }

  .skill-group-title {
    font-size: 0.68rem;
    font-family: 'DM Mono', monospace;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--accent2);
    margin-bottom: 10px;
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .tag {
    background: rgba(59,130,246,0.1);
    border: 1px solid rgba(59,130,246,0.2);
    color: var(--accent);
    font-size: 0.75rem;
    padding: 3px 10px;
    border-radius: 6px;
    font-family: 'DM Mono', monospace;
  }

  .tag.health {
    background: rgba(16,185,129,0.1);
    border-color: rgba(16,185,129,0.25);
    color: var(--health);
  }

  .tag.purple {
    background: rgba(139,92,246,0.1);
    border-color: rgba(139,92,246,0.25);
    color: #a78bfa;
  }

  /* ── EDUCATION / CERTS ── */
  .edu-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 14px;
  }

  .edu-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 22px 24px;
    transition: border-color 0.3s;
    position: relative;
    overflow: hidden;
  }

  .edu-card:hover { border-color: rgba(59,130,246,0.3); }

  .edu-card .icon-wrap {
    width: 38px; height: 38px;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    margin-bottom: 14px;
  }

  .edu-card h4 {
    font-size: 0.9rem;
    font-weight: 600;
    color: var(--text);
    margin-bottom: 4px;
    line-height: 1.4;
  }

  .edu-card .sub {
    font-size: 0.78rem;
    color: var(--text-dim);
    font-family: 'DM Mono', monospace;
  }

  .edu-card .status {
    margin-top: 10px;
    font-size: 0.7rem;
    font-family: 'DM Mono', monospace;
    text-transform: uppercase;
    letter-spacing: 0.06em;
  }

  .status.active {
    color: var(--health);
    display: flex; align-items: center; gap: 5px;
  }

  .status.active::before {
    content: '';
    width: 5px; height: 5px;
    border-radius: 50%;
    background: var(--health);
    animation: pulse-dot 2s infinite;
  }

  .status.done { color: var(--text-dim); }

  /* ── COURSES ── */
  .courses-list {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .course-item {
    display: flex;
    align-items: center;
    gap: 14px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 12px 18px;
    font-size: 0.86rem;
    transition: border-color 0.25s;
  }

  .course-item:hover { border-color: rgba(59,130,246,0.25); }

  .course-item .name { color: var(--text); flex: 1; }
  .course-item .hours {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--text-dim);
    background: var(--surface2);
    padding: 2px 8px;
    border-radius: 4px;
    border: 1px solid var(--border);
  }

  .course-item .year {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--accent2);
  }

  /* ── FOOTER ── */
  footer {
    margin-top: 80px;
    padding-top: 32px;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 12px;
  }

  .footer-name {
    font-family: 'DM Serif Display', serif;
    font-size: 1.1rem;
    color: var(--text-dim);
  }

  .footer-date {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--text-dim);
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @keyframes pulse-dot {
    0%, 100% { opacity: 1; transform: scale(1); }
    50%       { opacity: 0.4; transform: scale(0.7); }
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 600px) {
    header { grid-template-columns: 1fr; }
    .header-right { flex-direction: row; align-items: flex-start; flex-wrap: wrap; }
    .stat-pill { min-width: 100px; text-align: left; }
    .exp-card { padding: 22px 20px; }
  }
</style>
</head>
<body>

<div class="grid-bg"></div>

<div class="container">

  <!-- ══ HEADER ══ -->
  <header>
    <div class="header-left">
      <h1>Alais<br><em>Barbosa</em></h1>
      <p class="role-title">Gestão Hospitalar · BI &amp; Dados</p>
      <div class="contact-row">
        <a href="https://wa.me/5527998044027" target="_blank" rel="noopener" class="contact-item">
          <svg width="13" height="13" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413Z"/></svg>
          (27) 99804-4027
        </a>
        <a href="mailto:alaiscs@gmail.com" class="contact-item">
          <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
          alaiscs@gmail.com
        </a>
        <span class="contact-item">
          <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M20 10c0 6-8 12-8 12s-8-6-8-12a8 8 0 0 1 16 0Z"/><circle cx="12" cy="10" r="3"/></svg>
          Vila Velha, ES
        </span>
        <span class="contact-item">
          <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="3"/><path d="M16 8a6 6 0 0 1-6 6H8M8 8h8"/><line x1="8" y1="16" x2="8" y2="8"/></svg>
          CNH AB
        </span>
      </div>
    </div>

  </header>

  <!-- ══ ABOUT ══ -->
  <div class="about">
    <p>
      Profissional com experiência sólida em <strong>análise de dados, Business Intelligence e apoio estratégico à gestão hospitalar</strong>. 
      Atua na construção de dashboards, automação de processos e geração de indicadores para suporte à tomada de decisão em nível gerencial e diretivo. 
      Experiência na integração de dados de diferentes fontes, melhoria de processos e estruturação de informações para aumento da eficiência operacional.
    </p>
  </div>

  <!-- ══ EXPERIÊNCIA ══ -->
  <div class="section">
    <div class="section-header">
      <div class="section-icon" style="background:rgba(59,130,246,0.12); border:1px solid rgba(59,130,246,0.2)">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#3b82f6" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="7" width="20" height="14" rx="2"/><path d="M16 21V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v16"/></svg>
      </div>
      <span class="section-title">Experiência Profissional</span>
      <div class="section-line"></div>
    </div>

    <!-- iNOVA CAPIXABA -->
    <div class="exp-card">
      <div class="exp-top">
        <div>
          <div class="exp-company">Fundação Estadual de Inovação em Saúde — iNOVA CAPIXABA</div>
          <div class="exp-role">Assessora de Gestão III</div>
        </div>
        <span class="exp-period">ago 2024 → atual</span>
      </div>
      <div class="exp-bullets">
        <div class="exp-bullet">Criação de dashboards e relatórios para monitoramento de desempenho hospitalar (Power BI, Google Data Studio, Excel)</div>
        <div class="exp-bullet">Apoio à tomada de decisão com base em dados e indicadores estratégicos para diretoria</div>
        <div class="exp-bullet">Automação de tarefas e integração de dados utilizando Python e Google Apps Script</div>
        <div class="exp-bullet">Controle e análise de produção hospitalar, cirurgias e metas institucionais</div>
        <div class="exp-bullet">Organização de informações para reuniões gerenciais e de performance</div>
        <div class="exp-bullet">Apoio à gestão documental e padronização de processos administrativos</div>
      </div>
    </div>

    <!-- SESA / MGS -->
    <div class="exp-card">
      <div class="exp-top">
        <div>
          <div class="exp-company">Secretaria de Estado da Saúde do ES — MGS</div>
          <div class="exp-role">Assistente Administrativo</div>
        </div>
        <span class="exp-period">fev 2024 → ago 2024</span>
      </div>
      <div class="exp-bullets">
        <div class="exp-bullet">Elaboração de relatórios de produção e gestão hospitalar</div>
        <div class="exp-bullet">Extração de AIHs, controle de cirurgias eletivas e gestão documental (eDocs)</div>
        <div class="exp-bullet">Monitoramento de contratos e obrigações contratuais</div>
        <div class="exp-bullet">Aprimoramento de processos operacionais e suporte à comunicação entre equipes</div>
      </div>
    </div>

    <!-- TRE -->
    <div class="exp-card">
      <div class="exp-top">
        <div>
          <div class="exp-company">Tribunal Regional Eleitoral do Espírito Santo</div>
          <div class="exp-role">Estagiária em Sistemas de Informação</div>
        </div>
        <span class="exp-period">out 2014 → out 2016</span>
      </div>
      <div class="exp-bullets">
        <div class="exp-bullet">Suporte a sistemas, estrutura de dados, aplicações web e automação de processos</div>
      </div>
    </div>

    <!-- TJES -->
    <div class="exp-card">
      <div class="exp-top">
        <div>
          <div class="exp-company">Tribunal de Justiça do Espírito Santo</div>
          <div class="exp-role">Estagiária em Sistemas de Informação</div>
        </div>
        <span class="exp-period">jan 2014 → out 2014</span>
      </div>
      <div class="exp-bullets">
        <div class="exp-bullet">Atendimento técnico, manutenção de equipamentos e suporte ao usuário</div>
      </div>
    </div>
  </div>

  <!-- ══ HABILIDADES ══ -->
  <div class="section">
    <div class="section-header">
      <div class="section-icon" style="background:rgba(6,182,212,0.12); border:1px solid rgba(6,182,212,0.2)">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#06b6d4" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m12 3-1.912 5.813a2 2 0 0 1-1.275 1.275L3 12l5.813 1.912a2 2 0 0 1 1.275 1.275L12 21l1.912-5.813a2 2 0 0 1 1.275-1.275L21 12l-5.813-1.912a2 2 0 0 1-1.275-1.275L12 3Z"/></svg>
      </div>
      <span class="section-title">Habilidades &amp; Competências</span>
      <div class="section-line"></div>
    </div>

    <div class="skills-grid">
      <div class="skill-group">
        <div class="skill-group-title">Inteligência de Dados</div>
        <div class="skill-tags">
          <span class="tag">Power BI</span>
          <span class="tag">Google Data Studio</span>
          <span class="tag">Excel Avançado</span>
          <span class="tag">Google Sheets</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">Automação &amp; Dev</div>
        <div class="skill-tags">
          <span class="tag">Python</span>
          <span class="tag">Google Apps Script</span>
          <span class="tag">Integração de dados</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">Gestão Hospitalar</div>
        <div class="skill-tags">
          <span class="tag health">AIH</span>
          <span class="tag health">eDocs</span>
          <span class="tag health">Produção hospitalar</span>
          <span class="tag health">Indicadores SESA</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">Gestão &amp; Processos</div>
        <div class="skill-tags">
          <span class="tag purple">PDCA</span>
          <span class="tag purple">5S</span>
          <span class="tag purple">Gestão documental</span>
          <span class="tag purple">Contratos</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">Soft Skills</div>
        <div class="skill-tags">
          <span class="tag">Liderança</span>
          <span class="tag">Comunicação</span>
          <span class="tag">Proatividade</span>
          <span class="tag">Aprendizado ágil</span>
        </div>
      </div>
    </div>
  </div>

  <!-- ══ FORMAÇÃO ══ -->
  <div class="section">
    <div class="section-header">
      <div class="section-icon" style="background:rgba(139,92,246,0.12); border:1px solid rgba(139,92,246,0.2)">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#8b5cf6" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 10v6M2 10l10-5 10 5-10 5z"/><path d="M6 12v5c3 3 9 3 12 0v-5"/></svg>
      </div>
      <span class="section-title">Formação Acadêmica</span>
      <div class="section-line"></div>
    </div>

    <div class="edu-grid">
      <div class="edu-card">
        <div class="icon-wrap" style="background:rgba(139,92,246,0.12)">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#a78bfa" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="3" width="20" height="14" rx="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>
        </div>
        <h4>Bacharelado em Sistemas de Informação</h4>
        <div class="sub">Multivix · 7º período</div>
        <div class="status active">Em andamento</div>
      </div>
      <div class="edu-card">
        <div class="icon-wrap" style="background:rgba(16,185,129,0.1)">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#10b981" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/></svg>
        </div>
        <h4>Técnico em Informática</h4>
        <div class="sub">EEEM Mário Gurgel · 2011</div>
        <div class="status done">Concluído</div>
      </div>
    </div>
  </div>

  <!-- ══ CURSOS ══ -->
  <div class="section">
    <div class="section-header">
      <div class="section-icon" style="background:rgba(16,185,129,0.1); border:1px solid rgba(16,185,129,0.2)">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#10b981" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
      </div>
      <span class="section-title">Cursos &amp; Certificações</span>
      <div class="section-line"></div>
    </div>

    <div class="courses-list">
      <div class="course-item">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#3b82f6" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>
        <span class="name">Certificação Profissional Microsoft Power BI Data Analyst</span>
        <span class="year">2026</span>
        <span class="hours" style="color:var(--health); border-color:rgba(16,185,129,0.25)">em andamento</span>
      </div>
      <div class="course-item">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#f59e0b" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><path d="M3 9h18M9 21V9"/></svg>
        <span class="name">Excel com Inteligência Artificial — Santander / DIO</span>
        <span class="year">2025</span>
        <span class="hours">26h</span>
      </div>
      <div class="course-item">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#06b6d4" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><path d="M3 9h18M9 21V9"/></svg>
        <span class="name">Excel Avançado — ESESP</span>
        <span class="year">2024</span>
        <span class="hours">20h</span>
      </div>
      <div class="course-item">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#8b5cf6" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/></svg>
        <span class="name">eDocs — ESESP</span>
        <span class="year">2024</span>
        <span class="hours">4h</span>
      </div>
      <div class="course-item">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#10b981" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m12 3-1.912 5.813a2 2 0 0 1-1.275 1.275L3 12l5.813 1.912a2 2 0 0 1 1.275 1.275L12 21l1.912-5.813a2 2 0 0 1 1.275-1.275L21 12l-5.813-1.912a2 2 0 0 1-1.275-1.275L12 3Z"/></svg>
        <span class="name">Introdução ao 5S</span>
        <span class="year">2025</span>
        <span class="hours">20h</span>
      </div>
    </div>
  </div>

  <!-- ══ FOOTER ══ -->
  <footer>
    <span class="footer-name">Alais Cassimira Salino Barbosa</span>
    <span class="footer-date">Currículo · Vila Velha, ES · 2026</span>
  </footer>

</div>
</body>
</html>
