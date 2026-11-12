<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="description" content="GIORDANO BRUSCO — an independent creative house.">
  <title>GIORDANO BRUSCO — Creative House</title>
  <style>
    :root{
      --bg:#11110f;
      --panel:#191916;
      --ink:#e9e5dc;
      --muted:#a6a196;
      --line:#393831;
      --accent:#b7aa91;
    }
    *{box-sizing:border-box}
    html{scroll-behavior:smooth}
    body{margin:0;background:var(--bg);color:var(--ink);font-family:Arial,Helvetica,sans-serif;font-size:14px;letter-spacing:.02em}
    a{color:inherit;text-decoration:none}
    button{font:inherit;color:inherit;background:none;border:1px solid var(--line);padding:10px 14px;cursor:pointer;transition:all .2s}
    button:hover,a:hover{color:var(--accent);border-color:var(--accent)}
    .serif{font-family:Georgia,"Times New Roman",serif;font-weight:400;letter-spacing:-.045em}
    
    /* Header & Navigation */
    .top{height:68px;border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between;padding:0 4vw;position:sticky;top:0;background:rgba(17,17,15,.94);backdrop-filter:blur(10px);z-index:20}
    .wordmark{font-family:Georgia,serif;font-size:20px;letter-spacing:.11em}
    .top-right{display:flex;gap:14px;align-items:center;font-size:10px;letter-spacing:.13em}
    .menu{display:flex;gap:24px}
    .menu a{font-size:10px;letter-spacing:.14em;text-transform:uppercase}
    .mobile-menu-btn{display:none}
    .mobile-drawer{display:none;position:fixed;top:68px;left:0;right:0;background:var(--bg);border-bottom:1px solid var(--line);padding:24px 6vw;flex-direction:column;gap:18px;z-index:19}
    .mobile-drawer.open{display:flex}
    .mobile-drawer a{font-size:12px;letter-spacing:.15em;text-transform:uppercase;padding:6px 0;border-bottom:1px solid rgba(57,56,49,.4)}

    /* Hero */
    .hero{min-height:78vh;padding:12vh 8vw 8vh;display:flex;flex-direction:column;justify-content:space-between;border-bottom:1px solid var(--line);background:radial-gradient(ellipse at 70% 45%,#282720 0%,#171714 42%,#11110f 75%)}
    .eyebrow{font-size:10px;letter-spacing:.22em;color:var(--muted);text-transform:uppercase}
    .hero h1{font-size:clamp(54px,11vw,155px);line-height:.84;margin:8vh 0 5vh;max-width:1100px}
    .hero-bottom{display:flex;justify-content:space-between;align-items:end;gap:30px}
    .hero-bottom p{max-width:400px;color:#c2bdb2;line-height:1.7;margin:0}

    /* Sections */
    .section{padding:85px 8vw;border-bottom:1px solid var(--line)}
    .section-head{display:flex;justify-content:space-between;align-items:end;margin-bottom:40px;gap:20px}
    .section h2{font-size:clamp(34px,5vw,64px);margin:10px 0 0}
    .intro{max-width:620px;color:var(--muted);line-height:1.8;font-size:15px}

    /* Tiles */
    .tiles{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:1px;background:var(--line);border:1px solid var(--line)}
    .tile{background:var(--bg);min-height:210px;padding:28px;display:flex;flex-direction:column;justify-content:space-between;transition:background .25s}
    .tile:hover{background:#1c1b17}
    .tile .num{font-size:10px;color:var(--muted)}
    .tile h3{font:clamp(22px,2.8vw,34px) Georgia,serif;font-weight:400;margin:32px 0 8px;letter-spacing:-.03em}
    .tile p{font-size:10px;color:var(--muted);letter-spacing:.12em;text-transform:uppercase;margin:0}

    /* Featured Releases */
    .release-list{display:flex;flex-direction:column;gap:48px}
    .feature{display:grid;grid-template-columns:1fr 1.1fr;border:1px solid var(--line);background:var(--panel)}
    .feature-media{position:relative;aspect-ratio:1/1;overflow:hidden;background:#0c0c0b;border-right:1px solid var(--line)}
    .feature-media img{width:100%;height:100%;object-fit:cover;display:block;transition:transform .5s ease}
    .feature:hover .feature-media img{transform:scale(1.03)}
    .feature-copy{padding:clamp(28px,4.5vw,56px);display:flex;flex-direction:column;justify-content:space-between;gap:24px}
    .feature-copy h3{font:clamp(32px,4.2vw,54px) Georgia,serif;font-weight:400;line-height:.98;margin:14px 0 18px}
    .feature-copy p{color:var(--muted);line-height:1.75;max-width:460px;margin:0 0 24px}
    .feature-actions{display:flex;gap:12px;flex-wrap:wrap}

    /* Shop Grid */
    .shop-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:20px}
    .product{border:1px solid var(--line);padding:14px;background:var(--panel);display:flex;flex-direction:column;justify-content:space-between}
    .product-img{aspect-ratio:1/1;overflow:hidden;background:#0c0c0b;margin-bottom:16px}
    .product-img img{width:100%;height:100%;object-fit:cover;display:block;transition:transform .4s ease}
    .product:hover .product-img img{transform:scale(1.04)}
    .product h4{font:22px Georgia,serif;font-weight:400;margin:0 0 6px}
    .product small{display:block;color:var(--muted);letter-spacing:.12em;font-size:10px;margin-bottom:14px}
    .product-meta{display:flex;justify-content:space-between;align-items:center;border-top:1px solid var(--line);padding-top:12px;font-size:11px;letter-spacing:.1em}

    /* Modal */
    .modal-backdrop{display:none;position:fixed;inset:0;background:rgba(10,10,9,.88);backdrop-filter:blur(6px);z-index:50;align-items:center;justify-content:center;padding:20px}
    .modal-backdrop.active{display:flex}
    .modal{background:var(--bg);border:1px solid var(--line);max-width:920px;width:100%;max-height:90vh;overflow-y:auto;padding:32px;position:relative}
    .modal-close{position:absolute;top:20px;right:20px;font-size:11px;letter-spacing:.15em}
    .modal-grid{display:grid;grid-template-columns:1fr 1fr;gap:28px;margin-top:20px}
    .modal-covers{display:flex;flex-direction:column;gap:14px}
    .modal-covers img{width:100%;border:1px solid var(--line);display:block}
    .tracklist{list-style:none;padding:0;margin:16px 0;border-top:1px solid var(--line)}
    .tracklist li{padding:8px 0;border-bottom:1px solid rgba(57,56,49,.5);font-size:12px;color:#d4cfc4;display:flex;justify-content:space-between;gap:12px}
    .tracklist span.credits{color:var(--muted);font-size:11px;text-align:right}

    /* Footer */
    .footer{padding:50px 8vw;display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:20px;color:var(--muted);font-size:10px;letter-spacing:.15em}
    .footer-links{display:flex;gap:20px}
    .lang-es{display:none}

    @media(max-width:850px){
      .feature{grid-template-columns:1fr}
      .feature-media{border-right:none;border-bottom:1px solid var(--line)}
      .shop-grid{grid-template-columns:1fr 1fr}
      .modal-grid{grid-template-columns:1fr}
    }
    @media(max-width:700px){
      .top{padding:0 5vw}
      .menu{display:none}
      .mobile-menu-btn{display:block}
      .hero{padding:10vh 6vw 6vh;min-height:72vh}
      .hero h1{font-size:16vw}
      .hero-bottom{align-items:start;flex-direction:column}
      .section{padding:65px 6vw}
      .tiles{grid-template-columns:1fr}
      .tile{min-height:160px}
      .shop-grid{grid-template-columns:1fr}
      .footer{padding:35px 6vw;flex-direction:column;align-items:flex-start}
    }
  </style>
</head>
<body>

  <header class="top">
    <a class="wordmark" href="#home">GIORDANO BRUSCO</a>
    <nav class="menu">
      <a href="#house"><span class="en">The House</span><span class="lang-es">La Casa</span></a>
      <a href="#categories"><span class="en">Fields</span><span class="lang-es">Áreas</span></a>
      <a href="#projects"><span class="en">Releases</span><span class="lang-es">Lanzamientos</span></a>
      <a href="#shop"><span class="en">Shop</span><span class="lang-es">Tienda</span></a>
    </nav>
    <div class="top-right">
      <button id="language" aria-label="Switch language">ES</button>
      <button class="mobile-menu-btn" id="mobileToggle">MENU</button>
    </div>
  </header>

  <nav class="mobile-drawer" id="mobileDrawer">
    <a href="#house" onclick="closeDrawer()"><span class="en">01 / The House</span><span class="lang-es">01 / La Casa</span></a>
    <a href="#categories" onclick="closeDrawer()"><span class="en">02 / Fields of Work</span><span class="lang-es">02 / Áreas de Trabajo</span></a>
    <a href="#projects" onclick="closeDrawer()"><span class="en">03 / Selected Releases</span><span class="lang-es">03 / Lanzamientos</span></a>
    <a href="#shop" onclick="closeDrawer()"><span class="en">04 / Shop Catalogue</span><span class="lang-es">04 / Tienda</span></a>
  </nav>

  <main id="home">
    <!-- HERO -->
    <section class="hero">
      <div class="eyebrow en">Independent creative house · Est. 2026</div>
      <div class="eyebrow lang-es">Casa creativa independiente · Est. 2026</div>
      <h1 class="serif">GIORDANO<br>BRUSCO</h1>
      <div class="hero-bottom">
        <div class="eyebrow en">A house for ideas, objects & culture.</div>
        <div class="eyebrow lang-es">Una casa para las ideas, los objetos y la cultura.</div>
        <p class="en">We design, write, edit, publish, produce and collaborate across disciplines. An independent practice shaped by people, projects and ideas.</p>
        <p class="lang-es">Diseñamos, escribimos, editamos, publicamos, producimos y colaboramos en distintas disciplinas. Una práctica independiente construida alrededor de personas, proyectos e ideas.</p>
      </div>
    </section>

    <!-- 01 THE HOUSE -->
    <section class="section" id="house">
      <div class="section-head">
        <div>
          <div class="eyebrow">01 / <span class="en">The house</span><span class="lang-es">La casa</span></div>
          <h2 class="serif en">A creative practice.</h2>
          <h2 class="serif lang-es">Una práctica creativa.</h2>
        </div>
      </div>
      <p class="intro en">GIORDANO BRUSCO is an independent creative house working across design, language, moving image, music, objects and cultural projects. Each work carries its own authorship and its own story.</p>
# byGIORDANOBRUSCO
