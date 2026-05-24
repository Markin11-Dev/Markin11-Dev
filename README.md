<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Marco Antonio — Dev Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0d0f14;
    --surface: #131720;
    --card: #1a1f2e;
    --accent: #1A5276;
    --green: #2ECC71;
    --text: #e8eaf0;
    --muted: #7a8099;
    --border: #252d3f;
    --font-display: 'Syne', sans-serif;
    --font-mono: 'Space Mono', monospace;
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-display);
    min-height: 100vh;
    overflow-x: hidden;
  }
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(26,82,118,0.07) 1px, transparent 1px),
      linear-gradient(90deg, rgba(26,82,118,0.07) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }
  .container { max-width: 860px; margin: 0 auto; padding: 40px 20px 80px; position: relative; z-index: 1; }
  .header { text-align: center; padding: 60px 0 40px; }
  .header::after { content: ''; display: block; width: 120px; height: 3px; background: linear-gradient(90deg, var(--accent), var(--green)); margin: 24px auto 0; border-radius: 2px; }
  .header-name { font-size: clamp(2.4rem, 6vw, 4rem); font-weight: 800; letter-spacing: -1px; line-height: 1.1; background: linear-gradient(135deg, #fff 30%, var(--green)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; animation: fadeSlideDown 0.7s ease both; }
  .header-sub { margin-top: 10px; font-family: var(--font-mono); font-size: 0.85rem; color: var(--green); letter-spacing: 2px; animation: fadeSlideDown 0.7s 0.15s ease both; opacity: 0; animation-fill-mode: forwards; }
  .status-badge { display: inline-flex; align-items: center; gap: 8px; margin-top: 18px; padding: 7px 16px; background: rgba(46,204,113,0.1); border: 1px solid rgba(46,204,113,0.3); border-radius: 100px; font-size: 0.82rem; color: var(--green); font-family: var(--font-mono); animation: fadeSlideDown 0.7s 0.3s ease both; opacity: 0; animation-fill-mode: forwards; }
  .status-dot { width: 8px; height: 8px; border-radius: 50%; background: var(--green); animation: pulse 1.5s ease infinite; }
  .socials { display: flex; justify-content: center; gap: 12px; margin-top: 24px; flex-wrap: wrap; animation: fadeSlideDown 0.7s 0.45s ease both; opacity: 0; animation-fill-mode: forwards; }
  .social-btn { display: inline-flex; align-items: center; gap: 6px; padding: 8px 16px; border-radius: 8px; border: 1px solid var(--border); background: var(--card); color: var(--text); text-decoration: none; font-family: var(--font-mono); font-size: 0.78rem; transition: all 0.2s; }
  .social-btn:hover { border-color: var(--accent); background: rgba(26,82,118,0.2); transform: translateY(-2px); }
  .social-btn svg { width: 15px; height: 15px; }
  section { margin-top: 40px; }
  .section-label { font-family: var(--font-mono); font-size: 0.72rem; letter-spacing: 3px; color: var(--accent); text-transform: uppercase; margin-bottom: 16px; display: flex; align-items: center; gap: 12px; }
  .section-label::after { content: ''; flex: 1; height: 1px; background: var(--border); }
  .about-card { background: var(--card); border: 1px solid var(--border); border-radius: 14px; padding: 28px; font-family: var(--font-mono); font-size: 0.82rem; line-height: 2; position: relative; overflow: hidden; }
  .about-card::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px; background: linear-gradient(90deg, var(--accent), var(--green)); }
  .code-line { display: flex; gap: 16px; }
  .code-key { color: var(--accent); min-width: 90px; }
  .code-val { color: var(--green); }
  .code-str { color: #e8a87c; }
  .code-arr { color: var(--muted); }
  .code-bracket { color: var(--muted); }
  .skills-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 12px; }
  .skill-group { background: var(--card); border: 1px solid var(--border); border-radius: 12px; padding: 20px; transition: all 0.2s; }
  .skill-group:hover { border-color: var(--accent); transform: translateY(-3px); }
  .skill-group-title { font-size: 0.7rem; letter-spacing: 2px; color: var(--muted); text-transform: uppercase; margin-bottom: 12px; }
  .skill-tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .tag { padding: 4px 10px; border-radius: 6px; font-family: var(--font-mono); font-size: 0.72rem; border: 1px solid; }
  .tag-blue { background: rgba(26,82,118,0.15); border-color: rgba(26,82,118,0.4); color: #5dade2; }
  .tag-green { background: rgba(46,204,113,0.1); border-color: rgba(46,204,113,0.3); color: var(--green); }
  .tag-orange { background: rgba(231,76,60,0.1); border-color: rgba(231,76,60,0.3); color: #e67e73; }
  .projects-grid { display: grid; gap: 14px; }
  .project-card { background: var(--card); border: 1px solid var(--border); border-radius: 14px; padding: 22px 24px; display: flex; align-items: flex-start; gap: 18px; transition: all 0.25s; }
  .project-card:hover { border-color: var(--accent); background: rgba(26,82,118,0.08); transform: translateX(4px); }
  .project-icon { font-size: 1.8rem; min-width: 44px; text-align: center; }
  .project-info h3 { font-size: 1rem; font-weight: 700; margin-bottom: 5px; }
  .project-info p { font-size: 0.83rem; color: var(--muted); line-height: 1.6; margin-bottom: 10px; }
  .project-tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .cert-table { width: 100%; border-collapse: separate; border-spacing: 0 8px; }
  .cert-table thead th { font-family: var(--font-mono); font-size: 0.7rem; letter-spacing: 2px; color: var(--muted); text-transform: uppercase; padding: 0 16px 8px; text-align: left; }
  .cert-table tbody tr { background: var(--card); border: 1px solid var(--border); border-radius: 10px; transition: all 0.2s; }
  .cert-table tbody tr:hover { background: rgba(26,82,118,0.1); }
  .cert-table tbody td { padding: 14px 16px; font-size: 0.85rem; vertical-align: middle; }
  .cert-table tbody td:first-child { border-radius: 10px 0 0 10px; }
  .cert-table tbody td:last-child { border-radius: 0 10px 10px 0; }
  .cert-year { font-family: var(--font-mono); font-size: 0.78rem; color: var(--green); }
  .cert-hours { font-family: var(--font-mono); font-size: 0.78rem; color: var(--muted); }
  .learning-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(180px, 1fr)); gap: 12px; }
  .learning-card { background: var(--card); border: 1px solid var(--border); border-radius: 12px; padding: 18px; text-align: center; transition: all 0.2s; }
  .learning-card:hover { border-color: var(--green); transform: scale(1.03); }
  .learning-icon { font-size: 1.8rem; margin-bottom: 8px; }
  .learning-name { font-size: 0.85rem; font-weight: 700; }
  .learning-desc { font-size: 0.73rem; color: var(--muted); margin-top: 4px; font-family: var(--font-mono); }
  .cta-box { background: linear-gradient(135deg, rgba(26,82,118,0.2), rgba(46,204,113,0.08)); border: 1px solid rgba(26,82,118,0.4); border-radius: 16px; padding: 36px; text-align: center; margin-top: 48px; }
  .cta-box h2 { font-size: 1.6rem; font-weight: 800; margin-bottom: 10px; }
  .cta-box p { color: var(--muted); font-size: 0.9rem; margin-bottom: 24px; }
  .cta-btn { display: inline-flex; align-items: center; gap: 8px; padding: 12px 28px; background: var(--accent); color: #fff; border-radius: 10px; text-decoration: none; font-weight: 700; font-size: 0.9rem; transition: all 0.2s; font-family: var(--font-display); }
  .cta-btn:hover { background: #1a6494; transform: translateY(-2px); box-shadow: 0 8px 24px rgba(26,82,118,0.4); }
  .competencias-grid { display: flex; flex-wrap: wrap; gap: 10px; }
  .competencia-chip { display: flex; align-items: center; gap: 7px; padding: 9px 16px; background: var(--card); border: 1px solid var(--border); border-radius: 100px; font-size: 0.82rem; transition: all 0.2s; }
  .competencia-chip:hover { border-color: var(--green); color: var(--green); transform: translateY(-2px); }
  .stats-row { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; }
  @media (max-width: 540px) { .stats-row { grid-template-columns: 1fr; } }
  .stat-card { background: var(--card); border: 1px solid var(--border); border-radius: 14px; padding: 22px; display: flex; flex-direction: column; gap: 6px; }
  .stat-num { font-size: 2rem; font-weight: 800; color: var(--green); font-family: var(--font-mono); }
  .stat-label { font-size: 0.8rem; color: var(--muted); }
  .stat-bar { width: 100%; height: 4px; background: var(--border); border-radius: 2px; margin-top: 8px; overflow: hidden; }
  .stat-bar-fill { height: 100%; border-radius: 2px; background: linear-gradient(90deg, var(--accent), var(--green)); animation: barGrow 1.4s 0.5s ease both; transform-origin: left; }
  .lang-item { margin-bottom: 14px; }
  .lang-meta { display: flex; justify-content: space-between; font-family: var(--font-mono); font-size: 0.78rem; margin-bottom: 6px; }
  .lang-bar { height: 6px; background: var(--border); border-radius: 3px; overflow: hidden; }
  .lang-bar-fill { height: 100%; border-radius: 3px; animation: barGrow 1.2s ease both; transform-origin: left; }
  @keyframes fadeSlideDown { from { opacity: 0; transform: translateY(-16px); } to { opacity: 1; transform: translateY(0); } }
  @keyframes pulse { 0%, 100% { opacity: 1; } 50% { opacity: 0.3; } }
  @keyframes barGrow { from { transform: scaleX(0); } to { transform: scaleX(1); } }
  .reveal { opacity: 0; transform: translateY(24px); transition: opacity 0.55s ease, transform 0.55s ease; }
  .reveal.visible { opacity: 1; transform: none; }
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 3px; }
</style>
</head>
<body>
<div class="container">
  <div class="header">
    <div class="header-name">Marco Antonio</div>
    <div class="header-sub">// Analista de Dados · IA &amp; Sistemas · São Paulo 🇧🇷</div>
    <div class="status-badge"><div class="status-dot"></div>Aberto para Oportunidades de Estágio</div>
    <div class="socials">
      <a class="social-btn" href="mailto:marcoantonio2silva@gmail.com">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>Gmail
      </a>
      <a class="social-btn" href="https://linkedin.com" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>LinkedIn
      </a>
      <a class="social-btn" href="https://github.com/Markin11-Dev" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"/></svg>GitHub
      </a>
    </div>
  </div>

  <section class="reveal">
    <div class="section-label">sobre mim</div>
    <div class="about-card">
      <div class="code-line"><span class="code-key">nome</span><span class="code-val">= </span><span class="code-str">"Marco Antonio da Silva Melo"</span></div>
      <div class="code-line"><span class="code-key">localidade</span><span class="code-val">= </span><span class="code-str">"São Paulo – SP 🇧🇷"</span></div>
      <div class="code-line"><span class="code-key">formação</span><span class="code-val">= </span><span class="code-str">"Tecnólogo em ADS – FAM (2025–2026)"</span></div>
      <div class="code-line"><span class="code-key">foco</span><span class="code-val">= </span><span class="code-bracket">[</span><span class="code-str">"Python"</span><span class="code-arr">, </span><span class="code-str">"IA Generativa"</span><span class="code-arr">, </span><span class="code-str">"Análise de Dados"</span><span class="code-bracket">]</span></div>
      <div class="code-line"><span class="code-key">buscando</span><span class="code-val">= </span><span class="code-str">"Estágio em Dados / Desenvolvimento"</span></div>
      <div class="code-line"><span class="code-key">idiomas</span><span class="code-val">= </span><span class="code-bracket">[</span><span class="code-str">"Português (nativo)"</span><span class="code-arr">, </span><span class="code-str">"Inglês (técnico)"</span><span class="code-bracket">]</span></div>
      <div class="code-line"><span class="code-key">fun_fact</span><span class="code-val">= </span><span class="code-str">"Transformo dados em decisões 📊"</span></div>
    </div>
  </section>

  <section class="reveal">
    <div class="section-label">stack de tecnologias</div>
    <div class="skills-grid">
      <div class="skill-group"><div class="skill-group-title">Linguagens</div><div class="skill-tags"><span class="tag tag-blue">Python</span><span class="tag tag-blue">C</span><span class="tag tag-blue">SQL</span></div></div>
      <div class="skill-group"><div class="skill-group-title">Banco de Dados</div><div class="skill-tags"><span class="tag tag-green">MySQL</span><span class="tag tag-green">PostgreSQL</span></div></div>
      <div class="skill-group"><div class="skill-group-title">IA &amp; ML</div><div class="skill-tags"><span class="tag tag-orange">TensorFlow</span><span class="tag tag-orange">PyTorch</span><span class="tag tag-orange">LLMs</span></div></div>
      <div class="skill-group"><div class="skill-group-title">Ferramentas</div><div class="skill-tags"><span class="tag tag-blue">Jupyter</span><span class="tag tag-blue">Streamlit</span><span class="tag tag-blue">Git</span><span class="tag tag-blue">VS Code</span></div></div>
      <div class="skill-group"><div class="skill-group-title">Dados</div><div class="skill-tags"><span class="tag tag-green">Pandas</span><span class="tag tag-green">NumPy</span><span class="tag tag-green">Matplotlib</span></div></div>
    </div>
  </section>

  <section class="reveal">
    <div class="section-label">linguagens mais usadas</div>
    <div class="about-card" style="padding:24px 28px;">
      <div class="lang-item"><div class="lang-meta"><span>Python</span><span style="color:var(--green)">72%</span></div><div class="lang-bar"><div class="lang-bar-fill" style="width:72%; background: linear-gradient(90deg,#3776AB,#5faee3); animation-delay:0.1s;"></div></div></div>
      <div class="lang-item"><div class="lang-meta"><span>SQL</span><span style="color:var(--green)">18%</span></div><div class="lang-bar"><div class="lang-bar-fill" style="width:18%; background: linear-gradient(90deg,#005C84,#00c4e8); animation-delay:0.25s;"></div></div></div>
      <div class="lang-item"><div class="lang-meta"><span>C</span><span style="color:var(--green)">10%</span></div><div class="lang-bar"><div class="lang-bar-fill" style="width:10%; background: linear-gradient(90deg,#00599C,#60a0dc); animation-delay:0.4s;"></div></div></div>
    </div>
  </section>

  <section class="reveal">
    <div class="section-label">projetos em destaque</div>
    <div class="projects-grid">
      <div class="project-card"><div class="project-icon">💼</div><div class="project-info"><h3>Assistente de Investimentos com IA</h3><p>Aplicação com IA generativa para análise de perfil de investidor e recomendações personalizadas.</p><div class="project-tags"><span class="tag tag-blue">Python</span><span class="tag tag-orange">LLM API</span><span class="tag tag-green">Streamlit</span></div></div></div>
      <div class="project-card"><div class="project-icon">📈</div><div class="project-info"><h3>Análise de Transações Financeiras</h3><p>Pipeline de análise de dados para identificar padrões de consumo e gerar insights financeiros.</p><div class="project-tags"><span class="tag tag-blue">Python</span><span class="tag tag-green">Pandas</span><span class="tag tag-blue">Jupyter</span></div></div></div>
      <div class="project-card"><div class="project-icon">🕐</div><div class="project-info"><h3>Sistema de Controle de Ponto</h3><p>Sistema de registro e controle de horas com integração a banco de dados MySQL.</p><div class="project-tags"><span class="tag tag-orange">C</span><span class="tag tag-green">MySQL</span></div></div></div>
      <div class="project-card" style="border-style:dashed; opacity:0.7;"><div class="project-icon">🔮</div><div class="project-info"><h3>Em breve...</h3><p>Novos projetos com GenAI, ML e visualização de dados a caminho!</p><div class="project-tags"><span class="tag tag-orange">WIP</span></div></div></div>
    </div>
  </section>

  <section class="reveal">
    <div class="section-label">atualmente aprendendo</div>
    <div class="learning-grid">
      <div class="learning-card"><div class="learning-icon">🤖</div><div class="learning-name">GenAI &amp; LLMs</div><div class="learning-desc">Bootcamp 52h</div></div>
      <div class="learning-card"><div class="learning-icon">🔗</div><div class="learning-name">RAG Pipelines</div><div class="learning-desc">Embeddings &amp; vetores</div></div>
      <div class="learning-card"><div class="learning-icon">⚡</div><div class="learning-name">APIs REST</div><div class="learning-desc">FastAPI &amp; integração</div></div>
      <div class="learning-card"><div class="learning-icon">📊</div><div class="learning-name">Estatística</div><div class="learning-desc">Para ciência de dados</div></div>
    </div>
  </section>

  <section class="reveal">
    <div class="section-label">formação &amp; certificados</div>
    <p style="font-size:0.82rem; color:var(--muted); margin-bottom:16px; font-family:var(--font-mono);">🎓 Tecnólogo em ADS — FAM, SP · 2025–2026</p>
    <table class="cert-table">
      <thead><tr><th>Curso</th><th>Horas</th><th>Ano</th></tr></thead>
      <tbody>
        <tr><td>🤖 Bootcamp GenAI &amp; Dados</td><td class="cert-hours">52h</td><td class="cert-year">2026</td></tr>
        <tr><td>🗄️ Introdução a Banco de Dados</td><td class="cert-hours">3h</td><td class="cert-year">2026</td></tr>
        <tr><td>🌐 HTML, CSS e JavaScript</td><td class="cert-hours">2h</td><td class="cert-year">2025</td></tr>
        <tr><td>💻 Informática Aplicada</td><td class="cert-hours">100h</td><td class="cert-year">2022</td></tr>
        <tr><td>⚙️ Arduino e Automação</td><td class="cert-hours">20h</td><td class="cert-year">2019</td></tr>
      </tbody>
    </table>
  </section>

  <section class="reveal">
    <div class="section-label">competências</div>
    <div class="competencias-grid">
      <div class="competencia-chip"><span>🧠</span> Aprendizado Rápido</div>
      <div class="competencia-chip"><span>🚀</span> Proatividade</div>
      <div class="competencia-chip"><span>📋</span> Organização</div>
      <div class="competencia-chip"><span>🤝</span> Trabalho em Equipe</div>
      <div class="competencia-chip"><span>💬</span> Boa Comunicação</div>
      <div class="competencia-chip"><span>🌐</span> Inglês Técnico</div>
    </div>
  </section>

  <section class="reveal">
    <div class="section-label">github stats</div>
    <div class="stats-row">
      <div class="stat-card"><div class="stat-label">Commits (último ano)</div><div class="stat-num" id="commits">—</div><div class="stat-bar"><div class="stat-bar-fill" style="width:65%"></div></div></div>
      <div class="stat-card"><div class="stat-label">Linguagem Principal</div><div class="stat-num" style="font-size:1.1rem; margin-top:6px;">Python 🐍</div><div class="stat-bar"><div class="stat-bar-fill" style="width:72%"></div></div></div>
    </div>
    <div style="margin-top:14px;">
      <img src="https://github-readme-stats.vercel.app/api?username=Markin11-Dev&show_icons=true&theme=tokyonight&include_all_commits=true&count_private=true&hide_border=true&title_color=2E86C1&icon_color=2E86C1" alt="GitHub Stats" style="width:100%; border-radius:12px; border:1px solid var(--border);" onerror="this.style.display='none'" />
    </div>
  </section>

  <div class="cta-box reveal">
    <h2>Vamos nos conectar? 📬</h2>
    <p>Se você tem uma oportunidade de estágio ou quer trocar ideia sobre dados e IA, me chama!</p>
    <a class="cta-btn" href="mailto:marcoantonio2silva@gmail.com">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
      marcoantonio2silva@gmail.com
    </a>
  </div>
</div>

<script>
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => { if (entry.isIntersecting) entry.target.classList.add('visible'); });
  }, { threshold: 0.08 });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  function animateCount(el, target, duration) {
    duration = duration || 1800;
    let start = 0;
    const step = target / (duration / 16);
    const timer = setInterval(() => {
      start += step;
      if (start >= target) { el.textContent = target + '+'; clearInterval(timer); return; }
      el.textContent = Math.floor(start);
    }, 16);
  }

  const countersObs = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        animateCount(document.getElementById('commits'), 42);
        countersObs.disconnect();
      }
    });
  });
  const commitEl = document.getElementById('commits');
  if (commitEl) countersObs.observe(commitEl);
</script>
</body>
</html>
