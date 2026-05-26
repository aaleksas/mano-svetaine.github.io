<!DOCTYPE html>
<html lang="lt">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Muzikos Pasaulis</title>

    <link rel="icon" href="favicon.ico">

    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: #020617;
            color: white;
            overflow-x: hidden;
        }

        body::before {
            content: "";
            position: fixed;
            width: 700px;
            height: 700px;
            background: radial-gradient(circle, rgba(56,189,248,0.25), transparent 70%);
            top: -200px;
            left: -200px;
            z-index: -1;
        }

        body::after {
            content: "";
            position: fixed;
            width: 600px;
            height: 600px;
            background: radial-gradient(circle, rgba(168,85,247,0.25), transparent 70%);
            bottom: -200px;
            right: -200px;
            z-index: -1;
        }

        header {
            min-height: 100vh;
            background:
                linear-gradient(rgba(0,0,0,0.65), rgba(0,0,0,0.85)),
                url("https://images.unsplash.com/photo-1511671782779-c97d3d27a1d4");
            background-size: cover;
            background-position: center;
            display: flex;
            flex-direction: column;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 25px 60px;
            backdrop-filter: blur(10px);
            background: rgba(255,255,255,0.05);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        nav h1 {
            font-size: 28px;
            color: #38bdf8;
            letter-spacing: 2px;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 30px;
        }

        nav a {
            text-decoration: none;
            color: white;
            font-weight: 500;
            position: relative;
            transition: 0.3s;
        }

        nav a::after {
            content: "";
            position: absolute;
            width: 0%;
            height: 2px;
            background: #38bdf8;
            left: 0;
            bottom: -5px;
            transition: 0.3s;
        }

        nav a:hover::after {
            width: 100%;
        }

        nav a:hover {
            color: #38bdf8;
        }

        .hero {
            flex: 1;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            text-align: center;
            padding: 20px;
        }

        .hero h2 {
            font-size: 72px;
            font-weight: 700;
            background: linear-gradient(to right, #38bdf8, #a855f7);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: fadeIn 1.5s ease;
        }

        .hero p {
            margin-top: 20px;
            font-size: 22px;
            color: #cbd5e1;
            animation: fadeUp 2s ease;
        }

        .hero button {
            margin-top: 35px;
            padding: 14px 35px;
            border: none;
            border-radius: 50px;
            background: linear-gradient(135deg, #38bdf8, #a855f7);
            color: white;
            font-size: 16px;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 0 0 25px rgba(56,189,248,0.5);
        }

        .hero button:hover {
            transform: translateY(-5px) scale(1.05);
        }

        section {
            padding: 100px 10%;
        }

        h2.section-title {
            text-align: center;
            font-size: 42px;
            margin-bottom: 60px;
            color: #38bdf8;
        }

        .about-content {
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(255,255,255,0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            line-height: 1.9;
            font-size: 18px;
            color: #e2e8f0;
            box-shadow: 0 0 30px rgba(0,0,0,0.3);
        }

        .highlight {
            color: #38bdf8;
            font-weight: 600;
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 20px;
        }

        .gallery-grid img {
            width: 100%;
            height: 240px;
            object-fit: cover;
            border-radius: 20px;
            transition: 0.4s;
            cursor: pointer;
            box-shadow: 0 0 20px rgba(0,0,0,0.4);
        }

        .gallery-grid img:hover {
            transform: scale(1.07) rotate(1deg);
            box-shadow: 0 0 30px rgba(56,189,248,0.6);
        }

        .contact-box {
            background: rgba(255,255,255,0.05);
            padding: 40px;
            border-radius: 20px;
            text-align: center;
            backdrop-filter: blur(10px);
        }

        .contact-box p {
            margin: 15px 0;
            font-size: 18px;
        }

        .contact-box a {
            color: #38bdf8;
            text-decoration: none;
        }

        footer {
            text-align: center;
            padding: 25px;
            background: rgba(255,255,255,0.03);
            color: #94a3b8;
        }

        #lightbox {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.9);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 999;
        }

        #lightbox img {
            max-width: 90%;
            max-height: 90%;
            border-radius: 20px;
        }

        .close {
            position: absolute;
            top: 20px;
            right: 40px;
            font-size: 50px;
            cursor: pointer;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }

        @keyframes fadeUp {
            from { opacity: 0; transform: translateY(40px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @media (max-width: 768px) {
            nav { flex-direction: column; gap: 20px; padding: 20px; }
            nav ul { flex-wrap: wrap; justify-content: center; }
            .hero h2 { font-size: 42px; }
            .hero p { font-size: 18px; }
            section { padding: 70px 20px; }
        }
    </style>
</head>

<body>

<header>
    <nav>
        <h1>Muzikos Pasaulis</h1>
        <ul>
            <li><a href="#apie">Apie</a></li>
            <li><a href="#galerija">Galerija</a></li>
            <li><a href="#kontaktai">Kontaktai</a></li>
        </ul>
    </nav>

    <div class="hero">
        <h2>Pasinerk į muzikos pasaulį</h2>
        <p>Muzika sujungia emocijas, ritmą ir žmones</p>
        <button onclick="document.getElementById('galerija').scrollIntoView()">
            Žiūrėti galeriją
        </button>
    </div>
</header>

<section id="apie">
    <h2 class="section-title">Apie muziką</h2>
    <div class="about-content">
        Muzika yra viena svarbiausių
        <span class="highlight">meno formų</span>,
        lydinti žmoniją nuo seniausių laikų.
        Ji leidžia išreikšti
        <span class="highlight">emocijas</span>,
        kurti prisiminimus ir vienyti žmones.
        Šiuolaikiniame pasaulyje muzika tapo neatsiejama
        <span class="highlight">kasdienio gyvenimo</span>
        dalimi — nuo koncertų iki muzikos platformų telefone.
        Skirtingi žanrai leidžia kiekvienam atrasti savo
        <span class="highlight">mėgstamą stilių</span>.
    </div>
</section>

<section id="galerija">
    <h2 class="section-title">Galerija</h2>

    <div class="gallery-grid">
        <img src="https://images.unsplash.com/photo-1493225457124-a3eb161ffa5f" alt="Koncertas" onclick="openLightbox(this.src)">
        <img src="https://images.unsplash.com/photo-1507874457470-272b3c8d8ee2" alt="Scena" onclick="openLightbox(this.src)">
        <img src="https://images.unsplash.com/photo-1511379938547-c1f69419868d" alt="DJ" onclick="openLightbox(this.src)">
        <img src="https://images.unsplash.com/photo-1516280440614-37939bbacd81" alt="Gitara" onclick="openLightbox(this.src)">
        <img src="https://images.unsplash.com/photo-1505740420928-5e560c06d30e" alt="Ausinės" onclick="openLightbox(this.src)">
        <img src="https://images.unsplash.com/photo-1470225620780-dba8ba36b745" alt="Festivalis" onclick="openLightbox(this.src)">

        <!-- NAUJOS 4 NUOTRAUKOS -->
        <img src="https://images.unsplash.com/photo-1500530855697-b586d89ba3ee" alt="Koncerto minia" onclick="openLightbox(this.src)">
        <img src="https://images.unsplash.com/photo-1516450360452-9312f5e86fc7" alt="Muzikos studija" onclick="openLightbox(this.src)">
        <img src="https://images.unsplash.com/photo-1487180144351-b8472da7d491" alt="Būgnai" onclick="openLightbox(this.src)">
        <img src="https://images.unsplash.com/photo-1510915228340-29c85a43dcfe" alt="Mikrofonas" onclick="openLightbox(this.src)">
    </div>
</section>

<section id="kontaktai">
    <h2 class="section-title">Kontaktai</h2>

    <div class="contact-box">
        <p><strong>El. paštas:</strong> muzika@pasaulis.lt</p>
        <p><strong>Adresas:</strong> Muzikos g. 10, Vilnius</p>

        <p>
            <a href="https://facebook.com" target="_blank" rel="noopener noreferrer">
                Facebook puslapis
            </a>
        </p>
    </div>
</section>

<footer>
    <p id="copyright"></p>
</footer>

<div id="lightbox">
    <span class="close" onclick="closeLightbox()">&times;</span>
    <img id="lightbox-img">
</div>

<script>
function openLightbox(src) {
    document.getElementById("lightbox").style.display = "flex";
    document.getElementById("lightbox-img").src = src;
}

function closeLightbox() {
    document.getElementById("lightbox").style.display = "none";
}

document.getElementById("lightbox").addEventListener("click", function(e) {
    if (e.target.id === "lightbox") {
        closeLightbox();
    }
});

document.addEventListener("keydown", function(e) {
    if (e.key === "Escape") {
        closeLightbox();
    }
});

document.getElementById("copyright").innerHTML =
`© ${new Date().getFullYear()} Muzikos Pasaulis. Visos teisės saugomos.`;
</script>

</body>
</html>
