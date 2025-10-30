# EcoLive
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Eco & Environment Quiz</title>
<style>
  :root{
    --bg1: #0f1724; /* deep navy */
    --bg2: #0b1020; /* near-black */
    --accent1: #00f5a0; /* neon green */
    --accent2: #7b61ff; /* neon purple */
    --accent3: #00d4ff; /* neon cyan */
    --card: rgba(255,255,255,0.04);
    --glass: rgba(255,255,255,0.06);
    --glass-2: rgba(255,255,255,0.02);
    --text: #e6f5f3;
    --muted: #94a3b8;
    --success: #6ef0a1;
    --danger: #ff6b6b;
    font-family: Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
  }

  html,body{height:100%;}
  body{
    margin:0;
    background: linear-gradient(135deg,var(--bg1), var(--bg2));
    color:var(--text);
    -webkit-font-smoothing:antialiased;
    -moz-osx-font-smoothing:grayscale;
    display:flex;
    align-items:center;
    justify-content:center;
    min-height:100vh;
  }

  /* full-bleed app container */
  .app {
    width:100vw;
    height:100vh;
    display:grid;
    grid-template-columns: 1fr;
    grid-template-rows: auto 1fr auto;
    gap:20px;
    padding:28px;
    box-sizing:border-box;
    background:
      radial-gradient(800px 400px at 10% 10%, rgba(123,97,255,0.08), transparent 8%),
      radial-gradient(600px 300px at 90% 90%, rgba(0,212,255,0.05), transparent 12%),
      linear-gradient(180deg, rgba(255,255,255,0.02), transparent 15%);
  }

  header{
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:16px;
  }

  .brand{
    display:flex;
    align-items:center;
    gap:14px;
  }

  .logo {
    width:56px;
    height:56px;
    border-radius:12px;
    background: linear-gradient(135deg, var(--accent2), var(--accent3));
    display:flex;
    align-items:center;
    justify-content:center;
    font-weight:700;
    color:#021025;
    box-shadow: 0 8px 30px rgba(0,0,0,0.6), 0 0 20px rgba(123,97,255,0.12);
    transform:rotate(-10deg);
  }

  .title{
    font-size:20px;
    font-weight:700;
    letter-spacing:0.2px;
  }
  .subtitle{
    color:var(--muted);
    font-size:12px;
    margin-top:2px;
  }

  .controls{
    display:flex;
    gap:10px;
    align-items:center;
  }

  .btn {
    background: linear-gradient(90deg,var(--accent1), var(--accent3));
    color:#021025;
    border:none;
    padding:10px 14px;
    border-radius:10px;
    font-weight:600;
    cursor:pointer;
    box-shadow: 0 6px 18px rgba(0,0,0,0.45);
    transition:transform .15s ease, opacity .15s ease;
  }
  .btn.secondary{
    background: transparent;
    border:1px solid rgba(255,255,255,0.06);
    color:var(--text);
    padding:8px 12px;
    font-weight:600;
    box-shadow:none;
  }
  .btn:active{ transform:translateY(1px) scale(.997); }
  .btn:disabled{ opacity:.5; cursor:not-allowed; transform:none; }

  main{
    display:flex;
    gap:22px;
    align-items:stretch;
    width:100%;
  }

  /* left: question card */
  .card {
    flex:1.3;
    background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
    border-radius:18px;
    padding:28px;
    min-height:380px;
    box-shadow: 0 10px 40px rgba(2,8,23,0.6);
    border:1px solid var(--glass-2);
    display:flex;
    flex-direction:column;
    justify-content:space-between;
  }

  .question-head{
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:12px;
  }
  .q-index{
    background: linear-gradient(90deg,var(--accent3),var(--accent2));
    color:#021025;
    padding:8px 12px;
    border-radius:999px;
    font-weight:700;
    box-shadow: 0 8px 20px rgba(0,0,0,0.45);
  }
  .progress-wrap{
    flex:1;
    margin-left:12px;
  }
  .progress{
    height:12px;
    width:100%;
    background:linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
    border-radius:999px;
    overflow:hidden;
    border:1px solid rgba(255,255,255,0.03);
  }
  .progress > i{
    display:block;
    height:100%;
    width:0%;
    background: linear-gradient(90deg, rgba(0,245,160,0.9), rgba(123,97,255,0.9));
    box-shadow: 0 6px 18px rgba(123,97,255,0.12) inset;
    transition: width .45s cubic-bezier(.2,.9,.1,1);
  }

  .question {
    margin-top:18px;
    font-size:20px;
    font-weight:600;
    line-height:1.4;
  }

  .options{
    display:grid;
    gap:12px;
    margin-top:20px;
  }
  .option {
    background: rgba(255,255,255,0.02);
    border:1px solid rgba(255,255,255,0.03);
    padding:14px 16px;
    border-radius:12px;
    cursor:pointer;
    display:flex;
    align-items:center;
    gap:12px;
    transition: transform .12s ease, box-shadow .12s ease, background .12s ease;
    user-select:none;
  }
  .option:hover{ transform:translateY(-4px); box-shadow: 0 10px 30px rgba(2,8,23,0.6); }
  .option .label{
    width:36px;
    height:36px;
    background: linear-gradient(90deg,var(--accent2),var(--accent3));
    border-radius:10px;
    display:flex;
    align-items:center;
    justify-content:center;
    color:#021025;
    font-weight:700;
    flex-shrink:0;
    box-shadow: 0 8px 20px rgba(0,0,0,0.45);
  }
  .option .text{
    color:var(--text);
    font-weight:600;
  }

  .option.correct{
    background: linear-gradient(90deg, rgba(110,240,161,0.12), rgba(110,240,161,0.06));
    border-color: rgba(110,240,161,0.22);
    box-shadow: 0 8px 30px rgba(110,240,161,0.06);
  }
  .option.wrong{
    background: linear-gradient(90deg, rgba(255,107,107,0.08), rgba(255,107,107,0.03));
    border-color: rgba(255,107,107,0.22);
    box-shadow: 0 8px 30px rgba(255,107,107,0.04);
  }

  .actions{
    display:flex;
    align-items:center;
    justify-content:space-between;
    margin-top:18px;
  }
  .hint{
    color:var(--muted);
    font-size:13px;
  }

  /* right: scoreboard & explanations */
  aside {
    width:360px;
    display:flex;
    flex-direction:column;
    gap:18px;
  }
  .panel{
    flex:0 0 auto;
    background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
    padding:18px;
    border-radius:14px;
    border:1px solid var(--glass-2);
    box-shadow: 0 6px 24px rgba(2,8,23,0.5);
  }
  .score-big{
    font-size:36px;
    font-weight:800;
  }
  .meta{
    color:var(--muted);
    font-size:13px;
    margin-top:8px;
  }
  .explain{
    margin-top:10px;
    color:var(--muted);
    font-size:14px;
    line-height:1.5;
  }

  footer{
    display:flex;
    align-items:center;
    justify-content:space-between;
    color:var(--muted);
    font-size:13px;
    margin-top:8px;
  }

  /* responsive */
  @media (max-width:1000px){
    aside{ display:none; }
    .card{ padding:20px; }
    .title{ font-size:18px; }
  }
</style>
</head>
<body>
  <div class="app" role="application" aria-labelledby="appTitle">
    <header>
      <div class="brand">
        <div class="logo">E🌿</div>
        <div>
          <div id="appTitle" class="title">Eco & Environment Quiz</div>
          <div class="subtitle">10 questions • Test your ecological knowledge</div>
        </div>
      </div>

      <div class="controls">
        <button id="restartBtn" class="btn secondary" title="Restart quiz">Restart</button>
        <button id="nextBtn" class="btn" title="Next question">Next</button>
      </div>
    </header>

    <main>
      <section class="card" aria-live="polite">
        <div>
          <div class="question-head">
            <div class="q-index" id="qIndex">1 / 10</div>
            <div class="progress-wrap">
              <div class="progress" aria-hidden="true"><i id="progressBar"></i></div>
            </div>
          </div>

          <div class="question" id="questionText">
            <!-- question here -->
          </div>

          <div class="options" id="options">
            <!-- options -->
          </div>
        </div>

        <div class="actions">
          <div class="hint" id="feedback">Choose an answer to see if you're right.</div>
          <div style="display:flex;gap:10px;align-items:center;">
            <div style="color:var(--muted);font-size:13px;">Score: <strong id="scoreMini">0</strong></div>
          </div>
        </div>
      </section>

      <aside aria-hidden="false">
        <div class="panel">
          <div style="display:flex;justify-content:space-between;align-items:center;">
            <div>
              <div style="font-size:12px;color:var(--muted)">Current Score</div>
              <div class="score-big" id="score">0 / 10</div>
            </div>
            <div style="text-align:right;">
              <div style="font-size:12px;color:var(--muted)">Correct</div>
              <div style="font-weight:800;color:var(--success);font-size:20px" id="correctCount">0</div>
            </div>
          </div>

          <div class="meta" id="meta">Answer a question to get an explanation on the right.</div>
        </div>

        <div class="panel" id="explainPanel" style="min-height:160px;">
          <div style="font-weight:700">Explanation</div>
          <div class="explain" id="explanation">Select an option to see a short explanation.</div>
        </div>

        <div class="panel" style="text-align:center;">
          <div style="font-weight:700;margin-bottom:8px">Finish & Review</div>
          <div style="color:var(--muted);font-size:13px;margin-bottom:12px;">
            When you finish, click "Restart" to try again or review answers by navigating with Next.
          </div>
          <div style="display:flex;gap:10px;justify-content:center">
            <button id="showAnswers" class="btn secondary">Show Answers</button>
            <button id="finishBtn" class="btn">Finish</button>
          </div>
        </div>
      </aside>
    </main>

    <footer>
      <div>Designed with 🌿 • Modern • Flashy</div>
      <div id="footerRight">Good luck!</div>
    </footer>
  </div>

<script>
(function(){
  // Quiz data: 10 ecology/environment questions
  const quiz = [
    {
      q: "What is 'biodiversity'?",
      choices: [
        "The number of species in a specific area",
        "The variety of ecosystems, species, and genes in a region",
        "The number of endangered species worldwide",
        "The process of species evolving over time"
      ],
      a: 1,
      expl: "Biodiversity refers broadly to variation at all levels—ecosystems, species, and genetic diversity—within a region."
    },
    {
      q: "Which gas is considered the main driver of recent human-caused climate change?",
      choices: [
        "Nitrogen (N₂)",
        "Methane (CH₄)",
        "Carbon dioxide (CO₂)",
        "Oxygen (O₂)"
      ],
      a: 2,
      expl: "While methane is potent, CO₂ is the largest contributor to recent global warming due to massive emissions from fossil fuels and land use change."
    },
    {
      q: "Eutrophication of lakes is primarily caused by:",
      choices: [
        "Excess nutrients (e.g., nitrogen, phosphorus) entering water bodies",
        "Overfishing",
        "Volcanic ash",
        "Low oxygen levels due to cold water"
      ],
      a: 0,
      expl: "Runoff from fertilizers and sewage increases nutrient levels, causing algal blooms that deplete oxygen when they decompose."
    },
    {
      q: "Which energy source is renewable?",
      choices: [
        "Coal",
        "Wind",
        "Natural gas",
        "Nuclear (using mined uranium)"
      ],
      a: 1,
      expl: "Wind energy is renewable because it relies on ongoing natural processes, unlike fossil fuels or mined uranium."
    },
    {
      q: "What is an invasive species?",
      choices: [
        "A species native to a region that becomes rare",
        "A species introduced to a new area that causes harm",
        "A species that only lives in water",
        "A domesticated species used in agriculture"
      ],
      a: 1,
      expl: "Invasive species are non-native organisms that spread and cause ecological or economic harm in new environments."
    },
    {
      q: "Which practice best supports soil health and reduces erosion?",
      choices: [
        "Monoculture with frequent tilling",
        "Clear-cutting forests",
        "Cover cropping and reduced tillage",
        "Frequent pesticide spraying"
      ],
      a: 2,
      expl: "Cover crops and reduced tillage protect the soil surface, maintain structure, and reduce erosion and nutrient loss."
    },
    {
      q: "What is 'acid rain' primarily caused by?",
      choices: [
        "CO₂ emissions only",
        "Emissions of sulfur dioxide (SO₂) and nitrogen oxides (NOx)",
        "Excessive use of fertilizers",
        "Volcanic activity only"
      ],
      a: 1,
      expl: "SO₂ and NOx react in the atmosphere to form acidic compounds that fall as acid precipitation, damaging ecosystems and structures."
    },
    {
      q: "Which term describes the total mass of living organisms in an area?",
      choices: [
        "Biomass",
        "Biodiversity",
        "Biotic index",
        "Carrying capacity"
      ],
      a: 0,
      expl: "Biomass is the total weight (mass) of living organisms in a given area or ecosystem at a given time."
    },
    {
      q: "A food chain typically begins with:",
      choices: [
        "Top predators",
        "Primary consumers",
        "Producers (like plants and algae)",
        "Decomposers"
      ],
      a: 2,
      expl: "Producers convert solar energy into biomass and are the base of food chains, supporting consumers above them."
    },
    {
      q: "What does 'sustainable development' aim to achieve?",
      choices: [
        "Unlimited economic growth at all costs",
        "Meeting present needs without compromising future generations",
        "Maximizing short-term profits",
        "Exclusively preserving land without human use"
      ],
      a: 1,
      expl: "Sustainable development balances economic, social, and environmental needs so future generations can meet their needs too."
    }
  ];

  // state
  let current = 0;
  let score = 0;
  let correctCount = 0;
  let answered = Array(quiz.length).fill(null); // store selected index
  const qIndexEl = document.getElementById('qIndex');
  const progressBar = document.getElementById('progressBar');
  const questionText = document.getElementById('questionText');
  const optionsWrap = document.getElementById('options');
  const feedback = document.getElementById('feedback');
  const scoreEl = document.getElementById('score');
  const scoreMini = document.getElementById('scoreMini');
  const correctCountEl = document.getElementById('correctCount');
  const explanationEl = document.getElementById('explanation');
  const metaEl = document.getElementById('meta');
  const nextBtn = document.getElementById('nextBtn');
  const restartBtn = document.getElementById('restartBtn');
  const showAnswersBtn = document.getElementById('showAnswers');
  const finishBtn = document.getElementById('finishBtn');

  function renderQuestion(idx){
    const item = quiz[idx];
    qIndexEl.textContent = (idx+1) + " / " + quiz.length;
    const pct = Math.round(((idx)/quiz.length)*100);
    progressBar.style.width = pct + "%";
    questionText.textContent = item.q;

    // build options
    optionsWrap.innerHTML = '';
    item.choices.forEach((choice, i) => {
      const div = document.createElement('div');
      div.className = 'option';
      div.setAttribute('data-i', i);
      div.setAttribute('role','button');
      div.tabIndex = 0;
      div.innerHTML = `
        <div class="label">${String.fromCharCode(65+i)}</div>
        <div class="text">${choice}</div>
      `;
      // if already answered, show state
      if (answered[idx] !== null) {
        div.classList.add(i === item.a ? 'correct' : (i === answered[idx] ? 'wrong' : ''));
      }
      div.addEventListener('click', onSelect);
      div.addEventListener('keydown', (e)=>{ if(e.key==='Enter' || e.key===' ') onSelect(e); });
      optionsWrap.appendChild(div);
    });

    // update side info
    scoreEl.textContent = score + " / " + quiz.length;
    scoreMini.textContent = score;
    correctCountEl.textContent = correctCount;
    explanationEl.textContent = answered[idx] !== null ? quiz[idx].expl : "Select an option to see a short explanation.";
    metaEl.textContent = answered[idx] !== null ? "You answered this question." : "Answer to receive an explanation.";
    feedback.textContent = answered[idx] !== null ? (answered[idx] === item.a ? "Correct!" : "Incorrect.") : "Choose an answer to see if you're right.";

    // Next button state
    nextBtn.disabled = (idx >= quiz.length - 1);
  }

  function onSelect(e){
    const el = e.currentTarget;
    const idx = Number(el.getAttribute('data-i'));
    if(answered[current] !== null) return; // prevent re-answering

    answered[current] = idx;
    const correct = quiz[current].a;
    const opts = optionsWrap.querySelectorAll('.option');

    opts.forEach((o)=>{
      const oi = Number(o.getAttribute('data-i'));
      if(oi === correct) o.classList.add('correct');
      if(oi === idx && oi !== correct) o.classList.add('wrong');
      // remove hover transform after answer
      o.style.pointerEvents = 'none';
    });

    if(idx === correct){
      score += 1;
      correctCount += 1;
      feedback.textContent = "Correct! +" + 1;
    } else {
      feedback.textContent = "Incorrect.";
    }

    // update explanation and side panel
    explanationEl.textContent = quiz[current].expl;
    scoreEl.textContent = score + " / " + quiz.length;
    scoreMini.textContent = score;
    correctCountEl.textContent = correctCount;
    metaEl.textContent = "Explanation below.";

    // if last question, change next button to disabled and enable finish
    if(current >= quiz.length - 1){
      nextBtn.disabled = true;
    }
  }

  nextBtn.addEventListener('click', ()=>{
    if(current < quiz.length - 1){
      current++;
      renderQuestion(current);
    }
  });

  restartBtn.addEventListener('click', ()=>{
    if(!confirm("Restart the quiz? All progress will be reset.")) return;
    current = 0;
    score = 0;
    correctCount = 0;
    answered = Array(quiz.length).fill(null);
    renderQuestion(current);
    progressBar.style.width = "0%";
    feedback.textContent = "Choose an answer to see if you're right.";
    explanationEl.textContent = "Select an option to see a short explanation.";
    nextBtn.disabled = false;
  });

  showAnswersBtn.addEventListener('click', ()=>{
    // reveal all correct answers visually
    // mark each option with correct/wrong
    const oldIndex = current;
    for(let i=0;i<quiz.length;i++){
      // temporarily navigate to each and mark
      current = i;
      renderQuestion(i);
      // simulate selection of correct as "revealed"
      const opts = optionsWrap.querySelectorAll('.option');
      opts.forEach((o)=>{
        const oi = Number(o.getAttribute('data-i'));
        if(oi === quiz[i].a) o.classList.add('correct');
        o.style.pointerEvents = 'none';
      });
    }
    current = oldIndex;
    renderQuestion(current);
  });

  finishBtn.addEventListener('click', ()=>{
    const answeredCount = answered.filter(x => x !== null).length;
    const msg = `You answered ${answeredCount} of ${quiz.length} questions.\nScore: ${score} / ${quiz.length}\nCorrect: ${correctCount}\n\nPress OK to review answers.`;
    alert(msg);
  });

  // initialize render
  renderQuestion(0);

  // keyboard nav: left=previous, right=next
  window.addEventListener('keydown', (e)=>{
    if(e.key === 'ArrowRight') {
      if(current < quiz.length -1) { current++; renderQuestion(current); }
    } else if(e.key === 'ArrowLeft') {
      if(current > 0) { current--; renderQuestion(current); }
    }
  });

  // ensure progress updates when navigating
  const observer = new MutationObserver(()=>{
    const pct = Math.round(((current)/quiz.length)*100);
    progressBar.style.width = pct + "%";
  });
  observer.observe(qIndexEl, { childList:true, characterData:true, subtree:true });

})();
</script>
</body>
</html>
