<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Educación en Mercados Financieros</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Roboto', sans-serif;
        }
        body {
            background-color: #1e1e2f;
            color: #f5f5f5;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        header {
            background-color: #333;
            color: white;
            padding: 20px;
            text-align: center;
            width: 100%;
        }
        header h1 {
            font-size: 2.5em;
            margin-bottom: 5px;
        }
        header p {
            font-size: 1.1em;
        }
        .navbar {
            display: flex;
            justify-content: center;
            background-color: #4CAF50;
            width: 100%;
        }
        .navbar ul {
            list-style: none;
            display: flex;
        }
        .navbar ul li {
            margin: 0 15px;
        }
        .navbar ul li a {
            color: white;
            text-decoration: none;
            padding: 10px 15px;
            transition: background-color 0.3s;
        }
        .navbar ul li a:hover {
            background-color: #45a049;
            border-radius: 5px;
        }
        .section {
            width: 90%;
            max-width: 1200px;
            margin: 20px 0;
            text-align: center;
        }
        .section h2 {
            font-size: 2em;
            margin-bottom: 20px;
            color: #4CAF50;
        }
        .card {
            background-color: #2b2b3d;
            color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            display: inline-block;
            width: 45%;
            margin: 10px;
        }
        .card:hover {
            transform: scale(1.05);
            box-shadow: 0px 8px 20px rgba(0, 0, 0, 0.3);
        }
        .container {
            width: 100%;
            margin: auto;
        }
        .chart-container {
            width: 100%;
            max-width: 700px;
            margin: 20px auto;
        }
        footer {
            background-color: #333;
            padding: 20px;
            text-align: center;
            width: 100%;
            color: white;
        }
        footer p {
            margin: 10px 0;
        }
        .social a {
            color: white;
            margin: 0 10px;
            font-size: 1.2em;
        }
    </style>
</head>
<body>

<header>
    <h1>Mercados Financieros Interactivos</h1>
    <p>Explora y aprende con gráficos y simulaciones en tiempo real</p>
</header>

<nav class="navbar">
    <ul>
        <li><a href="#simulador">Simulador de Trading</a></li>
        <li><a href="#educacion">Educación en Mercados</a></li>
        <li><a href="#noticias">Noticias Semanales</a></li>
        <li><a href="#etf">ETF</a></li>
    </ul>
</nav>

<main>
    <section id="simulador" class="section">
        <h2>Simulador de Trading</h2>
        <p>Prueba tus habilidades de trading con nuestro simulador interactivo.</p>
        <div class="chart-container">
            <canvas id="simuladorChart"></canvas>
        </div>
    </section>

    <section id="educacion" class="section">
        <h2>Educación en Mercados Financieros</h2>
        <div class="card">
            <h3>Introducción a los Mercados</h3>
            <p>Aprende los conceptos básicos de los mercados financieros, análisis técnico y fundamental.</p>
        </div>
        <div class="card">
            <h3>Gestión de Riesgo</h3>
            <p>Descubre estrategias para gestionar el riesgo y mejorar tus inversiones.</p>
        </div>
    </section>

    <section id="noticias" class="section">
        <h2>Noticias Semanales</h2>
        <div class="card">
            <h3>Actualización de Mercados</h3>
            <p>Accede a las noticias más recientes y análisis semanal del mercado financiero.</p>
        </div>
        <div class="card">
            <h3>Tendencias de Inversión</h3>
            <p>Descubre las tendencias de inversión y los sectores en crecimiento.</p>
        </div>
    </section>

    <section id="etf" class="section">
        <h2>ETFs y Fondos de Inversión</h2>
        <div class="card">
            <h3>Inversión en ETFs</h3>
            <p>Explora los diferentes ETFs disponibles para diversificar tu portafolio.</p>
        </div>
    </section>
</main>

<footer>
    <p>&copy; 2024 Mercados Financieros. Todos los derechos reservados.</p>
    <div class="social">
        <a href="#"><i class="fab fa-twitter"></i></a>
        <a href="#"><i class="fab fa-facebook"></i></a>
        <a href="#"><i class="fab fa-linkedin"></i></a>
    </div>
</footer>

<script>
    // Simulador de Trading Chart
    const ctx = document.getElementById('simuladorChart').getContext('2d');
    let tradingData = generateRandomData();

    const simuladorChart = new Chart(ctx, {
        type: 'line',
        data: {
            labels: Array.from({ length: 20 }, (_, i) => `Minuto ${i + 1}`),
            datasets: [{
                label: 'Precio Simulado de la Acción',
                data: tradingData,
                borderColor: 'rgba(75, 192, 192, 1)',
                backgroundColor: 'rgba(75, 192, 192, 0.2)',
                borderWidth: 2,
                fill: true,
            }]
        },
        options: {
            responsive: true,
            scales: {
                y: {
                    beginAtZero: false
                }
            }
        }
    });

    function generateRandomData() {
        return Array.from({ length: 20 }, () => Math.floor(Math.random() * 50) + 100);
    }

    // Actualización simulada de datos cada 3 segundos
    setInterval(() => {
        tradingData.push(Math.floor(Math.random() * 50) + 100);
        if (tradingData.length > 20) tradingData.shift();
        simuladorChart.data.datasets[0].data = tradingData;
        simuladorChart.update();
    }, 3000);
</script>

</body>
</html>
git clone https://github.com/<
