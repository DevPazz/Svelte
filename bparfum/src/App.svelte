<script>
    import { decants, contacto } from './data.js';
</script>

<main>
    <header class="hero">
        <video muted autoplay loop playsinline controlslist="nodownload">
            <source src="/videoperfumes.mp4" type="video/mp4">
            Tu navegador no soporta videos.
        </video>
        <div class="hero-overlay"></div>

        <div class="hero-content">
            <img src="/logo.jpg" alt="bparfum logo" class="main-logo" />
            <p class="tagline">Decants de diseñador. Tu aroma, a tu medida. 💧</p>
        </div>
    </header>

    <section class="catalogo">
        {#each decants as perfume}
            <div class="tarjeta">
                <div class="foto-wrapper">
                    <img src={perfume.imagen} alt={perfume.nombre} class="foto-perfume" />
                    <div class="foto-shade"></div>
                </div>
                
                <p class="marca">{perfume.marca.toUpperCase()}</p>
                <h2>{perfume.nombre}</h2>
                
                <div class="lista-precios">
                    {#each perfume.opciones as opcion}
                        <div class="fila-precio">
                            <span class="ml" translate="no">DECANT {opcion.ml} ML</span>
                            <span class="precio">${opcion.precio}</span>
                        </div>
                    {/each}
                </div>
            </div>
        {/each}
    </section>

    <footer class="contacto">
        <h3>CONTÁCTANOS</h3>
        
        <div class="contact-links">
            <a href={contacto.whatsappLink} target="_blank" rel="noopener noreferrer" class="link-item">
                <span class="icon">💬</span> {contacto.telefono}
            </a>
            <a href={contacto.instaLink} target="_blank" rel="noopener noreferrer" class="link-item">
                <span class="icon">📸</span> {contacto.instagram}
            </a>
            <a href={contacto.fbLink} target="_blank" rel="noopener noreferrer" class="link-item">
                <span class="icon">👤</span> {contacto.facebook}
            </a>
        </div>
        
        <p class="nota">© {new Date().getFullYear()} bparfum. Solo información y precios.<br>Ubicados en Zapotlán.</p>
    </footer>
</main>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;700&display=swap');

    :global(body) {
        margin: 0;
        background-color: #f0f0f0;
        color: #1a1a1a;
        font-family: 'Montserrat', sans-serif;
    }

    .hero {
        position: relative;
        width: 100%;
        height: 80vh;
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #000;
    }

    .hero video {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        z-index: 1;
        opacity: 0.7;
    }

    .hero-overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0,0,0,0.5);
        z-index: 2;
    }

    .hero-content {
        position: relative;
        z-index: 3;
        text-align: center;
        color: white;
        padding: 0 1rem;
    }

    .main-logo {
        width: 100%;
        max-width: 300px;
        height: auto;
        margin-bottom: 1.5rem;
        border-radius: 8px;
        box-shadow: 0 4px 15px rgba(0,0,0,0.4);
        filter: invert(1) brightness(1.2);
    }

    .tagline {
        font-size: 1.2rem;
        font-weight: 300;
        letter-spacing: 1px;
        text-shadow: 1px 1px 3px rgba(0,0,0,0.8);
    }

    .catalogo {
        display: flex;
        flex-wrap: wrap;
        gap: 2rem;
        justify-content: center;
        padding: 3rem 1rem 4rem 1rem;
        max-width: 1200px;
        margin: 0 auto;
    }

    .tarjeta {
        background: white;
        width: 310px;
        border-radius: 4px;
        overflow: hidden;
        box-shadow: 0 6px 15px rgba(0,0,0,0.06);
        text-align: center;
        transition: transform 0.3s ease, box-shadow 0.3s ease;
        display: flex;
        flex-direction: column;
    }

    .tarjeta:hover {
        transform: translateY(-8px);
        box-shadow: 0 12px 25px rgba(0,0,0,0.12);
    }

    .foto-wrapper {
        position: relative;
        width: 100%;
        height: 340px;
        overflow: hidden;
    }

    .foto-perfume {
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: transform 0.3s ease;
    }

    .tarjeta:hover .foto-perfume {
        transform: scale(1.05);
    }

    .foto-shade {
        position: absolute;
        top: 0; left: 0; width: 100%; height: 100%;
        background: linear-gradient(to bottom, rgba(0,0,0,0) 60%, rgba(0,0,0,0.3) 100%);
    }

    .marca {
        color: #777;
        font-size: 0.8rem;
        font-weight: 400;
        letter-spacing: 1px;
        margin: 1.2rem 0 0.4rem 0;
    }

    h2 {
        font-size: 1.1rem;
        font-weight: 700;
        margin: 0 0 1rem 0;
        color: #1a1a1a;
        padding: 0 1rem;
        flex-grow: 1;
    }

    .lista-precios {
        background-color: #f9f9f9;
        border-top: 1px solid #eee;
        padding: 1rem;
        margin-top: auto;
    }

    .fila-precio {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0.4rem 0;
        border-bottom: 1px dashed #ddd;
    }

    .fila-precio:last-child {
        border-bottom: none;
    }

    .ml {
        font-size: 0.85rem;
        color: #555;
        font-weight: 400;
        letter-spacing: 1px;
    }

    .precio {
        font-weight: 700;
        color: #1a1a1a;
        font-size: 1.1rem;
    }

    .contacto {
        background-color: #111;
        color: white;
        text-align: center;
        padding: 4rem 1rem;
    }

    h3 {
        font-size: 2rem;
        font-weight: 700;
        margin: 0 0 2rem 0;
        letter-spacing: 2px;
    }

    .contact-links {
        display: flex;
        flex-direction: column;
        gap: 1rem;
        margin-bottom: 2.5rem;
    }

    .link-item {
        color: #ccc;
        text-decoration: none;
        font-size: 1.1rem;
        font-weight: 300;
        transition: color 0.2s, background-color 0.2s;
        display: inline-flex;
        justify-content: center;
        align-items: center;
        gap: 10px;
    }

    .link-item:hover {
        color: white;
    }

    .nota {
        font-size: 0.8rem;
        color: #666;
        margin-top: 2rem;
        font-weight: 300;
        line-height: 1.5;
    }
</style>