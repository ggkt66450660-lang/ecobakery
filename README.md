# ecobakery
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>EcoBakery — 지구를 위한 달콤한 변화</title>
  <style>
    body {
      font-family: "Noto Sans KR", sans-serif;
      background: #e9f9f0;
      color: #222;
      margin: 0;
      padding: 0;
    }
    header {
      background: linear-gradient(90deg, #4fae6b, #6fc8ff);
      color: white;
      text-align: center;
      padding: 40px 20px;
    }
    header h1 {
      margin: 0;
      font-size: 2em;
    }
    header p {
      margin-top: 8px;
    }
    section {
      background: white;
      margin: 20px auto;
      padding: 20px;
      border-radius: 12px;
      width: 90%;
      max-width: 800px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h2 {
      color: #1b5030;
    }
    button {
      background: #4fae6b;
      color: white;
      border: none;
      border-radius: 8px;
      padding: 8px 14px;
      cursor: pointer;
      margin-top: 10px;
    }
    button:hover {
      background: #3e965b;
    }
    input, textarea {
      width: 100%;
      padding: 8px;
      margin-top: 6px;
      border-radius: 6px;
      border: 1px solid #ccc;
      font-size: 14px;
    }
    footer {
      text-align: center;
      padding: 20px;
      font-size: 13px;
      color: #555;
    }
    .result {
      background: #f2fff7;
      border: 1px solid #bce2c6;
      padding: 10px;
      border-radius: 8px;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <header>
    <h1>EcoBakery — 지구를 위한 달콤한 한 입</h1>
    <p>함께 심어요, 푸른 내일을 🌿</p>
  </header>

  <section>
    <h2>1) 문제의식</h2>
    <p>제과제빵 산업에서는 포장 쓰레기, 식재료 낭비, 온실가스 배출이 심각합니다.  
    이를 해결하는 것은 음식 산업의 지속 가능한 발전에 매우 중요한 의미를 가집니다.</p>
  </section>

  <section>
    <h2>2) 핵심 아이디어</h2>
    <p><strong>제로웨이스트 베이커리 시스템</strong>을 제안합니다.</p>
    <ul>
      <li>친환경 포장재 사용</li>
      <li>남은 빵 재활용 메뉴 소개</li>
      <li>지역 농산물 활용 레시피</li>
      <li>AI 기반 재료 관리로 낭비 감소</li>
    </ul>
  </section>

  <section>
    <h2>3) 낭비 계산기</h2>
    <p>내가 하루에 만드는 빵 개수와 남는 비율을 입력하면 1년간 낭비되는 양을 계산할 수 있어요.</p>
    <label>하루 생산량(개): <input type="number" id="dailyProd" value="100"></label><br>
    <label>남는 비율(%): <input type="number" id="wasteRate" value="10"></label><br>
    <label>빵 1개의 무게(g): <input type="number" id="breadWeight" value="80"></label><br>
    <button onclick="calcWaste()">연간 낭비량 계산하기</button>
    <div class="result" id="resultBox">결과가 여기에 표시됩니다.</div>
  </section>

  <section>
    <h2>4) 재활용 레시피 공유</h2>
    <p>남은 빵을 활용한 레시피를 기록해보세요.</p>
    <textarea id="recipe" rows="4" placeholder="예: 어제의 빵으로 브레드푸딩 만들기"></textarea>
    <button onclick="saveRecipe()">저장하기</button>
    <div id="savedRecipes" class="result"></div>
  </section>

  <section>
    <h2>5) 성찰</h2>
    <p>이번 프로젝트를 통해 제과제빵 전공 지식이 환경 문제 해결에도 활용될 수 있음을 배웠습니다.  
    앞으로는 맛뿐만 아니라 환경을 생각하는 제빵사가 되고 싶습니다.</p>
  </section>

  <footer>
    © 2025 한수현 | EcoBakery 프로젝트
  </footer>

  <script>
    function calcWaste() {
      const daily = parseFloat(document.getElementById("dailyProd").value);
      const rate = parseFloat(document.getElementById("wasteRate").value);
      const weight = parseFloat(document.getElementById("breadWeight").value);
      const yearlyWaste = daily * (rate / 100) * weight * 365 / 1000;
      document.getElementById("resultBox").innerText =
        `연간 낭비량: 약 ${yearlyWaste.toFixed(1)} kg 입니다.`;
    }

    function saveRecipe() {
      const recipe = document.getElementById("recipe").value.trim();
      if (!recipe) {
        alert("레시피 내용을 입력하세요!");
        return;
      }
      let recipes = localStorage.getItem("ecoRecipes");
      recipes = recipes ? JSON.parse(recipes) : [];
      recipes.push(recipe);
      localStorage.setItem("ecoRecipes", JSON.stringify(recipes));
      showRecipes();
      document.getElementById("recipe").value = "";
    }

    function showRecipes() {
      const saved = document.getElementById("savedRecipes");
      let recipes = localStorage.getItem("ecoRecipes");
      recipes = recipes ? JSON.parse(recipes) : [];
      if (recipes.length === 0) {
        saved.innerText = "저장된 레시피가 없습니다.";
      } else {
        saved.innerHTML = "<strong>내가 저장한 레시피:</strong><br>" + recipes.map(r => "• " + r).join("<br>");
      }
    }

    showRecipes();
  </script>
</body>
</html>
