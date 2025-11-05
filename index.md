---
layout: default
title: Home
permalink: /
---

<figure class="intro-widget">
  <div class="intro-card">
    <img src="{{ '/assets/images/profiilikuva.png' | relative_url }}?v={{ site.time | date: '%s' }}"
    alt="" class="intro-bg" loading="lazy" decoding="async">
    <p class="intro-text">
      I'm Heikki<br>
      Final-year AI and Data Engineering student.<br>
      Passionate about continuous learning and building real world solutions
      with data,<br> modern AI methods, and web technologies.<br>
      Independent and entrepreneurial<br> with strong problem solving and
      great teamwork skills.<br>
      Currently studying <strong>Big Data</strong>, 
      <strong>Web Development</strong>, and 
      <strong>Large Language Models</strong>.
    </p>
  </div>
</figure>

<div class="section-heading">
  <h2 id="projects">Projects</h2>
</div>

<div class="widgets-grid">
  <article class="widget-card" tabindex="0" data-modal="modal-weather">
    <span class="widget-chip">LIVE</span><div class="widget-icon">🌦️</div>
    <h3>Weather Widget</h3>
    <p>Geolocation → Open-Meteo (no backend, CORS ok).</p>
  </article>

  <article class="widget-card" tabindex="0" data-modal="modal-dproc">
    <span class="widget-chip">DATA</span><div class="widget-icon">🧰</div>
    <h3>Data Processing</h3>
    <p>Pandas · DuckDB · Visualizations.</p>
  </article>

  <article class="widget-card" tabindex="0" data-modal="modal-dpipe">
    <span class="widget-chip">ETL</span><div class="widget-icon">🚉</div>
    <h3>Train Delay Pipeline</h3>
    <p>Digitraffic · dbt · Evidence.</p>
  </article>

  <article class="widget-card" tabindex="0" data-modal="modal-ml">
    <span class="widget-chip">ML</span><div class="widget-icon">🤖</div>
    <h3>LSTM Forecasting</h3>
    <p>dbt · DuckDB · Keras · Streamlit.</p>
  </article>

  <article class="widget-card" tabindex="0" data-modal="modal-image-recognition">
    <span class="widget-chip">VISION</span><div class="widget-icon">🖼️</div>
    <h3>Image Recognition (SAM + EfficientNet)</h3>
    <p>Segmentation ➜ classification with PyTorch & torchvision.</p>
  </article>

  <article class="widget-card" tabindex="0" data-modal="modal-wakatime">
    <span class="widget-chip">STATS</span><div class="widget-icon">⏱️</div>
    <h3>Wakatime Stats</h3>
    <p>My coding activity, languages, and editors.</p>
  </article>

  <article class="widget-card" tabindex="0" data-modal="modal-logos">
    <span class="widget-chip">STACK</span><div class="widget-icon">🛰️</div>
    <h3>Tech Stack (Floating Logos)</h3>
    <p>Tools & frameworks I work with.</p>
  </article>

  <article class="widget-card" tabindex="0" data-modal="modal-ai-code-assistant">
    <span class="widget-chip">AI</span><div class="widget-icon">🀄</div>
    <h3>AI Code Assistant</h3>
    <p>AI code assistance tool for commenting code and generating unit tests.</p>
  </article>

  <article class="widget-card" tabindex="0" data-modal="modal-chatbot">
    <span class="widget-chip">AI CHAT</span><div class="widget-icon">💬</div>
    <h3>Portfolio Chatbot</h3>
    <p>RAG-powered AI assistant · SmolLM2-135M · Transformers.js</p>
  </article>

  <article class="widget-card" tabindex="0" data-modal="modal-coming-soon">
    <span class="widget-chip">COMING SOON</span><div class="widget-icon">⏳</div>
    <h3>New Project</h3>
    <p>Details about the upcoming project will be available soon.</p>
  </article>




<template id="tpl-weather">
  {% include weather-widget.html %}
  <p style="margin-top:12px;opacity:.8">
    Data via <a href="https://open-meteo.com/" target="_blank" rel="noopener">Open-Meteo</a>.
  </p>
</template>

<template id="tpl-dproc">{% include widget_data.html %}</template>
<template id="tpl-dpipe">{% include widget_pipeline.html %}</template>
<template id="tpl-ml">{% include widget_ml.html %}</template>
<template id="tpl-image-recognition">{% include widget_deeplearn.html %}</template>
<template id="tpl-wakatime">{% include widget_wakatime.html %}</template>
<template id="tpl-logos">{% include widget_logos.html %}</template>
<template id="tpl-ai-code-assistant">{% include widget_ai_code_assistant.html %}</template>
<template id="tpl-chatbot">{% include widget_chatbot.html %}</template>
<template id="tpl-coming-soon">{% include widget_webapp.html %}</template>

<dialog id="app-modal" class="modal" aria-modal="true">
  <div class="modal-header">
    <div class="modal-title" id="modal-title">Title</div>
    <button class="modal-close" id="modal-close" aria-label="Close">Close</button>
  </div>
  <div class="modal-body" id="modal-body"></div>
</dialog>

<script>
(() => {
  const map = {
    "modal-weather": { title: "Weather Widget", tpl: "tpl-weather" },
    "modal-dproc":   { title: "Data Processing", tpl: "tpl-dproc" },
    "modal-dpipe":   { title: "Train Delay Pipeline", tpl: "tpl-dpipe" },
    "modal-ml":      { title: "LSTM Forecasting", tpl: "tpl-ml" },
    "modal-image-recognition": { title: "Image Recognition (Neural Networks)", tpl: "tpl-image-recognition" },
    "modal-wakatime": { title: "Wakatime Stats", tpl: "tpl-wakatime" },
    "modal-logos": { title: "Tech Stack (Floating Logos)", tpl: "tpl-logos" },
    "modal-ai-code-assistant": { title: "AI Code Assistant", tpl: "tpl-ai-code-assistant" },
    "modal-chatbot": { title: "Portfolio Chatbot (AI)", tpl: "tpl-chatbot" },
    "modal-coming-soon": { title: "New Project", tpl: "tpl-coming-soon" },
  };

  const modal = document.getElementById("app-modal");
  const body  = document.getElementById("modal-body");
  const title = document.getElementById("modal-title");
  const closeBtn = document.getElementById("modal-close");

  function openModal(key){
    const cfg = map[key]; if(!cfg) return;
    const tpl = document.getElementById(cfg.tpl); if(!tpl) return;

    title.textContent = cfg.title;
    body.innerHTML = "";
    body.appendChild(tpl.content.cloneNode(true));

    if (typeof modal.showModal === "function") modal.showModal();
    else modal.setAttribute("open","open");
    const video = body.querySelector('video');
    if (video) {
      const clone = video.cloneNode(true);
      video.replaceWith(clone);
    }
  }
  function closeModal(){ if (typeof modal.close === "function") modal.close(); else modal.removeAttribute("open"); }

  document.addEventListener("click", (e) => {
    const card = e.target.closest(".widget-card"); if(!card) return;
    openModal(card.getAttribute("data-modal"));
  });
  document.addEventListener("keydown", (e) => {
    if ((e.key === "Enter" || e.key === " ") && document.activeElement?.classList?.contains("widget-card")){
      e.preventDefault(); openModal(document.activeElement.getAttribute("data-modal"));
    }
    if (e.key === "Escape" && modal.hasAttribute("open")) closeModal();
  });
  closeBtn.addEventListener("click", closeModal);
  modal.addEventListener("click", (e) => {
    const r = modal.getBoundingClientRect();
    const inside = e.clientX >= r.left && e.clientX <= r.right && e.clientY >= r.top && e.clientY <= r.bottom;
    if (!inside) closeModal();
  });
})();
</script>
