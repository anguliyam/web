<script>
    import { Router, Link, Route } from "svelte-routing";
    import Header from "./components/Header.svelte";
    import Footer from "./components/Footer.svelte";
    import Home from "./routes/Home.svelte";
    import Services from "./routes/Services.svelte";
    import Contact from "./routes/Contact.svelte";
    import News from "./routes/News.svelte";
    export let url = "";
  </script>
  
  <Router {url}>
    <Header />
    <main>
      <div class="container">
        <Route path="/" component={Home} />
        <Route path="/services" component={Services} />
        <Route path="/contact" component={Contact} />
        <Route path="/news" component={News} />
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