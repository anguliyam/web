<script>
    import { Link } from "svelte-routing";
    
    let menuOpen = false;
  
    function toggleMenu() {
      menuOpen = !menuOpen;
    }
  
    function closeMenu() {
      menuOpen = false;
    }
  </script>
  
  <header>
    <div class="container">
      <div class="logo-container">
        <img src="/logo.png" alt="Anguliyam Logo" class="logo-image" />
        <span class="logo-text">Anguliyam</span>
      </div>
      <nav class:active={menuOpen}>
        <button class="menu-toggle" on:click={toggleMenu} class:active={menuOpen}>
          <span class="bar"></span>
          <span class="bar"></span>
          <span class="bar"></span>
        </button>
        <ul>
          <li>
            <Link to="/" on:click={closeMenu}>
              <i class="fas fa-home"></i>
              <span>Home</span>
            </Link>
          </li>
          <li>
            <Link to="/services" on:click={closeMenu}>
              <i class="fas fa-cogs"></i>
              <span>Services</span>
            </Link>
          </li>
          <li>
            <Link to="/about" on:click={closeMenu}>
              <i class="fas fa-info-circle"></i>
              <span>About</span>
            </Link>
          </li>
          <li>
            <Link to="/contact" on:click={closeMenu}>
              <i class="fas fa-envelope"></i>
              <span>Contact</span>
            </Link>
          </li>
        </ul>
      </nav>
    </div>
  </header>
  
  <style>
    header {
      background-color: #ffffff;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      z-index: 1000;
    }
  
    .container {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1rem;
      max-width: 1200px;
      margin: 0 auto;
    }
  
    .logo-container {
      display: flex;
      align-items: center;
    }
  
    .logo-image {
      height: 30px;
      width: auto;
      margin-right: 5px;
    }
  
    .logo-text {
      font-size: 1.2rem;
      font-weight: bold;
      color: #000000;
    }
  
    nav ul {
      display: flex;
      list-style-type: none;
      margin: 0;
      padding: 0;
    }
  
    nav li {
      margin-left: 1rem;
    }
  
    nav :global(a) {
      color: #000000;
      text-decoration: none;
      font-weight: 500;
      transition: color 0.3s ease;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
  
    nav :global(a:hover) {
      color: #666666;
      
    }
  
    nav :global(a i) {
      font-size: 1rem;
      margin-bottom: 0.25rem;
      color: #7b8787; /* Golden color for all icons */
    }
  
    .menu-toggle {
      display: none;
      background: none;
      border: none;
      cursor: pointer;
      padding: 1px;
      z-index: 1001;
    }
  
    .bar {
      display: block;
      width: 20px;
      height: 2.5px;
      margin: 5px 0;
      background-color: #000000;
      transition: all 0.3s ease-in-out;
    }
  
    .menu-toggle.active .bar:nth-child(1) {
      transform: rotate(45deg) translate(5px, 5px);
    }
  
    .menu-toggle.active .bar:nth-child(2) {
      opacity: 0;
    }
  
    .menu-toggle.active .bar:nth-child(3) {
      transform: rotate(-45deg) translate(7px, -7px);
    }
  
    @media (max-width: 768px) {

        
      .menu-toggle {
        display: block;
      }
  
      nav ul {
        display: none;
      }
  
      nav.active ul {
        display: flex;
        flex-direction: column;
        position: absolute;
        top: 100%;
        left: 0;
        right: 0;
        background-color: #ffffff;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
      }
  
      nav.active li {
        margin: 0;
        text-align: center;
      }
  
      nav.active :global(a) {
        flex-direction: row;
        justify-content: center;
        padding: 1rem;
      }
  
      nav.active :global(a i) {
        margin-right: 0.5rem;
        margin-bottom: 0;
      }
    }
  </style>