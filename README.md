<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>RP — Personal</title>
  <meta name="description" content="RP — personal site with photos, live tech news and weather." />

  <!-- Simple modern dark CSS -->
  <style>
    :root{
      --bg:#0b1020;
      --card:#0f1626;
      --muted:#97a0b8;
      --accent:#36b5ff;
      --glass: rgba(255,255,255,0.03);
      --radius:14px;
      --maxw:1100px;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family:Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background: linear-gradient(180deg, #05060a 0%, #0b1020 100%);
      color:#e6eef8;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      display:flex;
      align-items:flex-start;
      justify-content:center;
      padding:32px 20px;
    }

    .container{
      width:100%;
      max-width:var(--maxw);
      display:grid;
      grid-template-columns: 1fr 380px;
      gap:28px;
    }

    header{
      grid-column:1/-1;
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:16px;
      margin-bottom:6px;
    }
    .brand{
      display:flex;
      align-items:center;
      gap:14px;
    }
    .logo{
      width:64px;height:64px;border-radius:16px;
      background:linear-gradient(135deg,var(--accent),#7b6bff);
      display:flex;align-items:center;justify-content:center;
      font-weight:700;color:#071025;font-size:22px;
      box-shadow: 0 6px 24px rgba(54,181,255,0.12), inset 0 -6px 12px rgba(255,255,255,0.03);
    }
    h1{margin:0;font-size:20px;letter-spacing:0.6px}
    p.lead{margin:0;color:var(--muted);font-size:13px}

    /* Photo viewer card */
    .viewer{
      background:var(--card);
      border-radius:var(--radius);
      padding:18px;
      box-shadow: 0 6px 30px rgba(3,8,20,0.6);
      display:flex;
      flex-direction:column;
      gap:12px;
    }
    .photo-frame{
      background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);
      border-radius:12px;
      height:520px;
      display:flex;
      align-items:center;
      justify-content:center;
      overflow:hidden;
      position:relative;
    }
    .photo-frame img{
      max-width:100%;
      max-height:100%;
      object-fit:cover;
      transition:transform .35s ease;
    }
    .controls{
      display:flex;
      gap:8px;
      justify-content:center;
      align-items:center;
      margin-top:6px;
    }
    .btn{
      background:var(--glass);
      border:1px solid rgba(255,255,255,0.04);
      padding:10px 14px;
      border-radius:10px;
      cursor:pointer;
      color:var(--muted);
      font-weight:600;
      font-size:13px;
      transition:all .18s ease;
    }
    .btn:hover{transform:translateY(-3px); color:var(--accent)}
    .btn.primary{
      background:linear-gradient(90deg,var(--accent),#7b6bff);
      color:#071025;
      border:none;
    }

    /* Right column widgets */
    .sidebar{
      display:flex;
      flex-direction:column;
      gap:16px;
      align-self:start;
    }
    .card{
      background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);
      border-radius:12px;
      padding:12px;
      box-shadow: 0 6px 18px rgba(2,6,16,0.6);
      border:1px solid rgba(255,255,255,0.03);
    }
    .weather{
      display:flex;gap:12px;align-items:center;
    }
    .weather .temp{font-size:34px;font-weight:700}
    .meta{color:var(--muted);font-size:13px}

    .news-list{display:flex;flex-direction:column;gap:10px;max-height:360px;overflow:auto;padding-right:6px}
    .news-item{
      display:block;padding:10px;border-radius:8px;
      text-decoration:none;color:inherit;
      transition:background .12s ease;
    }
    .news-item:hover{background:rgba(255,255,255,0.02)}
    .news-item h4{margin:0;font-size:14px}
    .news-item p{margin:6px 0 0;color:var(--muted);font-size:12px}

    footer{
      grid-column:1/-1;
      margin-top:18px;
      color:var(--muted);
      font-size:13px;
      display:flex;justify-content:space-between;align-items:center;gap:8px;
    }

    /* Responsive */
    @media (max-width:980px){
      .container{grid-template-columns:1fr; padding-bottom:24px}
      .sidebar{order:2}
      .viewer{order:1}
    }

  </style>
</head>
<body>
  <main class="container" role="main">
    <header>
      <div class="brand">
        <div class="logo">RP</div>
        <div>
          <h1>Ragu — RP</h1>
          <p class="lead">AI & Future · Tech News · Weather Live · Personal Gallery</p>
        </div>
      </div>

      <div style="display:flex;gap:10px;align-items:center">
        <div class="meta">Built with ♥ · Dark theme</div>
      </div>
    </header>

    <!-- Photo viewer -->
    <section class="viewer" aria-label="Photo viewer">
      <div style="display:flex;justify-content:space-between;align-items:center">
        <strong>Photo Viewer</strong>
        <div class="meta">Use arrows or buttons to navigate • Click to zoom</div>
      </div>

      <div class="photo-frame" id="photoFrame" tabindex="0" aria-live="polite">
        <img id="mainPhoto" src="images/photo1.jpg" alt="RP photo">
      </div>

      <div class="controls">
        <button class="btn" id="prevBtn" title="Previous (←)">◀ Prev</button>
        <button class="btn primary" id="toggleFull" title="Toggle Fullscreen">Fullscreen</button>
        <button class="btn" id="nextBtn" title="Next (→)">Next ▶</button>
        <div style="width:10px"></div>
        <button class="btn" id="downloadBtn" title="Download current photo">Download</button>
      </div>
    </section>

    <!-- Sidebar: weather + news -->
    <aside class="sidebar" aria-label="Right column">

      <div class="card">
        <div style="display:flex;justify-content:space-between;align-items:center">
          <strong>Live Weather</strong>
          <div class="meta">Default: Bengaluru</div>
        </div>
        <div style="height:12px"></div>
        <div class="weather" id="weatherCard">
          <div>
            <div class="temp" id="temp">--°C</div>
            <div class="meta" id="desc">Loading...</div>
          </div>
          <div style="margin-left:auto;text-align:right">
            <div class="meta" id="loc">--</div>
            <div class="meta" id="wind">Wind: --</div>
          </div>
        </div>
        <div style="height:8px"></div>
        <div style="display:flex;gap:8px">
          <input id="cityInput" placeholder="Enter city (e.g. Delhi, IN)" style="flex:1;padding:8px;border-radius:8px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:inherit">
          <button class="btn" id="cityBtn">Show</button>
        </div>
      </div>

      <div class="card">
        <div style="display:flex;justify-content:space-between;align-items:center">
          <strong>Tech News (Global)</strong>
          <div class="meta">Live · AI & Tech</div>
        </div>
        <div style="height:10px"></div>
        <div class="news-list" id="newsList" aria-live="polite">
          <div class="meta">Loading top tech headlines…</div>
        </div>
        <div style="height:10px"></div>
        <div style="display:flex;justify-content:space-between;align-items:center">
          <div class="meta">Powered by News API</div>
          <button class="btn" id="refreshNews">Refresh</button>
        </div>
      </div>

    </aside>

    <footer>
      <div>© RP · <span id="year"></span></div>
      <div class="meta">Tip: For offline usage host images in <code>/images/</code>.</div>
    </footer>

  </main>

  <!-- JS: photo control, weather & news fetch -->
  <script>
    // ---------- CONFIG ----------
    const IMAGES = [
      'images/photo1.jpg',
      'images/photo2.jpg'
    ];
    // Default city for weather
    let currentCity = 'Bengaluru,IN';

    // Insert your API keys here:
    const OPENWEATHER_API_KEY = 'YOUR_OPENWEATHER_API_KEY';
    const NEWS_API_KEY = 'YOUR_NEWSAPI_KEY'; // e.g. from https://newsapi.org/ or gnews.io

    // News query parameters
    const NEWS_QUERY = 'technology OR AI OR "artificial intelligence"';
    const NEWS_PAGE_SIZE = 7;

    // ---------- UI & Photo Viewer ----------
    const mainPhoto = document.getElementById('mainPhoto');
    const photoFrame = document.getElementById('photoFrame');
    const prevBtn = document.getElementById('prevBtn');
    const nextBtn = document.getElementById('nextBtn');
    const toggleFull = document.getElementById('toggleFull');
    const downloadBtn = document.getElementById('downloadBtn');

    let idx = 0;
    function showPhoto(i){
      idx = (i + IMAGES.length) % IMAGES.length;
      mainPhoto.src = IMAGES[idx];
      mainPhoto.style.transform = 'scale(1)';
    }
    prevBtn.addEventListener('click', ()=> showPhoto(idx-1));
    nextBtn.addEventListener('click', ()=> showPhoto(idx+1));

    // Keyboard navigation
    document.addEventListener('keydown', (e)=>{
      if (e.key === 'ArrowLeft') showPhoto(idx-1);
      if (e.key === 'ArrowRight') showPhoto(idx+1);
      if (e.key === 'f' || e.key === 'F') toggleFullScreen();
    });

    // Zoom on click
    photoFrame.addEventListener('click', ()=>{
      const cur = mainPhoto.style.transform === 'scale(1.0)' ? 1.12 : 1.0;
      mainPhoto.style.transform = `scale(${cur})`;
    });

    // Fullscreen
    function toggleFullScreen(){
      if (!document.fullscreenElement) {
        photoFrame.requestFullscreen?.();
      } else {
        document.exitFullscreen?.();
      }
    }
    toggleFull.addEventListener('click', toggleFullScreen);

    // Download current photo
    downloadBtn.addEventListener('click', ()=>{
      const a = document.createElement('a');
      a.href = IMAGES[idx];
      a.download = `RP-photo-${idx+1}.jpg`;
      document.body.appendChild(a);
      a.click();
      a.remove();
    });

    // ---------- Weather ----------
    const tempEl = document.getElementById('temp');
    const descEl = document.getElementById('desc');
    const locEl = document.getElementById('loc');
    const windEl = document.getElementById('wind');
    const cityInput = document.getElementById('cityInput');
    const cityBtn = document.getElementById('cityBtn');

    async function fetchWeather(city = currentCity){
      if (!OPENWEATHER_API_KEY || OPENWEATHER_API_KEY === 'YOUR_OPENWEATHER_API_KEY') {
        descEl.textContent = 'Add OpenWeather API key in the code to see live weather.';
        return;
      }
      try{
        descEl.textContent = 'Loading…';
        const res = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${encodeURIComponent(city)}&units=metric&appid=${OPENWEATHER_API_KEY}`);
        if (!res.ok) throw new Error('Weather fetch failed');
        const data = await res.json();
        tempEl.textContent = Math.round(data.main.temp) + '°C';
        descEl.textContent = (data.weather[0].description || '').toUpperCase();
        locEl.textContent = data.name + ', ' + (data.sys?.country || '');
        windEl.textContent = `Wind: ${data.wind.speed} m/s • Humidity: ${data.main.humidity}%`;
      }catch(err){
        descEl.textContent = 'Unable to get weather. Check API key / city.';
        tempEl.textContent = '--°C';
        locEl.textContent = city;
        console.error(err);
      }
    }

    cityBtn.addEventListener('click', ()=>{
      const v = cityInput.value.trim();
      if (v) {
        currentCity = v;
        fetchWeather(currentCity);
      }
    });

    // ---------- News ----------
    const newsList = document.getElementById('newsList');
    async function fetchNews(){
      newsList.innerHTML = '<div class="meta">Loading tech headlines…</div>';
      if (!NEWS_API_KEY || NEWS_API_KEY === 'YOUR_NEWSAPI_KEY') {
        newsList.innerHTML = '<div class="meta">Add a News API key in the code (e.g. newsapi.org or gnews.io) to load live headlines.</div>';
        return;
      }
      try{
        // Using NewsAPI.org endpoint (requires API key). You may need to proxy if CORS blocked.
        const url = `https://newsapi.org/v2/everything?q=${encodeURIComponent(NEWS_QUERY)}&pageSize=${NEWS_PAGE_SIZE}&sortBy=publishedAt&language=en&apiKey=${NEWS_API_KEY}`;
        const res = await fetch(url);
        if (!res.ok) throw new Error('News fetch failed');
        const data = await res.json();
        if (!data.articles || data.articles.length === 0){
          newsList.innerHTML = '<div class="meta">No headlines found.</div>'; return;
        }
        newsList.innerHTML = '';
        data.articles.forEach(a => {
          const item = document.createElement('a');
          item.className = 'news-item';
          item.href = a.url;
          item.target = '_blank';
          item.rel = 'noopener';
          item.innerHTML = `<h4>${a.title}</h4><p>${a.source.name} · ${new Date(a.publishedAt).toLocaleString()}</p>`;
          newsList.appendChild(item);
        });
      }catch(err){
        newsList.innerHTML = '<div class="meta">Unable to load news. Check API key or CORS.</div>';
        console.error(err);
      }
    }

    document.getElementById('refreshNews').addEventListener('click', fetchNews);

    // ---------- Init ----------
    document.getElementById('year').textContent = new Date().getFullYear();
    showPhoto(0);
    fetchWeather(currentCity);
    fetchNews();

    // Helpful: prefetch images to avoid flicker
    IMAGES.forEach(src => {
      const i = new Image(); i.src = src;
    });
  </script>
</body>
</html>
