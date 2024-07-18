<script>
  import { Canvas } from '@threlte/core'
  import Scene from '../components/Scene.svelte'
  import { onMount } from 'svelte';
  import { gsap } from 'gsap';

  onMount(() => {
    // Animate hero section
    gsap.from('.hero h1', { opacity: 0, y: -50, duration: 1, delay: 0.5 });
    gsap.from('.hero p', { opacity: 0, y: -30, duration: 1, delay: 0.8 });

    // Animate service cards
    gsap.from('.service-card', {
      opacity: 0,
      y: 50,
      duration: 0.8,
      stagger: 0.2,
      delay: 1.2,
    });
  });
</script>

<div class="home-container">
  <section class="hero">
    <h1>AI Consultancy</h1>
    <p>Revolutionizing the future with intelligent solutions</p>
  </section>

  <section class="spaceship-scene">
    <Canvas>
      <Scene />
    </Canvas>
  </section>

  <section class="services">
    <h2>Our Services</h2>
    <div class="service-grid">
      <div class="service-card">
        <h3>AI Strategy</h3>
        <p>Develop cutting-edge AI strategies for your business</p>
      </div>
      <div class="service-card">
        <h3>Machine Learning</h3>
        <p>Implement advanced machine learning solutions</p>
      </div>
      <div class="service-card">
        <h3>Data Analytics</h3>
        <p>Unlock insights from your data with AI-powered analytics</p>
      </div>
    </div>
  </section>
</div>

<style>
  .home-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 2rem;
  }

  .hero {
    text-align: center;
    margin-bottom: 2rem;
  }

  .hero h1 {
    font-size: 3rem;
    margin-bottom: 1rem;
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

  .service-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1rem;
  }

  .service-card {
    background-color: #f0f0f0;
    padding: 1rem;
    border-radius: 8px;
    transition: transform 0.3s ease;
  }

  .service-card:hover {
    transform: translateY(-5px);
  }
</style>