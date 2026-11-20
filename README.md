<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>صدقة جارية | هند محمود</title>
<style>
  *{box-sizing:border-box}
  body{margin:0;font-family:'Segoe UI',Tahoma,sans-serif;background:#fdf6f8;color:#2b2b2b}
  header{background:linear-gradient(135deg,#6d2a4a,#a84874);color:#fff;text-align:center;padding:50px 20px 40px}
  header h1{margin:0;font-size:34px}
  header p{opacity:.9}
  .hero-name{font-size:26px;font-weight:bold;background:rgba(255,255,255,.18);display:inline-block;padding:10px 24px;border-radius:30px;margin-top:15px}
  .container{max-width:900px;margin:auto;padding:20px 16px 80px}
  .counter{background:#fff;border-radius:16px;padding:20px;text-align:center;box-shadow:0 5px 20px rgba(0,0,0,.05);margin-bottom:20px}
  .counter b{font-size:38px;color:#6d2a4a}
  .counter button{margin:5px;padding:10px 16px;border:0;border-radius:20px;background:#fdeef3;cursor:pointer;font-size:15px}
  .card{background:#fff;border-radius:16px;padding:22px;margin-bottom:16px;box-shadow:0 5px 20px rgba(0,0,0,.05);border-right:5px solid #d9a0b8}
  .card h3{margin:0 0 10px;color:#6d2a4a}
  .card p{font-size:20px;line-height:1.9;margin:0}
  .actions{margin-top:12px;display:flex;gap:8px;flex-wrap:wrap}
  .actions button{padding:8px 14px;border:1px solid #ddd;background:#fff;border-radius:20px;cursor:pointer}
  .share{position:fixed;bottom:16px;left:16px;right:16px;background:#6d2a4a;color:#fff;text-align:center;padding:14px;border-radius:14px;font-weight:bold;cursor:pointer;z-index:10}
  footer{text-align:center;color:#888;padding:20px;font-size:14px}
</style>
</head>
<body>

<header>
  <h1>🤲 صدقة جارية</h1>
  <p>ادعُ لمن تحب.. فالدعاء يصل</p>
  <div class="hero-name">اللهم ارحم هند محمود واغفر لها</div>
  <p style="margin-top:15px">اللهم اجعل قبرها روضة من رياض الجنة</p>
</header>

<div class="container">
  <div class="counter">
    <div>عدد الدعوات لهند محمود</div>
    <b id="count">0</b>
    <div>كل دعوة صدقة جارية</div>
    <div style="margin-top:12px">
      <button onclick="pray()">اللهم ارحم هند</button>
      <button onclick="pray()">اللهم اغفر لهند</button>
      <button onclick="pray()">اللهم اجعل قبرها نور</button>
    </div>
  </div>

  <div id="duas"></div>

  <div class="card" style="text-align:center;border-right:0;background:#6d2a4a;color:#fff">
    <h3 style="color:#fff">ادعُ لهند محمود وشارك الأجر</h3>
    <p style="color:#fff;font-size:16px">شارك الموقع عشان الدعاء لهند يفضل مستمر</p>
  </div>
</div>

<div class="share" onclick="shareSite()">شارك الموقع صدقة جارية عن هند محمود 📤</div>
<footer>صدقة جارية عن هند محمود .. لا تنسوها من صالح دعائكم</footer>

<script>
let count = parseInt(localStorage.getItem('duaCountHind')||0);
document.getElementById('count').innerText = count;

const duas = [
  {t:"دعاء الرحمة والمغفرة", d:"اللهم ارحم هند محمود واغفر لها، وتجاوز عن سيئاتها، واجعل قبرها روضة من رياض الجنة، ولا تجعله حفرة من حفر النار."},
  {t:"دعاء النور في القبر", d:"اللهم نوّر قبر هند محمود، ووسّع مدخلها، وآنس وحشتها، واجعلها في نعيمٍ مقيم إلى يوم يبعثون."},
  {t:"دعاء الجنة", d:"اللهم اجعل هند محمود من أهل الفردوس الأعلى، وارزقها لذة النظر إلى وجهك الكريم، واجمعنا بها في جنات النعيم."},
  {t:"دعاء التثبيت", d:"اللهم ثبّت هند محمود عند السؤال، ولقّنها حجتها، واجعل عملها الصالح شفيعًا لها، وارحمها برحمتك يا أرحم الراحمين."},
  {t:"دعاء العفو", d:"اللهم إنك عفوٌ تحب العفو فاعفُ عن هند محمود، اللهم اغسلها بالماء والثلج والبرد، ونقّها من الذنوب كما يُنقّى الثوب الأبيض من الدنس."},
  {t:"دعاء الاشتياق", d:"اللهم ارحم هند محمود، من اشتاقت لها قلوبنا وهي تحت التراب، اللهم ارحم من غاب عنّا جسدها وبقي في قلوبنا ذكرها."},
  {t:"دعاء ليلة الجمعة", d:"اللهم في ليلة الجمعة ارحم هند محمود، واغفر لها، واجعل لها نصيبًا من رحمتك ومغفرتك، وبلّغها دعاءنا."},
  {t:"دعاء الصبر لأهلها", d:"اللهم اربط على قلوب أهل هند محمود، وارزقهم الصبر والسلوان، واجعل فقدها رحمةً لا عذابًا، واجمعهم بها في الجنة."},
  {t:"دعاء الشفاعة", d:"اللهم شفّع في هند محمود القرآن والصيام والصلاة، واجعلها ممن يُقال لهن ادخلي الجنة بسلامٍ آمنة."},
  {t:"دعاء الدار الآخرة", d:"اللهم ارزق هند محمود دارًا خيرًا من دارها، وأهلًا خيرًا من أهلها، وجيرانًا خيرًا من جيرانها."},
  {t:"دعاء الرحمة الواسعة", d:"اللهم ارحم هند محمود رحمةً واسعة، واجعل قبرها بردًا وسلامًا، واجعل ملائكة الرحمة تحفّها من كل مكان."},
  {t:"دعاء الخاتمة", d:"اللهم اجعل هند محمود في أعلى عليين، مع النبيين والصديقين والشهداء والصالحين، وحسُن أولئك رفيقًا."},
];

document.getElementById('duas').innerHTML = duas.map((x,i)=>`
  <div class="card">
    <h3>${x.t}</h3>
    <p>${x.d}</p>
    <div class="actions">
      <button onclick="pray()">🤲 دعوت لهند</button>
      <button onclick="copyDua(${i})">📋 نسخ الدعاء</button>
    </div>
  </div>
`).join('');

function pray(){
  count++; localStorage.setItem('duaCountHind',count);
  document.getElementById('count').innerText = count;
}
function copyDua(i){
  navigator.clipboard.writeText(duas[i].d);
  alert('تم نسخ الدعاء');
}
function shareSite(){
  const text = 'صدقة جارية عن هند محمود 🤲 ادعُ لها وشارك الأجر ' + location.href;
  if(navigator.share) navigator.share({text});
  else { navigator.clipboard.writeText(text); alert('تم نسخ رابط المشاركة'); }
}
</script>
</body>
</html># Sadaka