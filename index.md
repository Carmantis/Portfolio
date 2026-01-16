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

<div class="carousel-wrapper">
  <div class="carousel-container">
    <div class="carousel-scene" id="carousel-scene">
      <!-- Cards will be positioned by JS -->
    </div>
  </div>
  <button class="carousel-nav carousel-nav--prev" id="carousel-prev" aria-label="Previous">&#10094;</button>
  <button class="carousel-nav carousel-nav--next" id="carousel-next" aria-label="Next">&#10095;</button>
  <div class="carousel-indicators" id="carousel-indicators"></div>
</div>

<!-- Hidden data for carousel items -->
<script id="carousel-data" type="application/json">
[
  { "modal": "modal-weather", "chip": "LIVE", "icon": "🌦️", "title": "Weather Widget", "desc": "Geolocation → Open-Meteo (no backend, CORS ok)." },
  { "modal": "modal-dproc", "chip": "DATA", "icon": "🧰", "title": "Data Processing", "desc": "Pandas · DuckDB · Visualizations." },
  { "modal": "modal-dpipe", "chip": "ETL", "icon": "🚉", "title": "Train Delay Pipeline", "desc": "Digitraffic · dbt · Evidence." },
  { "modal": "modal-ml", "chip": "ML", "icon": "🤖", "title": "LSTM Forecasting", "desc": "dbt · DuckDB · Keras · Streamlit." },
  { "modal": "modal-image-recognition", "chip": "VISION", "icon": "🖼️", "title": "Image Recognition (SAM + EfficientNet)", "desc": "Segmentation ➜ classification with PyTorch & torchvision." },
  { "modal": "modal-wakatime", "chip": "STATS", "icon": "⏱️", "title": "Wakatime Stats", "desc": "My coding activity, languages, and editors." },
  { "modal": "modal-logos", "chip": "STACK", "icon": "🛰️", "title": "Tech Stack (Floating Logos)", "desc": "Tools & frameworks I work with." },
  { "modal": "modal-ai-code-assistant", "chip": "AI", "icon": "🀄", "title": "AI Code Assistant", "desc": "AI code assistance tool for commenting code and generating unit tests." },
  { "modal": "modal-chatbot", "chip": "AI CHAT", "icon": "💬", "title": "Portfolio Chatbot", "desc": "RAG-powered AI assistant · Gemini API" },
  { "modal": "modal-aichatbot", "chip": "RAG", "icon": "🎓", "title": "RAG Chatbot", "desc": "Microservices · ChromaDB · FastAPI · Docker." },
  { "modal": "modal-coming-soon", "chip": "COMING SOON", "icon": "⏳", "title": "New Project", "desc": "Details about the upcoming project will be available soon." }
]
</script>




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
<template id="tpl-aichatbot">{% include widget_aichatbot.html %}</template>
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
  // ============================================
  // MODAL SYSTEM
  // ============================================
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
    "modal-aichatbot": { title: "AI-KAI: RAG Chatbot", tpl: "tpl-aichatbot" },
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

  closeBtn.addEventListener("click", closeModal);
  modal.addEventListener("click", (e) => {
    const r = modal.getBoundingClientRect();
    const inside = e.clientX >= r.left && e.clientX <= r.right && e.clientY >= r.top && e.clientY <= r.bottom;
    if (!inside) closeModal();
  });

  // ============================================
  // 3D CAROUSEL
  // ============================================
  const carouselData = JSON.parse(document.getElementById('carousel-data').textContent);
  const scene = document.getElementById('carousel-scene');
  const indicators = document.getElementById('carousel-indicators');
  const prevBtn = document.getElementById('carousel-prev');
  const nextBtn = document.getElementById('carousel-next');

  let currentIndex = 0;
  const itemCount = carouselData.length;
  const radius = 450; // Distance from center
  const angleStep = (2 * Math.PI) / itemCount;

  // Create carousel items
  carouselData.forEach((item, index) => {
    const card = document.createElement('div');
    card.className = 'carousel-item';
    card.setAttribute('data-modal', item.modal);
    card.setAttribute('data-index', index);
    card.innerHTML = `
      <span class="widget-chip">${item.chip}</span>
      <div class="widget-icon">${item.icon}</div>
      <h3>${item.title}</h3>
      <p>${item.desc}</p>
    `;
    scene.appendChild(card);

    // Click handler for modal
    card.addEventListener('click', () => {
      if (index === currentIndex) {
        openModal(item.modal);
      } else {
        goToSlide(index);
      }
    });
  });

  // Create indicator dots
  carouselData.forEach((_, index) => {
    const dot = document.createElement('button');
    dot.className = 'carousel-dot' + (index === 0 ? ' active' : '');
    dot.setAttribute('aria-label', `Go to slide ${index + 1}`);
    dot.addEventListener('click', () => goToSlide(index));
    indicators.appendChild(dot);
  });

  const items = scene.querySelectorAll('.carousel-item');
  const dots = indicators.querySelectorAll('.carousel-dot');

  function updateCarousel() {
    items.forEach((item, index) => {
      // Calculate position relative to current index
      let relativeIndex = index - currentIndex;

      // Normalize to shortest path around the circle
      if (relativeIndex > itemCount / 2) relativeIndex -= itemCount;
      if (relativeIndex < -itemCount / 2) relativeIndex += itemCount;

      const angle = relativeIndex * angleStep;
      const x = Math.sin(angle) * radius;
      const z = Math.cos(angle) * radius - radius;
      const rotateY = -angle * (180 / Math.PI);

      // Scale and opacity based on distance from front
      const distance = Math.abs(relativeIndex);
      const scale = Math.max(0.6, 1 - distance * 0.12);
      const opacity = Math.max(0.3, 1 - distance * 0.2);
      const zIndex = Math.round((itemCount - distance) * 10);

      item.style.transform = `translateX(${x}px) translateZ(${z}px) rotateY(${rotateY}deg) scale(${scale})`;
      item.style.opacity = opacity;
      item.style.zIndex = zIndex;
      item.style.pointerEvents = distance <= 2 ? 'auto' : 'none';
    });

    // Update dots
    dots.forEach((dot, index) => {
      dot.classList.toggle('active', index === currentIndex);
    });
  }

  function goToSlide(index) {
    currentIndex = ((index % itemCount) + itemCount) % itemCount;
    updateCarousel();
  }

  function nextSlide() {
    goToSlide(currentIndex + 1);
  }

  function prevSlide() {
    goToSlide(currentIndex - 1);
  }

  // Event listeners
  prevBtn.addEventListener('click', prevSlide);
  nextBtn.addEventListener('click', nextSlide);

  // Keyboard navigation
  document.addEventListener('keydown', (e) => {
    if (modal.hasAttribute('open')) {
      if (e.key === 'Escape') closeModal();
      return;
    }
    if (e.key === 'ArrowLeft') prevSlide();
    if (e.key === 'ArrowRight') nextSlide();
    if (e.key === 'Enter' || e.key === ' ') {
      e.preventDefault();
      const currentItem = carouselData[currentIndex];
      if (currentItem) openModal(currentItem.modal);
    }
  });

  // Initialize
  updateCarousel();

  // Auto-rotate (optional - can be disabled)
  let autoRotate = setInterval(nextSlide, 5000);

  // Pause on hover
  scene.addEventListener('mouseenter', () => clearInterval(autoRotate));
  scene.addEventListener('mouseleave', () => {
    autoRotate = setInterval(nextSlide, 5000);
  });

})();
</script>
