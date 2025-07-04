# Baby-a-Benzoindex.html
Mrecedes Benz site
<!DOCTYPE html>
<html lang="cs">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mercedes-Benz | Nejprodávanější modely</title>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">
  <style>
    /* Základní styly */
    :root {
      --mb-silver: #e5e5e5;
      --mb-black: #000000;
      --mb-blue: #00A1E4;
      --mb-red: #E30613;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Montserrat', sans-serif;
      background-color: var(--mb-black);
      color: var(--mb-silver);
      overflow-x: hidden;
      line-height: 1.6;
    }

    /* Hlavička */
    header {
      background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)),
        url('https://www.mercedes-benz.cz/passengercars/_jcr_content/root/chapterimage_stage_fullwidth/chapterimage_1254291852/image.component.damq1.3368341892416.jpg/mercedes-benz-vehicles-suv-gle-coupe-x167-stage-3400x1440-09-2020.jpg');
      background-size: cover;
      background-position: center;
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 0 2rem;
      position: relative;
    }

    .logo {
      width: 300px;
      margin-bottom: 2rem;
      animation: fadeIn 2s ease-in-out;
      cursor: pointer;
      transition: transform 0.3s ease;
    }

    .logo:hover {
      transform: scale(1.05);
    }

    h1 {
      font-family: 'Playfair+Display', serif;
      font-size: 4rem;
      margin-bottom: 1rem;
      color: var(--mb-silver);
      text-shadow: 0 0 10px rgba(0, 161, 228, 0.5);
      cursor: pointer;
      transition: color 0.3s ease;
    }

    h1:hover {
      color: var(--mb-blue);
    }

    .subtitle {
      font-size: 1.5rem;
      max-width: 800px;
      margin-bottom: 2rem;
      cursor: pointer;
      transition: transform 0.3s ease;
    }

    .subtitle:hover {
      transform: translateY(5px);
    }

    .scroll-down {
      position: absolute;
      bottom: 30px;
      left: 50%;
      transform: translateX(-50%);
      color: var(--mb-silver);
      font-size: 2rem;
      animation: bounce 2s infinite;
      cursor: pointer;
      transition: color 0.3s ease;
    }

    .scroll-down:hover {
      color: var(--mb-blue);
    }

    /* Sekce nejprodávanějších modelů */
    .best-sellers {
      max-width: 1200px;
      margin: 5rem auto;
      padding: 0 2rem;
    }

    .section-title {
      font-family: 'Playfair+Display', serif;
      font-size: 3rem;
      text-align: center;
      margin-bottom: 3rem;
      color: var(--mb-blue);
      position: relative;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    .section-title:hover {
      text-shadow: 0 0 15px rgba(0, 161, 228, 0.7);
    }

    .section-title::after {
      content: '';
      display: block;
      width: 100px;
      height: 4px;
      background: var(--mb-red);
      margin: 1rem auto;
    }

    .models-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
      gap: 2rem;
    }

    .model-card {
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(10px);
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
      transition: all 0.3s ease;
      opacity: 0;
      transform: translateY(50px);
      cursor: pointer;
    }

    .model-card.visible {
      opacity: 1;
      transform: translateY(0);
    }

    .model-card:hover {
      transform: translateY(-10px);
      box-shadow: 0 15px 35px rgba(0, 161, 228, 0.2);
    }

    .model-image {
      width: 100%;
      height: 190px;
      object-fit: cover;
      transition: transform 0.5s ease;
    }

    .model-card:hover .model-image {
      transform: scale(1.05);
    }

    .model-info {
      padding: 1.5rem;
    }

    .model-name {
      font-size: 1.5rem;
      font-weight: bold;
      margin-bottom: 0.5rem;
      color: white;
      transition: color 0.3s ease;
    }

    .model-card:hover .model-name {
      color: var(--mb-blue);
    }

    .model-sales {
      font-size: 1.1rem;
      color: var(--mb-blue);
      margin-bottom: 1rem;
    }

    .model-years {
      font-style: italic;
      margin-bottom: 1rem;
    }

    .model-description {
      margin-bottom: 1.5rem;
    }

    .model-stats {
      display: flex;
      justify-content: space-between;
      margin-top: 1rem;
      padding-top: 1rem;
      border-top: 1px solid rgba(255, 255, 255, 0.2);
    }

    .stat-item {
      text-align: center;
    }

    .stat-value {
      font-size: 1.3rem;
      font-weight: bold;
      color: var(--mb-blue);
    }

    .stat-label {
      font-size: 0.8rem;
      opacity: 0.8;
    }

    /* Milníky prodeje */
    .sales-milestones {
      max-width: 1200px;
      margin: 5rem auto;
      padding: 0 2rem;
    }

    .milestone {
      display: flex;
      align-items: center;
      margin-bottom: 3rem;
      opacity: 0;
      transform: translateX(-50px);
      transition: all 1s ease;
      cursor: pointer;
    }

    .milestone.visible {
      opacity: 1;
      transform: translateX(0);
    }

    .milestone:nth-child(even) {
      flex-direction: row-reverse;
      transform: translateX(50px);
    }

    .milestone:nth-child(even).visible {
      transform: translateX(0);
    }

    .milestone-image {
      width: 50%;
      border-radius: 10px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
      transition: transform 0.5s ease;
    }

    .milestone:hover .milestone-image {
      transform: scale(1.03);
    }

    .milestone-content {
      width: 50%;
      padding: 0 3rem;
    }

    .milestone-year {
      font-size: 2rem;
      font-weight: bold;
      color: var(--mb-blue);
      margin-bottom: 1rem;
      transition: color 0.3s ease;
    }

    .milestone:hover .milestone-year {
      color: var(--mb-red);
    }

    .milestone-title {
      font-size: 1.5rem;
      font-weight: bold;
      margin-bottom: 1rem;
      color: white;
    }

    /* Footer */
    footer {
      background-color: #111;
      padding: 3rem 2rem;
      text-align: center;
    }

    .footer-logo {
      width: 150px;
      margin-bottom: 1rem;
      cursor: pointer;
      transition: transform 0.3s ease;
    }

    .footer-logo:hover {
      transform: scale(1.1);
    }

    .footer-links {
      display: flex;
      justify-content: center;
      gap: 2rem;
      margin-bottom: 1.5rem;
    }

    .footer-link {
      color: var(--mb-silver);
      text-decoration: none;
      transition: color 0.3s;
    }

    .footer-link:hover {
      color: var(--mb-blue);
    }

    /* Animace */
    @keyframes fadeIn {
      from {
        opacity: 0;
      }

      to {
        opacity: 1;
      }
    }

    @keyframes bounce {

      0%,
      20%,
      50%,
      80%,
      100% {
        transform: translateY(0) translateX(-50%);
      }

      40% {
        transform: translateY(-20px) translateX(-50%);
      }

      60% {
        transform: translateY(-10px) translateX(-50%);
      }
    }

    /* Tlačítko zpět nahoru */
    .back-to-top {
      position: fixed;
      bottom: 30px;
      right: 30px;
      background-color: var(--mb-blue);
      color: white;
      width: 50px;
      height: 50px;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      opacity: 0;
      visibility: hidden;
      transition: all 0.3s ease;
      z-index: 1000;
    }

    .back-to-top.visible {
      opacity: 1;
      visibility: visible;
    }

    .back-to-top:hover {
      background-color: var(--mb-red);
      transform: translateY(-5px);
    }

    /* Responsivní design */
    @media (max-width: 768px) {
      h1 {
        font-size: 2.5rem;
      }

      .subtitle {
        font-size: 1.1rem;
      }

      .logo {
        width: 200px;
      }

      .section-title {
        font-size: 2rem;
      }

      .models-grid {
        grid-template-columns: 1fr;
      }

      .milestone,
      .milestone:nth-child(even) {
        flex-direction: column;
        transform: translateX(0);
      }

      .milestone-image,
      .milestone-content {
        width: 100%;
      }

      .milestone-content {
        padding: 1.5rem 0;
      }

      .footer-links {
        flex-direction: column;
        gap: 1rem;
      }

      .back-to-top {
        width: 40px;
        height: 40px;
        bottom: 20px;
        right: 20px;
      }
    }
  </style>
</head>

<body>
  <!-- Tlačítko zpět nahoru -->
  <div class="back-to-top" onclick="scrollToTop()">↑</div>

  <!-- Hlavička -->
  <header>
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/90/Mercedes-Logo.svg/2560px-Mercedes-Logo.svg.png" alt="Mercedes-Benz Logo" class="logo" onclick="scrollToBestSellers()">
    <h1 onclick="scrollToMilestones()">Nejprodávanější modely</h1>
    <p class="subtitle" onclick="scrollToFooter()">Od klasických ikon po moderní bestsellery - objevte vozy, které si získaly srdce milionů zákazníků</p>
    <div class="scroll-down" onclick="scrollToBestSellers()">↓</div>
  </header>

  <!-- Nejprodávanější modely -->
  <section class="best-sellers" id="best-sellers">
    <h2 class="section-title" onclick="scrollToMilestones()">Nejúspěšnější modely v historii</h2>

    <div class="models-grid">
      <div class="model-card" onclick="scrollToMilestones()">
        <img src="https://watchit.cz/wp-content/uploads/21C0053_003.jpg" alt="Mercedes-Benz C-Class" class="model-image">
        <div class="model-info">
          <h3 class="model-name">C-Class</h3>
          <div class="model-sales">10+ milionů prodaných kusů</div>
          <div class="model-years">1993 - současnost</div>
          <p class="model-description">Střední třída, která definovala segment prémiových sedanů. Nejprodávanější model v historii Mercedes-Benz.</p>
          <div class="model-stats">
            <div class="stat-item">
              <div class="stat-value">7</div>
              <div class="stat-label">generací</div>
            </div>
            <div class="stat-item">
              <div class="stat-value">120+</div>
              <div class="stat-label">trhů</div>
            </div>
            <div class="stat-item">
              <div class="stat-value">#1</div>
              <div class="stat-label">v Evropě</div>
            </div>
          </div>
        </div>
      </div>

      <div class="model-card" onclick="scrollToMilestones()">
        <img src="https://cdn.svolavacky.cz/wp-content/uploads/2024/03/Mercedes-Benz-E-Class-2021-48v-fire-risk-1024x576.jpg.avif" alt="Mercedes-Benz E-Class" class="model-image">
        <div class="model-info">
          <h3 class="model-name">E-Class</h3>
          <div class="model-sales">14+ milionů prodaných kusů</div>
          <div class="model-years">1953 - současnost</div>
          <p class="model-description">Vůz vyšší střední třídy, který kombinuje luxus, technologii a výkon. Oblíbený mezi podnikateli i rodinami.</p>
          <div class="model-stats">
            <div class="stat-item">
              <div class="stat-value">10</div>
              <div class="stat-label">generací</div>
            </div>
            <div class="stat-item">
              <div class="stat-value">60%</div>
              <div class="stat-label">firemních flotil</div>
            </div>
            <div class="stat-item">
              <div class="stat-value">#1</div>
              <div class="stat-label">v USA</div>
            </div>
          </div>
        </div>
      </div>

      <div class="model-card" onclick="scrollToMilestones()">
        <img src="https://bluesky-cogcms-prodb.cdn.imgeng.in/media/ssxan3ur/a-class-hatchback-amg-side.png?width=1200&scale=both" alt="Mercedes-Benz A-Class" class="model-image">
        <div class="model-info">
          <h3 class="model-name">A-Class</h3>
          <div class="model-sales">7+ milionů prodaných kusů</div>
          <div class="model-years">1997 - současnost</div>
          <p class="model-description">První kompaktní vůz Mercedes-Benz, který přivedl mladší zákazníky k značce. Revoluce v designu a technologiích.</p>
          <div class="model-stats">
            <div class="stat-item">
              <div class="stat-value">4</div>
              <div class="stat-label">generací</div>
            </div>
            <div class="stat-item">
              <div class="stat-value">35%</div>
              <div class="stat-label">nových zákazníků</div>
            </div>
            <div class="stat-item">
              <div class="stat-value">#1</div>
              <div class="stat-label">v Asii</div>
            </div>
          </div>
        </div>
      </div>

      <div class="model-card" onclick="scrollToMilestones()">
        <img src="https://www.autoibuy.com/user/documents/upload/Roman%202022/BMW%202023/X7%20web/23C0097_005_0.jpg" alt="Mercedes-Benz GLA" class="model-image">
        <div class="model-info">
          <h3 class="model-name">GLA</h3>
          <div class="model-sales">2+ milionů prodaných kusů</div>
          <div class="model-years">2013 - současnost</div>
          <p class="model-description">Kompaktní SUV, které dokonale zachycuje současné trendy. Nejrychleji rostoucí model v nabídce.</p>
          <div class="model-stats">
            <div class="stat-item">
              <div class="stat-value">2</div>
              <div class="stat-label">generací</div>
            </div>
            <div class="stat-item">
              <div class="stat-value">80%</div>
              <div class="stat-label">nových modelů</div>
            </div>
            <div class="stat-item">
              <div class="stat-value">#1</div>
              <div class="stat-label">v Číně</div>
            </div>
          </div>
        </div>
      </div>

      <div class="model-card" onclick="scrollToMilestones()">
        <img src="https://www.motortrend.com/files/662a7f23b9b4860008e14a0b/001-2024-mercedes-maybach-s680.jpg" alt="Mercedes-Benz S-Class" class="model-image">
        <div class="model-info">
          <h3 class="model-name">S-Class</h3>
          <div class="model-sales">4+ milionů prodaných kusů</div>
          <div class="model-years">1972 - současnost</div>
          <p class="model-description">Vlajková loď Mercedes-Benz, která vždy představovala špičku automobilových technologií a luxusu.</p>
          <div class="model-stats">
            <div class="stat-item">
              <div class="stat-value">7</div>
              <div class="stat-label">generací</div>
            </div>
            <div class="stat-item">
              <div class="stat-value">90%</div>
              <div class="stat-label">nových technologií</div>
            </div>
            <div class="stat-item">
              <div class="stat-value">#1</div>
              <div class="stat-label">luxusní sedan</div>
            </div>
          </div>
        </div>
      </div>

      <div class="model-card" onclick="scrollToMilestones()">
        <img src="https://d15-a.sdn.cz/d_15/c_img_QI_v/C39gN/mercedes-benz-glc-coupe-glc.jpeg?fl=cro,0,0,4961,3309%7Cres,2560,,1%7Cwebp,75" alt="Mercedes-Benz GLC" class="model-image">
        <div class="model-info">
          <h3 class="model-name">GLC</h3>
          <div class="model-sales">2.5+ milionů prodaných kusů</div>
          <div class="model-years">2015 - současnost</div>
          <p class="model-description">Středně velké SUV, které kombinuje praktičnost, eleganci a výkon. Ideální pro moderní rodiny.</p>
          <div class="model-stats">
            <div class="stat-item">
              <div class="stat-value">2</div>
              <div class="stat-label">generací</div>
            </div>
            <div class="stat-item">
              <div class="stat-value">70%</div>
              <div class="stat-label">ženských zákazníků</div>
            </div>
            <div class="stat-item">
              <div class="stat-value">#2</div>
              <div class="stat-label">v segmentu</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Milníky prodeje -->
  <section class="sales-milestones" id="milestones">
    <h2 class="section-title" onclick="scrollToMilestones()">Historické milníky prodejů</h2>

    <div class="milestone" onclick="scrollToFooter()">
      <img src="https://cdn.rmsothebys.com/2/5/1/8/8/8/2518881ade5f098b504ee93fe87d87d694f3c0af.webp" alt="1 milion prodaných vozů" class="milestone-image">
      <div class="milestone-content">
        <div class="milestone-year">1954</div>
        <h3 class="milestone-title">První milion prodaných vozů</h3>
        <p>Mercedes-Benz dosáhl milníku 1 milionu prodaných vozů, přičemž model 170 V byl jedním z nejpopulárnějších poválečných vozů.</p>
      </div>
    </div>

    <div class="milestone" onclick="scrollToFooter()">
      <img src="https://automanager.blob.core.windows.net/wmphotos/028910/996ed093d1fd476592f89b0672cc0574/0990f57154_1280.jpg" alt="10 milionů prodaných vozů" class="milestone-image">
      <div class="milestone-content">
        <div class="milestone-year">1978</div>
        <h3 class="milestone-title">10 milionů vozů na silnicích</h3>
        <p>Díky úspěchu modelů jako W114/W115 "Stroke Eight" dosáhl Mercedes-Benz 10 milionů prodaných vozů.</p>
      </div>
    </div>

    <div class="milestone" onclick="scrollToFooter()">
      <img src="https://cdn.svolavacky.cz/wp-content/uploads/2024/03/Mercedes-Benz-E-Class-sunroof-glass-1024x577.jpg.avif" alt="30 milionů prodaných vozů" class="milestone-image">
      <div class="milestone-content">
        <div class="milestone-year">2000</div>
        <h3 class="milestone-title">30 milionů vozů a expanze modelové řady</h3>
        <p>Zavedením úspěšné C-Class (W202) a dalších modelů Mercedes-Benz překonal hranici 30 milionů prodaných vozů.</p>
      </div>
    </div>

    <div class="milestone" onclick="scrollToFooter()">
      <img src="https://pictures.dealer.com/s/sonicwisimonson/1033/ac3285ddeafa6d8b9b76c144e9df1a26x.jpg" alt="50 milionů prodaných vozů" class="milestone-image">
      <div class="milestone-content">
        <div class="milestone-year">2021</div>
        <h3 class="milestone-title">50 milionů vozů a éra SUV</h3>
        <p>Díky popularitě SUV modelů jako GLC a GLE dosáhl Mercedes-Benz 50 milionů prodaných vozů.</p>
      </div>
    </div>
  </section>
  <!-- Přehled značek AMG, Brabus a Maybach -->
  <section class="brand-overview" id="Brands">
    <h2 class="section-title" onclick="scrollToFooter()">Značky vysokého luxusu a výkonu</h2>

    <!-- AMG -->
    <div class="milestone">
      <img src="https://image-cdn.hypb.st/https%3A%2F%2Fhypebeast.com%2Fimage%2F2016%2F06%2FMercedes-Benz-AMG-GT-R-1.jpg?q=90&w=1400&cbr=1&fit=max" alt="Mercedes-AMG GT" class="milestone-image">
      <div class="milestone-content">
        <h3 class="milestone-title">Mercedes-AMG</h3>
        <p><strong>AMG</strong> je sportovní a výkonnostní divize Mercedes-Benz. Vyrábí modely s důrazem na výkon, řízení a sportovní zvuk. Typickými znaky jsou silné motory, agresivní design a technologie převzaté z motorsportu. Modely jako <em>AMG GT, C 63, E 63</em> nebo <em>AMG One</em> patří mezi nejrychlejší silniční vozy značky.</p>
      </div>
    </div>

    <!-- Brabus -->
    <div class="milestone">
      <img src="https://image-cdn.hypb.st/https%3A%2F%2Fhypebeast.com%2Fimage%2F2020%2F10%2Fbrabus-rocket-900-mercedes-benz-amg-gt-63-s-4matic-plus-one-of-ten-900-bhp-tuned-1.jpg?w=1440&cbr=1&q=90&fit=max" alt="Brabus 900 Rocket" class="milestone-image">
      <div class="milestone-content">
        <h3 class="milestone-title">Brabus</h3>
        <p><strong>Brabus</strong> je nezávislý úpravce vozů Mercedes-Benz sídlící v Německu. Zaměřuje se na extrémní výkonnostní a vizuální úpravy. Brabus přestavuje standardní modely na exkluzivní supersporty s výkony často přesahujícími 800 koní. Typickým příkladem je <em>Brabus Rocket 900</em> nebo upravená třída G s brutálním vzhledem i zvukem.</p>
      </div>
    </div>

    <!-- Maybach -->
    <div class="milestone">
      <img src="https://hips.hearstapps.com/hmg-prod/images/2025-mercedes-maybach-103-66fac5ea8d508.jpg?crop=0.798xw:0.673xh;0.184xw,0.264xh&resize=2048:*" alt="Mercedes-Maybach" class="milestone-image">
      <div class="milestone-content">
        <h3 class="milestone-title">Mercedes-Maybach</h3>
        <p><strong>Maybach</strong> je synonymem pro nejvyšší luxus, komfort a exkluzivitu v rámci Mercedesu. Jedná se o prémiovou řadu založenou na modelech jako S-Class, která je rozšířena o prvotřídní interiér, delší rozvor, tišší kabinu a luxusní výbavu. Zákazníky jsou často hlavy států, diplomaté nebo klienti vyžadující maximální pohodlí.</p>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer id="footer">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/90/Mercedes-Logo.svg/2560px-Mercedes-Logo.svg.png" alt="Mercedes-Benz Logo" class="footer-logo" onclick="scrollToTop()">
    <div class="footer-links">
      <a href="index.html" class="footer-link">Historie</a>
      <a href="best-sellers.html" class="footer-link">Nejprodávanější modely</a>
      <a href="https://www.mercedes-benz.com" class="footer-link">Oficiální stránky</a>
    </div>
    <p>© 2025 Mercedes-Benz. Všechna práva vyhrazena.</p>
  </footer>

  <script>
    // Scroll na sekci nejprodávanějších modelů
    function scrollToBestSellers() {
      document.getElementById('best-sellers').scrollIntoView({
        behavior: 'smooth'
      });
    }
    // Scroll na sekci milníků
    function scrollToMilestones() {
      document.getElementById('milestones').scrollIntoView({
        behavior: 'smooth'
      });
    }
    // Scroll na sekci značek
    function scrollToMilestones() {
      document.getElementById('Brands').scrollIntoView({
        behavior: 'smooth'
      });
    }
    // Scroll na footer
    function scrollToFooter() {
      document.getElementById('footer').scrollIntoView({
        behavior: 'smooth'
      });
    }
    // Scroll nahoru
    function scrollToTop() {
      window.scrollTo({
        top: 0,
        behavior: 'smooth'
      });
    }
    // Animace karet modelů
    const modelCards = document.querySelectorAll('.model-card');
    const milestones = document.querySelectorAll('.milestone');

    function checkVisibility() {
      modelCards.forEach((card, index) => {
        const cardTop = card.getBoundingClientRect().top;
        if (cardTop < window.innerHeight * 0.8) {
          setTimeout(() => {
            card.classList.add('visible');
          }, index * 200);
        }
      });
      milestones.forEach(milestone => {
        const milestoneTop = milestone.getBoundingClientRect().top;
        if (milestoneTop < window.innerHeight * 0.8) {
          milestone.classList.add('visible');
        }
      });
      // Zobrazit/skrýt tlačítko zpět nahoru
      const backToTop = document.querySelector('.back-to-top');
      if (window.pageYOffset > 300) {
        backToTop.classList.add('visible');
      } else {
        backToTop.classList.remove('visible');
      }
    }
    window.addEventListener('scroll', checkVisibility);
    window.addEventListener('load', checkVisibility);
    // Dynamické načítání obrázků pro lepší výkon
    document.addEventListener("DOMContentLoaded", function() {
      const lazyImages = [].slice.call(document.querySelectorAll("img.lazy"));
      if ("IntersectionObserver" in window) {
        let lazyImageObserver = new IntersectionObserver(function(entries, observer) {
          entries.forEach(function(entry) {
            if (entry.isIntersecting) {
              let lazyImage = entry.target;
              lazyImage.src = lazyImage.dataset.src;
              lazyImage.classList.remove("lazy");
              lazyImageObserver.unobserve(lazyImage);
            }
          });
        });
        lazyImages.forEach(function(lazyImage) {
          lazyImageObserver.observe(lazyImage);
        });
      }
    });
    // Přidání posluchačů událostí pro interaktivitu
    document.querySelectorAll('.model-card, .milestone, .section-title, .logo, h1, .subtitle').forEach(element => {
      element.style.cursor = 'pointer';
      element.addEventListener('click', function() {
        this.style.transform = 'scale(0.98)';
        setTimeout(() => {
          this.style.transform = '';
        }, 200);
      });
    });
  </script>
</body>

</html>
