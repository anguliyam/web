<script>
    import { onMount } from 'svelte';
    import { fade, fly } from 'svelte/transition';
  
    let visible = false;
  
    onMount(() => {
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            visible = true;
          }
        });
      });
  
      observer.observe(document.querySelector('.about-us'));
  
      return () => observer.disconnect();
    });
  </script>
  
  <div class="about-us">
    <h1>About Us</h1>
    
    <div class="team">
      {#if visible}
        <div class="card" transition:fly="{{ y: 50, duration: 1000 }}">
          <img src="/contact_profile/a.png" alt="Arvinda Gillella" />
          <h2>Arvinda Gillella</h2>
          <h3>Co-Founder & CEO</h3>
          <p>AI is not just a technology of the future, it's a tool transforming our present.</p>
          <div class="social-icons">
            <div class="icon" data-info="arvindareddy@gmail.com">
              <i class="fas fa-envelope"></i>
            </div>
            <div class="icon" data-info="linkedin.com/in/aravind-reddy-gillella-55209911">
              <i class="fab fa-linkedin"></i>
            </div>
            <div class="icon" data-info="+1 (510)449-6348">
              <i class="fas fa-phone"></i>
            </div>
          </div>
        </div>
  
        <div class="card" transition:fly="{{ y: 50, duration: 1000, delay: 200 }}">
          <img src="/contact_profile/nithin.jpg" alt="M Hari Hara Nithin Reddy" />
          <h2>Hari Hara Nithin Reddy</h2>
          <h3>Co-Founder & CTO</h3>
          <p>AI is like an electricity.. its gonna progress across every business.</p>
          <div class="social-icons">
            <div class="icon" data-info="nithin@anguliyam.com">
              <i class="fas fa-envelope"></i>
            </div>
            <div class="icon" data-info="linkedin.com/in/hhnr/">
              <i class="fab fa-linkedin"></i>
            </div>
            <div class="icon" data-info="+1 (617)201-2157">
              <i class="fas fa-phone"></i>
            </div>
          </div>
        </div>
      {/if}
    </div>
  

  </div>
  
  <style>
    .about-us {
      max-width: 1200px;
      margin: 0 auto;
      padding: 2rem;
      font-family: Arial, sans-serif;
    }
  
    h1 {
      text-align: center;
      margin-bottom: 2rem;
    }
  
    .team {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 2rem;
    }
  
    .card {
      background-color: #fff;
      border: 2px solid #000;
      border-radius: 10px;
      padding: 1.5rem;
      width: 300px;
      text-align: center;
      box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.3);
      transition: transform 0.3s ease;
    }
  
    .card:hover {
      transform: translateY(-10px);
    }
  
    .card img {
      width: 150px;
      height: 150px;
      border-radius: 50%;
      object-fit: cover;
      margin-bottom: 1rem;
    }
  
    .social-icons {
      display: flex;
      justify-content: center;
      gap: 1rem;
      margin-top: 1rem;
    }
  
    .icon {
      font-size: 1.5rem;
      cursor: pointer;
      position: relative;
    }
  
    .icon:hover::after {
      content: attr(data-info);
      position: absolute;
      bottom: 100%;
      left: 50%;
      transform: translateX(-50%);
      background-color: #333;
      color: #fff;
      padding: 0.5rem;
      border-radius: 5px;
      font-size: 0.8rem;
      white-space: nowrap;
    }
  
  
    @media (max-width: 768px) {
      .team {
        flex-direction: column;
        align-items: center;
      }
  
      .card {
        width: 100%;
        max-width: 300px;
      }
    }
  </style>