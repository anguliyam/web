<script>
  import { Link } from "svelte-routing";

let menuOpen = false;
let burstAnimation = false;

function toggleMenu() {
  menuOpen = !menuOpen;
}

function closeMenu() {
  menuOpen = false;
}

function triggerBurst() {
  burstAnimation = true;
  setTimeout(() => burstAnimation = false, 300);
}
</script>

<header>
  <div class="container">
    <div class="logo-container">
      <Link to="/" on:click={() => { closeMenu(); triggerBurst(); }} class="logo-link">
        <ul>
          <li> <img src="/logo.png" alt="Anguliyam AI Logo" class="logo-image" /> </li>
          <li>         <span class="logo-text" class:burst={burstAnimation}>
            Anguliyam <span class="ai-text">AI</span>
          </span></li>
        </ul>
        
      </Link>
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
            <i class="icon icon-home"></i>
            <span>Home</span>
          </Link>
        </li>
        <li>
          <Link to="/services" on:click={closeMenu}>
            <i class="icon icon-services"></i>
            <span>Services</span>
          </Link>
        </li>
        <li>
          <Link to="/news" on:click={closeMenu}>
            <i class="icon icon-news"></i>
            <span>News</span>
          </Link>
        </li>
        <li>
          <Link to="/contact" on:click={closeMenu}>
            <i class="icon icon-contact"></i>
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
    justify-content: flex-start;
  }


  .logo-image {
    height: 40px;
    width: auto;
    margin-right: 10px;
  }

  .logo-text {
    font-size: 1.5rem;
    font-weight: bold;
    color: #000000;
    display: flex;
    align-items: center;
  }

  ul {
            list-style-type: none; /* Remove bullet points */
            padding: 0; /* Remove padding */
            margin: 0; /* Remove margin */
            display: flex; /* Display list items in a row */
        }
        li {
            margin-right: 10px; /* Add some space between items */
        }
        .logo-container li:nth-child(2) {
            margin-top: 7px; /* Add top margin only to the second item */
        }

  .ai-text {
    color: #007bff;
  }

  nav ul {
    display: flex;
    list-style-type: none;
    margin: 0;
    padding: 0;
  }

  nav li {
    margin-left: 1.5rem;
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
    color: #ffd700;
  }

  .icon {
    font-size: 1.5rem;
    margin-bottom: 0.25rem;
    transition: all 0.3s ease;
  }

  .icon-home { background-image: url('/icons/home.png'); }
  .icon-services { background-image: url('/icons/services.png'); }
  .icon-news { background-image: url('/icons/news.png'); }
  .icon-contact { background-image: url('/icons/contact.png'); }

  nav :global(a:hover .icon) {
    transform: scale(1.1);
    filter: brightness(0) saturate(100%) invert(79%) sepia(75%) saturate(552%) hue-rotate(359deg) brightness(103%) contrast(107%);
  }

  nav :global(a:active .icon) {
    animation: shine 0.5s ease-in-out;
  }

  @keyframes shine {
    0% { filter: brightness(1); }
    50% { filter: brightness(1.5); }
    100% { filter: brightness(1); }
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

    nav.active :global(a .icon) {
      margin-right: 0.5rem;
      margin-bottom: 0;
    }
  }

  .logo-container {
    display: flex;
    align-items: center;
    justify-content: flex-start;
  }


  .logo-text {
    font-size: 1.5rem;
    font-weight: bold;
    color: #000000;
    display: inline-flex;
    align-items: center;
  }

  .ai-text {
    color: #007bff;
  }

  .burst {
    animation: burstAnimation 0.3s ease-out;
  }

  @keyframes burstAnimation {
    0% {
      transform: scale(1);
    }
    50% {
      transform: scale(1.2);
    }
    100% {
      transform: scale(1);
    }
  }
</style>