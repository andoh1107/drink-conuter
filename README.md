# drink-conuter
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>酒のみかた - Sake no Mikata</title>
  <script src="[cdn.tailwindcss.com](https://cdn.tailwindcss.com)"></script>
  <link rel="stylesheet" href="[cdnjs.cloudflare.com/ajax/…/all.min.css](https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css)">
  <style>
    import-diff-notifier url('[fonts.googleapis.com/css2?family=…&display=swap](https://fonts.googleapis.com/css2?family=Zen+Maru+Gothic:wght@500;700;900&display=swap)');
    body {
      font-family: 'Zen Maru Gothic', sans-serif;
      background-color: 1A1A24_11A1A24_1;
      color: F3F4F6_1F3F4F6_1;
    }
    .glass-effect {
      background: rgba(30, 30, 45, 0.75);
      backdrop-filter: blur(12px);
      border: 1px solid rgba(255, 255, 255, 0.1);
    }
    .beer-liquid {
      transition: height 0.5s ease-in-out, background-color 0.5s;
    }
  </style>
</head>
<body class="pb-24">
  <!-- Header -->
  <header class="sticky top-0 z-50 glass-effect border-b border-amber-500/20 px-4 py-3 flex justify-between items-center">
    <div class="flex items-center space-x-2">
      <div class="w-10 h-10 rounded-full bg-amber-500 flex items-center justify-center text-slate-900 font-extrabold text-xl shadow-lg">
        🍺
      </div>
      <div>
        <h1 class="text-xl font-black text-amber-400 tracking-wider">酒のみかた</h1>
        <p class="text-xs text-gray-400">楽しいお酒と、最高の仲間</p>
      </div>
    </div>
  </header>

  <!-- Main Container -->
  <main class="max-w-md mx-auto p-4 space-y-6">
    <!-- TAB 1: カウンター -->
    <section id="tab-counter" class="tab-content space-y-4">
      <div class="glass-effect rounded-2xl p-5 text-center relative overflow-hidden">
        <h2 class="text-lg font-bold text-gray-200 mb-1">今夜の飲酒メーター</h2>
        <p class="text-xs text-gray-400 mb-4">目標杯数を超えないように楽しもう！</p>

        <!-- ジョッキアニメーション -->
        <div class="relative w-36 h-48 mx-auto border-4 border-amber-200/40 rounded-b-3xl rounded-t-sm overflow-hidden bg-slate-800/50 shadow-inner my-4">
          <div id="beer-foam" class="absolute top-0 left-0 right-0 h-4 bg-white/90 rounded-b-md z-10 transition-all duration-300 opacity-0"></div>
          <div id="beer-liquid" class="beer-liquid absolute bottom-0 left-0 right-0 bg-gradient-to-t from-amber-600 to-amber-400" style="height: 0%;"></div>
        </div>

        <div class="flex justify-center items-baseline space-x-2 mb-4">
          <span id="current-count" class="text-4xl font-black text-amber-400">0</span>
          <span class="text-gray-400 text-lg">/</span>
          <span id="target-display" class="text-xl font-bold text-gray-300">10</span>
          <span class="text-gray-400">杯</span>
        </div>

        <div id="overflow-warning" class="hidden text-red-400 font-bold text-sm bg-red-950/50 border border-red-500/30 rounded-lg p-2 mb-4 animate-bounce">
          ⚠️ 設定した杯数を超えました！飲みすぎ注意！
        </div>

        <div class="flex justify-center space-x-3">
          <button onclick="changeCount(-1)" class="w-12 h-12 bg-slate-700 hover:bg-slate-600 rounded-full text-2xl font-bold text-white shadow-md active:scale-95 transition">-</button>
          <button onclick="changeCount(1)" class="px-8 h-12 bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-400 hover:to-amber-500 rounded-full text-lg font-bold text-slate-900 shadow-lg active:scale-95 transition">🍺 1杯飲む！</button>
        </div>
      </div>
    </section>

    <!-- TAB 2: 飲み友募集 -->
    <section id="tab-recruit" class="tab-content hidden space-y-4">
      <div class="glass-effect rounded-2xl p-5">
        <h2 class="text-lg font-bold text-amber-400 mb-3"><i class="fa-solid fa-bullhorn mr-2"></i>今夜の飲み会を募る</h2>
        <div class="space-y-3">
          <input type="text" placeholder="例：渋谷の鳥貴族でサクッと！" class="w-full bg-slate-800/80 border border-gray-700 rounded-xl p-3 text-sm focus:outline-none focus:border-amber-400">
          <div class="flex space-x-2">
            <input type="time" value="21:00" class="w-1/2 bg-slate-800/80 border border-gray-700 rounded-xl p-3 text-sm text-gray-300">
            <span class="self-center text-xs text-gray-400">〆切</span>
          </div>
          <button class="w-full py-3 bg-amber-500 text-slate-900 font-bold rounded-xl shadow-lg hover:bg-amber-400 transition">募集を送信する</button>
        </div>
      </div>
    </section>

    <!-- TAB 3: メンバー＆コンディション -->
    <section id="tab-members" class="tab-content hidden space-y-4">
      <div class="glass-effect rounded-2xl p-5">
        <h2 class="text-lg font-bold text-amber-400 mb-3"><i class="fa-solid fa-users mr-2"></i>参加メンバーのコンディション</h2>
        <div class="space-y-3">
          <div class="bg-slate-800/60 p-3 rounded-xl flex justify-between items-center">
            <div>
              <p class="font-bold">たろう <span class="text-xs text-amber-400 ml-2">🔥 のみべ MAX</span></p>
              <p class="text-xs text-gray-400">終電: 23:45 (新宿駅)</p>
            </div>
            <span class="text-xs bg-emerald-900/50 text-emerald-400 px-2 py-1 rounded">23:15退店推奨</span>
          </div>
        </div>
      </div>
    </section>

    <!-- TAB 4: 酒評価 & レビュー -->
    <section id="tab-review" class="tab-content hidden space-y-4">
      <div class="glass-effect rounded-2xl p-5">
        <h2 class="text-lg font-bold text-amber-400 mb-3"><i class="fa-solid fa-star mr-2"></i>友達からの酒評価</h2>
        <p class="text-xs text-gray-400 mb-4">粗相なく楽しく飲めたか★で評価し合おう！</p>
        <div class="bg-slate-800/60 p-4 rounded-xl space-y-2">
          <div class="flex justify-between items-center">
            <span class="font-bold text-sm">昨日のお酒マナー評価</span>
            <span class="text-amber-400 font-bold">★ 4.8 / 5.0</span>
          </div>
          <p class="text-xs text-gray-300">「終電通りに帰れてえらかった！また飲もう」</p>
        </div>
      </div>
    </section>
  </main>

  <!-- Bottom Navigation -->
  <nav class="fixed bottom-0 left-0 right-0 glass-effect border-t border-gray-800 px-2 py-2">
    <div class="max-w-md mx-auto flex justify-around text-center">
      <button onclick="switchTab('counter')" id="nav-counter" class="nav-btn text-amber-400 flex flex-col items-center">
        <i class="fa-solid fa-beer-mug-empty text-lg"></i>
        <span class="text-[10px] mt-1">カウンター</span>
      </button>
      <button onclick="switchTab('recruit')" id="nav-recruit" class="nav-btn text-gray-400 flex flex-col items-center">
        <i class="fa-solid fa-paper-plane text-lg"></i>
        <span class="text-[10px] mt-1">募集</span>
      </button>
      <button onclick="switchTab('members')" id="nav-members" class="nav-btn text-gray-400 flex flex-col items-center">
        <i class="fa-solid fa-clock text-lg"></i>
        <span class="text-[10px] mt-1">終電・体調</span>
      </button>
      <button onclick="switchTab('review')" id="nav-review" class="nav-btn text-gray-400 flex flex-col items-center">
        <i class="fa-solid fa-star text-lg"></i>
        <span class="text-[10px] mt-1">酒評価</span>
      </button>
    </div>
  </nav>

  <script>
    let count = 0;
    const target = 10;

    function changeCount(delta) {
      count = Math.max(0, count + delta);
      document.getElementById('current-count').innerText = count;

      const liquid = document.getElementById('beer-liquid');
      const foam = document.getElementById('beer-foam');
      const warning = document.getElementById('overflow-warning');

      let percentage = (count / target) * 100;
      liquid.style.height = Math.min(percentage, 100) + '%';

      if (count > 0) {
        foam.style.opacity = '1';
      } else {
        foam.style.opacity = '0';
      }

      if (count > target) {
        liquid.style.backgroundColor = 'EF4444_1EF4444_1'; // あふれたら赤色に
        warning.classList.remove('hidden');
      } else {
        liquid.style.backgroundColor = 'D97706_1D97706_1';
        warning.classList.add('hidden');
      }
    }

    function switchTab(tabName) {
      document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
      document.querySelectorAll('.nav-btn').forEach(el => {
        el.classList.remove('text-amber-400');
        el.classList.add('text-gray-400');
      });

      document.getElementById('tab-' + tabName).classList.remove('hidden');
      document.getElementById('nav-' + tabName).classList.add('text-amber-400');
      document.getElementById('nav-' + tabName).classList.remove('text-gray-400');
    }
  </script>
</body>
</html>