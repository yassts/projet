# projet
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Intelligence Économique & Géopolitique – IA Générative</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
  <style>
    :root {
      --primary-dark: #0A192F;
      --accent-blue: #2A5C82;
      --accent-teal: #4ECDC4;
      --accent-red: #FF5A5F;
      --text-light: #F8F9FA;
      --bg-light: #f3f4f6;
      --bg-medium: #e5e7eb;
      --glass: rgba(255, 255, 255, 0.08);
    }
    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(45deg, var(--bg-light), var(--bg-medium));
      margin: 0;
      padding: 2rem;
      min-height: 100vh;
    }
    .dashboard {
      max-width: 1400px;
      margin: 2rem auto;
      background: white;
      border-radius: 24px;
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.12);
      overflow: hidden;
      border: 1px solid rgba(255, 255, 255, 0.2);
      transform: translateY(20px);
      opacity: 0;
      animation: fadeInUp 0.6s cubic-bezier(0.4, 0, 0.2, 1) forwards;
    }
    @keyframes fadeInUp {
      to { transform: translateY(0); opacity: 1; }
    }
    .header {
      background: linear-gradient(135deg, var(--primary-dark), #0F3460);
      padding: 2.5rem 2rem;
      color: var(--text-light);
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    .header::before {
      content: '';
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: radial-gradient(circle, var(--accent-teal) 0%, transparent 70%);
      opacity: 0.05;
      pointer-events: none;
    }
    .header h1 {
      margin: 0;
      font-size: 2.6rem;
      font-weight: 600;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 1.2rem;
      position: relative;
    }
    .header p {
      margin: 0.8rem 0 0;
      font-size: 1.1rem;
      opacity: 0.9;
      font-weight: 300;
    }
    .nav-tabs {
      position: relative;
      display: inline-flex;
      background: var(--glass);
      border-radius: 14px;
      padding: 0.4rem;
      margin-top: 2.5rem;
    }
    .nav-tabs .tab {
      padding: 1rem 2.2rem;
      border-radius: 12px;
      cursor: pointer;
      transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
      color: var(--text-light);
      font-weight: 500;
      backdrop-filter: blur(4px);
      position: relative;
      z-index: 1;
    }
    .nav-tabs .tab.active {
      color: var(--primary-dark);
      font-weight: 600;
    }
    .tab-indicator {
      position: absolute;
      height: 80%;
      background: var(--accent-teal);
      border-radius: 10px;
      transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
      z-index: 0;
    }
    .section {
      display: none;
      padding: 2.5rem;
    }
    .section.active {
      display: block;
    }
    h2 {
      color: var(--primary-dark);
      font-size: 2rem;
      margin-bottom: 2rem;
      position: relative;
      padding-bottom: 0.5rem;
    }
    h2::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 60px;
      height: 3px;
      background: var(--accent-teal);
      border-radius: 2px;
    }
    /* Chart container */
    .chart-container {
      padding: 1rem;
      background: white;
      border-radius: 18px;
      box-shadow: 0 8px 24px rgba(0,0,0,0.06);
      margin-bottom: 2rem;
    }
    /* Analyse Comparative */
    .grid-container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
      gap: 2rem;
      margin-bottom: 3rem;
    }
    .era-card {
      background: #fff;
      border-radius: 18px;
      padding: 2rem;
      box-shadow: 0 8px 24px rgba(0,0,0,0.06);
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      border-left: 6px solid var(--accent-blue);
      position: relative;
      overflow: hidden;
    }
    .era-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 4px;
      background: var(--accent-teal);
      opacity: 0;
      transition: opacity 0.3s ease;
    }
    .era-card:hover {
      transform: translateY(-8px);
      box-shadow: 0 12px 32px rgba(0,0,0,0.1);
    }
    .era-card:hover::before {
      opacity: 1;
    }
    .card-header {
      display: flex;
      align-items: center;
      gap: 1.2rem;
      margin-bottom: 1.5rem;
    }
    .era-icon {
      width: 56px;
      height: 56px;
      background: linear-gradient(135deg, var(--accent-teal), #3BA9A2);
      border-radius: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 1.6rem;
      box-shadow: 0 4px 12px rgba(78, 205, 196, 0.2);
    }
    .metric {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1rem;
      background: #f8f9fa;
      border-radius: 12px;
      margin: 1.5rem 0;
      font-weight: 500;
      border: 1px solid #e9ecef;
    }
    .progress-bar {
      height: 10px;
      background: #e9ecef;
      border-radius: 6px;
      overflow: hidden;
    }
    .progress {
      height: 100%;
      background: linear-gradient(90deg, var(--accent-teal), #3BA9A2);
      transition: width 0.8s cubic-bezier(0.4, 0, 0.2, 1);
    }
    .tech-list {
      list-style: none;
      padding: 0;
      margin: 0;
    }
    .tech-list li {
      margin: 0.8rem 0;
      padding: 0.8rem;
      background: rgba(78, 205, 196, 0.05);
      border-radius: 8px;
      display: flex;
      align-items: center;
      gap: 0.8rem;
      transition: transform 0.3s ease;
    }
    .tech-list li:hover {
      transform: translateX(8px);
      background: rgba(78, 205, 196, 0.1);
    }
    .analysis-details p {
      line-height: 1.8;
      margin-bottom: 1.5rem;
      color: #4a5568;
      font-size: 1.05rem;
    }
    /* Carte Mondiale */
    .map-container {
      position: relative;
      height: 600px;
      border-radius: 18px;
      overflow: hidden;
      background: url('https://upload.wikimedia.org/wikipedia/commons/thumb/8/80/World_map_-_low_resolution.svg/2560px-World_map_-_low_resolution.svg.png') no-repeat center center;
      background-size: cover;
      filter: brightness(1.1);
      border: 2px solid rgba(255,255,255,0.3);
      box-shadow: inset 0 4px 12px rgba(0,0,0,0.06);
    }
    .map-node {
      position: absolute;
      background: rgba(255,255,255,0.98);
      padding: 0.8rem 1.2rem;
      border-radius: 10px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.12);
      font-size: 0.95rem;
      text-align: center;
      cursor: pointer;
      transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
      border: 1px solid rgba(0,0,0,0.05);
      min-width: 140px;
    }
    .map-node:hover {
      transform: scale(1.08) translateY(-4px);
      box-shadow: 0 6px 16px rgba(0,0,0,0.15);
    }
    .map-node.dominant {
      background: var(--accent-red);
      color: #fff;
      border: 1px solid var(--accent-red);
    }
    .map-node.emergent {
      background: var(--accent-blue);
      color: #fff;
      border: 1px solid var(--accent-blue);
    }
    /* Légende repositionnée en bas à gauche et taille réduite */
    .legend {
      position: absolute;
      bottom: 20px;
      left: 20px;
      background: rgba(255,255,255,0.95);
      padding: 0.5rem 0.8rem;
      border-radius: 8px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.08);
      font-size: 0.8rem;
      backdrop-filter: blur(6px);
      border: 1px solid rgba(0,0,0,0.05);
    }
    .legend p {
      margin: 0.2rem 0;
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }
    /* Tooltip */
    .tooltip {
      position: absolute;
      background: rgba(0,0,0,0.9);
      color: white;
      padding: 0.8rem 1.2rem;
      border-radius: 8px;
      pointer-events: none;
      opacity: 0;
      transition: opacity 0.2s;
      font-size: 0.9rem;
    }
    /* Écosystème Paris-Saclay */
    .ecosystem-container {
      max-width: 1200px;
      margin: 0 auto;
    }
    .filter-bar {
      display: flex;
      gap: 1rem;
      margin-bottom: 2rem;
      justify-content: center;
      flex-wrap: wrap;
    }
    /* Modification des boutons de filtre pour améliorer la visibilité */
    .filter-btn {
      padding: 0.8rem 1.5rem;
      border-radius: 12px;
      cursor: pointer;
      transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
      background: rgba(0,0,0,0.05);
      color: var(--primary-dark);
      border: 1px solid rgba(0,0,0,0.1);
      font-weight: 500;
    }
    .filter-btn.active {
      background: var(--accent-teal);
      color: white;
      font-weight: 600;
      box-shadow: 0 4px 12px rgba(78, 205, 196, 0.3);
    }
    .ecosystem-layers {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 2rem;
      max-width: 1200px;
      margin: 0 auto;
    }
    .layer {
      background: #fff;
      padding: 2rem;
      border-radius: 18px;
      text-align: center;
      min-height: 280px;
      box-shadow: 0 8px 24px rgba(0,0,0,0.06);
      transition: transform 0.3s ease;
      border-top: 4px solid var(--accent-teal);
    }
    .layer:hover {
      transform: translateY(-8px);
    }
    .layer h3 {
      margin: 0 0 1.5rem;
      color: var(--primary-dark);
      font-size: 1.3rem;
      font-weight: 600;
    }
    .entity {
      background: rgba(78, 205, 196, 0.05);
      margin: 0.8rem 0;
      padding: 1rem;
      border-radius: 10px;
      transition: all 0.3s ease;
      border: 1px solid rgba(78, 205, 196, 0.1);
    }
    .entity:hover {
      background: rgba(78, 205, 196, 0.1);
      transform: translateX(6px);
    }
    @media (max-width: 768px) {
      body { padding: 1rem; }
      .dashboard { border-radius: 16px; }
      .header h1 { font-size: 2rem; }
      .tab { padding: 0.8rem 1.5rem; font-size: 0.9rem; }
      .section { padding: 1.5rem; }
      h2 { font-size: 1.6rem; }
    }
  </style>
</head>
<body>
  <div class="dashboard">
    <div class="header">
      <h1><i class="fas fa-brain"></i> Intelligence Économique & Géopolitique – IA Générative</h1>
      <p>Étudiant en Master E3IN – Ingénierie Informatique et Innovation Numérique</p>
      <div class="nav-tabs">
        <div class="tab-indicator"></div>
        <div class="tab active" data-section="analyse">Analyse Comparative</div>
        <div class="tab" data-section="carte">Carte Mondiale</div>
        <div class="tab" data-section="ecosystem">Écosystème Paris-Saclay</div>
      </div>
    </div>

    <!-- Section Analyse -->
    <div id="analyse" class="section active">
      <h2>Analyse Approfondie de l’IA Générative dans les Révolutions Industrielles</h2>
      <div class="chart-container">
        <canvas id="investmentChart"></canvas>
      </div>
      <div class="grid-container">
        <!-- Industrie 4.0 -->
        <div class="era-card">
          <div class="card-header">
            <div class="era-icon"><i class="fas fa-robot"></i></div>
            <div>
              <h3>Industrie 4.0 (2010)</h3>
              <p>Révolution Digitale</p>
            </div>
          </div>
          <div class="metric">
            <span>Productivité</span>
            <span>+30%</span>
          </div>
          <div class="progress-bar">
            <div class="progress" style="width: 30%"></div>
          </div>
          <ul class="tech-list">
            <li><i class="fas fa-cloud"></i> Cloud Computing</li>
            <li><i class="fas fa-microchip"></i> IoT</li>
            <li><i class="fas fa-database"></i> Big Data</li>
          </ul>
        </div>
        <!-- Industrie 5.0 -->
        <div class="era-card">
          <div class="card-header">
            <div class="era-icon"><i class="fas fa-hands-helping"></i></div>
            <div>
              <h3>Industrie 5.0 (2020)</h3>
              <p>Collaboration Humain-IA</p>
            </div>
          </div>
          <div class="metric">
            <span>Énergie économisée</span>
            <span>40%</span>
          </div>
          <div class="progress-bar">
            <div class="progress" style="width: 40%"></div>
          </div>
          <ul class="tech-list">
            <li><i class="fas fa-dna"></i> GAN Matériaux</li>
            <li><i class="fas fa-cogs"></i> Cobots</li>
            <li><i class="fas fa-leaf"></i> Éco-conception</li>
          </ul>
        </div>
        <!-- Industrie X.0 -->
        <div class="era-card">
          <div class="card-header">
            <div class="era-icon"><i class="fas fa-atom"></i></div>
            <div>
              <h3>Industrie X.0 (2030+)</h3>
              <p>Ère Cognitive</p>
            </div>
          </div>
          <div class="metric">
            <span>Personnalisation</span>
            <span>90%</span>
          </div>
          <div class="progress-bar">
            <div class="progress" style="width: 90%"></div>
          </div>
          <ul class="tech-list">
            <li><i class="fas fa-pills"></i> Médicaments génératifs</li>
            <li><i class="fab fa-ethereum"></i> Blockchain IA</li>
            <li><i class="fas fa-project-diagram"></i> Réseaux autonomes</li>
          </ul>
        </div>
      </div>
      <div class="analysis-details">
        <p>L’essor de l’IA générative – avec des technologies telles que ChatGPT, OpenAI Codex et MidJourney – révolutionne la production industrielle en automatisant la création de contenu et en optimisant les chaînes logistiques. Dans l’Industrie 4.0, ces innovations améliorent la productivité et la réactivité des systèmes.</p>
        <p>La transition vers l’Industrie 5.0 introduit une collaboration étroite entre l’humain et la machine, favorisant la personnalisation et intégrant des considérations de durabilité. Enfin, l’Industrie X.0 promet une hyper-personnalisation avec des innovations telles que la génération de médicaments sur mesure et l’usage de la blockchain pour sécuriser les modèles d’IA.</p>
        <p>Sur le plan géopolitique, ces évolutions soulèvent des enjeux critiques : la rivalité sino-américaine se traduit par des sanctions (ex. sur les exportations de puces NVIDIA), tandis que l’Europe tente d’imposer un cadre réglementaire avec le AI Act afin de préserver la diversité culturelle et linguistique.</p>
      </div>
    </div>

    <!-- Section Carte Mondiale -->
    <div id="carte" class="section">
      <h2>Carte Mondiale des Centres de Gravité – IA Générative</h2>
      <div class="map-container">
        <div class="legend">
          <h4>Légende</h4>
          <p><span style="color: var(--accent-red); font-weight: bold;">●</span> Centres Dominants</p>
          <p><span style="color: var(--accent-blue); font-weight: bold;">●</span> Centres Émergents</p>
          <p>Icônes : <span>💻</span>, <span>🎓</span>, <span>🏛️</span></p>
        </div>
        <div class="map-node dominant" style="top: 55%; left: 15%;" data-info="Silicon Valley : ~40% des investissements mondiaux en IA, acteurs clés tels qu'OpenAI et Anthropic.">
          💻 Silicon Valley<br><small>40% Invest.</small>
        </div>
        <div class="map-node dominant" style="top: 40%; left: 85%;" data-info="Pékin : Entreprises comme Baidu et SenseTime contribuent à ~25% des publications scientifiques en IA.">
          💻 Pékin<br><small>25% Pub.</small>
        </div>
        <div class="map-node emergent" style="top: 35%; left: 50%;" data-info="Paris-Saclay : Hub européen émergent avec des acteurs tels que Mistral AI et LightOn, soutenu par France 2030.">
          🎓 Paris-Saclay<br><small>Hub Européen</small>
        </div>
        <div class="map-node emergent" style="top: 50%; left: 70%;" data-info="Yaffa : Collaboration entre secteur militaire et civil, avec des acteurs tels qu'AI21 Labs.">
          🏛️ Yaffa<br><small>Collab. Mil-Civ</small>
        </div>
      </div>
    </div>

    <!-- Section Écosystème Paris-Saclay -->
    <div id="ecosystem" class="section">
      <h2>Schéma de l’Écosystème Paris-Saclay</h2>
      <div class="filter-bar">
        <button class="filter-btn active" data-filter="all">Tous</button>
        <button class="filter-btn" data-filter="research">Recherche</button>
        <button class="filter-btn" data-filter="startup">Startups</button>
        <button class="filter-btn" data-filter="funding">Financements</button>
        <button class="filter-btn" data-filter="partnership">Partenariats</button>
      </div>
      <div class="ecosystem-layers">
        <div class="layer research-layer">
          <h3>Centres de Recherche</h3>
          <div class="entity">INRIA</div>
          <div class="entity">CEA</div>
          <div class="entity">École Polytechnique</div>
        </div>
        <div class="layer startups-layer">
          <h3>Startups</h3>
          <div class="entity">Mistral AI</div>
          <div class="entity">Hugging Face</div>
          <div class="entity">LightOn</div>
        </div>
        <div class="layer funding-layer">
          <h3>Financements</h3>
          <div class="entity">France 2030</div>
          <div class="entity">Bpifrance</div>
        </div>
        <div class="layer partnerships-layer">
          <h3>Partenariats Publics-Privés</h3>
          <div class="entity">Thales</div>
          <div class="entity">TotalEnergies</div>
          <div class="entity">Opérateur Public</div>
        </div>
      </div>
    </div>
  </div>

  <!-- Scripts -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script>
    // Gestion des onglets avec indicateur animé
    const tabs = document.querySelectorAll('.nav-tabs .tab');
    const sections = document.querySelectorAll('.section');
    const tabIndicator = document.querySelector('.tab-indicator');
    tabs.forEach(tab => {
      tab.addEventListener('click', function() {
        const width = this.offsetWidth;
        const left = this.offsetLeft;
        tabIndicator.style.width = `${width}px`;
        tabIndicator.style.left = `${left}px`;
        tabs.forEach(t => t.classList.remove('active'));
        this.classList.add('active');
        sections.forEach(section => section.classList.remove('active'));
        const target = this.getAttribute('data-section');
        document.getElementById(target).classList.add('active');
      });
    });

    // Initialisation du graphique Chart.js
    const ctx = document.getElementById('investmentChart').getContext('2d');
    new Chart(ctx, {
      type: 'line',
      data: {
        labels: ['2018', '2019', '2020', '2021', '2022', '2023'],
        datasets: [{
          label: 'Investissements (en milliards $)',
          data: [2.5, 4.2, 6.8, 12.4, 18.9, 25.3],
          borderColor: '#4ECDC4',
          tension: 0.4,
          fill: false
        }]
      }
    });

    // Tooltip personnalisé pour les nœuds de la carte
    const tooltip = document.createElement('div');
    tooltip.className = 'tooltip';
    document.body.appendChild(tooltip);
    document.querySelectorAll('.map-node').forEach(node => {
      node.addEventListener('mousemove', (e) => {
        tooltip.style.left = `${e.pageX + 15}px`;
        tooltip.style.top = `${e.pageY + 15}px`;
        tooltip.textContent = node.getAttribute('data-info');
        tooltip.style.opacity = '1';
      });
      node.addEventListener('mouseleave', () => {
        tooltip.style.opacity = '0';
      });
    });

    // Filtrage dans l'écosystème
    const filterButtons = document.querySelectorAll('.filter-btn');
    const ecosystemLayers = document.querySelectorAll('.ecosystem-layers .layer');
    filterButtons.forEach(btn => {
      btn.addEventListener('click', () => {
        filterButtons.forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
        const filter = btn.getAttribute('data-filter');
        ecosystemLayers.forEach(layer => {
          if (filter === 'all') {
            layer.style.display = 'block';
          } else if (
            (filter === 'research' && layer.classList.contains('research-layer')) ||
            (filter === 'startup' && layer.classList.contains('startups-layer')) ||
            (filter === 'funding' && layer.classList.contains('funding-layer')) ||
            (filter === 'partnership' && layer.classList.contains('partnerships-layer'))
          ) {
            layer.style.display = 'block';
          } else {
            layer.style.display = 'none';
          }
        });
      });
    });
  </script>
</body>
</html><html>
<head>
    <meta charset="UTF-8" />
    <title>title</title>
</head>
<body>
    
</body>
</html>
