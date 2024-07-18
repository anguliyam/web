<script>
    import { Router, Link, Route } from "svelte-routing";
    import Header from "./components/Header.svelte";
    import Footer from "./components/Footer.svelte";
    import Home from "./routes/Home.svelte";
    import Services from "./routes/Services.svelte";
    import About from "./routes/About.svelte";
    import Contact from "./routes/Contact.svelte";
    
    export let url = "";
  </script>
  
  <Router {url}>
    <Header />
    <main>
      <div class="container">
        <Route path="/" component={Home} />
        <Route path="/services" component={Services} />
        <Route path="/about" component={About} />
        <Route path="/contact" component={Contact} />
      </div>
    </main>
    <Footer />
  </Router>
  
  <style>
    main {
      padding-top: 80px;
      padding-bottom: 80px;
      min-height: calc(100vh - 60px);
    }
  </style>