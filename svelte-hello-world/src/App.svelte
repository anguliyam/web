<!-- App.svelte -->
<script>
    let services = [
        {
            title: "Natural Language Processing",
            description: "Advanced text analysis and processing.",
            icon: "📝"
        },
        {
            title: "Computer Vision",
            description: "Visual recognition, object detection, and image analysis.",
            icon: "👁️"
        },
        {
            title: "Machine Learning",
            description: "Predictive modeling and data analysis.",
            icon: "🤖"
        }
    ];
</script>

<main>
    <header>
        <h1>Welcome to ANGULIYAM AI Services Platform</h1>
        <p>Explore our cutting-edge AI services below.</p>
    </header>

    <section class="services">
        {#each services as service}
            <div class="service">
                <span class="icon">{service.icon}</span>
                <h2>{service.title}</h2>
                <p>{service.description}</p>
            </div>
        {/each}
    </section>
</main>

<style>
    main {
        font-family: Arial, sans-serif;
        max-width: 800px;
        margin: 0 auto;
        padding: 20px;
    }

    header {
        text-align: center;
        margin-bottom: 40px;
    }

    h1 {
        font-size: 2.5em;
        margin-bottom: 10px;
    }

    p {
        font-size: 1.2em;
        color: #666;
    }

    .services {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 20px;
    }

    .service {
        border: 1px solid #ddd;
        border-radius: 8px;
        padding: 20px;
        text-align: center;
        transition: transform 0.3s;
    }

    .service:hover {
        transform: translateY(-5px);
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    }

    .icon {
        font-size: 3em;
    }

    h2 {
        font-size: 1.5em;
        margin-top: 10px;
    }

    p {
        color: #444;
    }
</style>
