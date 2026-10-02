<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Los Bros · Diamantes Free Fire</title>
<style>
:root{--bg:#0e1630;--card:#18244a;--ink:#f4f6ff;--mute:#a9b3d6;--acc:#ffb81c;--wa:#25d366;--line:#2c3b70;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:light){:root:not([data-theme="dark"]){--bg:#eef1fb;--card:#fff;--ink:#12183a;--mute:#4d5887;--line:#d3daf0}}
:root[data-theme="dark"]{--bg:#0e1630;--card:#18244a;--ink:#f4f6ff;--mute:#a9b3d6;--line:#2c3b70}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font-family:"Trebuchet MS","Segoe UI",system-ui,sans-serif;line-height:1.45}
main{max-width:560px;margin:0 auto;padding:20px 16px 40px}
h1{font-family:Impact,"Arial Black",sans-serif;font-size:2.4rem;line-height:1;margin:8px 0 6px;letter-spacing:.5px}
h2{font-size:1.15rem;margin:28px 0 10px}
.sub{color:var(--mute);margin:0 0 16px}
.badge{display:inline-block;background:var(--acc);color:#1a1300;font-weight:700;padding:3px 10px;border-radius:99px;font-size:.85rem}
.grid{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.item{background:var(--card);border:2px solid var(--line);border-radius:12px;padding:14px 10px;text-align:center;cursor:pointer;color:inherit;font:inherit}
.item b{display:block;font-size:1.25rem}
.item span{color:var(--acc);font-weight:700;font-size:1.05rem}
.item:focus-visible,.cta:focus-visible,.copy:focus-visible{outline:3px solid var(--acc);outline-offset:2px}
.item[aria-pressed="true"]{border-color:var(--acc);background:color-mix(in srgb,var(--acc) 18%,var(--card))}
.pases .item{text-align:left;display:flex;justify-content:space-between;gap:8px;width:100%;margin-bottom:10px}
.bank{background:var(--card);border:2px dashed var(--line);border-radius:12px;padding:14px}
.bank p{margin:4px 0}
.copy{margin-top:8px;background:var(--acc);color:#1a1300;border:0;border-radius:8px;padding:8px 14px;font-weight:700;font:inherit;font-weight:700;cursor:pointer}
.bar{position:sticky;bottom:0;padding:12px 16px calc(12px + env(safe-area-inset-bottom,0px));background:var(--bg);border-top:1px solid var(--line)}
.cta{display:block;max-width:528px;margin:0 auto;text-align:center;background:var(--wa);color:#04210f;font-weight:700;font-size:1.05rem;padding:14px;border-radius:12px;text-decoration:none}
label{display:block;margin:14px 0 6px;font-weight:700}
input{width:100%;padding:12px;border-radius:10px;border:2px solid var(--line);background:var(--card);color:var(--ink);font:inherit}
</style>
</head>
<body>
<main>
  <span class="badge">Solo por unos días</span>
  <h1>LOS BROS<br>DIAMANTES FREE FIRE</h1>
  <p class="sub">Elegí tu pack, ponés tu ID y nos escribís por WhatsApp.</p>

  <h2>Diamantes 🇦🇷</h2>
  <div class="grid" id="packs"></div>

  <h2>Pases</h2>
  <div class="pases" id="pases"></div>

  <label for="uid">Tu ID de Free Fire</label>
  <input id="uid" inputmode="numeric" placeholder="Ej: 123456789" autocomplete="off">

  <h2>💳 Datos para transferir</h2>
  <div class="bank">
    <p>Alias: <b id="alias">LOSBROS</b></p>
    <p>Titular: <b>AGUSTIN TOLAVA</b></p>
    <p>Banco: <b>Mercado Pago</b></p>
    <button class="copy" id="copyBtn" type="button">Copiar alias</button>
  </div>
</main>

<div class="bar"><a class="cta" id="wa" href="#" target="_blank" rel="noopener">Elegí un pack para pedir</a></div>

<script>
var NUM="5493874075605";
var packs=[["110 💎",1450],["220 💎",2900],["341 💎",4600],["451 💎",6050],["572 💎",6750],["913 💎",11350],["1.166 💎",12750],["2.398 💎",24100],["3.564 💎",36650],["4.798 💎",48000],["6.160 💎",59500]];
var pases=[["Pase de nivel por ID (1270 💎)",7000],["Pase Booyah",2500]];
var sel=null;
function fmt(n){return "$"+n.toString().replace(/\B(?=(\d{3})+(?!\d))/g,".")}
function mk(box,list){
  list.forEach(function(p){
    var b=document.createElement("button");
    b.type="button";b.className="item";b.setAttribute("aria-pressed","false");
    b.innerHTML="<b>"+p[0]+"</b><span>"+fmt(p[1])+"</span>";
    b.onclick=function(){
      document.querySelectorAll(".item").forEach(function(x){x.setAttribute("aria-pressed","false")});
      b.setAttribute("aria-pressed","true");sel=p;update();
    };
    box.appendChild(b);
  });
}
function update(){
  var a=document.getElementById("wa");
  if(!sel){a.removeAttribute("href");a.textContent="Elegí un pack para pedir";return}
  var id=document.getElementById("uid").value.trim();
  var msg="Hola Los Bros! Quiero comprar: "+sel[0]+" por "+fmt(sel[1])+"."+(id?" Mi ID de Free Fire es: "+id+".":" Te paso mi ID enseguida.")+" Ya tengo el alias, te mando el comprobante.";
  a.href="https://wa.me/"+NUM+"?text="+encodeURIComponent(msg);
  a.textContent="Pedir "+sel[0]+" por WhatsApp";
}
mk(document.getElementById("packs"),packs);
mk(document.getElementById("pases"),pases);
document.getElementById("uid").addEventListener("input",update);
document.getElementById("wa").addEventListener("click",function(e){if(!sel){e.preventDefault()}});
document.getElementById("copyBtn").onclick=function(){
  var t=document.getElementById("alias").textContent,b=this;
  try{navigator.clipboard.writeText(t).then(function(){b.textContent="¡Copiado!"},function(){b.textContent="Alias: "+t})}catch(e){b.textContent="Alias: "+t}
};
</script>
</body>
</html>

