# kagesanpo
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>かげさんぽ</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.css"/>
<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.js"></script>
<style>
* { margin:0; padding:0; box-sizing:border-box; -webkit-tap-highlight-color:transparent; }
:root {
  --green:#059669; --red:#dc2626; --blue:#2563eb;
  --purple:#7c3aed; --cyan:#0891b2; --orange:#ea580c;
  --surface:#fff; --bg:#f0fdf4; --text:#0f172a;
  --muted:#64748b; --border:#e2e8f0;
  --safe:env(safe-area-inset-bottom,16px);
}
html,body { height:100%; overflow:hidden; font-family:'Hiragino Kaku Gothic ProN','Hiragino Sans',sans-serif; background:var(--bg); }

#map { position:fixed; inset:0; z-index:1; }

/* トップバー */
#topbar { position:fixed; top:0; left:0; right:0; z-index:500; padding:12px 12px 0; pointer-events:none; }
#searchbox {
  pointer-events:all; display:flex; align-items:center; gap:8px;
  background:var(--surface); border-radius:24px; padding:10px 14px;
  box-shadow:0 2px 16px rgba(0,0,0,.15);
}
.app-name { font-size:16px; font-weight:800; color:var(--green); white-space:nowrap; }
#searchbox input { flex:1; border:none; outline:none; font-size:14px; color:var(--text); background:transparent; font-family:inherit; min-width:0; }
#searchbox input::placeholder { color:#94a3b8; }
.temp-badge { background:#f0fdf4; color:var(--green); font-size:11px; font-weight:700; padding:4px 9px; border-radius:14px; white-space:nowrap; flex-shrink:0; }

#chips { pointer-events:all; display:flex; gap:6px; overflow-x:auto; scrollbar-width:none; padding:8px 0 10px; }
#chips::-webkit-scrollbar { display:none; }
.chip { flex-shrink:0; padding:5px 13px; border-radius:18px; border:1.5px solid var(--border); background:var(--surface); font-size:12px; font-weight:600; cursor:pointer; color:var(--muted); box-shadow:0 1px 3px rgba(0,0,0,.07); white-space:nowrap; transition:all .15s; user-select:none; }
.chip.on { color:#fff !important; border-color:transparent !important; }
.chip[data-f=all].on     { background:#0f172a; }
.chip[data-f=shade].on   { background:var(--green); }
.chip[data-f=danger].on  { background:var(--red); }
.chip[data-f=vending].on { background:var(--blue); }
.chip[data-f=shop].on    { background:var(--purple); }
.chip[data-f=hospital].on{ background:var(--red); }
.chip[data-f=rest].on    { background:var(--cyan); }

/* 現在地ボタン */
#btn-locate { position:fixed; right:12px; bottom:112px; z-index:300; width:46px; height:46px; border-radius:50%; background:var(--surface); border:none; cursor:pointer; box-shadow:0 2px 12px rgba(0,0,0,.18); font-size:20px; display:flex; align-items:center; justify-content:center; transition:bottom .3s cubic-bezier(.32,.72,0,1); }

/* ボトムシート */
#sheet { position:fixed; bottom:0; left:0; right:0; z-index:400; background:var(--surface); border-radius:22px 22px 0 0; box-shadow:0 -2px 20px rgba(0,0,0,.12); display:flex; flex-direction:column; transition:height .32s cubic-bezier(.32,.72,0,1); height:72px; max-height:80vh; overscroll-behavior:contain; }
#sheet-handle-area { flex-shrink:0; padding:10px 0 0; cursor:pointer; display:flex; flex-direction:column; align-items:center; }
#sheet-handle { width:38px; height:4px; background:var(--border); border-radius:2px; margin-bottom:8px; }
#sheet-header { width:100%; padding:0 16px 10px; display:flex; align-items:center; justify-content:space-between; border-bottom:1px solid var(--border); }
#sheet-label { font-size:14px; font-weight:800; }
#sheet-count { font-size:12px; color:var(--muted); }
#spot-list { overflow-y:auto; flex:1; -webkit-overflow-scrolling:touch; }

/* スポット行 */
.srow { display:flex; align-items:center; gap:12px; padding:13px 16px; border-bottom:1px solid var(--border); cursor:pointer; }
.srow:last-child { border-bottom:none; }
.srow:active { background:#f8fafc; }
.spin { width:42px; height:42px; border-radius:13px; display:flex; align-items:center; justify-content:center; font-size:20px; flex-shrink:0; }
.sp-shade    { background:#d1fae5; } .sp-danger   { background:#fee2e2; }
.sp-vending  { background:#dbeafe; } .sp-shop     { background:#ede9fe; }
.sp-hospital { background:#fee2e2; } .sp-rest     { background:#cffafe; }
.sbody { flex:1; min-width:0; }
.sname { font-size:14px; font-weight:700; white-space:nowrap; overflow:hidden; text-overflow:ellipsis; }
.smeta { display:flex; gap:5px; margin-top:3px; flex-wrap:wrap; align-items:center; }
.stag { font-size:10px; font-weight:700; padding:2px 8px; border-radius:8px; white-space:nowrap; }
.t-shade    { background:#d1fae5; color:#065f46; } .t-danger   { background:#fee2e2; color:#991b1b; }
.t-vending  { background:#dbeafe; color:#1e40af; } .t-shop     { background:#ede9fe; color:#5b21b6; }
.t-hospital { background:#fee2e2; color:#991b1b; } .t-rest     { background:#cffafe; color:#155e75; }
.sdist { font-size:11px; color:var(--muted); font-weight:600; text-align:right; flex-shrink:0; line-height:1.5; }

/* 詳細パネル */
#detail { position:fixed; inset:0; z-index:700; display:flex; flex-direction:column; justify-content:flex-end; pointer-events:none; opacity:0; transition:opacity .25s; }
#detail.open { pointer-events:all; opacity:1; }
#detail-backdrop { position:absolute; inset:0; background:rgba(0,0,0,.25); }
#detail-card { position:relative; z-index:1; background:var(--surface); border-radius:24px 24px 0 0; padding:0 0 var(--safe); box-shadow:0 -4px 32px rgba(0,0,0,.2); transform:translateY(100%); transition:transform .3s cubic-bezier(.32,.72,0,1); max-height:82vh; display:flex; flex-direction:column; overscroll-behavior:contain; }
#detail.open #detail-card { transform:translateY(0); }

/* 詳細ヘッダー */
#d-top { flex-shrink:0; padding:16px 16px 0; display:flex; align-items:flex-start; gap:12px; }
#d-icon { font-size:34px; flex-shrink:0; line-height:1; }
#d-name { font-size:18px; font-weight:800; flex:1; line-height:1.3; }
#d-close { width:34px; height:34px; border-radius:50%; background:#f1f5f9; border:none; font-size:18px; cursor:pointer; flex-shrink:0; display:flex; align-items:center; justify-content:center; color:var(--muted); }
#d-tags { padding:10px 16px 4px; display:flex; gap:6px; flex-wrap:wrap; flex-shrink:0; }
.d-dist { display:inline-flex; align-items:center; gap:4px; background:#f0fdf4; color:var(--green); font-size:13px; font-weight:700; padding:5px 13px; border-radius:18px; }

/* 営業時間バナー */
#d-hours-banner { flex-shrink:0; margin:0 16px 4px; border-radius:12px; padding:10px 14px; display:flex; align-items:center; gap:10px; }
.hb-open  { background:#f0fdf4; border:1.5px solid #86efac; }
.hb-close { background:#fff7ed; border:1.5px solid #fdba74; }
.hb-unknown { background:#f8fafc; border:1.5px solid var(--border); }
.hb-allday  { background:#eff6ff; border:1.5px solid #93c5fd; }
.hb-icon { font-size:18px; flex-shrink:0; }
.hb-text { font-size:12px; line-height:1.5; }
.hb-status { font-weight:800; font-size:13px; }

#d-body { overflow-y:auto; flex:1; padding:4px 16px 4px; -webkit-overflow-scrolling:touch; }
.drow { display:flex; gap:10px; padding:11px 0; border-bottom:1px solid var(--border); align-items:flex-start; }
.drow:last-child { border-bottom:none; }
.dico { font-size:16px; width:22px; text-align:center; flex-shrink:0; margin-top:2px; }
.dtxt { font-size:13px; line-height:1.65; color:var(--text); }
.dtxt small { color:var(--muted); font-size:11px; }

#d-actions { flex-shrink:0; display:flex; gap:10px; padding:12px 16px; border-top:1px solid var(--border); }
.dbtn { flex:1; padding:13px; border-radius:14px; border:none; font-size:13px; font-weight:700; font-family:inherit; cursor:pointer; display:flex; align-items:center; justify-content:center; gap:5px; }
.dbtn-pri { background:#0f172a; color:#fff; }
.dbtn-sec { background:#f1f5f9; color:var(--text); }

/* マーカー */
.mkr { display:flex; align-items:center; justify-content:center; border-radius:50%; border:2.5px solid #fff; box-shadow:0 2px 8px rgba(0,0,0,.3); font-size:15px; cursor:pointer; }
.user-dot { width:16px; height:16px; border-radius:50%; background:#3b82f6; border:3px solid #fff; animation:pulse 2s infinite; box-shadow:0 0 0 0 rgba(59,130,246,.5); }
@keyframes pulse { 0%{box-shadow:0 0 0 0 rgba(59,130,246,.4)} 70%{box-shadow:0 0 0 10px rgba(59,130,246,0)} 100%{box-shadow:0 0 0 0 rgba(59,130,246,0)} }


/* 散歩ルート */
.route-tabs { display:flex; gap:8px; padding:12px 16px 6px; overflow-x:auto; scrollbar-width:none; }
.route-tabs::-webkit-scrollbar { display:none; }
.route-tab { flex:1; min-width:76px; padding:9px 10px; border-radius:14px; border:1.5px solid var(--border); background:#fff; font-size:12px; font-weight:800; color:var(--muted); cursor:pointer; font-family:inherit; }
.route-tab.on { background:#0f172a; color:#fff; border-color:#0f172a; }
.route-intro { padding:4px 16px 8px; font-size:12px; color:var(--muted); line-height:1.6; }
.route-card { margin:10px 16px; padding:14px; border:1.5px solid var(--border); border-radius:18px; background:#fff; box-shadow:0 1px 8px rgba(0,0,0,.06); cursor:pointer; }
.route-card.active { border-color:#0f172a; box-shadow:0 3px 14px rgba(15,23,42,.18); }
.route-title { display:flex; justify-content:space-between; gap:10px; align-items:flex-start; }
.route-name { font-size:15px; font-weight:900; color:var(--text); line-height:1.35; }
.route-time { flex-shrink:0; background:#f1f5f9; border-radius:14px; padding:5px 10px; font-size:12px; font-weight:900; color:#0f172a; }
.route-mood { margin-top:6px; font-size:12px; color:var(--muted); line-height:1.55; }
.route-meta { display:flex; gap:6px; flex-wrap:wrap; margin-top:10px; }
.route-pill { font-size:10px; font-weight:800; padding:4px 8px; border-radius:999px; background:#f0fdf4; color:#065f46; }
.route-pill.hot { background:#fee2e2; color:#991b1b; }
.route-steps { margin-top:10px; padding-top:10px; border-top:1px dashed var(--border); font-size:12px; color:#334155; line-height:1.7; }
.route-actions { display:flex; gap:8px; margin-top:10px; }
.route-btn { flex:1; border:none; border-radius:12px; padding:10px; font-size:12px; font-weight:800; font-family:inherit; cursor:pointer; }
.route-btn.primary { background:#0f172a; color:#fff; }
.route-btn.secondary { background:#f1f5f9; color:#0f172a; }
.route-legend { position:fixed; left:12px; bottom:86px; z-index:320; background:#fff; border-radius:14px; padding:8px 10px; box-shadow:0 2px 12px rgba(0,0,0,.15); font-size:11px; font-weight:800; color:#334155; display:none; }
.route-legend.show { display:block; }
.route-stop-label { background:#fff; border:2px solid #0f172a; border-radius:50%; width:24px; height:24px; display:flex; align-items:center; justify-content:center; font-size:11px; font-weight:900; box-shadow:0 1px 6px rgba(0,0,0,.25); }

</style>
</head>
<body>

<div id="map"></div>
<button id="btn-locate" onclick="locate()">📍</button>
<div id="route-legend" class="route-legend">🟣 選択中の散歩ルート</div>

<div id="topbar">
  <div id="searchbox">
    <span class="app-name">🌿 かげさんぽ</span>
    <input id="q" type="text" placeholder="スポットを検索…" oninput="onSearch()" autocomplete="off">
    <span class="temp-badge" id="tbadge">🌡️ --°C</span>
  </div>
  <div id="chips">
    <div class="chip on" data-f="all"      onclick="setF('all',this)">🗺️ すべて</div>
    <div class="chip"    data-f="shade"    onclick="setF('shade',this)">🌳 日陰</div>
    <div class="chip"    data-f="danger"   onclick="setF('danger',this)">☀️ 日向危険</div>
    <div class="chip"    data-f="vending"  onclick="setF('vending',this)">🥤 自販機</div>
    <div class="chip"    data-f="shop"     onclick="setF('shop',this)">🏪 お店</div>
    <div class="chip"    data-f="hospital" onclick="setF('hospital',this)">🏥 病院</div>
    <div class="chip"    data-f="rest"     onclick="setF('rest',this)">🪑 休憩</div>
    <div class="chip"    data-f="route"    onclick="setRouteMode...
