# TRQ-15-Chi

<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <title>舌繫帶限制問卷（TRQ）</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0, shrink-to-fit=no, viewport-fit=cover">
  <style>
    :root {
      --primary: #007AFF;
      --primary-active: #0056b3;
      --bg: #F2F2F7;
      --card-bg: #FFFFFF;
      --text-main: #000000;
      --text-muted: #6C6C70;
      --border: #D1D1D6;
      --selected-bg: #E3F0FF;
      --error-border: #FF3B30;
      --error-bg: #FFF2F2;
    }

    * {
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
      -webkit-text-size-adjust: 100%;
    }

    html, body {
      width: 100%;
      overflow-x: hidden;
      scroll-behavior: smooth;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "SF Pro Text", "SF Pro Display", "PingFang HK", "PingFang TC", "Noto Sans TC", sans-serif;
      background-color: var(--bg);
      color: var(--text-main);
      margin: 0;
      padding: env(safe-area-inset-top, 12px) 14px calc(36px + env(safe-area-inset-bottom, 20px)) 14px;
      font-size: clamp(17px, 4.8vw, 20px);
      line-height: 1.45;
    }

    .container {
      width: 100%;
      max-width: 600px;
      margin: 0 auto;
    }

    .header-card {
      background: var(--card-bg);
      border-radius: 16px;
      padding: 18px 16px;
      margin-top: 6px;
      margin-bottom: 14px;
      text-align: center;
      box-shadow: 0 1px 4px rgba(0,0,0,0.06);
      border: 1px solid var(--border);
    }

    .main-title {
      font-size: clamp(1.4rem, 5.5vw, 1.85rem);
      font-weight: 800;
      margin: 0 0 8px 0;
      color: var(--text-main);
      line-height: 1.25;
    }

    .instruction {
      font-size: clamp(1.05rem, 4.2vw, 1.2rem);
      color: var(--text-muted);
      margin: 0;
      line-height: 1.5;
    }

    /* Question Cards */
    .question-card, .slider-card {
      background: var(--card-bg);
      border-radius: 16px;
      padding: 18px 14px;
      margin-bottom: 14px;
      box-shadow: 0 1px 4px rgba(0,0,0,0.05);
      border: 1.5px solid var(--border);
      transition: border-color 0.2s, background-color 0.2s;
    }

    .question-card.highlight-error, .slider-card.highlight-error {
      border-color: var(--error-border) !important;
      background-color: var(--error-bg);
      animation: pulse-border 1.5s infinite;
    }

    @keyframes pulse-border {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.01); }
    }

    .question-title {
      font-size: clamp(1.2rem, 4.8vw, 1.4rem);
      font-weight: 700;
      color: var(--text-main);
      line-height: 1.35;
      margin-bottom: 12px;
    }

    /* Vertical Radio Options */
    .options-group {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .option-item {
      display: flex;
      align-items: center;
      padding: 14px 14px;
      border-radius: 14px;
      background: #F8F8FA;
      border: 2px solid transparent;
      cursor: pointer;
      font-size: clamp(1.05rem, 4.2vw, 1.2rem);
      color: #1C1C1E;
      transition: all 0.15s ease-in-out;
      user-select: none;
    }

    .option-item:active {
      transform: scale(0.99);
      background: #E5E5EA;
    }

    .option-item.selected {
      background: var(--selected-bg);
      border-color: var(--primary);
      color: #004CB8;
      font-weight: 700;
    }

    .custom-radio {
      width: 24px;
      height: 24px;
      border-radius: 50%;
      border: 2px solid #8E8E93;
      margin-right: 12px;
      flex-shrink: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #FFF;
      transition: border-color 0.15s, background-color 0.15s;
    }

    .option-item.selected .custom-radio {
      border-color: var(--primary);
      background: var(--primary);
    }

    .option-item.selected .custom-radio::after {
      content: "";
      width: 10px;
      height: 10px;
      background: #FFF;
      border-radius: 50%;
    }

    .option-text {
      flex-grow: 1;
      line-height: 1.4;
    }

    .hidden-radio {
      position: absolute;
      opacity: 0;
      pointer-events: none;
    }

    /* QoL Slider */
    .slider-header {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      margin-bottom: 8px;
    }

    .slider-badge {
      font-size: 1.35rem;
      font-weight: 800;
      color: var(--primary);
      text-align: right;
    }

    .slider-container {
      margin: 24px 6px 12px 6px;
    }

    .custom-slider {
      -webkit-appearance: none;
      width: 100%;
      height: 10px;
      border-radius: 5px;
      background: linear-gradient(to right, #34C759 0%, #FFCC00 50%, #FF9500 75%, #FF3B30 100%);
      outline: none;
      cursor: pointer;
    }

    .custom-slider::-webkit-slider-thumb {
      -webkit-appearance: none;
      appearance: none;
      width: 28px;
      height: 28px;
      border-radius: 50%;
      background: #FFFFFF;
      border: 3px solid var(--primary);
      box-shadow: 0 2px 6px rgba(0,0,0,0.3);
      cursor: pointer;
      transition: transform 0.1s;
    }

    .custom-slider::-webkit-slider-thumb:active {
      transform: scale(1.15);
    }

    .slider-labels {
      display: flex;
      justify-content: space-between;
      margin-top: 10px;
      font-size: 0.85rem;
      font-weight: 700;
      color: var(--text-muted);
    }

    .slider-labels span {
      flex: 1;
      text-align: center;
    }

    .slider-labels span:first-child {
      text-align: left;
    }

    .slider-labels span:last-child {
      text-align: right;
    }

    /* Submit Button */
    .calc-btn {
      margin-top: 16px;
      padding: 18px;
      width: 100%;
      background: var(--primary);
      color: #FFFFFF;
      font-size: clamp(1.2rem, 5vw, 1.35rem);
      font-weight: 700;
      border: none;
      border-radius: 16px;
      cursor: pointer;
      box-shadow: 0 4px 14px rgba(0, 122, 255, 0.35);
      transition: background 0.15s, transform 0.1s;
    }

    .calc-btn:active {
      background: var(--primary-active);
      transform: scale(0.98);
    }

    /* Modal */
    .modal {
      display: none;
      position: fixed;
      z-index: 999;
      inset: 0;
      background: rgba(0, 0, 0, 0.5);
      backdrop-filter: blur(8px);
      -webkit-backdrop-filter: blur(8px);
      align-items: center;
      justify-content: center;
      padding: 16px;
    }

    .modal-content {
      background: #FFFFFF;
      padding: 24px 18px;
      border-radius: 22px;
      width: 100%;
      max-width: 400px;
      text-align: center;
      box-shadow: 0 12px 36px rgba(0,0,0,0.25);
    }

    .modal-content h2 {
      margin: 0 0 12px 0;
      font-size: 1.6rem;
    }

    .result-block {
      background: #F8F8FA;
      border-radius: 14px;
      padding: 14px 12px;
      margin-bottom: 12px;
    }

    .result-label {
      font-size: 1rem;
      color: var(--text-muted);
      margin: 0 0 4px 0;
    }

    .result-val {
      font-size: 2.2rem;
      font-weight: 800;
      color: var(--primary);
      margin: 0;
    }

    .notice-box {
      background: #FFF9E6;
      border: 1.5px solid #FFD666;
      padding: 14px;
      margin: 16px 0;
      font-size: 1.05rem;
      color: #874D00;
      border-radius: 12px;
      line-height: 1.5;
      font-weight: 700;
    }

    .close-btn {
      width: 100%;
      padding: 16px;
      background: #1C1C1E;
      color: #FFF;
      font-size: 1.2rem;
      font-weight: 700;
      border: none;
      border-radius: 14px;
      cursor: pointer;
    }
  </style>
</head>
<body>

<div class="container">
  <div class="header-card">
    <h1 class="main-title">舌繫帶限制問卷<br>（TRQ）</h1>
    <p class="instruction">請勾選符合的情況，以協助我們評估是否存在舌繫帶限制問題。</p>
  </div>

  <form id="evaluationForm">
    <!-- 第 1 至 15 題（目前面對的問題） -->
    <div id="questionsContainer"></div>

    <!-- 生活質素影響滑動桿卡片 -->
    <div class="slider-card" id="qolCard">
      <div class="slider-header">
        <span class="question-title" style="margin-bottom: 0;">16. 對生活質素的影響程度</span>
        <span id="qolDisplay" class="slider-badge">完全沒有影響</span>
      </div>
      <p style="font-size: 0.95rem; color: var(--text-muted); margin: 6px 0 16px 0;">這些問題對生活質素造成多大程度的影響？</p>
      
      <div class="slider-container">
        <input type="range" min="0" max="3" value="0" step="1" class="custom-slider" id="qolSlider" oninput="updateQol(this.value)">
      </div>
      
      <div class="slider-labels">
        <span>完全沒有影響</span>
        <span>少許影響</span>
        <span>顯著影響</span>
        <span>極大影響</span>
      </div>
    </div>

    <button type="button" class="calc-btn" onclick="submitAssessment()">計算評估結果</button>
  </form>
</div>

<!-- 結果彈窗 -->
<div id="scoreModal" class="modal" role="dialog" aria-modal="true" aria-labelledby="modalTitle" onclick="handleBackdropClick(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <h2 id="modalTitle">評估結果</h2>
    
    <div class="result-block">
      <p class="result-label">符合情況總計</p>
      <p id="modalYesCount" class="result-val">0 / 15 項</p>
      <p id="modalScoreSubtitle" style="font-size: 0.95rem; margin: 6px 0 0 0; color: var(--text-muted);"></p>
    </div>

    <div class="result-block">
      <p class="result-label">生活質素影響程度</p>
      <p id="modalQolText" class="result-val" style="font-size: 1.6rem;">完全沒有影響</p>
    </div>

    <div class="notice-box">
      請不要離開此畫面，並出示給您的醫護人員／治療師。<br>
      您亦可以進行螢幕截圖。<br>
      謝謝。
    </div>
    
    <button type="button" class="close-btn" onclick="closeModal()">關閉</button>
  </div>
</div>

<script>
var standardOptions = [
  { key: "yes", value: 1, label: "是" },
  { key: "no",  value: 0, label: "否" }
];

var items = [
  "在言語溝通上感到挫折",
  "發音有困難、難以讓人理解，或說話含糊不清",
  "語言發展遲緩",
  "進食緩慢或難以完成一餐",
  "挑食，特別對某些質地的食物（例如：肉類、薯蓉）感到排斥",
  "進食液體或固體食物時容易嗆到或引發嘔吐反射",
  "吐出食物，或習慣將食物塞在兩頰",
  "睡眠不安穩（睡覺時踢被或翻來覆去）",
  "夜間磨牙",
  "睡覺時張開嘴巴",
  "打鼾／扯鼻鼾（聲音輕微或響亮）",
  "顳下頜關節（TMJ）問題（有聲響、喀喀聲或疼痛）",
  "經常頭痛或頸痛",
  "日間習慣用口呼吸",
  "過度活躍或注意力不集中"
];

var qolLevels = [
  "完全沒有影響",
  "少許影響",
  "顯著影響",
  "極大影響"
];

function renderQuestions() {
  var container = document.getElementById("questionsContainer");
  if (!container) return;
  container.innerHTML = "";

  items.forEach(function(titleText, index) {
    var qNum = index + 1;
    var card = document.createElement("div");
    card.className = "question-card";
    card.id = "card-q" + qNum;

    var title = document.createElement("div");
    title.className = "question-title";
    title.textContent = qNum + ". " + titleText;
    card.appendChild(title);

    var optionsGroup = document.createElement("div");
    optionsGroup.className = "options-group";

    standardOptions.forEach(function(opt) {
      var label = document.createElement("label");
      label.className = "option-item";
      label.htmlFor = "q" + qNum + "_" + opt.key;

      var radio = document.createElement("input");
      radio.type = "radio";
      radio.name = "q" + qNum;
      radio.id = "q" + qNum + "_" + opt.key;
      radio.value = opt.value;
      radio.className = "hidden-radio";

      radio.addEventListener("change", function() {
        var siblings = optionsGroup.querySelectorAll(".option-item");
        siblings.forEach(function(el) { el.classList.remove("selected"); });
        if (radio.checked) {
          label.classList.add("selected");
          card.classList.remove("highlight-error");
        }
      });

      var dot = document.createElement("span");
      dot.className = "custom-radio";
      dot.setAttribute("aria-hidden", "true");

      var itemText = document.createElement("span");
      itemText.className = "option-text";
      itemText.textContent = opt.label;

      label.appendChild(radio);
      label.appendChild(dot);
      label.appendChild(itemText);
      optionsGroup.appendChild(label);
    });

    card.appendChild(optionsGroup);
    container.appendChild(card);
  });
}

if (document.readyState === "loading") {
  document.addEventListener("DOMContentLoaded", renderQuestions);
} else {
  renderQuestions();
}

function updateQol(val) {
  document.getElementById("qolDisplay").textContent = qolLevels[val];
}

function submitAssessment() {
  var unanswered = [];
  document.querySelectorAll(".question-card").forEach(function(c) {
    c.classList.remove("highlight-error");
  });

  for (var i = 1; i <= items.length; i++) {
    if (!document.querySelector('input[name="q' + i + '"]:checked')) {
      unanswered.push(i);
    }
  }

  if (unanswered.length > 0) {
    unanswered.forEach(function(num) {
      var card = document.getElementById("card-q" + num);
      if (card) card.classList.add("highlight-error");
    });

    var firstCard = document.getElementById("card-q" + unanswered[0]);
    if (firstCard) {
      firstCard.scrollIntoView({ behavior: "smooth", block: "center" });
    }
    return;
  }

  var yesCount = 0;
  for (var j = 1; j <= items.length; j++) {
    var selected = document.querySelector('input[name="q' + j + '"]:checked');
    if (selected && selected.value === "1") {
      yesCount++;
    }
  }

  var qolIndex = document.getElementById("qolSlider").value;
  var qolText = qolLevels[qolIndex];

  document.getElementById("modalYesCount").textContent = yesCount + " / 15 項";
  document.getElementById("modalScoreSubtitle").innerHTML = 
    "選擇「是」的項目總計：<strong>" + yesCount + "</strong> 項";
  document.getElementById("modalQolText").textContent = qolText;

  var modal = document.getElementById("scoreModal");
  modal.style.display = "flex";
}

function closeModal() {
  document.getElementById("scoreModal").style.display = "none";
}

function handleBackdropClick(e) {
  if (e.target.id === "scoreModal") {
    closeModal();
  }
}

document.addEventListener("keydown", function(e) {
  if (e.key === "Escape") {
    closeModal();
  }
});
</script>

</body>
</html>
