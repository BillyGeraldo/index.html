<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Photo Dashboard</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@600&display=swap');
  :root {
    --color-bg: #ffffff;
    --color-text-primary: #111827;
    --color-text-secondary: #6b7280;
    --color-card-bg: #f9fafb;
    --color-shadow: rgba(0,0,0,0.05);
    --border-radius: 12px;
    --max-container-width: 1200px;
    --gap: 1.5rem;
    --transition-duration: 0.3s;

    /* New color variables for attractive theme */
    --gradient-header-bg: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    --nav-link-color: #d1d5db;
    --nav-link-hover-color: #ffffff;
    --nav-link-hover-bg: rgba(255 255 255 / 0.2);
    --card-hover-bg: linear-gradient(135deg, #f3e6ff 0%, #d1c4e9 100%);
    --card-hover-shadow: rgba(118, 75, 162, 0.3);
    --card-caption-highlight: #764ba2;
  }
  * {
    box-sizing: border-box;
  }
  html {
    scroll-behavior: smooth;
  }
  body {
    margin: 0;
    font-family: 'Inter', sans-serif;
    /* Adding subtle pastel vertical gradient background behind content */
    background: linear-gradient(180deg, #e0e7ff 0%, #fefefe 70%, #e0f2fe 100%);
    color: var(--color-text-secondary);
    line-height: 1.5;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    /* Adding a little padding around sides for breathing room on small screens */
    padding: 1rem;
  }
  header {
    position: sticky;
    top: 0;
    width: 100%;
    background: var(--gradient-header-bg);
    box-shadow: 0 3px 10px rgba(102, 126, 234, 0.45);
    z-index: 10;
  }
  nav {
    max-width: var(--max-container-width);
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1rem 1.5rem;
  }
  .logo {
    font-weight: 700;
    font-size: 1.5rem;
    color: var(--nav-link-hover-color);
    user-select: none;
    letter-spacing: 0.05em;
  }
  .nav-links {
    display: flex;
    gap: 1.5rem;
  }
  .nav-links a {
    color: var(--nav-link-color);
    text-decoration: none;
    font-weight: 500;
    font-size: 1rem;
    padding: 0.25rem 0.5rem;
    border-radius: var(--border-radius);
    transition: color var(--transition-duration), background-color var(--transition-duration);
  }
  .nav-links a:hover,
  .nav-links a:focus {
    color: var(--nav-link-hover-color);
    background-color: var(--nav-link-hover-bg);
    outline: none;
  }

  main {
    max-width: var(--max-container-width);
    width: 100%;
    flex-grow: 1;
  }
  section {
    background-color: var(--color-bg);
    border-radius: var(--border-radius);
    box-shadow: 0 8px 24px rgba(102, 126, 234, 0.15);
    padding: 3rem 2rem 4rem;
    margin-bottom: 3rem;
  }
  #home {
    text-align: center;
    padding-top: 4rem;
    padding-bottom: 3rem;
  }
  h1 {
    color: var(--color-text-primary);
    font-size: 3.5rem;
    font-weight: 700;
    margin-bottom: 0.5rem;
  }
  p.description,
  p.about-text,
  p.contact-text {
    font-size: 1.125rem;
    max-width: 650px;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 2rem;
    color: var(--color-text-secondary);
  }
  section.photo-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill,minmax(240px,1fr));
    gap: var(--gap);
  }
  article.photo-card {
    background-color: var(--color-card-bg);
    border-radius: var(--border-radius);
    box-shadow: 0 2px 8px var(--color-shadow);
    overflow: hidden;
    cursor: pointer;
    transition: transform var(--transition-duration), box-shadow var(--transition-duration), background var(--transition-duration);
    display: flex;
    flex-direction: column;
  }
  article.photo-card:hover,
  article.photo-card:focus-within {
    transform: scale(1.05);
    box-shadow: 0 8px 20px var(--card-hover-shadow);
    background: var(--card-hover-bg);
    outline: none;
  }
  article.photo-card img {
    width: 100%;
    height: auto;
    display: block;
    aspect-ratio: 4 / 3;
    object-fit: cover;
    border-bottom: 1px solid #ddd;
    border-radius: var(--border-radius) var(--border-radius) 0 0;
  }
  article.photo-card figcaption {
    padding: 0.75rem 1rem;
    font-size: 1rem;
    color: var(--card-caption-highlight);
    font-weight: 700;
    user-select: none;
  }

  /* About Section */
  #about h2,
  #contact h2 {
    font-size: 2.75rem;
    font-weight: 700;
    color: var(--color-text-primary);
    margin-bottom: 1rem;
    text-align: center;
  }

  /* Contact Form */
  form {
    max-width: 550px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    gap: 1.25rem;
  }
  label {
    display: block;
    font-weight: 600;
    margin-bottom: 0.3rem;
    color: var(--color-text-primary);
  }
  input[type="text"],
  input[type="email"],
  textarea {
    width: 100%;
    padding: 0.6rem 1rem;
    border-radius: var(--border-radius);
    border: 1.5px solid #d1d5db;
    font-size: 1rem;
    font-family: inherit;
    transition: border-color var(--transition-duration);
    resize: vertical;
  }
  input[type="text"]:focus,
  input[type="email"]:focus,
  textarea:focus {
    outline: none;
    border-color: #667eea;
    box-shadow: 0 0 6px rgba(102, 126, 234, 0.5);
  }
  textarea {
    min-height: 120px;
  }
  button[type="submit"] {
    background: #667eea;
    color: white;
    font-weight: 700;
    font-size: 1.125rem;
    padding: 0.75rem;
    border: none;
    border-radius: var(--border-radius);
    cursor: pointer;
    transition: background-color var(--transition-duration);
  }
  button[type="submit"]:hover,
  button[type="submit"]:focus {
    background: #5563ca;
    outline: none;
  }

  @media (max-width: 480px){
    h1 {
      font-size: 2.5rem;
    }
    #about h2,
    #contact h2 {
      font-size: 2rem;
    }
  }
</style>
</head>
<body>
<header>
  <nav role="navigation" aria-label="Main navigation">
    <div class="logo" tabindex="0">wartaa.id</div>
    <div class="nav-links">
      <a href="#home" tabindex="0">Home</a>
      <a href="#gallery" tabindex="0">Gallery</a>
      <a href="#about" tabindex="0">About</a>
      <a href="#contact" tabindex="0">Contact</a>
    </div>
  </nav>
</header>

<main>
  <section id="home">
    <h1>Kenangan Wartaa</h1>
    <p class="description">Beberapa foto bersama teman terbaik.</p>
  </section>

  <section id="gallery" class="photo-grid" aria-label="Photo gallery">
    <article class="photo-card" tabindex="0">
      <img src="WhatsApp Image 2025-06-10 at 09.14.49_5a051e1b.jpg" 
      figcaption>wartaa</figcaption>
    </article>
    <article class="photo-card" tabindex="0">
      <img src="WhatsApp Image 2025-06-10 at 09.14.55_c8ba3268.jpg" 
      figcaption>Anging Mammiri</figcaption>
    </article>
    <article class="photo-card" tabindex="0">
      <img src="WhatsApp Image 2025-06-10 at 09.14.58_afacca30.jpg" 
      figcaption>Anging Mammiri</figcaption>
    </article>
    <article class="photo-card" tabindex="0">
      <img src="WhatsApp Image 2025-06-10 at 09.14.59_65613c95.jpg" 
      figcaption>Pantai Biru</figcaption>
    </article>
    <article class="photo-card" tabindex="0">
      <img src="WhatsApp Image 2025-06-10 at 09.14.59_c2a65d50.jpg" 
      figcaption>Blok D</figcaption>
    </article>
    <article class="photo-card" tabindex="0">
      <img src="WhatsApp Image 2025-06-10 at 09.15.05_2d0c7fe5.jpg"
      figcaption>Monumen Mandala</figcaption>
    </article>
  </section>

  <section id="about" aria-label="About photo dashboard">
    <h2>About</h2>
    <p class="about-text">"Setiap gambar bercerita, dan ini adalah bab dari perjalanan indah kita.".</p>
    <p class="about-text">"Hidup adalah kumpulan momen, dan ini adalah favoritku.".</p>
  </section>

  <section id="contact" aria-label="Contact">
    <h2>Contact</h2>
    <p class="contact-text">Have questions, suggestions, or want to get in touch? Use the form below to send us a message — we’d love to hear from you!</p>
    <form action="#" method="post" novalidate>
      <label for="name">Name</label>
      <input type="text" id="name" name="name" placeholder="Your full name" required />
      
      <label for="email">Email</label>
      <input type="email" id="email" name="email" placeholder="you@example.com" required />
      
      <label for="message">Message</label>
      <textarea id="message" name="message" placeholder="Write your message..." required></textarea>
      
      <button type="submit">Send Message</button>
    </form>
  </section>
</main>
</body>
</html>

