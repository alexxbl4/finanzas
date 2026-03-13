<!DOCTYPE html>

<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>MoonTrade</title>
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700;800;900&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg0:#07090e;--bg1:#0d1219;--bg2:#121820;--bg3:#18202c;--bg4:#1e2835;
  --b1:rgba(255,255,255,0.06);--b2:rgba(255,255,255,0.11);--b3:rgba(255,255,255,0.18);
  --acc:#b8f03c;--acc2:rgba(184,240,60,0.12);--acc3:rgba(184,240,60,0.20);
  --grn:#2dda7a;--grn2:rgba(45,218,122,0.12);
  --red:#f05050;--red2:rgba(240,80,80,0.12);
  --amb:#f0a830;--amb2:rgba(240,168,48,0.12);
  --t1:#dce8f5;--t2:#6e8299;--t3:#35485a;
  --r1:8px;--r2:12px;--r3:16px;
  --sans:'Montserrat',sans-serif;--mono:'JetBrains Mono',monospace
}
html{scroll-behavior:smooth}
body{
  background:var(--bg0);color:var(--t1);font-family:var(--sans);
  -webkit-font-smoothing:antialiased;min-height:100vh;
  display:flex;flex-direction:column;max-width:480px;margin:0 auto
}
.topbar{
  background:var(--bg1);border-bottom:1px solid var(--b1);
  display:flex;align-items:center;justify-content:space-between;
  padding:0 18px;height:52px;flex-shrink:0;
  position:sticky;top:0;z-index:100
}
.logo-wrap{display:flex;align-items:center;gap:8px}
.logo-mark{width:28px;height:28px;background:var(--acc);border-radius:7px;display:flex;align-items:center;justify-content:center}
.logo-mark svg{width:14px;height:14px}
.logo-txt{font-size:16px;font-weight:800;letter-spacing:-0.3px}
.logo-txt span{color:var(--acc)}
.page-badge{font-size:11px;font-weight:600;color:var(--t2);letter-spacing:0.4px}
.content{flex:1;overflow-y:auto;overflow-x:hidden;-webkit-overflow-scrolling:touch}
.page{display:none;padding:18px 16px 100px;animation:fi 0.2s ease}
.page.on{display:block}
@keyframes fi{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}
.nav{background:var(--bg1);border-top:1px solid var(--b1);display:flex;align-items:stretch;height:62px;position:sticky;bottom:0;z-index:100;flex-shrink:0}
.ni{flex:1;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:3px;cursor:pointer;color:var(--t3);transition:color 0.15s;user-select:none;-webkit-tap-highlight-color:transparent}
.ni svg{width:20px;height:20px}
.ni span{font-size:9px;font-weight:700;letter-spacing:0.6px;text-transform:uppercase}
.ni.on{color:var(--acc)}
.ni-center{flex:0 0 64px}
.nadd{width:44px;height:44px;background:var(--acc);border-radius:13px;display:flex;align-items:center;justify-content:center;margin-bottom:2px;box-shadow:0 4px 16px var(--acc3)}
.nadd svg{width:20px;height:20px;color:#07090e}
.m2{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:12px}
.mc{background:var(--bg2);border:1px solid var(--b1);border-radius:var(--r2);padding:14px 13px}
.ml{font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:1.2px;color:var(--t3);margin-bottom:8px}
.mv{font-family:var(--mono);font-size:20px;font-weight:700;line-height:1;color:var(--t1)}
.mv.up{color:var(--grn)}.mv.dn{color:var(--red)}.mv.ac{color:var(--acc)}
.ms{font-family:var(--mono);font-size:10px;color:var(--t2);margin-top:5px}
.card{background:var(--bg2);border:1px solid var(--b1);border-radius:var(--r3);padding:16px;margin-bottom:12px}
.sec-h{display:flex;justify-content:space-between;align-items:center;margin-bottom:14px}
.sec-t{font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:1.3px;color:var(--t3)}
.sec-b{font-size:9px;font-weight:600;color:var(--t3);font-family:var(--mono)}
.cw{position:relative;width:100%}
.pg-t{font-size:22px;font-weight:800;letter-spacing:-0.5px;margin-bottom:4px}
.pg-s{font-size:12px;font-weight:500;color:var(--t2);margin-bottom:18px}
.fg{margin-bottom:14px}
.fg label{display:block;font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:1.2px;color:var(--t3);margin-bottom:7px}
.fg input,.fg select,.fg textarea{width:100%;background:var(--bg3);border:1px solid var(--b1);border-radius:var(--r1);padding:12px 14px;font-size:14px;font-weight:500;color:var(--t1);font-family:var(--sans);outline:none;transition:border-color 0.15s;-webkit-appearance:none;appearance:none}
.fg select{background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='6'%3E%3Cpath d='M0 0l5 6 5-6z' fill='%2335485a'/%3E%3C/svg%3E");background-repeat:no-repeat;background-position:right 14px center;padding-right:32px;cursor:pointer}
.fg select option{background:var(--bg3)}
.fg input:focus,.fg select:focus,.fg textarea:focus{border-color:var(--acc);background:var(--bg4)}
.fg input::placeholder,.fg textarea::placeholder{color:var(--t3);font-weight:400}
.fg textarea{resize:vertical;min-height:76px;line-height:1.5}
.f2{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.stgl{display:flex;gap:8px}
.sb{flex:1;padding:12px;border-radius:var(--r1);border:1px solid var(--b1);background:var(--bg3);color:var(--t2);font-size:12px;font-weight:700;font-family:var(--sans);letter-spacing:0.4px;cursor:pointer;text-align:center;display:flex;align-items:center;justify-content:center;gap:6px;transition:all 0.15s}
.sb.sl{background:var(--grn2);border-color:var(--grn);color:var(--grn)}
.sb.ss{background:var(--red2);border-color:var(--red);color:var(--red)}
.btn{display:flex;align-items:center;justify-content:center;gap:7px;padding:14px 18px;border-radius:var(--r2);font-size:13px;font-weight:700;font-family:var(--sans);letter-spacing:0.3px;cursor:pointer;border:1px solid transparent;transition:all 0.15s;width:100%}
.btn-a{background:var(--acc);color:var(--bg0)}
.btn-g{background:transparent;color:var(--t2);border-color:var(--b2)}
.btn-row{display:flex;gap:10px;margin-top:6px}
.btn-del{background:none;border:none;color:var(--t3);cursor:pointer;padding:6px;border-radius:6px;display:flex;align-items:center;justify-content:center;transition:all 0.15s}
.btn-del svg{width:14px;height:14px}
.btn-del:active{color:var(--red)}
.ti{background:var(--bg2);border:1px solid var(--b1);border-radius:var(--r2);padding:14px;margin-bottom:8px}
.tr1{display:flex;align-items:center;justify-content:space-between;margin-bottom:10px}
.tr2{display:flex;align-items:center;justify-content:space-between}
.tsw{display:flex;align-items:center;gap:10px}
.tic{width:36px;height:36px;border-radius:9px;background:var(--bg4);border:1px solid var(--b1);display:flex;align-items:center;justify-content:center;font-family:var(--mono);font-size:10px;font-weight:700;color:var(--acc);flex-shrink:0;letter-spacing:-0.5px}
.tsym{font-size:14px;font-weight:700;letter-spacing:-0.2px}
.tmeta{font-size:11px;color:var(--t2);margin-top:1px;font-weight:500}
.tpnl{font-family:var(--mono);font-size:15px;font-weight:700;text-align:right}
.tpnl.up{color:var(--grn)}.tpnl.dn{color:var(--red)}.tpnl.nu{color:var(--t2)}
.pr{display:flex;gap:14px;align-items:center}
.pi{display:flex;flex-direction:column;gap:2px}
.pl{font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:0.8px;color:var(--t3)}
.pv{font-family:var(--mono);font-size:12px;font-weight:500}
.tact{display:flex;align-items:center;gap:5px}
.badge{display:inline-flex;align-items:center;padding:3px 8px;border-radius:5px;font-size:10px;font-weight:700;font-family:var(--mono);letter-spacing:0.4px}
.bl{background:var(--grn2);color:var(--grn)}.bs{background:var(--red2);color:var(--red)}
.bo{background:var(--amb2);color:var(--amb)}.bw{background:var(--grn2);color:var(--grn)}.blo{background:var(--red2);color:var(--red)}
.lev{display:inline-flex;align-items:center;padding:2px 6px;border-radius:4px;font-size:9px;font-weight:700;font-family:var(--mono);background:var(--amb2);color:var(--amb);margin-left:4px}
.sr{display:flex;justify-content:space-between;align-items:center;padding:11px 0;border-bottom:1px solid var(--b1)}
.sr:last-child{border-bottom:none}
.sl2{font-size:12px;font-weight:500;color:var(--t2)}
.sv{font-family:var(--mono);font-size:13px;font-weight:700;color:var(--t1)}
.sv.up{color:var(--grn)}.sv.dn{color:var(--red)}.sv.ac{color:var(--acc)}
.hc{background:var(--bg2);border:1px solid var(--b1);border-radius:var(--r3);padding:16px;margin-bottom:10px}
.hh{display:flex;align-items:center;justify-content:space-between;margin-bottom:14px}
.hsym{font-size:20px;font-weight:800;letter-spacing:-0.4px}
.hbadges{display:flex;gap:6px;align-items:center}
.hg{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.hl{font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:1px;color:var(--t3);margin-bottom:3px}
.hv{font-family:var(--mono);font-size:13px;font-weight:600}
.pills{display:flex;gap:6px;overflow-x:auto;padding-bottom:4px;margin-bottom:14px;scrollbar-width:none}
.pills::-webkit-scrollbar{display:none}
.pill{flex-shrink:0;padding:6px 13px;border-radius:100px;border:1px solid var(--b1);background:transparent;color:var(--t2);font-size:11px;font-weight:600;font-family:var(--sans);cursor:pointer;transition:all 0.15s}
.pill.on{background:var(--acc2);border-color:var(--acc);color:var(--acc)}
.srch-w{position:relative;margin-bottom:14px}
.srch-w svg{position:absolute;left:12px;top:50%;transform:translateY(-50%);width:14px;height:14px;color:var(--t3);pointer-events:none}
.srch{width:100%;background:var(--bg2);border:1px solid var(--b1);border-radius:var(--r1);padding:10px 14px 10px 36px;font-size:13px;font-weight:500;color:var(--t1);font-family:var(--sans);outline:none;-webkit-appearance:none}
.srch:focus{border-color:var(--b2)}.srch::placeholder{color:var(--t3)}
.prev-box{background:var(--bg3);border:1px solid var(--b2);border-radius:var(--r2);padding:14px;margin-bottom:16px;display:none}
.prev-lbl{font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:1.2px;color:var(--t3);margin-bottom:8px}
.prev-pnl{font-family:var(--mono);font-size:28px;font-weight:700;margin-bottom:6px}
.prev-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-top:10px}
.prev-fl{font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:0.8px;color:var(--t3);margin-bottom:2px}
.prev-fv{font-family:var(--mono);font-size:13px;font-weight:600}
.drow{display:grid;grid-template-columns:120px 1fr;gap:16px;align-items:center}
.lgi{display:flex;align-items:center;gap:7px;padding:6px 0;border-bottom:1px solid var(--b1)}
.lgi:last-child{border-bottom:none}
.lgd{width:7px;height:7px;border-radius:2px;flex-shrink:0}
.lgn{font-size:12px;font-weight:600;flex:1}
.lgc{font-family:var(--mono);font-size:10px;color:var(--t2)}
.empty{text-align:center;padding:48px 20px}
.ei{width:46px;height:46px;border-radius:13px;background:var(--bg3);border:1px solid var(--b1);display:flex;align-items:center;justify-content:center;margin:0 auto 13px}
.ei svg{width:22px;height:22px;color:var(--t3)}
.et{font-size:14px;font-weight:700;color:var(--t2);margin-bottom:4px}
.es{font-size:12px;font-weight:500;color:var(--t3)}
.toast{position:fixed;bottom:80px;left:50%;transform:translateX(-50%) translateY(12px);max-width:480px;width:calc(100% - 32px);background:var(--bg3);border:1px solid var(--b2);border-radius:var(--r2);padding:12px 16px;font-size:13px;font-weight:600;display:flex;align-items:center;gap:10px;z-index:999;opacity:0;transition:all 0.25s cubic-bezier(0.34,1.56,0.64,1);pointer-events:none}
.toast.on{transform:translateX(-50%) translateY(0);opacity:1}
.toast.ok{border-color:var(--grn)}.toast.err{border-color:var(--red)}
.tdot{width:6px;height:6px;border-radius:50%;flex-shrink:0}
.toast.ok .tdot{background:var(--grn)}.toast.err .tdot{background:var(--red)}
::-webkit-scrollbar{width:4px}::-webkit-scrollbar-track{background:transparent}::-webkit-scrollbar-thumb{background:var(--bg4);border-radius:2px}
</style>
</head>
<body>

<header class="topbar">
  <div class="logo-wrap">
    <div class="logo-mark">
      <svg viewBox="0 0 14 14" fill="none">
        <path d="M7 1.5a5.5 5.5 0 1 0 0 11 5.5 5.5 0 0 0 0-11zm0 1.4A4.1 4.1 0 1 1 2.9 7 4.1 4.1 0 0 1 7 2.9z" fill="#07090e"/>
        <circle cx="7" cy="7" r="1.1" fill="#07090e"/>
        <path d="M9.5 4.5 7 7l-2-1.4" stroke="#07090e" stroke-width="1.1" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>
    <span class="logo-txt">Moon<span>Trade</span></span>
  </div>
  <span class="page-badge" id="tb-lbl">Dashboard</span>
</header>

<div class="content">

  <!-- DASHBOARD -->

  <div class="page on" id="p-dash">
    <div class="m2">
      <div class="mc"><div class="ml">PnL Total</div><div class="mv" id="m-pnl">$0.00</div><div class="ms" id="m-pct">—</div></div>
      <div class="mc"><div class="ml">Win Rate</div><div class="mv ac" id="m-wr">—</div><div class="ms" id="m-wl">0W · 0L</div></div>
      <div class="mc"><div class="ml">Mejor trade</div><div class="mv up" id="m-best">—</div><div class="ms" id="m-bsym">—</div></div>
      <div class="mc"><div class="ml">Peor trade</div><div class="mv dn" id="m-worst">—</div><div class="ms" id="m-wsym">—</div></div>
    </div>
    <div class="card">
      <div class="sec-h"><span class="sec-t">PnL Acumulado</span><span class="sec-b" id="d-ct">0 cerradas</span></div>
      <div class="cw" style="height:160px"><canvas id="c-pnl"></canvas></div>
    </div>
    <div class="card">
      <div class="sec-h"><span class="sec-t">Por activo</span></div>
      <div class="drow">
        <div class="cw" style="height:110px"><canvas id="c-don"></canvas></div>
        <div id="d-leg"></div>
      </div>
    </div>
    <div class="sec-h" style="margin-top:4px">
      <span class="sec-t">Últimas operaciones</span>
      <span class="sec-b" id="d-total">0 total</span>
    </div>
    <div id="d-rec"></div>
  </div>

  <!-- NUEVA -->

  <div class="page" id="p-new">
    <div class="pg-t">Nueva operación</div>
    <div class="pg-s">Registra los detalles del trade</div>
    <div class="prev-box" id="prev-box">
      <div class="prev-lbl">Vista previa · PnL estimado</div>
      <div class="prev-pnl" id="prev-pnl">—</div>
      <div class="prev-grid" id="prev-grid"></div>
    </div>
    <div class="card">
      <div class="fg"><label>Activo</label><input type="text" id="f-sym" placeholder="BTC, ETH, SOL..." autocomplete="off" oninput="this.value=this.value.toUpperCase();lp()"></div>
      <div class="fg"><label>Dirección</label>
        <div class="stgl">
          <button class="sb sl" id="btn-l" onclick="setSide('LONG')">
            <svg width="9" height="9" viewBox="0 0 9 9"><path d="M4.5 0l4.5 9H0z" fill="currentColor"/></svg>LONG
          </button>
          <button class="sb" id="btn-s" onclick="setSide('SHORT')">
            <svg width="9" height="9" viewBox="0 0 9 9"><path d="M4.5 9l4.5-9H0z" fill="currentColor"/></svg>SHORT
          </button>
        </div>
      </div>
      <div class="f2">
        <div class="fg"><label>Entrada ($)</label><input type="number" id="f-en" placeholder="0.00" step="any" min="0" oninput="lp()"></div>
        <div class="fg"><label>Salida ($)</label><input type="number" id="f-ex" placeholder="vacío = abierta" step="any" min="0" oninput="lp()"></div>
        <div class="fg"><label>Cantidad</label><input type="number" id="f-qt" placeholder="0.00" step="any" min="0" oninput="lp()"></div>
        <div class="fg"><label>Leverage</label><input type="number" id="f-lv" value="1" min="1" max="200" oninput="lp()"></div>
        <div class="fg"><label>Exchange</label><input type="text" id="f-exch" placeholder="Binance, Bybit..."></div>
        <div class="fg"><label>Fecha</label><input type="date" id="f-dt"></div>
      </div>
      <div class="fg"><label>Notas / Estrategia</label><textarea id="f-no" placeholder="Setup, razón de entrada, gestión del riesgo..."></textarea></div>
      <div class="btn-row">
        <button class="btn btn-a" onclick="addTrade()">Guardar operación</button>
        <button class="btn btn-g" style="width:auto;padding:14px 16px" onclick="clrForm()">
          <svg width="13" height="13" viewBox="0 0 13 13" fill="none"><path d="M1 1l11 11M12 1L1 12" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/></svg>
        </button>
      </div>
    </div>
  </div>

  <!-- HISTORIAL -->

  <div class="page" id="p-hist">
    <div class="pg-t">Historial</div>
    <div class="pg-s" id="h-sub">Todas las operaciones</div>
    <div class="pills">
      <button class="pill on" onclick="setF('all',this)">Todas</button>
      <button class="pill" onclick="setF('long',this)">LONG</button>
      <button class="pill" onclick="setF('short',this)">SHORT</button>
      <button class="pill" onclick="setF('open',this)">Abiertas</button>
      <button class="pill" onclick="setF('closed',this)">Cerradas</button>
      <button class="pill" onclick="setF('win',this)">WIN</button>
      <button class="pill" onclick="setF('loss',this)">LOSS</button>
    </div>
    <div class="srch-w">
      <svg viewBox="0 0 14 14" fill="none"><circle cx="6" cy="6" r="4.5" stroke="currentColor" stroke-width="1.4"/><path d="m9.5 9.5 3 3" stroke="currentColor" stroke-width="1.4" stroke-linecap="round"/></svg>
      <input class="srch" type="text" id="srch" placeholder="Buscar activo..." oninput="rHist()">
    </div>
    <div id="h-list"></div>
    <div id="h-emp" class="empty" style="display:none">
      <div class="ei"><svg viewBox="0 0 22 22" fill="none"><circle cx="10" cy="10" r="7" stroke="currentColor" stroke-width="1.4"/><path d="m15 15 4 4" stroke="currentColor" stroke-width="1.4" stroke-linecap="round"/></svg></div>
      <div class="et">Sin resultados</div><div class="es">Prueba otros filtros</div>
    </div>
  </div>

  <!-- PORTFOLIO -->

  <div class="page" id="p-port">
    <div class="pg-t">Portfolio</div>
    <div class="pg-s">Posiciones abiertas</div>
    <div id="p-list"></div>
    <div id="p-emp" class="empty" style="display:none">
      <div class="ei"><svg viewBox="0 0 22 22" fill="none"><rect x="2" y="7" width="18" height="12" rx="2" stroke="currentColor" stroke-width="1.4"/><path d="M7 7V5a4 4 0 0 1 8 0v2" stroke="currentColor" stroke-width="1.4" stroke-linecap="round"/></svg></div>
      <div class="et">Sin posiciones abiertas</div><div class="es">Registra un trade sin precio de salida</div>
    </div>
    <div class="sec-h" style="margin-top:6px"><span class="sec-t">Exposición por activo</span></div>
    <div class="card"><div class="cw" style="height:180px"><canvas id="c-exp"></canvas></div></div>
  </div>

  <!-- ESTADÍSTICAS -->

  <div class="page" id="p-stats">
    <div class="pg-t">Estadísticas</div>
    <div class="pg-s">Análisis de rendimiento</div>
    <div class="card"><div class="sec-h"><span class="sec-t">Rendimiento general</span></div><div id="s-gen"></div></div>
    <div class="card">
      <div class="sec-h"><span class="sec-t">LONG vs SHORT</span></div>
      <div class="cw" style="height:160px;margin-bottom:12px"><canvas id="c-ls"></canvas></div>
      <div id="s-ls"></div>
    </div>
    <div class="card"><div class="sec-h"><span class="sec-t">PnL por activo</span></div><div class="cw" style="height:200px"><canvas id="c-sym"></canvas></div></div>
    <div class="card"><div class="sec-h"><span class="sec-t">Actividad mensual</span></div><div class="cw" style="height:160px"><canvas id="c-mon"></canvas></div></div>
  </div>

</div>

<nav class="nav">
  <div class="ni on" id="ni-d" onclick="gp('dash',this,'Dashboard')">
    <svg viewBox="0 0 20 20" fill="none"><rect x="2" y="2" width="7" height="7" rx="1.5" stroke="currentColor" stroke-width="1.4"/><rect x="11" y="2" width="7" height="7" rx="1.5" stroke="currentColor" stroke-width="1.4"/><rect x="2" y="11" width="7" height="7" rx="1.5" stroke="currentColor" stroke-width="1.4"/><rect x="11" y="11" width="7" height="7" rx="1.5" stroke="currentColor" stroke-width="1.4"/></svg>
    <span>Inicio</span>
  </div>
  <div class="ni" id="ni-h" onclick="gp('hist',this,'Historial')">
    <svg viewBox="0 0 20 20" fill="none"><path d="M3 5h14M3 10h14M3 15h8" stroke="currentColor" stroke-width="1.4" stroke-linecap="round"/></svg>
    <span>Trades</span>
  </div>
  <div class="ni ni-center" id="ni-n" onclick="gp('new',this,'Nueva operación')">
    <div class="nadd"><svg viewBox="0 0 20 20" fill="none"><path d="M10 4v12M4 10h12" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg></div>
  </div>
  <div class="ni" id="ni-p" onclick="gp('port',this,'Portfolio')">
    <svg viewBox="0 0 20 20" fill="none"><rect x="2" y="7" width="16" height="11" rx="1.5" stroke="currentColor" stroke-width="1.4"/><path d="M7 7V5a3 3 0 0 1 6 0v2" stroke="currentColor" stroke-width="1.4" stroke-linecap="round"/></svg>
    <span>Portfolio</span>
  </div>
  <div class="ni" id="ni-s" onclick="gp('stats',this,'Estadísticas')">
    <svg viewBox="0 0 20 20" fill="none"><path d="M3 17V9M7 17V7M11 17V11M15 17V4M19 17H1" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/></svg>
    <span>Stats</span>
  </div>
</nav>

<div class="toast" id="toast"><div class="tdot"></div><span id="t-msg"></span></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>

<script>
function loadTrades(){try{return JSON.parse(localStorage.getItem('mt4')||'[]')}catch(e){return[]}}
function saveTrades(){try{localStorage.setItem('mt4',JSON.stringify(TR))}catch(e){}}
var TR=loadTrades(),filt='all',side='LONG',CH={};
var PAL=['#b8f03c','#2dda7a','#5b9cf6','#f0a830','#f05050','#a78bfa','#38bdf8','#fb7185','#4ade80','#facc15'];
function cpnl(t){if(!t.exit)return null;return(t.side==='LONG'?1:-1)*(t.exit-t.entry)*t.qty*(t.leverage||1)}
function fm(v,sg){if(sg===undefined)sg=true;if(v===null||v===undefined)return'—';var a=Math.abs(v);var s=a>=10000?'$'+(a/1000).toFixed(1)+'k':a>=1000?'$'+a.toLocaleString('en-US',{minimumFractionDigits:2,maximumFractionDigits:2}):'$'+a.toFixed(2);return sg?((v<0?'−':'+')+s):s}
function fp(v){if(!v&&v!==0)return'—';var n=parseFloat(v);return'$'+n.toLocaleString('en-US',{minimumFractionDigits:2,maximumFractionDigits:n<1?6:n<100?3:2})}
function dc(id){if(CH[id]){CH[id].destroy();delete CH[id]}}
function co(yf){return{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false}},scales:{y:{grid:{color:'rgba(255,255,255,0.03)'},ticks:{color:'#35485a',font:{family:"'JetBrains Mono'",size:9},callback:yf}},x:{grid:{display:false},ticks:{color:'#35485a',font:{family:"'JetBrains Mono'",size:9},maxTicksLimit:6}}}}}
var TT;
function toast(msg,ok){if(ok===undefined)ok=true;var el=document.getElementById('toast');document.getElementById('t-msg').textContent=msg;el.className='toast '+(ok?'ok':'err');el.classList.add('on');clearTimeout(TT);TT=setTimeout(function(){el.classList.remove('on')},3200)}
function gp(id,el,title){
  document.querySelectorAll('.page').forEach(function(p){p.classList.remove('on')});
  document.querySelectorAll('.ni').forEach(function(n){n.classList.remove('on')});
  document.getElementById('p-'+id).classList.add('on');
  el.classList.add('on');
  document.getElementById('tb-lbl').textContent=title;
  document.querySelector('.content').scrollTop=0;
  if(id==='dash')updDash();
  if(id==='hist')rHist();
  if(id==='port')rPort();
  if(id==='stats')rStats()
}
function setSide(s){
  side=s;
  document.getElementById('btn-l').className='sb'+(s==='LONG'?' sl':'');
  document.getElementById('btn-s').className='sb'+(s==='SHORT'?' ss':'');
  lp()
}
function clrForm(){
  ['f-sym','f-en','f-ex','f-qt','f-exch','f-no'].forEach(function(i){document.getElementById(i).value=''});
  document.getElementById('f-lv').value='1';
  document.getElementById('f-dt').value=new Date().toISOString().split('T')[0];
  setSide('LONG');
  document.getElementById('prev-box').style.display='none'
}
function addTrade(){
  var sym=document.getElementById('f-sym').value.trim().toUpperCase();
  var en=parseFloat(document.getElementById('f-en').value);
  var exv=document.getElementById('f-ex').value.trim();
  var ex=exv?parseFloat(exv):null;
  var qt=parseFloat(document.getElementById('f-qt').value);
  var lv=parseFloat(document.getElementById('f-lv').value)||1;
  var exch=document.getElementById('f-exch').value.trim();
  var no=document.getElementById('f-no').value.trim();
  var dt=document.getElementById('f-dt').value||new Date().toISOString().split('T')[0];
  if(!sym)return toast('El activo es obligatorio',false);
  if(!en||en<=0)return toast('Precio de entrada inválido',false);
  if(!qt||qt<=0)return toast('Cantidad inválida',false);
  var t={id:Date.now(),symbol:sym,side:side,entry:en,exit:ex,qty:qt,leverage:lv,exchange:exch,notes:no,date:dt};
  TR.unshift(t);saveTrades();
  var p=cpnl(t);
  toast(p!==null?'Guardado · PnL '+fm(p):'Operación abierta registrada',true);
  clrForm()
}
function lp(){
  var en=parseFloat(document.getElementById('f-en').value);
  var ex=parseFloat(document.getElementById('f-ex').value);
  var qt=parseFloat(document.getElementById('f-qt').value);
  var lv=parseFloat(document.getElementById('f-lv').value)||1;
  var pb=document.getElementById('prev-box');
  if(!en||!ex||!qt){pb.style.display='none';return}
  var p=(side==='LONG'?1:-1)*(ex-en)*qt*lv;
  var pct=((ex-en)/en*100*(side==='LONG'?1:-1)).toFixed(2);
  var up=p>=0;
  pb.style.display='block';
  var pe=document.getElementById('prev-pnl');
  pe.textContent=fm(p);pe.style.color=up?'var(--grn)':'var(--red)';
  document.getElementById('prev-grid').innerHTML='<div><div class="prev-fl">Retorno</div><div class="prev-fv" style="color:'+(up?'var(--grn)':'var(--red)')+'">'+(up?'+':'')+pct+'%</div></div><div><div class="prev-fl">Coste</div><div class="prev-fv">'+fm(en*qt,false)+'</div></div>'+(lv>1?'<div><div class="prev-fl">Lev.</div><div class="prev-fv" style="color:var(--amb)">×'+lv+'</div></div>':'')
}
function tCard(t,compact){
  if(compact===undefined)compact=false;
  var p=cpnl(t);
  var pcls=p===null?'nu':p>=0?'up':'dn';
  var stat=p===null?'<span class="badge bo">OPEN</span>':p>=0?'<span class="badge bw">WIN</span>':'<span class="badge blo">LOSS</span>';
  var lbg=t.leverage>1?'<span class="lev">×'+t.leverage+'</span>':'';
  var del=!compact?'<button class="btn-del" onclick="delT('+t.id+')"><svg viewBox="0 0 14 14" fill="none"><path d="M1 3h12M5 3V2a1 1 0 0 1 4 0v1M3.5 3l.8 8.5h5.4l.8-8.5" stroke="currentColor" stroke-width="1.2" stroke-linecap="round" stroke-linejoin="round"/></svg></button>':'';
  return '<div class="ti"><div class="tr1"><div class="tsw"><div class="tic">'+t.symbol.slice(0,3)+'</div><div><div class="tsym">'+t.symbol+'</div><div class="tmeta">'+t.date+(t.exchange?' · '+t.exchange:'')+'</div></div></div><div style="text-align:right"><div class="tpnl '+pcls+'">'+(p!==null?fm(p):'—')+'</div><div style="margin-top:3px">'+stat+'</div></div></div><div class="tr2"><div class="pr"><div class="pi"><div class="pl">Entrada</div><div class="pv">'+fp(t.entry)+'</div></div><div style="color:var(--t3);font-size:10px;margin-top:8px">→</div><div class="pi"><div class="pl">Salida</div><div class="pv">'+(t.exit?fp(t.exit):'<span style="color:var(--amb);font-size:11px">abierta</span>')+'</div></div><div class="pi"><div class="pl">Qty</div><div class="pv">'+t.qty+'</div></div></div><div class="tact"><span class="badge b'+t.side.toLowerCase()+'">'+t.side+'</span>'+lbg+del+'</div></div>'+(t.notes&&!compact?'<div style="font-size:11px;font-weight:500;color:var(--t3);padding-top:8px;border-top:1px solid var(--b1);margin-top:4px">'+t.notes+'</div>':'')+'</div>'
}
function updDash(){
  var cl=TR.filter(function(t){return t.exit});
  var pnls=cl.map(cpnl).filter(function(p){return p!==null});
  var ws=pnls.filter(function(p){return p>0}),ls=pnls.filter(function(p){return p<0});
  var tot=pnls.reduce(function(a,b){return a+b},0);
  var pe=document.getElementById('m-pnl');
  pe.textContent=fm(tot);pe.className='mv '+(tot>=0?'up':'dn');
  var inv=cl.reduce(function(a,t){return a+t.entry*t.qty},0);
  document.getElementById('m-pct').textContent=inv>0?(tot>=0?'+':'')+(tot/inv*100).toFixed(2)+'% ROI':'—';
  document.getElementById('m-wr').textContent=pnls.length?((ws.length/pnls.length)*100).toFixed(1)+'%':'—';
  document.getElementById('m-wl').textContent=ws.length+'W · '+ls.length+'L';
  document.getElementById('d-ct').textContent=cl.length+' cerradas';
  document.getElementById('d-total').textContent=TR.length+' total';
  if(pnls.length){var mx=Math.max.apply(null,pnls),mn=Math.min.apply(null,pnls);document.getElementById('m-best').textContent=fm(mx);document.getElementById('m-bsym').textContent=(cl[pnls.indexOf(mx)]||{}).symbol||'—';document.getElementById('m-worst').textContent=fm(mn);document.getElementById('m-wsym').textContent=(cl[pnls.indexOf(mn)]||{}).symbol||'—'}
  var sorted=[].concat(cl).sort(function(a,b){return a.date.localeCompare(b.date)});
  var cum=0,cumD=sorted.map(function(t){return parseFloat((cum+=cpnl(t)).toFixed(2))}),lbls=sorted.map(function(t){return t.date.slice(5)});
  dc('pnl');
  CH['pnl']=new Chart(document.getElementById('c-pnl'),{type:'line',data:{labels:lbls.length?lbls:['—'],datasets:[{data:cumD.length?cumD:[0],borderColor:tot>=0?'#2dda7a':'#f05050',backgroundColor:tot>=0?'rgba(45,218,122,0.06)':'rgba(240,80,80,0.06)',borderWidth:2,fill:true,tension:0.4,pointRadius:cumD.length>25?0:3,pointBackgroundColor:tot>=0?'#2dda7a':'#f05050',pointBorderColor:'#0d1219',pointBorderWidth:2}]},options:Object.assign({},co(function(v){return'$'+v.toFixed(0)}),{plugins:{legend:{display:false},tooltip:{callbacks:{label:function(c){return' '+fm(c.parsed.y)}}}}})});
  var bS={};TR.forEach(function(t){bS[t.symbol]=(bS[t.symbol]||0)+1});
  var sk=Object.keys(bS),sv=sk.map(function(s){return bS[s]}),tot2=sv.reduce(function(a,b){return a+b},0);
  dc('don');
  if(sk.length){CH['don']=new Chart(document.getElementById('c-don'),{type:'doughnut',data:{labels:sk,datasets:[{data:sv,backgroundColor:PAL.slice(0,sk.length),borderWidth:0,borderRadius:3}]},options:{responsive:true,maintainAspectRatio:false,cutout:'70%',plugins:{legend:{display:false}}}});document.getElementById('d-leg').innerHTML=sk.slice(0,6).map(function(s,i){return'<div class="lgi"><div class="lgd" style="background:'+PAL[i]+'"></div><span class="lgn">'+s+'</span><span class="lgc">'+bS[s]+' · '+((bS[s]/tot2)*100).toFixed(0)+'%</span></div>'}).join('')}else{document.getElementById('d-leg').innerHTML=''}
  var rec=TR.slice(0,5);
  document.getElementById('d-rec').innerHTML=rec.length?rec.map(function(t){return tCard(t,true)}).join(''):'<div class="empty"><div class="ei"><svg viewBox="0 0 22 22" fill="none"><path d="M8 11h6M8 15h4M6 4H4a2 2 0 0 0-2 2v13a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6a2 2 0 0 0-2-2h-2M8 4h6v2H8V4z" stroke="currentColor" stroke-width="1.4" stroke-linecap="round"/></svg></div><div class="et">Sin operaciones</div><div class="es">Registra tu primer trade</div></div>'
}
function setF(f,el){filt=f;document.querySelectorAll('.pill').forEach(function(p){p.classList.remove('on')});el.classList.add('on');rHist()}
function rHist(){
  var s=(document.getElementById('srch').value||'').toUpperCase();
  var fd=TR.filter(function(t){
    if(s&&!t.symbol.includes(s))return false;
    if(filt==='long'&&t.side!=='LONG')return false;
    if(filt==='short'&&t.side!=='SHORT')return false;
    if(filt==='open'&&t.exit)return false;
    if(filt==='closed'&&!t.exit)return false;
    if(filt==='win'){var p=cpnl(t);if(p===null||p<=0)return false}
    if(filt==='loss'){var p=cpnl(t);if(p===null||p>=0)return false}
    return true
  });
  document.getElementById('h-sub').textContent=fd.length+' operaciones encontradas';
  document.getElementById('h-emp').style.display=fd.length?'none':'block';
  document.getElementById('h-list').innerHTML=fd.map(function(t){return tCard(t,false)}).join('')
}
function delT(id){if(!confirm('¿Eliminar esta operación?'))return;TR=TR.filter(function(t){return t.id!==id});saveTrades();rHist();updDash()}
function rPort(){
  var op=TR.filter(function(t){return!t.exit});
  var pl=document.getElementById('p-list'),pe=document.getElementById('p-emp');
  if(!op.length){pl.innerHTML='';pe.style.display='block'}
  else{
    pe.style.display='none';
    pl.innerHTML=op.map(function(t){return'<div class="hc"><div class="hh"><div class="hsym">'+t.symbol+'</div><div class="hbadges"><span class="badge b'+t.side.toLowerCase()+'">'+t.side+'</span>'+(t.leverage>1?'<span class="lev">×'+t.leverage+'</span>':'')+(t.exchange?'<span style="font-size:10px;font-weight:600;color:var(--t3)">'+t.exchange+'</span>':'')+'</div></div><div class="hg"><div><div class="hl">Precio entrada</div><div class="hv">'+fp(t.entry)+'</div></div><div><div class="hl">Cantidad</div><div class="hv">'+t.qty+'</div></div><div><div class="hl">Coste total</div><div class="hv">'+fm(t.entry*t.qty,false)+'</div></div><div><div class="hl">Fecha</div><div class="hv" style="font-size:11px">'+t.date+'</div></div></div>'+(t.notes?'<div style="margin-top:10px;padding-top:9px;border-top:1px solid var(--b1);font-size:11px;font-weight:500;color:var(--t3)">'+t.notes+'</div>':'')+'</div>'}).join('')
  }
  var bS={};op.forEach(function(t){bS[t.symbol]=(bS[t.symbol]||0)+t.entry*t.qty});
  var sk=Object.keys(bS),sv=sk.map(function(s){return parseFloat(bS[s].toFixed(2))});
  dc('exp');CH['exp']=new Chart(document.getElementById('c-exp'),{type:'bar',data:{labels:sk.length?sk:['—'],datasets:[{data:sv.length?sv:[0],backgroundColor:PAL.slice(0,sk.length),borderWidth:0,borderRadius:5}]},options:co(function(v){return'$'+v.toLocaleString()})})
}
function rStats(){
  var cl=TR.filter(function(t){return t.exit});
  var pnls=cl.map(cpnl),ws=pnls.filter(function(p){return p>0}),ls=pnls.filter(function(p){return p<0});
  var tot=pnls.reduce(function(a,b){return a+b},0),gw=ws.reduce(function(a,b){return a+b},0),gl=Math.abs(ls.reduce(function(a,b){return a+b},0));
  var pf=gl>0?(gw/gl).toFixed(2):gw>0?'∞':'—';
  document.getElementById('s-gen').innerHTML=[['Operaciones totales',TR.length,''],['Cerradas',cl.length,''],['Abiertas',TR.filter(function(t){return!t.exit}).length,''],['Win rate',pnls.length?((ws.length/pnls.length)*100).toFixed(1)+'%':'—','ac'],['Profit factor',pf,''],['PnL total',fm(tot),tot>=0?'up':'dn'],['Media por trade',pnls.length?fm(tot/pnls.length):'—',tot>=0?'up':'dn'],['Avg. ganadora',ws.length?fm(gw/ws.length):'—','up'],['Avg. perdedora',ls.length?fm(ls.reduce(function(a,b){return a+b},0)/ls.length):'—','dn'],['Mejor trade',ws.length?fm(Math.max.apply(null,ws)):'—','up'],['Peor trade',ls.length?fm(Math.min.apply(null,ls)):'—','dn']].map(function(r){return'<div class="sr"><span class="sl2">'+r[0]+'</span><span class="sv '+r[2]+'">'+r[1]+'</span></div>'}).join('');
  var lo=cl.filter(function(t){return t.side==='LONG'}),sh=cl.filter(function(t){return t.side==='SHORT'});
  var lp=lo.map(cpnl),sp=sh.map(cpnl);
  dc('ls');CH['ls']=new Chart(document.getElementById('c-ls'),{type:'doughnut',data:{labels:['LONG','SHORT'],datasets:[{data:[lo.length||0,sh.length||0],backgroundColor:['#2dda7a','#f05050'],borderWidth:0,borderRadius:3}]},options:{responsive:true,maintainAspectRatio:false,cutout:'65%',plugins:{legend:{display:false}}}});
  document.getElementById('s-ls').innerHTML='<div class="sr"><span class="sl2" style="color:var(--grn)">LONG — '+lo.length+' trades</span><span class="sv up">'+(lp.length?fm(lp.reduce(function(a,b){return a+b},0)):'—')+'</span></div><div class="sr"><span class="sl2" style="color:var(--red)">SHORT — '+sh.length+' trades</span><span class="sv dn">'+(sp.length?fm(sp.reduce(function(a,b){return a+b},0)):'—')+'</span></div>';
  var sP={};cl.forEach(function(t){var p=cpnl(t);sP[t.symbol]=(sP[t.symbol]||0)+p});
  var sk2=Object.keys(sP).sort(function(a,b){return sP[b]-sP[a]}),sv2=sk2.map(function(s){return parseFloat(sP[s].toFixed(2))});
  dc('sym');CH['sym']=new Chart(document.getElementById('c-sym'),{type:'bar',data:{labels:sk2.length?sk2:['—'],datasets:[{data:sv2.length?sv2:[0],backgroundColor:sv2.map(function(v){return v>=0?'rgba(45,218,122,0.8)':'rgba(240,80,80,0.8)'}),borderWidth:0,borderRadius:5}]},options:co(function(v){return(v>=0?'+':'')+'$'+Math.abs(v).toFixed(0)})});
  var mo={};TR.forEach(function(t){var m=t.date.slice(0,7);mo[m]=(mo[m]||0)+1});
  var ms=Object.keys(mo).sort(),mv=ms.map(function(m){return mo[m]});
  dc('mon');CH['mon']=new Chart(document.getElementById('c-mon'),{type:'bar',data:{labels:ms.length?ms.map(function(m){return m.slice(5)+'/'+m.slice(2,4)}):['—'],datasets:[{data:mv.length?mv:[0],backgroundColor:'rgba(184,240,60,0.65)',borderWidth:0,borderRadius:5}]},options:co(function(v){return String(v)})})
}
document.getElementById('f-dt').value=new Date().toISOString().split('T')[0];
updDash();
</script>

</body>
</html>