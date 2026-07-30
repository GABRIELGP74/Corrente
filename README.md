(https://github.com/user-attachments/files/30527087/corrente-v7-login-contas.html)
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Corrente</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap');

:root{
  --bg:#0B0B0D;
  --surface:#151517;
  --surface-2:#1D1D20;
  --border:#26262A;
  --text:#F5F5F7;
  --dim:#9A9AA1;
  --faint:#5C5C61;
  --green:#34C759;
  --green-bg:rgba(52,199,89,0.13);
  --blue:#0A84FF;
  --blue-bg:rgba(10,132,255,0.13);
  --yellow:#FFD60A;
  --yellow-bg:rgba(255,214,10,0.13);
  --red:#FF453A;
  --red-bg:rgba(255,69,58,0.13);
}
*{box-sizing:border-box;-webkit-tap-highlight-color:transparent;}
html,body{margin:0;padding:0;}
body{
  background:var(--bg);color:var(--text);
  font-family:'Inter',-apple-system,sans-serif;
  min-height:100vh;-webkit-font-smoothing:antialiased;
  font-variant-numeric:tabular-nums;
}
#app{max-width:500px;margin:0 auto;padding:24px 18px 70px;}
.fade{animation:fadeIn .25s ease;}
@keyframes fadeIn{from{opacity:0;transform:translateY(4px);}to{opacity:1;transform:none;}}

.topbar{display:flex;justify-content:space-between;align-items:center;margin-bottom:20px;}
.brand{font-weight:800;font-size:17px;letter-spacing:-0.2px;}
.brand-dot{color:var(--blue);}

/* pills */
.pills{display:flex;gap:8px;overflow-x:auto;padding-bottom:4px;margin-bottom:22px;scrollbar-width:none;}
.pills::-webkit-scrollbar{display:none;}
.pill{
  flex:0 0 auto;padding:9px 15px;border-radius:22px;font-size:13px;font-weight:600;
  border:1px solid var(--border);color:var(--text);background:var(--surface);cursor:pointer;white-space:nowrap;
  transition:background .12s,color .12s,border-color .12s,transform .1s;
}
.pill:active{transform:scale(0.96);}
.pill.selected{background:var(--text);color:#000;border-color:var(--text);}
.pill.new{border-style:dashed;color:var(--dim);background:transparent;}

/* alerts */
.alerts{display:flex;flex-direction:column;gap:8px;margin-bottom:20px;}
.alert{
  display:flex;align-items:flex-start;gap:9px;background:var(--red-bg);border:1px solid rgba(255,69,58,0.25);
  border-radius:12px;padding:11px 13px;font-size:12.5px;color:#FFD3D0;line-height:1.4;
}
.alert.info{background:var(--blue-bg);border-color:rgba(10,132,255,0.25);color:#CFE6FF;}
.alert.warn{background:var(--yellow-bg);border-color:rgba(255,214,10,0.25);color:#FBEBB0;}

/* hero */
.hero-label{font-size:13px;color:var(--dim);font-weight:500;}
.hero-value{font-size:42px;font-weight:800;letter-spacing:-1px;margin-top:4px;}

/* metric grid (dashboard) */
.metric-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin:20px 0 26px;}
.metric-card{
  background:linear-gradient(180deg,#18181B,#131315);border:1px solid var(--border);border-radius:16px;
  padding:14px 15px;box-shadow:0 1px 0 rgba(255,255,255,0.03) inset;
}
.metric-label{font-size:11px;color:var(--dim);font-weight:600;text-transform:uppercase;letter-spacing:0.4px;}
.metric-value{font-size:19px;font-weight:700;margin-top:6px;letter-spacing:-0.3px;}
.metric-value.green{color:var(--green);}
.metric-value.blue{color:var(--blue);}
.metric-value.small{font-size:17px;}

.section-title{font-size:12px;font-weight:700;color:var(--dim);text-transform:uppercase;letter-spacing:0.5px;margin:26px 0 12px;}

/* category cards (todos view) */
.cat-cards{display:flex;flex-direction:column;gap:10px;}
.cat-card{
  background:linear-gradient(180deg,#18181B,#131315);border:1px solid var(--border);border-radius:16px;
  padding:15px 16px;cursor:pointer;transition:transform .1s,border-color .12s;
}
.cat-card:active{transform:scale(0.98);}
.cat-card:hover{border-color:#3a3a40;}
.cat-card-top{display:flex;justify-content:space-between;align-items:flex-start;}
.cat-card-left{display:flex;align-items:center;gap:12px;}
.cat-icon{width:42px;height:42px;border-radius:12px;background:var(--surface-2);display:flex;align-items:center;justify-content:center;font-size:19px;flex:0 0 auto;}
.cat-name{font-weight:700;font-size:15px;}
.cat-conta{font-size:11.5px;color:var(--dim);margin-top:2px;}
.cat-value{font-weight:700;font-size:16px;text-align:right;}
.cat-lucro{font-size:11.5px;color:var(--green);text-align:right;margin-top:3px;font-weight:600;}
.cat-meta-row{display:flex;gap:14px;margin-top:12px;padding-top:12px;border-top:1px solid var(--border);}
.cat-meta{font-size:11px;color:var(--dim);}
.cat-meta b{color:var(--text);font-weight:600;}

.card-new{
  border:1.5px dashed var(--border);border-radius:16px;padding:16px;text-align:center;
  color:var(--dim);font-size:13px;font-weight:600;cursor:pointer;
}
.card-new:hover{border-color:var(--blue);color:var(--blue);}

/* category detail header */
.cat-header{display:flex;align-items:center;gap:13px;margin:8px 0 4px;}
.cat-icon-big{font-size:26px;background:var(--surface-2);width:50px;height:50px;border-radius:14px;display:flex;align-items:center;justify-content:center;}
.cat-title{font-weight:800;font-size:23px;letter-spacing:-0.3px;}
.cat-sub{font-size:12px;color:var(--dim);margin-top:2px;}

/* distribution bar */
.dist-block{margin:18px 0;}
.dist-bar{display:flex;height:9px;border-radius:5px;overflow:hidden;background:var(--surface-2);}
.dist-seg{height:100%;}
.dist-legend{display:flex;flex-wrap:wrap;gap:14px;margin-top:10px;}
.dist-item{display:flex;align-items:center;gap:6px;font-size:12px;color:var(--dim);}
.dist-dot{width:8px;height:8px;border-radius:50%;}
.dist-item b{color:var(--text);font-weight:600;}

/* indicators grid */
.ind-grid{display:grid;grid-template-columns:1fr 1fr;gap:9px;margin:18px 0;}
.ind-tile{background:var(--surface);border:1px solid var(--border);border-radius:13px;padding:12px 13px;}
.ind-label{font-size:10.5px;color:var(--dim);font-weight:600;text-transform:uppercase;letter-spacing:0.3px;}
.ind-value{font-size:16px;font-weight:700;margin-top:5px;}

/* progress */
.progress-block{background:var(--surface);border:1px solid var(--border);border-radius:14px;padding:15px 16px;margin:18px 0;}
.progress-top{display:flex;justify-content:space-between;font-size:12px;color:var(--dim);margin-bottom:8px;}
.progress-top b{color:var(--text);font-weight:700;}
.progress-track{height:6px;background:var(--surface-2);border-radius:5px;overflow:hidden;}
.progress-fill{height:100%;background:var(--blue);border-radius:5px;transition:width .4s ease;}
.progress-fill.done{background:var(--green);}
.progress-note{font-size:12px;color:var(--dim);margin-top:9px;line-height:1.5;}
.progress-note b{color:var(--text);}
.progress-note.done b{color:var(--green);}

/* tabs */
.tabs{display:flex;gap:22px;margin:24px 0 14px;border-bottom:1px solid var(--border);}
.tab{padding-bottom:10px;font-size:13.5px;font-weight:700;color:var(--dim);cursor:pointer;border-bottom:2px solid transparent;margin-bottom:-1px;}
.tab.active{color:var(--text);border-color:var(--text);}
.tab-count{color:var(--faint);font-weight:600;}
.tab.active .tab-count{color:var(--dim);}

/* status badge */
.status-badge{display:inline-flex;align-items:center;gap:4px;font-size:10px;font-weight:700;padding:3px 8px;border-radius:20px;text-transform:uppercase;letter-spacing:0.2px;}

/* product rows */
.prod-row{border-bottom:1px solid var(--border);}
.prod-head{display:flex;justify-content:space-between;align-items:center;padding:13px 2px;cursor:pointer;gap:10px;}
.prod-left{display:flex;align-items:center;gap:11px;min-width:0;}
.prod-thumb{width:38px;height:38px;border-radius:10px;background:var(--surface-2);flex:0 0 auto;display:flex;align-items:center;justify-content:center;font-size:15px;overflow:hidden;}
.prod-thumb img{width:100%;height:100%;object-fit:cover;}
.prod-name{font-weight:600;font-size:14px;}
.prod-sub{font-size:11.5px;color:var(--dim);margin-top:2px;}
.prod-right{text-align:right;flex:0 0 auto;}
.prod-value{font-weight:700;font-size:14px;}
.prod-days{font-size:11px;color:var(--faint);margin-top:2px;}
.prod-detail{padding:2px 2px 16px;display:none;}
.prod-detail.open{display:block;}
.detail-line{display:flex;justify-content:space-between;font-size:12.5px;color:var(--dim);padding:5px 0;}
.detail-line b{color:var(--text);font-weight:600;}
.detail-photo{width:100%;max-height:160px;object-fit:cover;border-radius:12px;margin-bottom:10px;}
.stepper{display:flex;align-items:center;margin:12px 0 14px;}
.step-dot{width:8px;height:8px;border-radius:50%;background:var(--border);flex:0 0 auto;}
.step-dot.done{background:var(--blue);}
.step-line{flex:1;height:2px;background:var(--border);}
.step-line.done{background:var(--blue);}
.step-labels{display:flex;justify-content:space-between;font-size:9px;color:var(--faint);margin-top:5px;}
.step-labels span{flex:1;text-align:center;}
.step-labels span.done{color:var(--dim);}
.detail-actions{display:flex;gap:8px;margin-top:11px;flex-wrap:wrap;}

/* cash available block */
.cash-block{background:var(--green-bg);border:1px solid rgba(52,199,89,0.25);border-radius:14px;padding:13px 15px;margin-top:8px;}
.cash-title{font-size:11.5px;font-weight:700;color:var(--green);text-transform:uppercase;letter-spacing:0.3px;}
.cash-row{display:flex;justify-content:space-between;align-items:center;margin-top:9px;padding-top:9px;border-top:1px solid rgba(52,199,89,0.18);}
.cash-row:first-of-type{border-top:none;padding-top:0;margin-top:8px;}
.cash-name{font-size:13px;font-weight:600;}
.cash-value{font-size:13px;font-weight:700;color:var(--green);}

/* extrato feed */
.feed-row{display:flex;justify-content:space-between;padding:13px 2px;border-bottom:1px solid var(--border);gap:10px;}
.feed-row:last-child{border-bottom:none;}
.feed-date{font-size:10.5px;color:var(--faint);margin-bottom:3px;}
.feed-desc{font-size:13.5px;font-weight:600;}
.feed-note{font-size:11.5px;color:var(--dim);margin-top:2px;}
.feed-value{font-weight:700;font-size:13.5px;white-space:nowrap;}
.feed-value.pos{color:var(--green);}
.feed-value.pending{color:var(--red);}
.feed-value.out{color:var(--text);}

/* forms */
.btn{font-size:12.5px;font-weight:700;padding:9px 14px;border-radius:9px;border:none;cursor:pointer;}
.btn-primary{background:var(--blue);color:#fff;}
.btn-primary:hover{opacity:0.87;}
.btn-green{background:var(--green);color:#04240F;}
.btn-ghost{background:var(--surface-2);color:var(--text);}
.btn-add{
  width:100%;margin-top:16px;padding:13px;border-radius:12px;border:1.5px dashed var(--border);
  background:transparent;color:var(--dim);font-size:13px;font-weight:700;cursor:pointer;
}
.btn-add:hover{border-color:var(--blue);color:var(--blue);}
.form-card{background:var(--surface);border:1px solid var(--border);border-radius:14px;padding:15px;margin-top:14px;}
.form-title{font-size:11.5px;font-weight:700;color:var(--dim);text-transform:uppercase;letter-spacing:0.4px;margin-bottom:12px;}
.form-row{display:flex;gap:8px;margin-bottom:9px;}
.form-row>*{flex:1;}
label{display:block;font-size:11px;color:var(--dim);margin-bottom:4px;font-weight:600;}
input,select,textarea{
  width:100%;background:var(--surface-2);border:1px solid var(--border);color:var(--text);
  padding:9px 10px;border-radius:8px;font-family:'Inter',sans-serif;font-size:13.5px;
}
textarea{resize:vertical;min-height:44px;}
input::placeholder,textarea::placeholder{color:var(--faint);}
input:focus,select:focus,textarea:focus{outline:none;border-color:var(--blue);}
input[type="date"],select{color-scheme:dark;}
input[type="file"]{padding:7px 8px;font-size:12px;}
.icon-grid{display:flex;gap:7px;flex-wrap:wrap;}
.icon-opt{width:38px;height:38px;border-radius:10px;background:var(--surface-2);border:1.5px solid var(--border);display:flex;align-items:center;justify-content:center;font-size:16px;cursor:pointer;}
.icon-opt.picked{border-color:var(--blue);background:rgba(10,132,255,0.12);}
.form-actions{display:flex;gap:8px;margin-top:10px;}
.foto-preview-wrap{margin-top:6px;}
.foto-preview{width:64px;height:64px;border-radius:10px;object-fit:cover;display:none;background:var(--surface-2);}

.reserva-card{background:var(--surface);border:1px solid var(--border);border-radius:16px;padding:20px;margin-top:8px;text-align:center;}
.reserva-amount{font-size:30px;font-weight:800;margin:6px 0;}
.reserva-desc{font-size:12.5px;color:var(--dim);}

/* mapa */
.mapa-legend{display:flex;gap:12px;margin-bottom:14px;flex-wrap:wrap;}
.legend-item{display:flex;align-items:center;gap:6px;font-size:11px;color:var(--dim);}
.legend-dot{width:8px;height:8px;border-radius:50%;}
.mapa-wrap{overflow-x:auto;margin:0 -18px;padding:4px 18px 10px;-webkit-overflow-scrolling:touch;}
.mapa-wrap svg{display:block;}
.mapa-empty{font-size:12.5px;color:var(--dim);margin-top:14px;}

.hidden{display:none !important;}
.foot-note{text-align:center;color:var(--faint);font-size:11px;margin-top:34px;}

/* toasts */
.toast-container{
  position:fixed;left:0;right:0;bottom:0;z-index:1000;
  display:flex;flex-direction:column;align-items:center;gap:8px;
  padding:0 18px calc(18px + env(safe-area-inset-bottom));pointer-events:none;
}
.toast{
  max-width:460px;width:100%;background:var(--surface-2);border:1px solid var(--border);
  border-radius:13px;padding:12px 15px;font-size:13px;font-weight:600;color:var(--text);
  box-shadow:0 10px 30px -6px rgba(0,0,0,0.55);pointer-events:auto;
  display:flex;align-items:center;gap:9px;
  animation:toastIn .28s cubic-bezier(.2,.9,.3,1);
}
.toast.out{animation:toastOut .2s ease forwards;}
.toast.success{border-color:rgba(52,199,89,0.35);}
.toast.error{border-color:rgba(255,69,58,0.35);}
.toast-icon{font-size:15px;flex:0 0 auto;}
@keyframes toastIn{from{opacity:0;transform:translateY(14px) scale(.98);}to{opacity:1;transform:none;}}
@keyframes toastOut{to{opacity:0;transform:translateY(10px) scale(.98);}}
</style>
</head>
<body>
<div id="app"></div>
<div class="toast-container" id="toast-container"></div>

<script>
/* ---------------- status meta ---------------- */
const STATUS = {
  estoque:{label:'Em Estoque', emoji:'🔵', color:'#0A84FF', bg:'rgba(10,132,255,0.14)'},
  reservado:{label:'Reservado', emoji:'🟡', color:'#FFD60A', bg:'rgba(255,214,10,0.14)'},
  aguardando_pagamento:{label:'Aguardando Pagto', emoji:'🔴', color:'#FF453A', bg:'rgba(255,69,58,0.14)'},
  disponivel:{label:'Disponível', emoji:'🟢', color:'#34C759', bg:'rgba(52,199,89,0.14)'}
};
const ICONS = ['📱','🐂','🎧','📦','🚗','🏠','💻','👟','🛠️','💵'];

/* ---------------- state ---------------- */
function seedDemoData(){
  return {
    categories:[
      {
        id:'celulares', name:'Celulares', icon:'📱', type:'corrente', contaPrincipal:'C6 Bank',
        items:[
          {id:'a', name:'iPhone A', buyValue:3000, buyDate:'2025-08-20', fundedBy:null, sellValue:4200, sellDate:'2025-09-18', status:'disponivel', localizacao:null},
          {id:'b', name:'iPhone B', buyValue:3200, buyDate:'2025-08-28', fundedBy:null, sellValue:4400, sellDate:'2025-09-30', status:'disponivel', localizacao:null},
          {id:'c', name:'iPhone C', buyValue:4200, buyDate:'2025-09-18', fundedBy:'a', sellValue:5100, sellDate:'2025-11-02', status:'disponivel', localizacao:null},
          {id:'d', name:'iPhone D', buyValue:4400, buyDate:'2025-09-30', fundedBy:'b', sellValue:5600, sellDate:'2025-11-15', status:'disponivel', localizacao:null},
          {id:'e', name:'iPhone E', buyValue:3500, buyDate:'2025-10-10', fundedBy:null, sellValue:4600, sellDate:'2025-12-05', status:'disponivel', localizacao:null},
          {id:'f', name:'iPhone F', buyValue:5100, buyDate:'2025-11-02', fundedBy:'c', marketValue:5300, status:'estoque'},
          {id:'g', name:'iPhone G', buyValue:5600, buyDate:'2025-11-15', fundedBy:'d', marketValue:5800, status:'reservado'},
          {id:'h', name:'iPhone H', buyValue:4600, buyDate:'2025-12-05', fundedBy:'e', sellValue:5300, sellDate:'2026-07-20', status:'aguardando_pagamento'},
          {id:'i', name:'iPhone I', buyValue:3800, buyDate:'2026-01-08', fundedBy:null, marketValue:4000, status:'estoque'},
          {id:'m', name:'iPhone M', buyValue:4000, buyDate:'2025-07-01', fundedBy:null, sellValue:5200, sellDate:'2025-08-10', status:'disponivel', localizacao:'Espécie'}
        ]
      },
      {
        id:'gado', name:'Gado', icon:'🐂', type:'corrente', contaPrincipal:'Espécie',
        items:[
          {id:'g1', name:'Lote de gado A', buyValue:20000, buyDate:'2025-09-05', fundedBy:null, sellValue:26000, sellDate:'2026-01-10', status:'disponivel'},
          {id:'g2', name:'Lote de gado B', buyValue:26000, buyDate:'2026-01-10', fundedBy:'g1', marketValue:29000, status:'estoque'},
          {id:'g3', name:'Lote de gado C', buyValue:8000, buyDate:'2025-06-01', fundedBy:null, sellValue:15000, sellDate:'2025-10-01', status:'disponivel'}
        ]
      },
      {
        id:'fones', name:'Fones', icon:'🎧', type:'corrente', contaPrincipal:'Mercado Pago',
        items:[
          {id:'f1', name:'Lote fones bluetooth', buyValue:5000, buyDate:'2025-11-01', fundedBy:null, sellValue:6200, sellDate:'2026-01-01', status:'disponivel'},
          {id:'f2', name:'Fones — 2ª leva', buyValue:6200, buyDate:'2026-01-01', fundedBy:'f1', marketValue:6800, status:'estoque'}
        ]
      },
      {
        id:'poupanca', name:'Poupança', icon:'💰', type:'reserva', contaPrincipal:'Nubank', value:2000
      }
    ],
    contas:[{id:'c6', nome:'C6 Bank', tipo:'Banco'},{id:'esp', nome:'Espécie', tipo:'Espécie'},{id:'mp', nome:'Mercado Pago', tipo:'Carteira digital'},{id:'nu', nome:'Nubank', tipo:'Banco'}]
  };
}

let categories = [];
let contas = [];
let currentProfile = null;
let auth = {screen:'login', profiles:[], loading:true};

let view = {selected:'todos', tab:'produtos', expanded:null, formOpen:null, sellingId:null, draftFoto:null, draftIcon:ICONS[0]};


/* ---------------- helpers ---------------- */
const fmt = v => (v||0).toLocaleString('pt-BR',{style:'currency',currency:'BRL',maximumFractionDigits:0});
const fmtDateShort = d => { const [y,m,dd]=d.split('-'); const meses=['jan','fev','mar','abr','mai','jun','jul','ago','set','out','nov','dez']; return `${dd} ${meses[parseInt(m)-1]}`; };
const daysBetween = (a,b) => Math.round((new Date(b)-new Date(a))/86400000);
const today = () => new Date().toISOString().slice(0,10);
const contaIcon = s => {
  const registrada = contas.find(c=>c.nome.toLowerCase()===(s||'').toLowerCase());
  if(registrada){
    if(registrada.tipo==='Espécie') return '💵';
    if(registrada.tipo==='Carteira digital') return '💳';
    return '🏦';
  }
  return /esp[eé]cie/i.test(s||'') ? '💵' : '🏦';
};
const itemById = (cat,id) => cat.items.find(i=>i.id===id);
const usedAsFunding = (cat,id) => cat.items.some(i=>i.fundedBy===id);

function capitalInvestido(cat){ return cat.items.filter(i=>i.status==='estoque'||i.status==='reservado').reduce((s,i)=>s+i.buyValue,0); }
function capitalAReceber(cat){ return cat.items.filter(i=>i.status==='aguardando_pagamento').reduce((s,i)=>s+i.sellValue,0); }
function capitalDisponivelUnused(cat){ return cat.items.filter(i=>i.status==='disponivel' && !usedAsFunding(cat,i.id)).reduce((s,i)=>s+i.sellValue,0); }
function lucroRealizado(cat){ return cat.items.filter(i=>i.status==='aguardando_pagamento'||i.status==='disponivel').reduce((s,i)=>s+(i.sellValue-i.buyValue),0); }
function capitalInicial(cat){ return cat.items.filter(i=>!i.fundedBy).reduce((s,i)=>s+i.buyValue,0); }
function capitalTotalCategoria(cat){
  if(cat.type==='reserva') return cat.value;
  return capitalInvestido(cat)+capitalAReceber(cat)+capitalDisponivelUnused(cat);
}
function lastActivityDays(cat){
  const dates = cat.items.flatMap(i=>[i.buyDate, i.sellDate].filter(Boolean));
  if(!dates.length) return null;
  const max = dates.reduce((a,b)=> a>b?a:b);
  return daysBetween(max, today());
}

function itemLocal(cat, item){ return item.localizacao || cat.contaPrincipal || 'Sem conta'; }

function capitalPorConta(cat){
  const map = {};
  if(cat.type==='reserva'){ map[cat.contaPrincipal||'Sem conta'] = cat.value; return map; }
  cat.items.filter(i=>i.status==='disponivel' && !usedAsFunding(cat,i.id)).forEach(i=>{
    const loc = itemLocal(cat,i);
    map[loc] = (map[loc]||0) + i.sellValue;
  });
  return map;
}

function categoryHasEspecie(cat){
  const map = capitalPorConta(cat);
  return Object.keys(map).some(k=>/esp[eé]cie/i.test(k));
}

function accountBreakdownGlobal(){
  const map = {};
  categories.forEach(cat=>{
    const porConta = capitalPorConta(cat);
    Object.entries(porConta).forEach(([loc,val])=>{
      map[loc] = map[loc] || {total:0, sources:{}};
      map[loc].total += val;
      map[loc].sources[cat.name] = (map[loc].sources[cat.name]||0) + val;
    });
  });
  return map;
}

function ensureConta(nome){
  if(!nome) return;
  const exists = contas.some(c=>c.nome.toLowerCase()===nome.toLowerCase());
  if(!exists) contas.push({id:'ct'+Date.now()+Math.random().toString(36).slice(2,6), nome, tipo:/esp[eé]cie/i.test(nome)?'Espécie':'Banco'});
}

/* ---------------- persistência ---------------- */
async function loadProfiles(){
  try{ const r = await window.storage.get('corrente-profiles', false); return r? JSON.parse(r.value) : []; }
  catch(e){ return []; }
}
async function saveProfiles(){
  try{ await window.storage.set('corrente-profiles', JSON.stringify(auth.profiles), false); }
  catch(e){ console.error('Falha ao salvar perfis', e); }
}
async function loadProfileData(nome){
  try{ const r = await window.storage.get('corrente-data-'+nome.toLowerCase(), false); return r? JSON.parse(r.value) : null; }
  catch(e){ return null; }
}
async function saveProfileData(){
  if(!currentProfile) return;
  try{ await window.storage.set('corrente-data-'+currentProfile.toLowerCase(), JSON.stringify({categories, contas}), false); }
  catch(e){ console.error('Falha ao salvar dados', e); }
}

/* global metrics */
function globalPatrimonio(){ return categories.reduce((s,c)=>s+capitalTotalCategoria(c),0); }
function globalDisponivel(){ return categories.reduce((s,c)=> s + (c.type==='reserva'?c.value:capitalDisponivelUnused(c)), 0); }
function globalInvestido(){ return categories.filter(c=>c.type==='corrente').reduce((s,c)=>s+capitalInvestido(c),0); }
function globalAReceber(){ return categories.filter(c=>c.type==='corrente').reduce((s,c)=>s+capitalAReceber(c),0); }
function globalLucro(){ return categories.filter(c=>c.type==='corrente').reduce((s,c)=>s+lucroRealizado(c),0); }
function globalQtdProdutos(){ return categories.filter(c=>c.type==='corrente').reduce((s,c)=>s+c.items.length,0); }

/* alerts */
function buildAlerts(){
  const alerts = [];
  categories.forEach(cat=>{
    if(cat.type!=='corrente') return;
    const receber = capitalAReceber(cat);
    if(receber>0) alerts.push({type:'alert', text:`🔴 ${fmt(receber)} aguardando pagamento em ${cat.name}`});
    cat.items.filter(i=>i.status==='estoque'||i.status==='reservado').forEach(i=>{
      const d = daysBetween(i.buyDate, today());
      if(d>45) alerts.push({type:'warn', text:`🕓 ${i.name} está parado há ${d} dias em ${cat.name}`});
    });
    if(/esp[eé]cie/i.test(cat.contaPrincipal||'')){
      const cash = capitalDisponivelUnused(cat);
      if(cash>10000) alerts.push({type:'warn', text:`💵 ${fmt(cash)} parado em espécie em ${cat.name} — considera guardar num banco`});
    }
    const inactivity = lastActivityDays(cat);
    if(inactivity!==null && inactivity>90) alerts.push({type:'info', text:`💤 ${cat.name} sem movimentação há ${inactivity} dias`});
  });
  return alerts;
}

/* ---------------- toast ---------------- */
function showToast(message, type){
  const container = document.getElementById('toast-container');
  const el = document.createElement('div');
  el.className = 'toast ' + type;
  el.innerHTML = `<span class="toast-icon">${type==='success'?'✅':'⚠️'}</span><span>${message}</span>`;
  container.appendChild(el);
  setTimeout(()=>{
    el.classList.add('out');
    setTimeout(()=> el.remove(), 220);
  }, 2800);
}

/* ---------------- autenticação (perfil local do protótipo) ---------------- */
function renderAuth(){
  const app = document.getElementById('app');
  const isSignup = auth.screen==='signup';
  const hint = auth.profiles.length===0 ? `<div class="progress-note" style="margin-bottom:14px;">Nenhum perfil cadastrado ainda neste protótipo — crie o seu abaixo.</div>` : '';
  app.innerHTML = `
    <div class="fade" style="padding-top:18vh;max-width:360px;margin:0 auto;">
      <div class="brand" style="font-size:22px;text-align:center;margin-bottom:4px;">Corrente<span class="brand-dot">.</span></div>
      <div style="text-align:center;color:var(--dim);font-size:12.5px;margin-bottom:26px;">${isSignup?'Criar perfil':'Entrar'}</div>
      ${hint}
      <div class="form-card">
        <div class="form-row"><div><label>Nome</label><input type="text" id="auth-nome" placeholder="seu nome"/></div></div>
        <div class="form-row"><div><label>Senha</label><input type="password" id="auth-senha" placeholder="sua senha"/></div></div>
        ${isSignup?`<div class="form-row"><div><label>Confirmar senha</label><input type="password" id="auth-senha2" placeholder="repita a senha"/></div></div>`:''}
        <div class="form-actions" style="margin-top:4px;">
          <button class="btn btn-primary" data-auth-submit="1" style="flex:1;">${isSignup?'Criar perfil e entrar':'Entrar'}</button>
        </div>
      </div>
      <div style="text-align:center;margin-top:16px;font-size:12.5px;color:var(--dim);">
        ${isSignup?'Já tem perfil?':'Ainda não tem perfil?'}
        <span data-auth-switch="1" style="color:var(--blue);cursor:pointer;font-weight:600;">${isSignup?'Entrar':'Criar um novo'}</span>
      </div>
      <div style="text-align:center;margin-top:22px;font-size:11px;color:var(--faint);line-height:1.5;">
        Protótipo — isso separa os dados de cada pessoa durante os testes,<br/>não é uma autenticação segura de verdade.
      </div>
    </div>
    <div class="toast-container" id="toast-container-auth"></div>
  `;
  document.querySelectorAll('[data-auth-switch]').forEach(el=>{
    el.onclick = ()=>{ auth.screen = isSignup ? 'login' : 'signup'; renderAuth(); };
  });
  const submitBtn = document.querySelector('[data-auth-submit]');
  if(submitBtn) submitBtn.onclick = async ()=>{
    const nome = document.getElementById('auth-nome').value.trim();
    const senha = document.getElementById('auth-senha').value;
    if(!nome || !senha){ authToast('Preencha nome e senha.', 'error'); return; }

    if(isSignup){
      const senha2 = document.getElementById('auth-senha2').value;
      if(senha!==senha2){ authToast('As senhas não conferem.', 'error'); return; }
      if(auth.profiles.some(p=>p.nome.toLowerCase()===nome.toLowerCase())){ authToast('Já existe um perfil com esse nome.', 'error'); return; }
      auth.profiles.push({nome, senha});
      await saveProfiles();
      categories = []; contas = [];
      currentProfile = nome;
      await saveProfileData();
      view = {selected:'todos', tab:'produtos', expanded:null, formOpen:null, sellingId:null, draftFoto:null, draftIcon:ICONS[0]};
      render();
    } else {
      const perfil = auth.profiles.find(p=>p.nome.toLowerCase()===nome.toLowerCase());
      if(!perfil || perfil.senha!==senha){ authToast('Nome ou senha incorretos.', 'error'); return; }
      const data = await loadProfileData(nome);
      categories = data ? data.categories : [];
      contas = data ? data.contas : [];
      currentProfile = perfil.nome;
      view = {selected:'todos', tab:'produtos', expanded:null, formOpen:null, sellingId:null, draftFoto:null, draftIcon:ICONS[0]};
      render();
    }
  };
}
function authToast(message, type){
  const container = document.getElementById('toast-container-auth');
  if(!container) return;
  const el = document.createElement('div');
  el.className = 'toast ' + type;
  el.innerHTML = `<span class="toast-icon">${type==='success'?'✅':'⚠️'}</span><span>${message}</span>`;
  container.appendChild(el);
  setTimeout(()=>{ el.classList.add('out'); setTimeout(()=> el.remove(), 220); }, 2800);
}

/* ---------------- render root ---------------- */
function render(){
  const app = document.getElementById('app');
  let inner;
  if(view.selected==='todos') inner = renderDashboard();
  else if(view.selected==='contas') inner = renderContas();
  else inner = renderCategoria(view.selected);
  app.innerHTML = `<div class="fade">${inner}</div>`;
  bindEvents();
}

function pillsHtml(){
  const pills = categories.map(c=>{
    const sel = view.selected===c.id ? 'selected':'';
    const especieTag = categoryHasEspecie(c) ? ' 💵' : '';
    return `<div class="pill ${sel}" data-select="${c.id}">${c.icon} ${c.name}${especieTag}</div>`;
  }).join('');
  const todosSel = view.selected==='todos' ? 'selected':'';
  const contasSel = view.selected==='contas' ? 'selected':'';
  return `<div class="pills">
    <div class="pill ${todosSel}" data-select="todos">Todos</div>
    <div class="pill ${contasSel}" data-select="contas">🏦 Contas</div>
    ${pills}
    <div class="pill new" data-new-cat="1">+ novo portfólio</div>
  </div>`;
}

function alertsHtml(){
  const a = buildAlerts();
  if(!a.length) return '';
  return `
    <div class="section-title">Alertas</div>
    <div class="alerts">${a.map(x=>`<div class="alert ${x.type==='alert'?'':x.type}">${x.text}</div>`).join('')}</div>
  `;
}

/* ---------------- contas (onde o dinheiro está guardado) ---------------- */
function renderContas(){
  const map = accountBreakdownGlobal();
  const allNames = Array.from(new Set([...contas.map(c=>c.nome), ...Object.keys(map)]));
  const entries = allNames.map(name=>[name, map[name] || {total:0, sources:{}}]).sort((a,b)=>b[1].total-a[1].total);
  const totalAll = entries.reduce((s,[,v])=>s+v.total,0);

  const cards = entries.map(([name,data])=>{
    const sourcesHtml = Object.entries(data.sources).map(([catName,amt])=>
      `<div class="dist-item">${catName}: <b>${fmt(amt)}</b></div>`
    ).join('') || `<div class="dist-item" style="color:var(--faint);">ainda sem valores aqui</div>`;
    return `<div class="cat-card">
      <div class="cat-card-top">
        <div class="cat-card-left">
          <div class="cat-icon">${contaIcon(name)}</div>
          <div><div class="cat-name">${name}</div><div class="cat-conta">${Object.keys(data.sources).length} portfólio(s) usando essa conta</div></div>
        </div>
        <div class="cat-value">${fmt(data.total)}</div>
      </div>
      <div class="dist-legend" style="margin-top:12px;padding-top:12px;border-top:1px solid var(--border);">${sourcesHtml}</div>
    </div>`;
  }).join('') || `<div class="progress-note">Nenhuma conta cadastrada ainda.</div>`;

  const newContaForm = view.newContaForm ? `
    <div class="form-card">
      <div class="form-title">Nova conta</div>
      <div class="form-row"><div><label>Nome do banco/conta *</label><input type="text" id="conta-nome" placeholder="ex: Banco Inter, Carteira"/></div></div>
      <div class="form-row"><div><label>Tipo</label>
        <select id="conta-tipo">
          <option value="Banco">Banco</option>
          <option value="Carteira digital">Carteira digital</option>
          <option value="Espécie">Espécie</option>
          <option value="Outro">Outro</option>
        </select>
      </div></div>
      <div class="form-actions">
        <button class="btn btn-primary" data-confirm-new-conta="1">Adicionar conta</button>
        <button class="btn btn-ghost" data-cancel-new-conta="1">Cancelar</button>
      </div>
    </div>
  ` : `<button class="btn-add" data-open-new-conta="1">+ Nova conta</button>`;

  return `
    <div class="topbar"><div class="brand">Corrente<span class="brand-dot">.</span></div><div style="display:flex;align-items:center;gap:10px;"><span style="font-size:11.5px;color:var(--dim);">${currentProfile}</span><span data-logout="1" style="font-size:11.5px;color:var(--dim);text-decoration:underline;cursor:pointer;">Sair</span></div></div>
    ${pillsHtml()}
    <div class="hero-label">Total guardado (disponível)</div>
    <div class="hero-value">${fmt(totalAll)}</div>
    <div class="section-title">Por conta / local</div>
    <div class="cat-cards">${cards}</div>
    ${newContaForm}
    <div class="foot-note">soma do dinheiro já disponível de cada portfólio, agrupado por onde está guardado</div>
  `;
}

/* ---------------- dashboard (todos) ---------------- */
function renderDashboard(){
  const total = globalPatrimonio();

  const newCatForm = view.newCatForm ? renderNewCatForm() : '';

  const cards = categories.map(cat=>{
    const val = capitalTotalCategoria(cat);
    if(cat.type==='reserva'){
      return `<div class="cat-card" data-select="${cat.id}">
        <div class="cat-card-top">
          <div class="cat-card-left">
            <div class="cat-icon">${cat.icon}</div>
            <div><div class="cat-name">${cat.name}</div><div class="cat-conta">${contaIcon(cat.contaPrincipal)} ${cat.contaPrincipal||'—'}</div></div>
          </div>
          <div><div class="cat-value">${fmt(val)}</div><div class="cat-lucro" style="color:var(--dim);">reserva</div></div>
        </div>
      </div>`;
    }
    const lucro = lucroRealizado(cat);
    const qtd = cat.items.length;
    return `<div class="cat-card" data-select="${cat.id}">
      <div class="cat-card-top">
        <div class="cat-card-left">
          <div class="cat-icon">${cat.icon}</div>
          <div><div class="cat-name">${cat.name}</div><div class="cat-conta">${contaIcon(cat.contaPrincipal)} ${cat.contaPrincipal||'—'}</div></div>
        </div>
        <div><div class="cat-value">${fmt(val)}</div><div class="cat-lucro">+${fmt(lucro)}</div></div>
      </div>
      <div class="cat-meta-row">
        <div class="cat-meta"><b>${qtd}</b> produtos</div>
        <div class="cat-meta"><b>${cat.items.filter(i=>i.status==='estoque'||i.status==='reservado').length}</b> em estoque</div>
      </div>
    </div>`;
  }).join('');

  return `
    <div class="topbar"><div class="brand">Corrente<span class="brand-dot">.</span></div><div style="display:flex;align-items:center;gap:10px;"><span style="font-size:11.5px;color:var(--dim);">${currentProfile}</span><span data-logout="1" style="font-size:11.5px;color:var(--dim);text-decoration:underline;cursor:pointer;">Sair</span></div></div>
    ${pillsHtml()}
    <div class="hero-label">Patrimônio total</div>
    <div class="hero-value">${fmt(total)}</div>

    <div class="metric-grid">
      <div class="metric-card"><div class="metric-label">Disponível</div><div class="metric-value green">${fmt(globalDisponivel())}</div></div>
      <div class="metric-card"><div class="metric-label">Investido</div><div class="metric-value blue">${fmt(globalInvestido())}</div></div>
      <div class="metric-card"><div class="metric-label">A Receber</div><div class="metric-value small">${fmt(globalAReceber())}</div></div>
      <div class="metric-card"><div class="metric-label">Lucro Acumulado</div><div class="metric-value green">${fmt(globalLucro())}</div></div>
      <div class="metric-card"><div class="metric-label">Categorias</div><div class="metric-value">${categories.length}</div></div>
      <div class="metric-card"><div class="metric-label">Produtos</div><div class="metric-value">${globalQtdProdutos()}</div></div>
    </div>

    <div class="section-title">Seus portfólios</div>
    ${categories.length===0 ? `
      <div class="form-card">
        <div class="form-title">Nenhum portfólio ainda</div>
        <div class="progress-note" style="margin-bottom:12px;">Comece cadastrando seu primeiro portfólio real, ou carregue os dados de exemplo pra explorar o app.</div>
        <div class="form-actions">
          <button class="btn btn-primary" data-new-cat="1">+ Primeiro portfólio</button>
          <button class="btn btn-ghost" data-load-demo="1">Carregar dados de exemplo</button>
        </div>
      </div>
    ` : `
      <div class="cat-cards">
        ${cards}
        <div class="card-new" data-new-cat="1">+ Adicionar novo portfólio</div>
      </div>
    `}
    ${newCatForm}
    ${alertsHtml()}
    <div class="foot-note">dados fictícios · protótipo</div>
  `;
}

function renderNewCatForm(){
  const iconOpts = ICONS.map(ic=>`<div class="icon-opt ${view.draftIcon===ic?'picked':''}" data-pick-icon="${ic}">${ic}</div>`).join('');
  const contaOpts = contas.map(c=>`<option value="${c.nome}">${contaIcon(c.nome)} ${c.nome}</option>`).join('');
  return `
    <div class="form-card">
      <div class="form-title">Novo portfólio</div>
      <div class="form-row"><div><label>Nome *</label><input type="text" id="nc-name" placeholder="ex: Motos"/></div></div>
      <div class="form-row">
        <div><label>Tipo</label>
          <select id="nc-tipo">
            <option value="corrente">Corrente (compra/venda)</option>
            <option value="reserva">Reserva parada</option>
          </select>
        </div>
        <div><label>Conta principal *</label>
          <select id="nc-conta">
            <option value="">Selecione...</option>
            ${contaOpts}
            <option value="__new__">+ Nova conta...</option>
          </select>
        </div>
      </div>
      <div class="form-row" id="nc-conta-new-wrap" style="display:none;"><div><label>Nome da nova conta</label><input type="text" id="nc-conta-new" placeholder="ex: Banco Inter"/></div></div>
      <div class="form-row"><div><label>Valor inicial *</label><input type="number" id="nc-valor" placeholder="ex: 10000"/></div></div>
      <label>Ícone</label>
      <div class="icon-grid">${iconOpts}</div>
      <div class="form-actions">
        <button class="btn btn-primary" data-confirm-new-cat="1">Criar portfólio</button>
        <button class="btn btn-ghost" data-cancel-new-cat="1">Cancelar</button>
      </div>
    </div>
  `;
}

/* ---------------- category detail ---------------- */
function renderCategoria(catId){
  const cat = categories.find(c=>c.id===catId);

  if(cat.type==='reserva'){
    return `
      <div class="topbar"><div class="brand">Corrente<span class="brand-dot">.</span></div><div style="display:flex;align-items:center;gap:10px;"><span style="font-size:11.5px;color:var(--dim);">${currentProfile}</span><span data-logout="1" style="font-size:11.5px;color:var(--dim);text-decoration:underline;cursor:pointer;">Sair</span></div></div>
      ${pillsHtml()}
      <div class="cat-header">
        <div class="cat-icon-big">${cat.icon}</div>
        <div class="cat-title">${cat.name}</div>
      </div>
      <div class="hero-label">Patrimônio</div>
      <div class="hero-value">${fmt(cat.value)}</div>
      <div class="ind-tile" style="margin:16px 0 0;">
        <div class="ind-label">${contaIcon(cat.contaPrincipal)} Conta Principal (${cat.contaPrincipal||'—'})</div>
        <div class="ind-value" style="color:var(--green);margin-top:7px;font-size:19px;">${fmt(cat.value)}</div>
      </div>
      <div class="reserva-card">
        <div class="reserva-desc">Reserva parada — sem corrente de reinvestimento</div>
      </div>
    `;
  }

  const cap = capitalInicial(cat);
  const lucro = lucroRealizado(cat);
  const pct = cap>0 ? Math.min(100,(lucro/cap)*100) : 100;
  const done = lucro>=cap;
  const investido = capitalInvestido(cat);
  const aReceber = capitalAReceber(cat);
  const disponivel = capitalDisponivelUnused(cat);
  const capTotal = investido+aReceber+disponivel || 1;

  const heroPatrimonio = `
    <div class="hero-label">Patrimônio</div>
    <div class="hero-value">${fmt(capitalTotalCategoria(cat))}</div>
  `;

  const contaPorLocal = capitalPorConta(cat);
  const locaisHtml = Object.entries(contaPorLocal).map(([loc,val])=>`
    <div class="cash-row" style="border-top:1px solid var(--border);padding-top:9px;margin-top:9px;">
      <div class="cash-name">${contaIcon(loc)} ${loc}</div>
      <div class="cash-value">${fmt(val)}</div>
    </div>
  `).join('');
  const contaPrincipalBlock = `
    <div class="ind-tile" style="margin:16px 0 0;">
      <div class="ind-label">Onde o dinheiro disponível está guardado</div>
      ${locaisHtml || `<div class="progress-note" style="margin-top:8px;">Nenhum valor disponível ainda.</div>`}
    </div>
  `;

  const distBlock = `
    <div class="dist-block">
      <div class="dist-bar">
        <div class="dist-seg" style="width:${disponivel/capTotal*100}%;background:var(--green);"></div>
        <div class="dist-seg" style="width:${investido/capTotal*100}%;background:var(--blue);"></div>
        <div class="dist-seg" style="width:${aReceber/capTotal*100}%;background:var(--red);"></div>
      </div>
      <div class="dist-legend">
        <div class="dist-item"><span class="dist-dot" style="background:var(--green);"></span>${contaIcon(cat.contaPrincipal)} ${cat.contaPrincipal}: <b>${fmt(disponivel)}</b></div>
        <div class="dist-item"><span class="dist-dot" style="background:var(--blue);"></span>📦 Estoque: <b>${fmt(investido)}</b></div>
        ${aReceber>0?`<div class="dist-item"><span class="dist-dot" style="background:var(--red);"></span>🔴 A receber: <b>${fmt(aReceber)}</b></div>`:''}
      </div>
    </div>
  `;

  const vendidos = cat.items.filter(i=>i.status==='disponivel'||i.status==='aguardando_pagamento');
  const diasMedList = cat.items.filter(i=>i.status==='estoque'||i.status==='reservado').map(i=>daysBetween(i.buyDate,today()));
  const diasMedio = diasMedList.length ? Math.round(diasMedList.reduce((a,b)=>a+b,0)/diasMedList.length) : 0;
  const receita = vendidos.reduce((s,i)=>s+i.sellValue,0);
  const margem = receita>0 ? (lucro/receita*100) : 0;
  const roi = cap>0 ? (lucro/cap*100) : 0;

  const indicators = `
    <div class="ind-grid">
      <div class="ind-tile"><div class="ind-label">Dias em estoque (méd.)</div><div class="ind-value">${diasMedio}d</div></div>
      <div class="ind-tile"><div class="ind-label">Lucro realizado</div><div class="ind-value" style="color:var(--green);">${fmt(lucro)}</div></div>
      <div class="ind-tile"><div class="ind-label">Margem</div><div class="ind-value">${margem.toFixed(0)}%</div></div>
      <div class="ind-tile"><div class="ind-label">ROI sobre capital</div><div class="ind-value">${roi.toFixed(0)}%</div></div>
    </div>
  `;

  const progressHtml = `
    <div class="progress-block">
      <div class="progress-top"><span>${done?'Capital recuperado':'Recuperando capital'}</span><b>${Math.round(pct)}%</b></div>
      <div class="progress-track"><div class="progress-fill ${done?'done':''}" style="width:${pct}%"></div></div>
      <div class="progress-note ${done?'done':''}">${done
        ? `<b>Capital de ${fmt(cap)} recuperado</b> — o que vier a partir daqui é lucro líquido.`
        : `Lucro acumulado <b>${fmt(lucro)}</b> de <b>${fmt(cap)}</b> investidos. Faltam <b>${fmt(cap-lucro)}</b>.`}
      </div>
    </div>
  `;

  const ativos = cat.items.filter(i=>i.status==='estoque'||i.status==='reservado'||i.status==='aguardando_pagamento');
  const disponiveis = cat.items.filter(i=>i.status==='disponivel' && !usedAsFunding(cat,i.id));
  const historico = cat.items.filter(i=>i.status==='disponivel' && usedAsFunding(cat,i.id));

  const tabsHtml = `
    <div class="tabs">
      <div class="tab ${view.tab==='produtos'?'active':''}" data-tab="produtos">Produtos <span class="tab-count">${ativos.length}</span></div>
      <div class="tab ${view.tab==='extrato'?'active':''}" data-tab="extrato">Extrato <span class="tab-count">${historico.length}</span></div>
      <div class="tab ${view.tab==='mapa'?'active':''}" data-tab="mapa">Mapa</div>
    </div>
  `;

  let content = '';
  if(view.tab==='produtos'){
    content = ativos.map(it=>renderProdutoRow(cat,it)).join('') || `<div class="progress-note">Nenhum produto ativo agora.</div>`;

    if(disponiveis.length){
      content += `
        <div class="cash-block">
          <div class="cash-title">💰 Disponível pra reinvestir</div>
          ${disponiveis.map(i=>`
            <div class="cash-row">
              <div>
                <div class="cash-name">${i.name}</div>
                <div style="font-size:11px;color:var(--dim);margin-top:2px;">📍 ${itemLocal(cat,i)} <span data-edit-local="${i.id}" style="text-decoration:underline;cursor:pointer;margin-left:4px;">mudar</span></div>
              </div>
              <div style="display:flex;align-items:center;gap:10px;">
                <div class="cash-value">${fmt(i.sellValue)}</div>
                <button class="btn btn-green" data-reinvest="${i.id}" style="padding:6px 10px;font-size:11px;">Reinvestir</button>
              </div>
            </div>
          `).join('')}
        </div>
      `;
    }

    if(view.formOpen==='sell'){
      const it = itemById(cat, view.sellingId);
      content += `
        <div class="form-card">
          <div class="form-title">Vender ${it.name}</div>
          <div class="form-row">
            <div><label>Valor de venda</label><input type="number" id="f-sellValue" placeholder="ex: 5300"/></div>
            <div><label>Data</label><input type="date" id="f-sellDate" value="${today()}"/></div>
          </div>
          <div class="form-actions">
            <button class="btn btn-primary" data-confirm-sell="1">Confirmar venda</button>
            <button class="btn btn-ghost" data-cancel-form="1">Cancelar</button>
          </div>
        </div>
      `;
    } else if(view.formOpen==='new'){
      const funding = disponiveis;
      const options = `<option value="">Capital novo</option>` + funding.map(f=>`<option value="${f.id}" ${view.reinvestFrom===f.id?'selected':''}>Lucro de ${f.name} (${fmt(f.sellValue)} disponível)</option>`).join('');
      content += `
        <div class="form-card">
          <div class="form-title">Novo produto</div>
          <div class="form-row"><div><label>Nome</label><input type="text" id="f-name" placeholder="ex: iPhone 15"/></div></div>
          <div class="form-row">
            <div><label>Modelo (opcional)</label><input type="text" id="f-modelo" placeholder="ex: 128GB"/></div>
            <div><label>Nº série (opcional)</label><input type="text" id="f-serie" placeholder="ex: A1B2C3"/></div>
          </div>
          <div class="form-row">
            <div><label>Valor de compra</label><input type="number" id="f-buyValue" value="${view.reinvestFrom ? itemById(cat,view.reinvestFrom).sellValue : ''}" placeholder="ex: 4000"/></div>
            <div><label>Data</label><input type="date" id="f-buyDate" value="${today()}"/></div>
          </div>
          <div class="form-row"><div><label>Origem do dinheiro</label><select id="f-funded">${options}</select></div></div>
          <div class="form-row"><div><label>Foto (opcional)</label><input type="file" id="f-foto" accept="image/*"/></div></div>
          <div class="foto-preview-wrap"><img class="foto-preview" id="foto-preview"/></div>
          <div class="form-row"><div><label>Observações (opcional)</label><textarea id="f-obs" placeholder="ex: comprado com desconto, tela com risco leve"></textarea></div></div>
          <div class="form-actions">
            <button class="btn btn-primary" data-confirm-new="1">Adicionar produto</button>
            <button class="btn btn-ghost" data-cancel-form="1">Cancelar</button>
          </div>
        </div>
      `;
    } else {
      content += `<button class="btn-add" data-open-form="new">+ novo produto</button>`;
    }
  } else if(view.tab==='extrato'){
    let events = [];
    cat.items.forEach(it=>{
      events.push({date:it.buyDate, type:'compra', item:it});
      if(it.status==='aguardando_pagamento'||it.status==='disponivel') events.push({date:it.sellDate, type:'venda', item:it});
    });
    events.sort((a,b)=> new Date(b.date)-new Date(a.date));
    content = events.map(ev=>{
      const it = ev.item;
      if(ev.type==='venda'){
        const profit = it.sellValue-it.buyValue;
        const pending = it.status==='aguardando_pagamento';
        return `<div class="feed-row">
          <div><div class="feed-date">${fmtDateShort(ev.date)}</div><div class="feed-desc">${pending?'Vendeu (aguardando pagto)':'Vendeu'} ${it.name}</div><div class="feed-note">lucro de ${fmt(profit)}</div></div>
          <div class="feed-value ${pending?'pending':'pos'}">${pending?'':'+'}${fmt(it.sellValue)}</div>
        </div>`;
      } else {
        const funded = it.fundedBy ? itemById(cat,it.fundedBy) : null;
        return `<div class="feed-row">
          <div><div class="feed-date">${fmtDateShort(ev.date)}</div><div class="feed-desc">Comprou ${it.name}</div>${funded?`<div class="feed-note">usando o lucro do ${funded.name}</div>`:''}</div>
          <div class="feed-value out">${fmt(it.buyValue)}</div>
        </div>`;
      }
    }).join('');
    if(!content) content = `<div class="progress-note">Ainda não há histórico.</div>`;
  } else {
    content = `
      <div class="mapa-legend">
        <div class="legend-item"><span class="legend-dot" style="background:var(--blue);"></span>Em estoque</div>
        <div class="legend-item"><span class="legend-dot" style="background:var(--yellow);"></span>Reservado</div>
        <div class="legend-item"><span class="legend-dot" style="background:var(--red);"></span>Aguardando pagto</div>
        <div class="legend-item"><span class="legend-dot" style="background:var(--green);"></span>Disponível</div>
      </div>
      <div class="mapa-wrap">${renderMapaSvg(cat)}</div>
    `;
  }

  return `
    <div class="topbar"><div class="brand">Corrente<span class="brand-dot">.</span></div><div style="display:flex;align-items:center;gap:10px;"><span style="font-size:11.5px;color:var(--dim);">${currentProfile}</span><span data-logout="1" style="font-size:11.5px;color:var(--dim);text-decoration:underline;cursor:pointer;">Sair</span></div></div>
    ${pillsHtml()}
    <div class="cat-header">
      <div class="cat-icon-big">${cat.icon}</div>
      <div class="cat-title">${cat.name}</div>
    </div>
    ${heroPatrimonio}
    ${contaPrincipalBlock}
    ${distBlock}
    ${indicators}
    ${progressHtml}
    ${tabsHtml}
    ${content}
    ${alertsHtml()}
  `;
}

function renderProdutoRow(cat, it){
  const days = daysBetween(it.buyDate, today());
  const funded = it.fundedBy ? itemById(cat,it.fundedBy) : null;
  const open = view.expanded===it.id;
  const s = STATUS[it.status];
  const val = it.status==='estoque'||it.status==='reservado' ? (it.marketValue ?? it.buyValue) : it.sellValue;
  const thumb = it.foto ? `<img src="${it.foto}"/>` : (cat.icon);

  let actions = '';
  if(it.status==='estoque'){
    actions = `<button class="btn btn-ghost" data-reservar="${it.id}">Reservar</button><button class="btn btn-primary" data-sell="${it.id}">Marcar vendido</button>`;
  } else if(it.status==='reservado'){
    actions = `<button class="btn btn-ghost" data-voltar-estoque="${it.id}">Voltar p/ estoque</button><button class="btn btn-primary" data-sell="${it.id}">Confirmar venda</button>`;
  } else if(it.status==='aguardando_pagamento'){
    actions = `<button class="btn btn-green" data-receber="${it.id}">Marcar pagamento recebido</button>`;
  }

  // linha da vida do produto
  const order = ['estoque','reservado','aguardando_pagamento','disponivel'];
  const idx = order.indexOf(it.status);
  const stepLabels = ['Compra','Estoque','Reservado','Vendido','Recebido'];
  const stepDone = i => i<=idx+1;

  return `
    <div class="prod-row">
      <div class="prod-head" data-toggle="${it.id}">
        <div class="prod-left">
          <div class="prod-thumb">${thumb}</div>
          <div>
            <div class="prod-name">${it.name}</div>
            <div class="prod-sub"><span class="status-badge" style="background:${s.bg};color:${s.color};">${s.emoji} ${s.label}</span></div>
          </div>
        </div>
        <div class="prod-right">
          <div class="prod-value">${fmt(val)}</div>
          <div class="prod-days">${days}d</div>
        </div>
      </div>
      <div class="prod-detail ${open?'open':''}">
        ${it.foto?`<img class="detail-photo" src="${it.foto}"/>`:''}
        <div class="stepper">
          ${stepLabels.map((l,i)=>`${i>0?`<div class="step-line ${stepDone(i)?'done':''}"></div>`:''}<div class="step-dot ${stepDone(i)?'done':''}"></div>`).join('')}
        </div>
        <div class="step-labels">${stepLabels.map((l,i)=>`<span class="${stepDone(i)?'done':''}">${l}</span>`).join('')}</div>
        <div class="detail-line"><span>Comprado em</span><b>${fmtDateShort(it.buyDate)} · ${fmt(it.buyValue)}</b></div>
        ${it.modelo?`<div class="detail-line"><span>Modelo</span><b>${it.modelo}</b></div>`:''}
        ${it.numeroSerie?`<div class="detail-line"><span>Nº série</span><b>${it.numeroSerie}</b></div>`:''}
        ${funded?`<div class="detail-line"><span>Origem do dinheiro</span><b>lucro de ${funded.name}</b></div>`:''}
        ${it.sellValue?`<div class="detail-line"><span>Venda</span><b>${fmtDateShort(it.sellDate)} · ${fmt(it.sellValue)}</b></div>`:''}
        ${it.observacoes?`<div class="detail-line"><span>Obs.</span><b>${it.observacoes}</b></div>`:''}
        <div class="detail-actions">${actions}</div>
      </div>
    </div>
  `;
}

/* ---------------- mapa mental (svg) ---------------- */
function renderMapaSvg(cat){
  if(cat.items.length===0) return `<div class="mapa-empty">Nada pra mostrar ainda.</div>`;

  const nodeW=140, nodeH=54, colGap=56, rowGap=24, padX=6, padY=10;
  const roots = cat.items.filter(i=>!i.fundedBy);
  const lane={}, depth={};
  function assign(item, laneIdx, d){
    lane[item.id]=laneIdx; depth[item.id]=d;
    const child = cat.items.find(i=>i.fundedBy===item.id);
    if(child) assign(child, laneIdx, d+1);
  }
  roots.forEach((r,idx)=>assign(r, idx, 0));

  const laneCount = roots.length;
  const maxDepth = Math.max(...cat.items.map(i=>depth[i.id]));
  const svgW = padX*2 + (maxDepth+1)*nodeW + maxDepth*colGap;
  const svgH = padY*2 + laneCount*nodeH + Math.max(0,laneCount-1)*rowGap;

  function pos(item){ return { x: padX + depth[item.id]*(nodeW+colGap), y: padY + lane[item.id]*(nodeH+rowGap) }; }

  let defs = '';
  let edges = '';
  cat.items.forEach(it=>{
    if(it.fundedBy){
      const parent = itemById(cat, it.fundedBy);
      const p = pos(parent), c = pos(it);
      const x1=p.x+nodeW, y1=p.y+nodeH/2, x2=c.x, y2=c.y+nodeH/2;
      const profit = parent.sellValue-parent.buyValue;
      const midX=(x1+x2)/2;
      edges += `
        <line x1="${x1}" y1="${y1}" x2="${x2}" y2="${y2}" stroke="#2A2A2E" stroke-width="2"/>
        <circle cx="${midX}" cy="${y1}" r="3" fill="#34C759"/>
        <text class="edge-label" x="${midX}" y="${y1-9}" text-anchor="middle" fill="#34C759" font-size="10" font-weight="700" font-family="Inter,sans-serif">+${fmt(profit).replace('R$','')}</text>
      `;
    }
  });

  let nodes = '';
  cat.items.forEach((it,i)=>{
    const p = pos(it);
    const s = STATUS[it.status];
    const value = (it.status==='estoque'||it.status==='reservado') ? (it.marketValue ?? it.buyValue) : it.sellValue;
    let photoEl = '';
    let textX = p.x+12;
    if(it.foto){
      const clipId = 'clip'+cat.id+i;
      defs += `<clipPath id="${clipId}"><circle cx="${p.x+20}" cy="${p.y+18}" r="11"/></clipPath>`;
      photoEl = `<image href="${it.foto}" x="${p.x+9}" y="${p.y+7}" width="22" height="22" clip-path="url(#${clipId})" preserveAspectRatio="xMidYMid slice"/>`;
      textX = p.x+38;
    }
    nodes += `
      <g>
        <rect x="${p.x}" y="${p.y}" width="${nodeW}" height="${nodeH}" rx="12" fill="${s.bg}" stroke="${s.color}" stroke-width="1.3"/>
        ${photoEl}
        <text x="${textX}" y="${p.y+16}" font-size="8.5" font-weight="700" font-family="Inter,sans-serif" fill="${s.color}" letter-spacing="0.3">${s.emoji} ${s.label.toUpperCase()}</text>
        <text x="${textX}" y="${p.y+31}" font-size="12" font-weight="700" font-family="Inter,sans-serif" fill="#F5F5F7">${it.name}</text>
        <text x="${textX}" y="${p.y+45}" font-size="10.5" font-weight="500" font-family="Inter,sans-serif" fill="#9A9AA1">${fmt(value)}</text>
      </g>
    `;
  });

  return `<svg width="${svgW}" height="${svgH}" viewBox="0 0 ${svgW} ${svgH}" xmlns="http://www.w3.org/2000/svg"><defs>${defs}</defs>${edges}${nodes}</svg>`;
}

/* ---------------- events ---------------- */
function bindEvents(){
  const logoutBtn = document.querySelector('[data-logout]');
  if(logoutBtn) logoutBtn.onclick = ()=>{
    currentProfile = null; categories = []; contas = [];
    auth.screen = 'login';
    renderAuth();
  };
  const demoBtn = document.querySelector('[data-load-demo]');
  if(demoBtn) demoBtn.onclick = ()=>{
    const demo = seedDemoData();
    categories = demo.categories; contas = demo.contas;
    render(); saveProfileData();
    showToast('Dados de exemplo carregados.', 'success');
  };
  const openNewConta = document.querySelector('[data-open-new-conta]');
  if(openNewConta) openNewConta.onclick = ()=>{ view.newContaForm=true; render(); };
  const cancelNewConta = document.querySelector('[data-cancel-new-conta]');
  if(cancelNewConta) cancelNewConta.onclick = ()=>{ view.newContaForm=false; render(); };
  const confirmNewConta = document.querySelector('[data-confirm-new-conta]');
  if(confirmNewConta) confirmNewConta.onclick = ()=>{
    const nome = document.getElementById('conta-nome').value.trim();
    const tipo = document.getElementById('conta-tipo').value;
    if(!nome){ showToast('Informe o nome da conta.', 'error'); return; }
    if(contas.some(c=>c.nome.toLowerCase()===nome.toLowerCase())){ showToast('Já existe uma conta com esse nome.', 'error'); return; }
    contas.push({id:'ct'+Date.now(), nome, tipo});
    view.newContaForm=false; render(); saveProfileData();
    showToast(`Conta "${nome}" adicionada.`, 'success');
  };
  document.querySelectorAll('[data-select]').forEach(el=>{
    el.onclick = ()=>{ view = {selected:el.dataset.select, tab:'produtos', expanded:null, formOpen:null, draftFoto:null}; render(); };
  });
  document.querySelectorAll('[data-tab]').forEach(el=>{
    el.onclick = ()=>{ view.tab=el.dataset.tab; view.formOpen=null; view.expanded=null; render(); };
  });
  document.querySelectorAll('[data-toggle]').forEach(el=>{
    el.onclick = ()=>{ view.expanded = view.expanded===el.dataset.toggle ? null : el.dataset.toggle; render(); };
  });

  document.querySelectorAll('[data-sell]').forEach(el=>{
    el.onclick = (e)=>{ e.stopPropagation(); view.formOpen='sell'; view.sellingId=el.dataset.sell; render(); };
  });
  document.querySelectorAll('[data-reservar]').forEach(el=>{
    el.onclick = (e)=>{ e.stopPropagation(); const cat=categories.find(c=>c.id===view.selected); itemById(cat,el.dataset.reservar).status='reservado'; render(); saveProfileData(); };
  });
  document.querySelectorAll('[data-voltar-estoque]').forEach(el=>{
    el.onclick = (e)=>{ e.stopPropagation(); const cat=categories.find(c=>c.id===view.selected); itemById(cat,el.dataset.voltarEstoque).status='estoque'; render(); saveProfileData(); };
  });
  document.querySelectorAll('[data-receber]').forEach(el=>{
    el.onclick = (e)=>{ e.stopPropagation(); const cat=categories.find(c=>c.id===view.selected); const it=itemById(cat,el.dataset.receber); it.status='disponivel'; if(!it.localizacao) it.localizacao=cat.contaPrincipal; render(); saveProfileData(); showToast(`Pagamento de ${it.name} recebido.`, 'success'); };
  });
  document.querySelectorAll('[data-edit-local]').forEach(el=>{
    el.onclick = (e)=>{
      e.stopPropagation();
      const cat = categories.find(c=>c.id===view.selected);
      const it = itemById(cat, el.dataset.editLocal);
      const novo = prompt('Onde esse dinheiro está guardado? Contas cadastradas: ' + (contas.map(c=>c.nome).join(', ')||'nenhuma ainda') + ' — ou digite uma nova.', itemLocal(cat,it));
      if(novo && novo.trim()){ it.localizacao = novo.trim(); ensureConta(it.localizacao); render(); saveProfileData(); showToast('Local atualizado.', 'success'); }
    };
  });
  document.querySelectorAll('[data-reinvest]').forEach(el=>{
    el.onclick = ()=>{ view.formOpen='new'; view.reinvestFrom=el.dataset.reinvest; render(); };
  });

  document.querySelectorAll('[data-open-form]').forEach(el=>{
    el.onclick = ()=>{ view.formOpen=el.dataset.openForm; view.reinvestFrom=null; view.draftFoto=null; render(); };
  });
  const cancel = document.querySelector('[data-cancel-form]');
  if(cancel) cancel.onclick = ()=>{ view.formOpen=null; view.reinvestFrom=null; render(); };

  const fFoto = document.getElementById('f-foto');
  if(fFoto) fFoto.onchange = (e)=>{
    const file = e.target.files[0]; if(!file) return;
    const reader = new FileReader();
    reader.onload = ()=>{ view.draftFoto = reader.result; const prev=document.getElementById('foto-preview'); if(prev){prev.src=reader.result; prev.style.display='block';} };
    reader.readAsDataURL(file);
  };

  const confirmSell = document.querySelector('[data-confirm-sell]');
  if(confirmSell) confirmSell.onclick = ()=>{
    const cat = categories.find(c=>c.id===view.selected);
    const it = itemById(cat, view.sellingId);
    const sellValue = parseFloat(document.getElementById('f-sellValue').value);
    const sellDate = document.getElementById('f-sellDate').value;
    if(!sellValue || sellValue<=0){ showToast('Informe um valor de venda válido.', 'error'); return; }
    if(!sellDate){ showToast('Informe a data da venda.', 'error'); return; }
    it.status='aguardando_pagamento'; it.sellValue=sellValue; it.sellDate=sellDate;
    view.formOpen=null; view.expanded=null; render();
    saveProfileData();
    showToast(`${it.name} marcado como vendido.`, 'success');
  };

  const confirmNew = document.querySelector('[data-confirm-new]');
  if(confirmNew) confirmNew.onclick = ()=>{
    const cat = categories.find(c=>c.id===view.selected);
    const name = document.getElementById('f-name').value.trim();
    const modelo = document.getElementById('f-modelo').value || null;
    const numeroSerie = document.getElementById('f-serie').value || null;
    const buyValue = parseFloat(document.getElementById('f-buyValue').value);
    const buyDate = document.getElementById('f-buyDate').value;
    const funded = document.getElementById('f-funded').value || null;
    const obs = document.getElementById('f-obs').value || null;
    if(!name){ showToast('Informe o nome do produto.', 'error'); return; }
    if(!buyValue || buyValue<=0){ showToast('Informe um valor de compra válido.', 'error'); return; }
    if(!buyDate){ showToast('Informe a data da compra.', 'error'); return; }
    cat.items.push({id:'n'+Date.now(), name, modelo, numeroSerie, observacoes:obs, foto:view.draftFoto, buyValue, buyDate, fundedBy:funded, marketValue:buyValue, status:'estoque'});
    view.formOpen=null; view.reinvestFrom=null; view.draftFoto=null; render();
    saveProfileData();
    showToast(`${name} adicionado ao portfólio.`, 'success');
  };

  document.querySelectorAll('[data-new-cat]').forEach(el=>{
    el.onclick = ()=>{ view.selected='todos'; view.tab='produtos'; view.newCatForm=true; view.draftIcon=ICONS[0]; render(); };
  });
  document.querySelectorAll('[data-pick-icon]').forEach(el=>{
    el.onclick = ()=>{ view.draftIcon = el.dataset.pickIcon; render(); };
  });
  const cancelNewCat = document.querySelector('[data-cancel-new-cat]');
  if(cancelNewCat) cancelNewCat.onclick = ()=>{ view.newCatForm=false; render(); };
  const ncContaSelect = document.getElementById('nc-conta');
  if(ncContaSelect) ncContaSelect.onchange = ()=>{
    document.getElementById('nc-conta-new-wrap').style.display = ncContaSelect.value==='__new__' ? 'block' : 'none';
  };
  const confirmNewCat = document.querySelector('[data-confirm-new-cat]');
  if(confirmNewCat) confirmNewCat.onclick = ()=>{
    const name = document.getElementById('nc-name').value.trim();
    const tipo = document.getElementById('nc-tipo').value;
    const contaSel = document.getElementById('nc-conta').value;
    const contaNova = document.getElementById('nc-conta-new').value.trim();
    const conta = contaSel==='__new__' ? contaNova : contaSel;
    const valorRaw = document.getElementById('nc-valor').value;
    const valor = parseFloat(valorRaw);

    if(!name){ showToast('Informe um nome para o portfólio.', 'error'); return; }
    if(categories.some(c=>c.name.toLowerCase()===name.toLowerCase())){ showToast('Já existe um portfólio com esse nome.', 'error'); return; }
    if(!conta){ showToast('Selecione ou informe a conta principal.', 'error'); return; }
    if(!valorRaw || isNaN(valor) || valor<=0){ showToast('Informe um valor inicial válido.', 'error'); return; }

    ensureConta(conta);
    const id = name.toLowerCase().replace(/[^a-z0-9]/g,'-')+'-'+Date.now();
    if(tipo==='reserva'){
      categories.push({id, name, icon:view.draftIcon, type:'reserva', contaPrincipal:conta, value:valor});
    } else {
      categories.push({id, name, icon:view.draftIcon, type:'corrente', contaPrincipal:conta,
        items:[{id:'n'+Date.now(), name:name+' — item 1', buyValue:valor, buyDate:today(), fundedBy:null, marketValue:valor, status:'estoque'}]});
    }
    view.newCatForm=false; view.selected=id; view.tab='produtos';
    render();
    saveProfileData();
    showToast(`Portfólio "${name}" criado com sucesso!`, 'success');
  };
}

async function boot(){
  document.getElementById('app').innerHTML = `<div class="fade" style="text-align:center;padding-top:30vh;color:var(--dim);font-size:13px;">Carregando…</div>`;
  auth.profiles = await loadProfiles();
  auth.loading = false;
  renderAuth();
}
boot();
</script>
</body>
</html>
