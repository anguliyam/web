<script>
  import { Canvas } from '@threlte/core'
  import Scene from '../components/Scene.svelte'
  import { onMount } from 'svelte';
  import { gsap } from 'gsap';
  import { fade, fly, scale } from 'svelte/transition';
  import { elasticOut } from 'svelte/easing';

  let theme = 'light';
  let mounted = false;

  const services = [
    { title: 'AI Strategy', description: 'Develop cutting-edge AI strategies for your business', icon: 'strategy' },
    { title: 'Machine Learning', description: 'Implement advanced machine learning solutions', icon: 'machine-learning' },
    { title: 'Data Analytics', description: 'Unlock insights from your data with AI-powered analytics', icon: 'analytics' }
  ];

  function toggleTheme() {
    theme = theme === 'light' ? 'dark' : 'light';
  }

  onMount(() => {
    mounted = true;

    gsap.from('.hero h2', { opacity: 0, y: -50, duration: 1, delay: 0 });
    gsap.from('.hero h1', { opacity: 0, scale: 0.5, duration: 1, delay: 0 });
    gsap.from('.hero p', { opacity: 0, y: 50, duration: 1, delay: 0 });

    gsap.from('.service-card', {
      opacity: 0,
      y: 50,
      duration: 0.8,
      stagger: 0.2,
      delay: 1.2,
    });
  });
</script>

<div class="home-container {theme}">


  <section class="hero">
    <h2>We make your life better with</h2>
    <h1 class="highlight">AI</h1>
    <p>Revolutionizing the future with intelligent solutions</p>
  </section>

  <section class="spaceship-scene">
    <Canvas>
      <Scene />
    </Canvas>
  </section>

  <section class="services">
    <h2 in:fly="{{ x: -50, duration: 1000 }}" out:fly="{{ x: -50, duration: 1000 }}">
      Our Services
    </h2>
    <div class="service-grid">
      {#each services as service, i}
        {#if mounted}
          <div class="service-card" in:fly="{{ y: 50, delay: i * 200, duration: 1000 }}">
            <div class="icon {service.icon}"></div>
            <h3>{service.title}</h3>
            <p>{service.description}</p>
          </div>
        {/if}
      {/each}
    </div>
  </section>
</div>

<style>
  .home-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 2rem;
    transition: background-color 0.3s, color 0.3s;
    min-height: 100vh;
  }

  .light {
    background-color: white;
    color: black;
  }

  .dark {
    background-color: #121212;
    color: white;
  }

  .theme-toggle {
    position: fixed;
    top: 20px;
    right: 20px;
    background-color: #007bff;
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    border-radius: 5px;
    cursor: pointer;
    transition: transform 0.3s, box-shadow 0.3s;
  }

  .theme-toggle:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .hero {
    text-align: center;
    margin-bottom: 2rem;
  }

  .hero h2, .hero h1 {
    margin: 0;
    line-height: 1.1;
  }

  .hero h2 {
    font-size: 2rem;
  }

  .hero h1 {
    font-size: 4rem;
  }

  .highlight {
    color: #007bff;
    display: inline-block;
  }

  .spaceship-scene {
    width: 100%;
    height: 60vh;
    margin-bottom: 2rem;
  }

  .services {
    width: 100%;
    max-width: 1200px;
  }

  .services h2 {
    text-align: center;
    font-size: 2.5rem;
    margin-bottom: 2rem;
  }

  .service-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }

  .service-card {
    border: 2px solid black;
    border-radius: 10px;
    padding: 2rem;
    text-align: center;
    transition: transform 0.3s, box-shadow 0.3s;
    cursor: pointer;
    background-color: rgba(255, 255, 255, 0.1);
  }

  .dark .service-card {
    border-color: white;
  }

  .service-card:hover {
    transform: translateY(-10px) rotate(2deg);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
  }

  .icon {
    font-size: 3rem;
    margin-bottom: 1rem;
  }

  .icon.strategy::before { content: '✰'; }
  .icon.machine-learning::before { content: '✰'; }
  .icon.analytics::before { content: '✰'; }

  h3 {
    font-size: 1.5rem;
    margin-bottom: 1rem;
  }

  @keyframes float {
    0% { transform: translateY(0px); }
    50% { transform: translateY(-10px); }
    100% { transform: translateY(0px); }
  }

  .service-card {
    animation: float 5s ease-in-out infinite;
  }

  @keyframes pulse {
    0% { transform: scale(1); }
    50% { transform: scale(1.05); }
    100% { transform: scale(1); }
  }

  .highlight {
    animation: pulse 2s infinite;
  }

  @keyframes rotate {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }

  .icon {
    display: inline-block;
    animation: linear;
  }

  @keyframes shimmer {
    0% { background-position: -1000px 0; }
    100% { background-position: 1000px 0; }
  }

  .service-card::after {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: linear-gradient(
      to right,
      rgba(255, 255, 255, 0) 0%,
      rgba(255, 255, 255, 0.3) 50%,
      rgba(255, 255, 255, 0) 100%
    );
    transform: rotate(30deg);
    animation: shimmer 6s infinite;
  }
</style>