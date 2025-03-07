<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Intelligence Économique & Géopolitique – IA Générative</title>
  <style>
    /* Basique: reset minimal + styles globaux */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(45deg, #f3f4f6, #e5e7eb);
      margin: 0;
      padding: 2rem;
      min-height: 100vh;
    }
    .dashboard {
      max-width: 1400px;
      margin: 0 auto;
      background: white;
      border-radius: 24px;
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.12);
      overflow: hidden;
      border: 1px solid rgba(255, 255, 255, 0.2);
    }

    /* Header + onglets */
    .header {
      background: linear-gradient(135deg, #0A192F, #0F3460);
      padding: 2.5rem 2rem;
      color: #F8F9FA;
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
      background: radial-gradient(circle, #4ECDC4 0%, transparent 70%);
      opacity: 0.05;
      pointer-events: none;
    }
    .header h1 {
      margin: 0;
      font-size: 2.6rem;
      font-weight: 600;
      display: inline-flex;
      align-items: center;
      gap: 1.2rem;
    }
    .header p {
      margin-top: 0.8rem;
      font-size: 1.1rem;
      opacity: 0.9;
      font-weight: 300;
    }

    .nav-tabs {
      display: flex;
      gap: 1rem;
      justify-content: center;
      margin-top: 2.5rem;
      flex-wrap: wrap;
    }
    .tab {
      padding: 1rem 2.2rem;
      border-radius: 12px;
      cursor: pointer;
      transition: all 0.3s;
      background: rgba(255, 255, 255, 0.08);
      color: #F8F9FA;
      border: 1px solid rgba(255, 255, 255, 0.1);
      font-weight: 500;
      backdrop-filter: blur(4px);
    }
    .tab:hover {
      transform: translateY(-2px);
      background: rgba(255, 255, 255, 0.15);
    }
    .tab.active {
      background: #4ECDC4;
      font-weight: 600;
      box-shadow: 0 4px 12px rgba(78, 205, 196, 0.3);
    }

    /* Sections */
    .section {
      display: none;
      padding: 2.5rem;
    }
    .section.active {
      display: block;
    }
    h2 {
      color: #0A192F;
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
      background: #4ECDC4;
      border-radius: 2px;
    }

    /* SECTION 1 : Analyse Comparative */
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
      border-left: 6px solid #2A5C82; 
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
      background: #4ECDC4;
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
      background: linear-gradient(135deg, #4ECDC4, #3BA9A2);
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
      background: linear-gradient(90deg, #4ECDC4, #3BA9A2);
      transition: width 0.8s;
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

    /* SECTION 2 : Carte Mondiale */
    .map-container {
      position: relative;
      height: 600px;
      border-radius: 18px;
      overflow: hidden;
      background: url('https://upload.wikimedia.org/wikipedia/commons/thumb/8/80/World_map_-_low_resolution.svg/2880px-World_map_-_low_resolution.svg.png') no-repeat center center;
      background-size: cover;
      border: 2px solid rgba(255,255,255,0.3);
      box-shadow: inset 0 4px 12px rgba(0,0,0,0.06);
    }
    .map-node {
      position: absolute;
      padding: 0.8rem 1.2rem;
      border-radius: 10px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.12);
      font-size: 0.95rem;
      text-align: center;
      cursor: pointer;
      transition: all 0.3s ease;
      border: 1px solid rgba(0,0,0,0.05);
      min-width: 140px;
    }
    .map-node:hover {
      transform: scale(1.08) translateY(-4px);
      box-shadow: 0 6px 16px rgba(0,0,0,0.15);
    }
    .map-node.dominant {
      background: #FF5A5F;
      color: #fff;
      border: 1px solid #FF5A5F;
    }
    .map-node.emergent {
      background: #2A5C82;
      color: #fff;
      border: 1px solid #2A5C82;
    }
    .legend {
      position: absolute;
      bottom: 20px;
      left: 20px;
      background: rgba(255,255,255,0.95);
      padding: 1rem 1.2rem;
      border-radius: 10px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.08);
      font-size: 0.9rem;
      backdrop-filter: blur(6px);
      border: 1px solid rgba(0,0,0,0.05);
    }
    .legend p {
      margin: 0.4rem 0;
      display: flex;
      align-items: center;
      gap: 0.8rem;
    }
  </style>
</head>
<body>

  <div class="dashboard">
    <!-- Header + Tabs -->
    <div class="header">
      <h1><i class="fas fa-brain"></i> Intelligence Économique & Géopolitique – IA Générative</h1>
      <p>Étudiant en Master E3IN – Ingénierie Informatique et Innovation Numérique</p>
      <div class="nav-tabs">
        <div class="tab active" data-section="analyse">Analyse Comparative</div>
        <div class="tab" data-section="carte">Carte Mondiale</div>
      </div>
    </div>

    <!-- SECTION 1: Analyse Comparative -->
    <div id="analyse" class="section active">
      <h2>Analyse Approfondie de l’IA Générative dans les Révolutions Industrielles</h2>
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
            <div class="progress" style="width:30%"></div>
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
            <div class="progress" style="width:40%"></div>
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
            <div class="progress" style="width:90%"></div>
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

    <!-- SECTION 2: Carte Mondiale -->
    <div id="carte" class="section">
      <h2>Carte Mondiale des Centres de Gravité – IA Générative</h2>
      <div class="map-container">
        <div class="legend">
          <h4>Légende</h4>
          <p><span style="color:#FF5A5F;font-weight:bold;">●</span> Centres Dominants</p>
          <p><span style="color:#2A5C82;font-weight:bold;">●</span> Centres Émergents</p>
          <p>Icônes : <span>💻</span>, <span>🎓</span>, <span>🏛️</span></p>
        </div>

        <!-- Points sur la carte -->
        <div class="map-node dominant" style="top:40%; left:22%;" data-info="Silicon Valley : ~40% des investissements mondiaux en IA, acteurs clés tels qu'OpenAI et Anthropic.">
          💻 Silicon Valley<br><small>40% Invest.</small>
        </div>
        <div class="map-node dominant" style="top:38%; left:82%;" data-info="Pékin : Entreprises comme Baidu et SenseTime contribuent à ~25% des publications scientifiques en IA.">
          💻 Pékin<br><small>25% Pub.</small>
        </div>
        <div class="map-node emergent" style="top:32%; left:50%;" data-info="Paris-Saclay : Hub européen émergent avec des acteurs tels que Mistral AI et LightOn, soutenu par France 2030.">
          🎓 Paris-Saclay<br><small>Hub Européen</small>
        </div>
        <div class="map-node emergent" style="top:50%; left:68%;" data-info="Tel Aviv : Collaboration entre secteur militaire et civil, avec des acteurs tels qu'AI21 Labs.">
          🏛️ Tel Aviv<br><small>Collab. Mil-Civ</small>
        </div>
      </div>
    </div>
  </div>

  <script>
    // Navigation par onglets
    const tabs = document.querySelectorAll('.tab');
    const sections = document.querySelectorAll('.section');
    tabs.forEach(tab => {
      tab.addEventListener('click', () => {
        tabs.forEach(t => t.classList.remove('active'));
        tab.classList.add('active');
        sections.forEach(section => section.classList.remove('active'));
        const target = tab.getAttribute('data-section');
        document.getElementById(target).classList.add('active');
      });
    });

    // Interaction sur la carte
    document.querySelectorAll('.map-node').forEach(node => {
      node.addEventListener('click', () => {
        alert(node.getAttribute('data-info'));
      });
    });
  </script>

  <!-- Font Awesome pour les icônes (ex: fas fa-brain) -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/js/all.min.js"></script>
</body>
</html>
