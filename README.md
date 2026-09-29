<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="theme-color" content="#030712" />
  <title>Bar Orel — Software Engineer</title>
  <meta name="description" content="Bar Orel — Software Engineer focused on backend engineering, AI-native systems, realtime apps and full-stack architecture." />
  <style>
    :root{
      --bg:#030712;
      --bg2:#08111f;
      --panel:rgba(9,18,34,.62);
      --panel2:rgba(15,23,42,.78);
      --text:#eef4ff;
      --muted:#93a4bd;
      --line:rgba(148,163,184,.16);
      --red:#ff3b4f;
      --blue:#5aa8ff;
      --cyan:#67e8f9;
      --violet:#9b87f5;
      --max:1180px;
    }

    *{box-sizing:border-box}
    html{scroll-behavior:smooth}
    body{
      margin:0;
      color:var(--text);
      background:
        radial-gradient(circle at 50% -20%, rgba(68,94,170,.22), transparent 38%),
        radial-gradient(circle at 80% 20%, rgba(144,30,65,.12), transparent 28%),
        var(--bg);
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      overflow-x:hidden;
    }

    a{color:inherit;text-decoration:none}
    ::selection{background:rgba(255,59,79,.35)}

    #space{
      position:fixed; inset:0; width:100%; height:100%;
      z-index:-5; pointer-events:none;
    }

    .noise{
      position:fixed; inset:0; z-index:-3; pointer-events:none; opacity:.035;
      background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 180 180' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='.7'/%3E%3C/svg%3E");
    }

    .progress{
      position:fixed; top:0; left:0; width:0; height:2px; z-index:100;
      background:linear-gradient(90deg,var(--red),var(--blue),var(--cyan));
      box-shadow:0 0 18px rgba(90,168,255,.7);
    }

    .nav{
      position:fixed; top:18px; left:50%; transform:translateX(-50%);
      z-index:50; width:min(calc(100% - 28px), 760px);
      padding:10px 14px;
      border:1px solid var(--line);
      background:rgba(3,7,18,.55);
      backdrop-filter:blur(18px);
      border-radius:999px;
      display:flex; align-items:center; justify-content:space-between;
      box-shadow:0 10px 40px rgba(0,0,0,.28);
    }

    .nav .brand{
      display:flex; gap:10px; align-items:center; font-weight:800; letter-spacing:.08em;
      font-size:.84rem;
    }
    .dot{width:9px;height:9px;border-radius:50%;background:var(--red);box-shadow:0 0 16px var(--red)}
    .nav-links{display:flex;gap:6px}
    .nav-links a{
      color:var(--muted); font-size:.84rem; padding:8px 11px; border-radius:999px;
      transition:.25s ease;
    }
    .nav-links a:hover{color:white;background:rgba(255,255,255,.06)}

    .hero{
      min-height:100vh; display:grid; place-items:center; position:relative; isolation:isolate;
      padding:110px 24px 80px;
    }

    .planet{
      position:absolute; width:min(62vw,850px); aspect-ratio:1;
      right:-22vw; top:-16vw; border-radius:50%; z-index:-2;
      background:
        radial-gradient(circle at 32% 27%, rgba(255,255,255,.20), transparent 3%),
        radial-gradient(circle at 38% 32%, rgba(62,91,128,.28), transparent 18%),
        radial-gradient(circle at 62% 72%, rgba(17,24,39,.94), rgba(4,8,16,.98) 66%),
        linear-gradient(145deg,#243b55,#090d16 65%);
      box-shadow:
        -45px 18px 90px rgba(90,168,255,.14),
        inset 38px -18px 90px rgba(0,0,0,.86),
        inset -18px 12px 50px rgba(140,182,255,.15);
      filter:saturate(.8);
      transform:translate3d(0,var(--planetY,0),0);
      transition:transform .1s linear;
    }
    .planet:before{
      content:""; position:absolute; inset:-2px; border-radius:50%;
      border-left:2px solid rgba(169,206,255,.38);
      filter:drop-shadow(-8px 0 14px rgba(90,168,255,.36));
    }

    .hero-grid{
      width:min(var(--max),100%);
      display:grid; grid-template-columns:1.1fr .9fr; gap:56px; align-items:center;
    }

    .eyebrow{
      color:#cbd5e1; text-transform:uppercase; letter-spacing:.28em;
      font-size:.75rem; display:flex; align-items:center; gap:10px;
    }
    .eyebrow:before{content:"";width:34px;height:1px;background:var(--red)}

    h1{
      margin:18px 0 18px;
      font-size:clamp(4rem,10vw,8.4rem);
      line-height:.84; letter-spacing:-.065em; font-weight:900;
    }
    .accent{color:transparent;-webkit-text-stroke:1px rgba(255,255,255,.76);text-shadow:0 0 34px rgba(90,168,255,.11)}
    .hero p{
      max-width:680px; color:#afbdd2; font-size:clamp(1rem,2vw,1.22rem); line-height:1.8;
      margin:0;
    }

    .hero-actions{display:flex;gap:12px;flex-wrap:wrap;margin-top:30px}
    .btn{
      display:inline-flex; align-items:center; gap:10px; padding:12px 17px; border-radius:12px;
      border:1px solid var(--line); background:rgba(255,255,255,.03);
      transition:.25s ease; font-weight:700; font-size:.92rem;
    }
    .btn.primary{background:white;color:#07101c;border-color:white}
    .btn:hover{transform:translateY(-2px);box-shadow:0 12px 34px rgba(0,0,0,.28)}
    .btn.primary:hover{box-shadow:0 12px 36px rgba(255,255,255,.12)}

    .mission-card{
      align-self:end; justify-self:end; width:min(100%,400px); padding:22px;
      border:1px solid var(--line); border-radius:22px;
      background:linear-gradient(145deg,rgba(15,23,42,.62),rgba(3,7,18,.36));
      backdrop-filter:blur(18px);
      box-shadow:0 34px 100px rgba(0,0,0,.35);
      transform:translateY(var(--cardY,0));
    }
    .mission-card small{color:#708198;text-transform:uppercase;letter-spacing:.16em}
    .mission-card h3{margin:12px 0 8px;font-size:1.35rem}
    .mission-card p{font-size:.9rem;line-height:1.7;color:#93a4bd}
    .signal{
      margin-top:20px; display:grid; grid-template-columns:repeat(3,1fr); gap:8px;
    }
    .signal div{
      border:1px solid var(--line); border-radius:12px; padding:11px 9px; text-align:center;
      background:rgba(255,255,255,.025)
    }
    .signal strong{display:block;font-size:.98rem}
    .signal span{font-size:.67rem;color:#718096;text-transform:uppercase;letter-spacing:.08em}

    main{position:relative}
    .section{
      width:min(var(--max),calc(100% - 40px)); margin:0 auto; padding:120px 0;
      position:relative;
    }
    .section-head{
      display:grid;grid-template-columns:140px 1fr;gap:26px;align-items:start;margin-bottom:46px
    }
    .index{font-family:ui-monospace,SFMono-Regular,Menlo,monospace;color:#5a6b82;font-size:.8rem;letter-spacing:.16em}
    .section h2{margin:0;font-size:clamp(2.2rem,5vw,4.4rem);letter-spacing:-.04em}
    .section-lead{color:#93a4bd;max-width:700px;line-height:1.8;margin-top:13px}

    .about-grid{display:grid;grid-template-columns:1.1fr .9fr;gap:18px}
    .panel{
      border:1px solid var(--line); border-radius:22px; padding:26px;
      background:linear-gradient(145deg,rgba(15,23,42,.58),rgba(3,7,18,.34));
      backdrop-filter:blur(12px);
    }
    .panel h3{margin-top:0;font-size:1.25rem}
    .panel p{color:#99a8bb;line-height:1.8}
    .tags{display:flex;flex-wrap:wrap;gap:8px;margin-top:18px}
    .tag{padding:8px 10px;border:1px solid var(--line);border-radius:999px;color:#c5d0df;font-size:.78rem;background:rgba(255,255,255,.025)}

    .radar{
      min-height:320px;display:grid;place-items:center;position:relative;overflow:hidden;
    }
    .orbit{
      position:absolute;border:1px solid rgba(103,232,249,.14);border-radius:50%;
      animation:spin linear infinite;
    }
    .orbit.o1{width:230px;height:230px;animation-duration:18s}
    .orbit.o2{width:170px;height:170px;animation-duration:13s;animation-direction:reverse}
    .orbit.o3{width:105px;height:105px;animation-duration:8s}
    .orbit:before{
      content:"";position:absolute;top:-4px;left:50%;width:8px;height:8px;border-radius:50%;
      background:var(--cyan);box-shadow:0 0 18px var(--cyan)
    }
    .core{
      width:56px;height:56px;border-radius:50%;display:grid;place-items:center;font-weight:900;
      background:radial-gradient(circle,#fff,#7dd3fc 18%,#2563eb 44%,#0b1120 70%);
      box-shadow:0 0 40px rgba(90,168,255,.5);
    }
    @keyframes spin{to{transform:rotate(360deg)}}

    .projects{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}
    .project{
      min-height:330px; border:1px solid var(--line); border-radius:24px; padding:25px;
      background:linear-gradient(165deg,rgba(18,29,50,.72),rgba(5,9,18,.74));
      position:relative;overflow:hidden;transition:.35s ease;
    }
    .project:hover{transform:translateY(-7px);border-color:rgba(90,168,255,.38)}
    .project:after{
      content:"";position:absolute;width:180px;height:180px;border-radius:50%;right:-80px;bottom:-90px;
      background:radial-gradient(circle,rgba(90,168,255,.23),transparent 70%);
      transition:.35s ease;
    }
    .project:hover:after{transform:scale(1.5)}
    .project .num{font-family:ui-monospace,monospace;color:#53657e;font-size:.76rem}
    .project h3{font-size:1.55rem;margin:44px 0 10px}
    .project p{color:#94a3b8;line-height:1.7}
    .project .stack{margin-top:22px;display:flex;flex-wrap:wrap;gap:7px}
    .project .stack span{font-size:.72rem;color:#c3cfdf;border:1px solid var(--line);padding:6px 8px;border-radius:9px}
    .project .open{position:absolute;bottom:22px;left:25px;font-weight:800;font-size:.82rem;color:#dbeafe}

    .skills-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:14px}
    .skill{
      border:1px solid var(--line);border-radius:18px;padding:20px;min-height:210px;
      background:rgba(8,15,28,.56)
    }
    .skill h3{margin:0 0 16px;font-size:1rem}
    .skill ul{list-style:none;padding:0;margin:0;display:grid;gap:9px;color:#91a0b4;font-size:.9rem}
    .skill li:before{content:"›";color:var(--red);margin-right:8px}

    .ai-flow{
      display:grid;grid-template-columns:repeat(7,auto);gap:10px;align-items:center;justify-content:center;
      padding:36px 18px;border:1px solid var(--line);border-radius:24px;background:rgba(6,12,24,.62);
      overflow:auto;
    }
    .node{
      padding:11px 14px;border:1px solid var(--line);border-radius:12px;
      background:#0b1424;font-size:.82rem;white-space:nowrap
    }
    .arrow{color:#64748b}

    .manifesto{
      text-align:center;max-width:900px;margin:0 auto
    }
    .manifesto blockquote{
      margin:0;font-size:clamp(2rem,5vw,4.6rem);line-height:1.05;font-weight:850;letter-spacing:-.05em
    }
    .manifesto blockquote span{color:#6f819a}
    .manifesto p{color:#8797ac;line-height:1.8;margin:28px auto 0;max-width:720px}

    footer{
      width:min(var(--max),calc(100% - 40px));margin:0 auto;padding:70px 0 46px;
      border-top:1px solid var(--line);display:flex;justify-content:space-between;gap:20px;align-items:flex-end
    }
    footer h2{font-size:clamp(2.3rem,6vw,5.6rem);margin:0;letter-spacing:-.055em}
    footer p{color:#6f8097;max-width:460px;line-height:1.7}
    .footer-links{display:flex;gap:10px;flex-wrap:wrap}

    .reveal{opacity:0;transform:translateY(32px);transition:opacity .8s ease, transform .8s ease}
    .reveal.visible{opacity:1;transform:none}

    @media(max-width:900px){
      .hero-grid,.about-grid{grid-template-columns:1fr}
      .mission-card{justify-self:start}
      .projects{grid-template-columns:1fr}
      .skills-grid{grid-template-columns:1fr 1fr}
      .section-head{grid-template-columns:1fr}
      .index{display:none}
      .planet{width:900px;right:-580px;top:-200px}
      .nav-links a:nth-child(2),.nav-links a:nth-child(3){display:none}
      footer{flex-direction:column;align-items:flex-start}
    }

    @media(max-width:600px){
      .skills-grid{grid-template-columns:1fr}
      .hero{padding-inline:20px}
      .section{width:min(var(--max),calc(100% - 28px));padding:88px 0}
      .ai-flow{justify-content:flex-start}
      h1{font-size:4rem}
    }
  </style>
</head>
<body>
  <canvas id="space"></canvas>
  <div class="noise"></div>
  <div class="progress" id="progress"></div>

  <nav class="nav">
    <a href="#top" class="brand"><span class="dot"></span> BAR OREL</a>
    <div class="nav-links">
      <a href="#about">About</a>
      <a href="#projects">Projects</a>
      <a href="#stack">Stack</a>
      <a href="#contact">Contact</a>
    </div>
  </nav>

  <header class="hero" id="top">
    <div class="planet" id="planet"></div>
    <div class="hero-grid">
      <div>
        <div class="eyebrow">Software Engineer // Ramat Gan, IL</div>
        <h1>BAR<br><span class="accent">OREL</span></h1>
        <p>
          Backend-first software engineer building <strong>AI-native systems</strong>,
          realtime products, agentic workflows and full-stack experiences with
          C#/.NET, Angular and a lot of curiosity.
        </p>
        <div class="hero-actions">
          <a class="btn primary" href="#projects">Explore my work ↓</a>
          <a class="btn" href="https://www.linkedin.com/in/barorel/" target="_blank" rel="noreferrer">LinkedIn ↗</a>
          <a class="btn" href="https://github.com/BarOrel" target="_blank" rel="noreferrer">GitHub ↗</a>
        </div>
      </div>

      <aside class="mission-card" id="missionCard">
        <small>Current transmission</small>
        <h3>Building software that can remember, reason & act.</h3>
        <p>
          Exploring agent orchestration, persistent memory, context engineering,
          retrieval, realtime systems and practical AI inside real products.
        </p>
        <div class="signal">
          <div><strong>3+ yrs</strong><span>Production</span></div>
          <div><strong>.NET</strong><span>Core Stack</span></div>
          <div><strong>AI</strong><span>Current Focus</span></div>
        </div>
      </aside>
    </div>
  </header>

  <main>
    <section class="section reveal" id="about">
      <div class="section-head">
        <div class="index">01 / IDENTITY</div>
        <div>
          <h2>I like systems with moving parts.</h2>
          <p class="section-lead">
            APIs, queues, state, realtime updates, agents, memory, mobile clients,
            infrastructure — the fun starts when the pieces have to work together.
          </p>
        </div>
      </div>

      <div class="about-grid">
        <div class="panel">
          <h3>What I bring</h3>
          <p>
            3+ years building production software, mostly in C#/.NET and Angular.
            My strongest area is backend engineering, but I enjoy owning features
            end-to-end — architecture, API, UI, data, deployment and debugging.
          </p>
          <p>
            Recently I've been going deep on AI-native development: agents,
            orchestration, context selection, persistent memory, RAG concepts
            and using coding agents as part of the actual engineering workflow.
          </p>
          <div class="tags">
            <span class="tag">Backend Engineering</span>
            <span class="tag">Full Stack</span>
            <span class="tag">AI Agents</span>
            <span class="tag">Realtime</span>
            <span class="tag">System Design</span>
            <span class="tag">Product-minded</span>
          </div>
        </div>

        <div class="panel radar">
          <div class="orbit o1"></div>
          <div class="orbit o2"></div>
          <div class="orbit o3"></div>
          <div class="core">BO</div>
        </div>
      </div>
    </section>

    <section class="section reveal" id="projects">
      <div class="section-head">
        <div class="index">02 / BUILDS</div>
        <div>
          <h2>Projects I actually care about.</h2>
          <p class="section-lead">
            A few systems that represent how I think and what I like building.
            The repositories go deeper — this page is the map.
          </p>
        </div>
      </div>

      <div class="projects">
        <a class="project" href="https://github.com/BarOrel/LifeOS" target="_blank" rel="noreferrer">
          <div class="num">MISSION / 001</div>
          <h3>🧠 Life OS</h3>
          <p>
            Agentic personal AI system built around specialized agents, memory,
            context engineering, orchestration, background jobs and multiple clients.
          </p>
          <div class="stack">
            <span>.NET 8</span><span>Angular</span><span>SignalR</span>
            <span>Hangfire</span><span>SQL Server</span><span>Claude</span>
          </div>
          <div class="open">OPEN REPOSITORY ↗</div>
        </a>

        <article class="project">
          <div class="num">MISSION / 002</div>
          <h3>🏡 Homeiy</h3>
          <p>
            AI-assisted real-estate platform with natural-language property search,
            maps, geolocation, mobile UX and realtime updates.
          </p>
          <div class="stack">
            <span>.NET 8</span><span>Angular</span><span>Ionic</span>
            <span>SignalR</span><span>Docker</span>
          </div>
          <div class="open">PRODUCT EXPERIMENT</div>
        </article>

        <article class="project">
          <div class="num">MISSION / 003</div>
          <h3>⚙️ Workflow Engine</h3>
          <p>
            Extensible .NET workflow execution engine for configurable business flows,
            conditional branching and strategy-based operations.
          </p>
          <div class="stack">
            <span>.NET 8</span><span>CQRS</span>
            <span>Clean Architecture</span><span>Strategy Pattern</span>
          </div>
          <div class="open">BACKEND SYSTEM</div>
        </article>
      </div>
    </section>

    <section class="section reveal" id="stack">
      <div class="section-head">
        <div class="index">03 / ARSENAL</div>
        <div>
          <h2>Tools are temporary. Systems thinking isn't.</h2>
          <p class="section-lead">
            Still, these are the tools I reach for most often.
          </p>
        </div>
      </div>

      <div class="skills-grid">
        <div class="skill">
          <h3>Backend</h3>
          <ul>
            <li>C# / .NET / ASP.NET Core</li>
            <li>REST APIs & Microservices</li>
            <li>EF Core / SQL Server</li>
            <li>Redis / RabbitMQ</li>
            <li>SignalR</li>
          </ul>
        </div>
        <div class="skill">
          <h3>Frontend & Mobile</h3>
          <ul>
            <li>Angular</li>
            <li>TypeScript</li>
            <li>Ionic / Capacitor</li>
            <li>React</li>
            <li>Realtime UX</li>
          </ul>
        </div>
        <div class="skill">
          <h3>AI Systems</h3>
          <ul>
            <li>AI Agents</li>
            <li>Agent Orchestration</li>
            <li>Context Engineering</li>
            <li>Memory Systems</li>
            <li>RAG / Retrieval Concepts</li>
          </ul>
        </div>
        <div class="skill">
          <h3>Architecture & Infra</h3>
          <ul>
            <li>Clean Architecture</li>
            <li>CQRS / DDD</li>
            <li>Docker / Linux</li>
            <li>CI/CD</li>
            <li>Kubernetes fundamentals</li>
          </ul>
        </div>
      </div>
    </section>

    <section class="section reveal">
      <div class="section-head">
        <div class="index">04 / AI-NATIVE</div>
        <div>
          <h2>How I work with coding agents.</h2>
          <p class="section-lead">
            I don't use AI as fancy autocomplete. I use it as a fast collaborator
            inside a controlled engineering loop.
          </p>
        </div>
      </div>

      <div class="ai-flow">
        <div class="node">SPEC</div><div class="arrow">→</div>
        <div class="node">DECOMPOSE</div><div class="arrow">→</div>
        <div class="node">AGENT</div><div class="arrow">→</div>
        <div class="node">REVIEW</div><div class="arrow">→</div>
        <div class="node">TEST</div><div class="arrow">→</div>
        <div class="node">REFINE / SHIP</div>
      </div>
    </section>

    <section class="section reveal">
      <div class="manifesto">
        <blockquote>
          Build fast. <span>Think slower.</span><br>
          Ship what survives review.
        </blockquote>
        <p>
          AI can accelerate implementation dramatically. It doesn't own architecture,
          correctness, failure modes or maintainability. I do.
        </p>
      </div>
    </section>
  </main>

  <footer id="contact">
    <div>
      <div class="eyebrow">Open channel</div>
      <h2>Let's build<br>something interesting.</h2>
      <p>
        Backend systems, AI-native products, realtime architecture or something
        ambitious enough to require all three.
      </p>
    </div>
    <div class="footer-links">
      <a class="btn primary" href="https://www.linkedin.com/in/barorel/" target="_blank" rel="noreferrer">LinkedIn ↗</a>
      <a class="btn" href="https://github.com/BarOrel" target="_blank" rel="noreferrer">GitHub ↗</a>
    </div>
  </footer>

  <script>
    const canvas = document.getElementById('space');
    const ctx = canvas.getContext('2d');
    let stars = [];
    let mouse = {x:0,y:0};

    function resize(){
      const dpr = Math.min(window.devicePixelRatio || 1, 2);
      canvas.width = innerWidth * dpr;
      canvas.height = innerHeight * dpr;
      canvas.style.width = innerWidth + 'px';
      canvas.style.height = innerHeight + 'px';
      ctx.setTransform(dpr,0,0,dpr,0,0);
      stars = Array.from({length: Math.min(260, Math.floor(innerWidth/4))}, () => ({
        x: Math.random()*innerWidth,
        y: Math.random()*innerHeight,
        z: Math.random()*1+.15,
        r: Math.random()*1.5+.2
      }));
    }

    function draw(){
      ctx.clearRect(0,0,innerWidth,innerHeight);
      for(const s of stars){
        const dx = (mouse.x-innerWidth/2) * .003 * s.z;
        const dy = (mouse.y-innerHeight/2) * .003 * s.z;
        ctx.beginPath();
        ctx.arc(s.x+dx, s.y+dy, s.r*s.z, 0, Math.PI*2);
        ctx.fillStyle = `rgba(205,225,255,${0.24 + s.z*.55})`;
        ctx.fill();
      }
      requestAnimationFrame(draw);
    }

    window.addEventListener('resize', resize);
    window.addEventListener('mousemove', e => {
      mouse.x = e.clientX; mouse.y = e.clientY;
    });

    const progress = document.getElementById('progress');
    const planet = document.getElementById('planet');
    const missionCard = document.getElementById('missionCard');

    function onScroll(){
      const max = document.documentElement.scrollHeight - innerHeight;
      const p = max ? scrollY/max : 0;
      progress.style.width = `${p*100}%`;

      planet.style.setProperty('--planetY', `${scrollY * .14}px`);
      missionCard.style.setProperty('--cardY', `${Math.min(scrollY*.04,28)}px`);
    }
    window.addEventListener('scroll', onScroll, {passive:true});

    const observer = new IntersectionObserver(entries => {
      entries.forEach(entry => {
        if(entry.isIntersecting) entry.target.classList.add('visible');
      });
    }, {threshold:.12});
    document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

    resize();
    draw();
    onScroll();
  </script>
</body>
</html>
