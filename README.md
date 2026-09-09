<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>66 Türchen – Formel 1 & andere Wunder</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Titillium+Web:wght@400;600;700;900&family=Barlow:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --bg: #12151b;
    --panel: #1b1f28;
    --panel-hi: #232833;
    --line: #2c3140;
    --red: #e10600;
    --red-dim: #8a0d09;
    --gold: #c9a227;
    --cream: #f1efe9;
    --muted: #8b92a0;
    --radius: 6px;
  }

  *{ box-sizing: border-box; }

  html{ scroll-behavior: smooth; }

  body{
    margin:0;
    background: var(--bg);
    color: var(--cream);
    font-family: 'Barlow', sans-serif;
    font-size: 16px;
    line-height: 1.5;
    -webkit-font-smoothing: antialiased;
  }

  h1, h2, .display{
    font-family: 'Titillium Web', sans-serif;
    font-weight: 900;
    letter-spacing: 0.01em;
  }

  /* ---------- Hero ---------- */

  .hero{
    position: relative;
    overflow: hidden;
    padding: 5.5rem 1.5rem 4rem;
    border-bottom: 1px solid var(--line);
    background:
      radial-gradient(120% 90% at 15% -10%, rgba(225,6,0,0.16), transparent 55%),
      var(--bg);
  }

  .hero-inner{
    max-width: 780px;
    margin: 0 auto;
    position: relative;
    z-index: 2;
  }

  .track-line{
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    opacity: 0.55;
  }

  .track-line path{
    fill: none;
    stroke: var(--red);
    stroke-width: 2;
    stroke-linecap: round;
    stroke-dasharray: 2400;
    stroke-dashoffset: 2400;
    animation: draw 2.6s ease-out forwards 0.2s;
  }

  @keyframes draw{
    to{ stroke-dashoffset: 0; }
  }

  .eyebrow-plain{
    color: var(--gold);
    font-family: 'Barlow', sans-serif;
    font-weight: 600;
    font-size: 1.05rem;
    margin: 0 0 0.6rem;
  }

  .hero h1{
    font-size: clamp(3.2rem, 13vw, 6.5rem);
    line-height: 0.92;
    margin: 0;
    color: var(--cream);
  }

  .hero h1 span{
    display: block;
    color: var(--red);
    font-size: clamp(1.4rem, 4.5vw, 2.1rem);
    margin-top: 0.6rem;
  }

  .hero p{
    max-width: 46ch;
    margin: 1.6rem 0 0;
    color: var(--muted);
    font-size: 1.08rem;
  }

  .progress{
    margin-top: 2.4rem;
    max-width: 340px;
  }

  .progress-label{
    display:flex;
    justify-content: space-between;
    font-size: 0.92rem;
    color: var(--muted);
    margin-bottom: 0.4rem;
  }

  .progress-track{
    height: 6px;
    background: var(--panel);
    border-radius: 3px;
    overflow: hidden;
    border: 1px solid var(--line);
  }

  .progress-fill{
    height: 100%;
    width: 0%;
    background: linear-gradient(90deg, var(--red), var(--gold));
    transition: width 0.5s ease;
  }

  /* ---------- Grid ---------- */

  .grid-section{
    max-width: 980px;
    margin: 0 auto;
    padding: 3.2rem 1.5rem 5rem;
  }

  .grid{
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(76px, 1fr));
    gap: 10px;
  }

  .door{
    position: relative;
    aspect-ratio: 1 / 1;
    background: var(--panel);
    border: 1px solid var(--line);
    border-radius: var(--radius);
    color: var(--cream);
    font-family: 'Titillium Web', sans-serif;
    font-weight: 700;
    font-size: 1.25rem;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: background 0.15s ease, border-color 0.15s ease, transform 0.1s ease;
  }

  .door:hover{
    background: var(--panel-hi);
    border-color: var(--red);
    transform: translateY(-2px);
  }

  .door:focus-visible{
    outline: 2px solid var(--gold);
    outline-offset: 2px;
  }

  .door.opened{
    background: var(--panel);
    border-color: var(--gold);
    color: var(--gold);
  }

  .door.opened::after{
    content: "";
    position: absolute;
    inset: 4px;
    border-radius: 3px;
    background-image: repeating-conic-gradient(var(--line) 0% 25%, transparent 0% 50%);
    background-size: 8px 8px;
    opacity: 0.35;
    z-index: 0;
  }

  .door span{
    position: relative;
    z-index: 1;
  }

  /* ---------- Modal ---------- */

  .overlay{
    position: fixed;
    inset: 0;
    background: rgba(10, 11, 14, 0.82);
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 1.5rem;
    z-index: 50;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.2s ease;
  }

  .overlay.active{
    opacity: 1;
    pointer-events: auto;
  }

  .modal{
    width: 100%;
    max-width: 460px;
    background: var(--panel);
    border: 1px solid var(--line);
    border-top: 3px solid var(--red);
    border-radius: var(--radius);
    padding: 2.2rem 1.9rem 1.9rem;
    position: relative;
    transform: translateY(14px);
    transition: transform 0.2s ease;
  }

  .overlay.active .modal{
    transform: translateY(0);
  }

  .modal-num{
    font-family: 'Titillium Web', sans-serif;
    font-weight: 900;
    font-size: 0.95rem;
    color: var(--gold);
    margin: 0 0 0.9rem;
  }

  .modal-cat{
    display: inline-block;
    font-size: 0.78rem;
    font-weight: 600;
    color: var(--muted);
    margin-left: 0.6rem;
  }

  .modal p{
    font-size: 1.22rem;
    line-height: 1.5;
    margin: 0;
    color: var(--cream);
  }

  .modal-close{
    position: absolute;
    top: 0.9rem;
    right: 0.9rem;
    background: none;
    border: none;
    color: var(--muted);
    font-size: 1.4rem;
    line-height: 1;
    cursor: pointer;
    padding: 0.4rem;
  }

  .modal-close:hover{ color: var(--cream); }

  /* ---------- Footer ---------- */

  footer{
    text-align: center;
    padding: 2rem 1.5rem 3rem;
    color: var(--muted);
    font-size: 0.9rem;
  }

  @media (prefers-reduced-motion: reduce){
    .track-line path{ animation: none; stroke-dashoffset: 0; }
    html{ scroll-behavior: auto; }
    .door, .overlay, .modal, .progress-fill{ transition: none; }
  }

  @media (max-width: 480px){
    .hero{ padding: 4rem 1.2rem 3rem; }
    .grid{ grid-template-columns: repeat(auto-fill, minmax(58px, 1fr)); gap: 8px; }
    .door{ font-size: 1.05rem; }
  }
</style>
</head>
<body>

<header class="hero">
  <svg class="track-line" viewBox="0 0 800 400" preserveAspectRatio="none" aria-hidden="true">
    <path d="M -20 320 C 120 380, 180 200, 300 220 S 420 340, 520 260 S 620 60, 760 120 S 860 260, 900 200" />
  </svg>
  <div class="hero-inner">
    <p class="eyebrow-plain">Für den besten Papa im Fahrerlager</p>
    <h1>66<span>Türchen voller Fun Facts – Formel 1 und alles, was sonst noch überrascht</span></h1>
    <p>Jedes Türchen versteckt eine kleine Wahrheit: mal von der Rennstrecke, mal aus der ganzen weiten Welt. Kein Advent, keine Reihenfolge – einfach öffnen, was dich reizt.</p>
    <div class="progress">
      <div class="progress-label">
        <span>Geöffnete Türchen</span>
        <span id="progressText">0 / 66</span>
      </div>
      <div class="progress-track">
        <div class="progress-fill" id="progressFill"></div>
      </div>
    </div>
  </div>
</header>

<main class="grid-section">
  <div class="grid" id="grid"></div>
</main>

<div class="overlay" id="overlay">
  <div class="modal" role="dialog" aria-modal="true" aria-labelledby="modalNum">
    <button class="modal-close" id="modalClose" aria-label="Schließen">×</button>
    <p class="modal-num" id="modalNum">Türchen 00 <span class="modal-cat" id="modalCat"></span></p>
    <p id="modalFact"></p>
  </div>
</div>

<footer>Handverlesen zusammengestellt – 66 Türchen, ein Boxenstopp Freude.</footer>

<script>
  const facts = [
    { cat: "Formel 1", text: "Die Formel-1-Weltmeisterschaft wurde 1950 ins Leben gerufen, das erste Rennen fand in Silverstone statt." },
    { cat: "Formel 1", text: "Giuseppe Farina wurde 1950 der allererste Formel-1-Weltmeister der Geschichte." },
    { cat: "Formel 1", text: "Monaco ist mit rund 3,3 Kilometern die kürzeste Strecke im Kalender." },
    { cat: "Formel 1", text: "Der Circuit de Spa-Francorchamps in Belgien gilt wegen seiner Höhenunterschiede als eine der anspruchsvollsten Strecken der Welt." },
    { cat: "Formel 1", text: "Ayrton Senna gewann den Grand Prix von Monaco sechsmal – bis heute unerreicht." },
    { cat: "Formel 1", text: "Der Halo-Kopfschutz wurde 2018 eingeführt und hat seither mehrfach Leben von Fahrern gerettet." },
    { cat: "Formel 1", text: "Ein Formel-1-Auto bremst schneller, als es beschleunigt: von 100 auf 0 km/h braucht es unter 2 Sekunden." },
    { cat: "Formel 1", text: "Die Reifen eines F1-Autos erreichen im Renneinsatz oft Temperaturen von über 100 Grad Celsius." },
    { cat: "Formel 1", text: "DRS (Drag Reduction System) wurde 2011 eingeführt, um Überholmanöver zu erleichtern." },
    { cat: "Formel 1", text: "Das Mindestgewicht eines Formel-1-Autos inklusive Fahrer liegt bei über 800 Kilogramm." },
    { cat: "Formel 1", text: "Michael Schumacher bestritt sein Formel-1-Debüt 1991 für das Team Jordan." },
    { cat: "Formel 1", text: "Die Nürburgring-Nordschleife war einst Teil des F1-Kalenders, bevor sie 1976 als zu gefährlich galt." },
    { cat: "Formel 1", text: "Juan Manuel Fangio gewann seine fünf Weltmeistertitel für vier verschiedene Teams – ein bis heute einzigartiger Rekord." },
    { cat: "Formel 1", text: "Ein moderner Boxenstopp-Crew besteht aus über 20 Personen für einen einzigen Reifenwechsel." },
    { cat: "Formel 1", text: "Die Reifenmischung wird farblich markiert: Weiß steht für Hart, Gelb für Medium, Rot für Weich." },
    { cat: "Formel 1", text: "Ein Formel-1-Lenkrad hat über 20 Knöpfe und Schalter und kostet mehr als so mancher Kleinwagen." },
    { cat: "Formel 1", text: "In schnellen Kurven wirken auf die Fahrer G-Kräfte von bis zu 6G – das Sechsfache des eigenen Körpergewichts." },
    { cat: "Formel 1", text: "Monaco wird traditionell am Sonntagnachmittag gefahren – anders als etwa der Nachtgrandprix in Singapur." },
    { cat: "Formel 1", text: "Singapur war 2008 der erste Nachtrennen-Grand-Prix der Formel-1-Geschichte." },
    { cat: "Formel 1", text: "Das KERS (Kinetic Energy Recovery System) war ein früher Vorläufer der heutigen Hybridantriebe." },
    { cat: "Formel 1", text: "Seit 2014 fahren Formel-1-Autos mit turbogeladenen V6-Hybridmotoren statt der früheren V8-Saugmotoren." },
    { cat: "Formel 1", text: "Der Grand Prix von Italien in Monza gehört seit 1950 fast ununterbrochen zum Kalender." },
    { cat: "Formel 1", text: "2021 führte die Formel 1 eine Kostenobergrenze (Budget Cap) für die Teams ein." },
    { cat: "Formel 1", text: "Sprintrennen wurden 2021 erstmals eingeführt, um zusätzliche Spannung an Rennwochenenden zu schaffen." },
    { cat: "Formel 1", text: "Lella Lombardi ist bis heute die einzige Frau, die in der Formel-1-Weltmeisterschaft Punkte holte." },
    { cat: "Formel 1", text: "Die Startaufstellung wird im Qualifying über drei Runden ermittelt: Q1, Q2 und Q3." },
    { cat: "Formel 1", text: "Sebastian Vettel wurde 2010 im Alter von 23 Jahren der bis dahin jüngste Formel-1-Weltmeister." },
    { cat: "Formel 1", text: "Juan Manuel Fangio war mit 46 Jahren der bislang älteste Fahrer, der einen WM-Titel gewann." },
    { cat: "Formel 1", text: "Der Grand Prix von Großbritannien 1950 war das allererste offizielle Rennen der WM-Geschichte." },
    { cat: "Formel 1", text: "Formel-1-Motoren drehen bis über 15.000 Umdrehungen pro Minute." },
    { cat: "Formel 1", text: "Ferrari ist das einzige Team, das seit Beginn der Weltmeisterschaft 1950 ununterbrochen dabei ist." },
    { cat: "Formel 1", text: "Die Strecke in Baku, Aserbaidschan, hat mit über 2 Kilometern die längste Gerade im Kalender." },
    { cat: "Formel 1", text: "Ein klassisches Formel-1-Rennwochenende besteht aus freiem Training, Qualifying und dem Hauptrennen am Sonntag." },
    { cat: "Formel 1", text: "Die Safety Cars der Formel 1 stammen meist von Mercedes-AMG oder Aston Martin." },
    { cat: "Formel 1", text: "Der Begriff „Pole Position“ bezeichnet den ersten Startplatz, benannt nach der Innenseite („Pol“) der Bahn." },
    { cat: "Formel 1", text: "Formel-1-Bremsscheiben bestehen aus Kohlefaser und können über 1.000 Grad Celsius heiß werden." },
    { cat: "Formel 1", text: "Das Punktesystem der Formel 1 wurde im Laufe der Geschichte mehrfach verändert – heute gibt es Punkte bis Platz 10." },
    { cat: "Formel 1", text: "Niki Lauda überlebte 1976 einen schweren Feuerunfall am Nürburgring und kehrte wenige Wochen später zurück ins Cockpit." },
    { cat: "Formel 1", text: "Der Grand Prix von Las Vegas fand 2023 nach jahrzehntelanger Pause erstmals wieder statt." },
    { cat: "Formel 1", text: "Formel-1-Teams simulieren Rennstrategien oft tausende Male am Computer, bevor sie eine Entscheidung treffen." },
    { cat: "Wusstest du?", text: "Honig verdirbt praktisch nie – in ägyptischen Gräbern wurde Jahrtausende alter, noch genießbarer Honig gefunden." },
    { cat: "Wusstest du?", text: "Oktopusse haben drei Herzen und blaues Blut." },
    { cat: "Wusstest du?", text: "Bananen zählen botanisch gesehen zu den Beeren – Erdbeeren dagegen nicht." },
    { cat: "Wusstest du?", text: "Der Eiffelturm wird im Sommer durch die Hitze bis zu 15 Zentimeter höher." },
    { cat: "Wusstest du?", text: "Ein Tag auf der Venus dauert länger als ein Jahr auf der Venus." },
    { cat: "Wusstest du?", text: "Wombats haben würfelförmigen Kot – vermutlich, damit er nicht wegrollt." },
    { cat: "Wusstest du?", text: "Der Mount Everest wächst durch tektonische Bewegungen jedes Jahr ein kleines Stück weiter." },
    { cat: "Wusstest du?", text: "Menschen teilen erstaunlich viel ihrer DNA mit Bananen – ein Erbe der gemeinsamen Evolution." },
    { cat: "Wusstest du?", text: "Der längste Non-Stop-Passagierflug der Welt dauert über 18 Stunden." },
    { cat: "Wusstest du?", text: "Ein Blitz ist etwa fünfmal heißer als die Oberfläche der Sonne." },
    { cat: "Wusstest du?", text: "Delfine geben sich gegenseitig individuelle „Namen“ in Form charakteristischer Pfeiflaute." },
    { cat: "Wusstest du?", text: "Die Sahara war vor rund 10.000 Jahren eine grüne, fruchtbare Landschaft." },
    { cat: "Wusstest du?", text: "Katzen können über 100 verschiedene Laute von sich geben – Hunde nur etwa 10." },
    { cat: "Wusstest du?", text: "Das menschliche Herz schlägt im Laufe eines Lebens rund 2,5 Milliarden Mal." },
    { cat: "Wusstest du?", text: "Der Großteil des Sauerstoffs auf der Erde stammt aus dem Ozean, nicht aus den Wäldern." },
    { cat: "Wusstest du?", text: "Das Great Barrier Reef ist das größte lebende Bauwerk der Welt und sogar aus dem All erkennbar." },
    { cat: "Wusstest du?", text: "Schokolade wurde von den Azteken einst als Zahlungsmittel verwendet." },
    { cat: "Wusstest du?", text: "Ein Kolibri kann seine Flügel bis zu 80 Mal pro Sekunde schlagen." },
    { cat: "Wusstest du?", text: "Grönland gehört geografisch zu Nordamerika, politisch aber zu Dänemark." },
    { cat: "Wusstest du?", text: "Entgegen einem populären Mythos ist die Chinesische Mauer mit bloßem Auge aus dem Weltall nicht sichtbar." },
    { cat: "Wusstest du?", text: "Bienen können einfache Rechenaufgaben wie Addition und Subtraktion lernen." },
    { cat: "Wusstest du?", text: "Ein einziger Blitzeinschlag enthält genug Energie, um einen Toaster tagelang zu betreiben." },
    { cat: "Wusstest du?", text: "Gemessen an der Niederschlagsmenge ist die Antarktis die größte Wüste der Welt." },
    { cat: "Wusstest du?", text: "Der Nasenabdruck von Koalas ist so einzigartig wie ein menschlicher Fingerabdruck." },
    { cat: "Wusstest du?", text: "Am Nordpol gibt es keine Zeitzone, da sich dort alle Längengrade treffen." },
    { cat: "Ziel erreicht", text: "Herzlichen Glückwunsch – du hast alle 66 Türchen geöffnet! Zeit für eine Pause an der Box. 🏁" }
  ];

  const grid = document.getElementById('grid');
  const overlay = document.getElementById('overlay');
  const modalNum = document.getElementById('modalNum');
  const modalCat = document.getElementById('modalCat');
  const modalFact = document.getElementById('modalFact');
  const modalClose = document.getElementById('modalClose');
  const progressFill = document.getElementById('progressFill');
  const progressText = document.getElementById('progressText');

  const STORAGE_KEY = 'tuerchen66-opened';
  let opened = new Set();
  try{
    const saved = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');
    opened = new Set(saved);
  }catch(e){ opened = new Set(); }

  function updateProgress(){
    progressText.textContent = opened.size + ' / 66';
    progressFill.style.width = (opened.size / 66 * 100) + '%';
  }

  function persist(){
    try{ localStorage.setItem(STORAGE_KEY, JSON.stringify([...opened])); }
    catch(e){ /* Speichern nicht möglich, kein Problem */ }
  }

  facts.forEach((fact, i) => {
    const n = i + 1;
    const btn = document.createElement('button');
    btn.className = 'door' + (opened.has(n) ? ' opened' : '');
    btn.setAttribute('data-n', n);
    btn.setAttribute('aria-label', 'Türchen ' + n + (opened.has(n) ? ' (bereits geöffnet)' : ''));
    btn.innerHTML = '<span>' + n + '</span>';
    btn.addEventListener('click', () => openDoor(n, btn));
    grid.appendChild(btn);
  });

  updateProgress();

  function openDoor(n, btn){
    const fact = facts[n - 1];
    modalNum.childNodes[0].nodeValue = 'Türchen ' + String(n).padStart(2, '0') + ' ';
    modalCat.textContent = fact.cat;
    modalFact.textContent = fact.text;
    overlay.classList.add('active');

    if(!opened.has(n)){
      opened.add(n);
      btn.classList.add('opened');
      btn.setAttribute('aria-label', 'Türchen ' + n + ' (bereits geöffnet)');
      updateProgress();
      persist();
    }
  }

  function closeModal(){
    overlay.classList.remove('active');
  }

  modalClose.addEventListener('click', closeModal);
  overlay.addEventListener('click', (e) => {
    if(e.target === overlay) closeModal();
  });
  document.addEventListener('keydown', (e) => {
    if(e.key === 'Escape') closeModal();
  });
</script>

</body>
</html>
