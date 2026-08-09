<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pramod Sonawane — Design & Web</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#1B1B1B;
    --charcoal:#323232;
    --cream:#FFE7D0;
    --orange:#FC6E20;
    --cream-soft:#fff4e8;
    --ease:cubic-bezier(.16,.8,.28,1);
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--cream);
    color:var(--ink);
    font-family:'Inter',sans-serif;
    overflow-x:hidden;
    -webkit-font-smoothing:antialiased;
  }
  ::selection{background:var(--orange);color:var(--ink);}
  a{color:inherit;text-decoration:none;}

  .label{
    font-family:'JetBrains Mono',monospace;
    font-size:12px;
    letter-spacing:.14em;
    text-transform:uppercase;
    color:var(--orange);
    display:inline-flex;
    align-items:center;
    gap:8px;
  }
  .label::before{
    content:'';
    width:8px;height:8px;
    background:var(--orange);
    border-radius:2px;
    display:inline-block;
  }

  h1,h2,h3{
    font-family:'Space Grotesk',sans-serif;
    letter-spacing:-.02em;
  }

  /* reveal on scroll */
  .reveal{opacity:0;transform:translateY(24px);transition:opacity .8s var(--ease),transform .8s var(--ease);}
  .reveal.in{opacity:1;transform:translateY(0);}

  /* ---------- NAV ---------- */
  nav{
    position:fixed;top:0;left:0;right:0;
    z-index:100;
    display:flex;
    align-items:center;
    justify-content:space-between;
    padding:22px 6vw;
    background:rgba(255,231,208,.82);
    backdrop-filter:blur(10px);
    border-bottom:1px solid rgba(27,27,27,.08);
    transition:transform .5s var(--ease);
  }
  nav .logo{
    font-family:'Space Grotesk',sans-serif;
    font-weight:700;
    font-size:18px;
  }
  nav .logo span{color:var(--orange);}
  nav .navlinks{
    display:flex;gap:32px;
    font-size:14px;
    font-weight:500;
  }
  nav .navlinks a{
    position:relative;
    padding-bottom:2px;
  }
  nav .navlinks a::after{
    content:'';
    position:absolute;left:0;bottom:-2px;
    width:0;height:1px;
    background:var(--orange);
    transition:width .3s var(--ease);
  }
  nav .navlinks a:hover::after{width:100%;}
  nav .navcta{
    background:var(--ink);
    color:var(--cream);
    padding:9px 18px;
    border-radius:100px;
    font-size:13px;
    font-weight:600;
    transition:background .3s var(--ease),transform .3s var(--ease);
  }
  nav .navcta:hover{background:var(--orange);transform:translateY(-1px);}
  .navlinks{display:flex;}
  @media(max-width:720px){.navlinks{display:none;}}

  /* ---------- HERO ---------- */
  .hero{
    min-height:100svh;
    background:var(--ink);
    color:var(--cream);
    display:flex;
    flex-direction:column;
    justify-content:center;
    padding:140px 6vw 80px;
    position:relative;
    overflow:hidden;
  }
  .hero::before{
    content:'';
    position:absolute;
    width:60vw;height:60vw;
    max-width:700px;max-height:700px;
    background:radial-gradient(circle,var(--orange) 0%,transparent 70%);
    opacity:.28;
    top:-20%;right:-15%;
    border-radius:50%;
    animation:float 12s ease-in-out infinite;
    pointer-events:none;
  }
  @keyframes float{
    0%,100%{transform:translate(0,0) scale(1);}
    50%{transform:translate(-30px,30px) scale(1.08);}
  }
  .hero-inner{position:relative;z-index:2;max-width:980px;}
  .hero .label{color:var(--orange);margin-bottom:26px;opacity:0;animation:fadeUp .8s var(--ease) .1s forwards;}
  .hero h1{
    font-size:clamp(2.4rem,6.6vw,5.2rem);
    line-height:1.04;
    font-weight:700;
    opacity:0;animation:fadeUp .9s var(--ease) .25s forwards;
  }
  .hero h1 em{
    font-style:normal;
    color:var(--orange);
  }
  .hero .sub{
    margin-top:26px;
    font-size:clamp(1rem,1.6vw,1.2rem);
    color:#d8cfc4;
    max-width:560px;
    line-height:1.6;
    opacity:0;animation:fadeUp .9s var(--ease) .4s forwards;
  }
  .hero .motto{
    margin-top:8px;
    font-family:'JetBrains Mono',monospace;
    font-size:13px;
    color:var(--orange);
    letter-spacing:.04em;
  }
  .hero-actions{
    margin-top:44px;
    display:flex;
    gap:18px;
    flex-wrap:wrap;
    opacity:0;animation:fadeUp .9s var(--ease) .55s forwards;
  }
  .btn-primary{
    background:var(--orange);
    color:var(--ink);
    padding:15px 30px;
    border-radius:100px;
    font-weight:600;
    font-size:15px;
    display:inline-flex;
    align-items:center;
    gap:8px;
    transition:transform .3s var(--ease),box-shadow .3s var(--ease);
  }
  .btn-primary:hover{transform:translateY(-2px);box-shadow:0 10px 30px rgba(252,110,32,.35);}
  .btn-ghost{
    border:1px solid rgba(255,231,208,.3);
    color:var(--cream);
    padding:15px 30px;
    border-radius:100px;
    font-weight:500;
    font-size:15px;
    transition:border-color .3s var(--ease),background .3s var(--ease);
  }
  .btn-ghost:hover{border-color:var(--orange);background:rgba(252,110,32,.08);}
  @keyframes fadeUp{
    from{opacity:0;transform:translateY(18px);}
    to{opacity:1;transform:translateY(0);}
  }

  /* ---------- MARQUEE ---------- */
  .marquee-wrap{
    background:var(--orange);
    color:var(--ink);
    overflow:hidden;
    padding:14px 0;
    white-space:nowrap;
  }
  .marquee{
    display:inline-flex;
    animation:scroll 22s linear infinite;
  }
  .marquee span{
    font-family:'JetBrains Mono',monospace;
    font-weight:500;
    font-size:14px;
    letter-spacing:.05em;
    padding:0 28px;
    text-transform:uppercase;
    display:inline-flex;
    align-items:center;
    gap:10px;
  }
  .marquee span::after{content:'✦';opacity:.6;}
  @keyframes scroll{
    from{transform:translateX(0);}
    to{transform:translateX(-50%);}
  }

  /* ---------- SECTION SHARED ---------- */
  section{padding:120px 6vw;}
  .section-head{max-width:640px;margin-bottom:64px;}
  .section-head .label{margin-bottom:18px;}
  .section-head h2{
    font-size:clamp(1.8rem,3.6vw,2.8rem);
    font-weight:600;
    line-height:1.15;
  }
  .section-head p{
    margin-top:16px;
    color:var(--charcoal);
    font-size:16px;
    line-height:1.6;
  }

  /* ---------- SERVICES ---------- */
  .services{background:var(--cream);}
  .cards{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:24px;
  }
  @media(max-width:900px){.cards{grid-template-columns:1fr;}}
  .card{
    background:var(--ink);
    color:var(--cream);
    border-radius:20px;
    padding:38px 32px;
    position:relative;
    overflow:hidden;
    transition:transform .45s var(--ease);
  }
  .card:hover{transform:translateY(-8px);}
  .card::before{
    content:'';
    position:absolute;top:0;left:0;right:0;height:3px;
    background:var(--orange);
    transform:scaleX(0);
    transform-origin:left;
    transition:transform .5s var(--ease);
  }
  .card:hover::before{transform:scaleX(1);}
  .card .num{
    font-family:'JetBrains Mono',monospace;
    color:var(--orange);
    font-size:13px;
    letter-spacing:.1em;
  }
  .card h3{
    margin-top:22px;
    font-size:22px;
    font-weight:600;
  }
  .card p{
    margin-top:14px;
    font-size:14.5px;
    line-height:1.65;
    color:#cfc5b9;
  }
  .card .tags{
    margin-top:22px;
    display:flex;
    flex-wrap:wrap;
    gap:8px;
  }
  .card .tags span{
    font-family:'JetBrains Mono',monospace;
    font-size:11px;
    border:1px solid rgba(255,231,208,.25);
    padding:5px 10px;
    border-radius:100px;
    color:#d8cfc4;
  }

  /* ---------- TESTIMONIAL ---------- */
  .testimonial{
    background:var(--charcoal);
    color:var(--cream);
    text-align:center;
    position:relative;
  }
  .testimonial .quote-mark{
    font-family:'Space Grotesk',sans-serif;
    font-size:100px;
    color:var(--orange);
    line-height:1;
    opacity:.5;
  }
  .testimonial blockquote{
    max-width:760px;
    margin:0 auto;
    font-family:'Space Grotesk',sans-serif;
    font-size:clamp(1.3rem,2.6vw,2rem);
    font-weight:500;
    line-height:1.45;
  }
  .testimonial .who{
    margin-top:32px;
    display:flex;
    flex-direction:column;
    align-items:center;
    gap:4px;
  }
  .testimonial .who .name{font-weight:600;font-size:15px;}
  .testimonial .who .role{
    font-family:'JetBrains Mono',monospace;
    font-size:12px;
    color:var(--orange);
    text-transform:uppercase;
    letter-spacing:.08em;
  }

  /* ---------- CTA / CONTACT ---------- */
  .cta{
    background:var(--ink);
    color:var(--cream);
    border-radius:28px;
    margin:0 6vw 80px;
    padding:80px 6vw;
    position:relative;
    overflow:hidden;
  }
  .cta::after{
    content:'';
    position:absolute;
    bottom:-30%;left:-10%;
    width:50vw;height:50vw;
    max-width:500px;max-height:500px;
    background:radial-gradient(circle,var(--orange) 0%,transparent 70%);
    opacity:.22;
    border-radius:50%;
  }
  .cta-grid{
    position:relative;z-index:2;
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:60px;
    align-items:start;
  }
  @media(max-width:820px){.cta-grid{grid-template-columns:1fr;gap:40px;}}
  .cta h2{
    font-size:clamp(1.8rem,3.4vw,2.6rem);
    font-weight:600;
    line-height:1.15;
  }
  .cta p{
    margin-top:16px;
    color:#d8cfc4;
    line-height:1.6;
    font-size:15.5px;
  }
  .contact-info{margin-top:32px;display:flex;flex-direction:column;gap:12px;}
  .contact-info a{
    font-family:'JetBrains Mono',monospace;
    font-size:14px;
    color:var(--cream);
    display:flex;align-items:center;gap:10px;
    transition:color .3s;
  }
  .contact-info a:hover{color:var(--orange);}
  .contact-info .dot{width:6px;height:6px;background:var(--orange);border-radius:50%;}

  form{display:flex;flex-direction:column;gap:16px;}
  .field{display:flex;flex-direction:column;gap:8px;}
  .field label{
    font-family:'JetBrains Mono',monospace;
    font-size:11px;
    text-transform:uppercase;
    letter-spacing:.1em;
    color:#a89d8f;
  }
  .field input,.field textarea{
    background:transparent;
    border:none;
    border-bottom:1px solid rgba(255,231,208,.25);
    color:var(--cream);
    font-family:'Inter',sans-serif;
    font-size:15px;
    padding:10px 0;
    outline:none;
    transition:border-color .3s;
    resize:none;
  }
  .field input:focus,.field textarea:focus{border-color:var(--orange);}
  .field input::placeholder,.field textarea::placeholder{color:#6b6459;}
  .submit-btn{
    margin-top:8px;
    background:var(--orange);
    color:var(--ink);
    border:none;
    padding:15px 30px;
    border-radius:100px;
    font-weight:600;
    font-size:15px;
    cursor:pointer;
    width:fit-content;
    transition:transform .3s var(--ease),box-shadow .3s var(--ease);
  }
  .submit-btn:hover{transform:translateY(-2px);box-shadow:0 10px 30px rgba(252,110,32,.35);}

  footer{
    text-align:center;
    padding:34px 6vw 44px;
    font-family:'JetBrains Mono',monospace;
    font-size:12px;
    color:var(--charcoal);
    letter-spacing:.04em;
  }
  footer span{color:var(--orange);}

  @media (prefers-reduced-motion: reduce){
    *{animation-duration:.01ms !important;animation-iteration-count:1 !important;transition-duration:.01ms !important;scroll-behavior:auto !important;}
  }

  :focus-visible{outline:2px solid var(--orange);outline-offset:3px;}
</style>
</head>
<body>

<nav>
  <div class="logo">pramod<span>.</span>sonawane</div>
  <div class="navlinks">
    <a href="#services">Services</a>
    <a href="#work">Work</a>
    <a href="#contact">Contact</a>
  </div>
  <a href="#contact" class="navcta">Let's talk</a>
</nav>

<header class="hero">
  <div class="hero-inner">
    <div class="label">Design & Web · Taloda</div>
    <h1>Posters, sites, and brands<br>that show up <em>right.</em></h1>
    <p class="sub">I'm Pramod — an 18-year-old designer & developer building visual identity and websites for local cafes, shops, clinics, and startups. Clean work, on time, every time.</p>
    <p class="motto">"Your respect, our responsibility."</p>
    <div class="hero-actions">
      <a href="#contact" class="btn-primary">Start a project →</a>
      <a href="#services" class="btn-ghost">See services</a>
    </div>
  </div>
</header>

<div class="marquee-wrap">
  <div class="marquee">
    <span>Namo Cafe</span><span>Prajyot Sports Wear</span><span>D27 Sportswear</span><span>Local Brands</span><span>Startups</span><span>Clinics</span>
    <span>Namo Cafe</span><span>Prajyot Sports Wear</span><span>D27 Sportswear</span><span>Local Brands</span><span>Startups</span><span>Clinics</span>
  </div>
</div>

<section class="services" id="services">
  <div class="section-head reveal">
    <div class="label">What I do</div>
    <h2>Three ways I help brands look and work better.</h2>
    <p>From a poster that gets a cafe noticed on the street to a website that turns visitors into clients — I handle design and build end to end.</p>
  </div>
  <div class="cards">
    <div class="card reveal">
      <div class="num">01</div>
      <h3>Poster & Ad Design</h3>
      <p>Print-ready posters and ad creatives for cafes, shops, startups, and educational campaigns — built to grab attention fast.</p>
      <div class="tags"><span>Cafes</span><span>Shops</span><span>Startups</span><span>Education</span></div>
    </div>
    <div class="card reveal">
      <div class="num">02</div>
      <h3>Website Building</h3>
      <p>Fast, clean, mobile-ready websites for salons, clinics, startups, and any brand that needs a real home online.</p>
      <div class="tags"><span>Salons</span><span>Clinics</span><span>Startups</span><span>Any brand</span></div>
    </div>
    <div class="card reveal">
      <div class="num">03</div>
      <h3>Social & Content</h3>
      <p>Reels, captions, and brand content that sounds like your business, not a template — planned and written for real engagement.</p>
      <div class="tags"><span>Reels</span><span>Captions</span><span>Strategy</span></div>
    </div>
  </div>
</section>

<section class="testimonial" id="work">
  <div class="reveal">
    <div class="quote-mark">"</div>
    <blockquote>Pramod redesigned our posters and menu boards in days — footfall from the street noticeably picked up, and he actually listened to what we wanted instead of pushing a template.</blockquote>
    <div class="who">
      <div class="name">Owner, Namo Cafe</div>
      <div class="role">Local business client</div>
    </div>
  </div>
</section>

<section id="contact">
  <div class="cta reveal">
    <div class="cta-grid">
      <div>
        <h2>Have a poster or website in mind?</h2>
        <p>Send a few details and I'll get back to you with ideas, timeline, and pricing. Usually within a day.</p>
        <div class="contact-info">
          <a href="tel:+917972281667"><span class="dot"></span>+91 79722 81667</a>
          <a href="mailto:pramod07913@gmail.com"><span class="dot"></span>pramod07913@gmail.com</a>
          <a href="#"><span class="dot"></span>Based in Taloda, India</a>
        </div>
      </div>
      <form id="contactForm">
        <div class="field">
          <label for="name">Name</label>
          <input type="text" id="name" placeholder="Your name" required>
        </div>
        <div class="field">
          <label for="email">Email</label>
          <input type="email" id="email" placeholder="you@email.com" required>
        </div>
        <div class="field">
          <label for="message">Project details</label>
          <textarea id="message" rows="4" placeholder="Tell me about your poster or website..." required></textarea>
        </div>
        <button type="submit" class="submit-btn">Send message →</button>
      </form>
    </div>
  </div>
</section>

<footer>
  © 2026 Pramod Sonawane <span>·</span> Design & Web, Taloda
</footer>

<script>
  // scroll reveal
  const revealEls = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries)=>{
    entries.forEach(e=>{
      if(e.isIntersecting){
        e.target.classList.add('in');
        io.unobserve(e.target);
      }
    });
  },{threshold:.15});
  revealEls.forEach(el=>io.observe(el));

  // nav hide on scroll down
  let lastY = window.scrollY;
  const nav = document.querySelector('nav');
  window.addEventListener('scroll',()=>{
    const y = window.scrollY;
    if(y > lastY && y > 120){
      nav.style.transform = 'translateY(-110%)';
    } else {
      nav.style.transform = 'translateY(0)';
    }
    lastY = y;
  });

  // Set this to your deployed Railway backend URL, e.g.
  // "https://your-app.up.railway.app/api/contact"
  window.PRAMOD_API_URL = "";

  // contact form -> backend API (falls back to mailto if API isn't set/reachable)
  const contactForm = document.getElementById('contactForm');
  const submitBtn = contactForm.querySelector('.submit-btn');

  function fallbackMailto(name, email, message){
    const subject = encodeURIComponent('New project inquiry from ' + name);
    const body = encodeURIComponent(`Name: ${name}\nEmail: ${email}\n\n${message}`);
    window.location.href = `mailto:pramod07913@gmail.com?subject=${subject}&body=${body}`;
  }

  contactForm.addEventListener('submit', async function(e){
    e.preventDefault();
    const name = document.getElementById('name').value.trim();
    const email = document.getElementById('email').value.trim();
    const message = document.getElementById('message').value.trim();

    if(!window.PRAMOD_API_URL){
      fallbackMailto(name, email, message);
      return;
    }

    const originalText = submitBtn.textContent;
    submitBtn.textContent = 'Sending...';
    submitBtn.disabled = true;

    try{
      const res = await fetch(window.PRAMOD_API_URL, {
        method: 'POST',
        headers: {'Content-Type': 'application/json'},
        body: JSON.stringify({name, email, message})
      });
      const data = await res.json();

      if(res.ok && data.ok){
        submitBtn.textContent = 'Sent ✓';
        contactForm.reset();
        setTimeout(()=>{ submitBtn.textContent = originalText; submitBtn.disabled = false; }, 2500);
      } else {
        throw new Error(data.errors ? JSON.stringify(data.errors) : 'Request failed');
      }
    } catch(err){
      console.error('Contact API failed, falling back to email client:', err);
      fallbackMailto(name, email, message);
      submitBtn.textContent = originalText;
      submitBtn.disabled = false;
    }
  });
</script>

</body>
</html>
