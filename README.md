<!DOCTYPE html>
<html lang="az">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Rəng görmə mini testi</title>

<style>
body{font-family:Arial,sans-serif;background:#f5f5f5;margin:0;padding:24px;color:#171717}
.card{max-width:720px;margin:auto;background:white;border-radius:18px;padding:24px;box-shadow:0 8px 30px #0001}
h1{margin-top:0}.muted{color:#666}
.grid{display:grid;grid-template-columns:repeat(2,1fr);gap:14px;margin-top:20px}
.item{border:1px solid #ddd;border-radius:14px;padding:14px}
.swatch{height:95px;border-radius:10px;margin-bottom:10px}
select{width:100%;padding:11px;border-radius:9px;border:1px solid #ccc;font-size:16px}
button{margin-top:20px;width:100%;padding:13px;border:0;border-radius:10px;background:#111;color:#fff;font-size:17px}
#result{margin-top:18px;font-weight:bold}
@media(max-width:520px){.grid{grid-template-columns:1fr}}
</style>
</head>

<body>
<div class="card">
<h1>🎨 Rəng görmə mini testi</h1>

<p class="muted">
Rəngləri ekranda mümkün qədər təbii işıqda qiymətləndir.
Bu, tibbi diaqnoz deyil.
</p>

<div id="test" class="grid"></div>

<button onclick="check()">Nəticəni göstər</button>

<div id="result"></div>
</div>

<script>

const questions=[
["#F0E94A","Sarı"],
["#C9D94E","Sarı-yaşıl"],
["#B8D85A","Açıq yaşıl"],
["#D9E34B","Sarı-yaşıl"],
["#B9E1C8","Açıq mavi-yaşıl"],
["#79CFC8","Mavi-yaşıl"],
["#77BFC9","Mavi-yaşıl"],
["#78AFC8","Mavi"],
["#9CC7D4","Açıq mavi"],
["#A6D1B1","Yaşıl-mavi"]
];

const options=[
"Sarı",
"Sarı-yaşıl",
"Açıq yaşıl",
"Yaşıl-mavi",
"Mavi-yaşıl",
"Mavi",
"Açıq mavi"
];

const box=document.getElementById("test");

questions.forEach((q,i)=>{
let opts=options.map(x=>`<option>${x}</option>`).join("");

box.innerHTML+=`
<div class="item">
<div class="swatch" style="background:${q[0]}"></div>
<b>${i+1}.</b>

<select id="a${i}">
<option value="">Seç</option>
${opts}
</select>

</div>`;
});

function check(){

let score=0;

questions.forEach((q,i)=>{
if(document.getElementById("a"+i).value===q[1])
score++;
});

const r=document.getElementById("result");

r.textContent=`Nəticə: ${score}/10 düzgün.`;

if(score<7)
r.textContent+=
" Bu yalnız evdə ilkin yoxlamadır; rəngləri tez-tez qarışdırırsansa, oftalmoloqda rəng görmə testi daha etibarlıdır.";

else
r.textContent+=
" Bu mini testdə yaxşı nəticədir, amma rəng görmənin normal olduğunu təsdiqləmir.";

}

</script>
</body>
</html>
