<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>¡Feliz Cumpleaños Suegrita! 🎂</title>

<style>
*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Arial,Helvetica,sans-serif;
}

body{
background:linear-gradient(135deg,#ffdde1,#ee9ca7);
overflow:hidden;
display:flex;
justify-content:center;
align-items:center;
height:100vh;
}

.card{
width:90%;
max-width:700px;
background:white;
padding:40px;
border-radius:25px;
text-align:center;
box-shadow:0 20px 50px rgba(0,0,0,.25);
animation:aparecer 1.5s;
position:relative;
z-index:2;
}

h1{
font-size:3em;
color:#d63384;
margin-bottom:15px;
}

h2{
color:#ff4081;
margin-bottom:20px;
}

p{
font-size:20px;
line-height:1.7;
color:#444;
}

.flores{
font-size:45px;
margin-bottom:15px;
}

.pastel{
font-size:90px;
animation:flotar 2s infinite alternate;
margin:20px 0;
}

button{
margin-top:25px;
padding:15px 30px;
font-size:18px;
border:none;
border-radius:40px;
background:#ff4081;
color:white;
cursor:pointer;
transition:.4s;
}

button:hover{
transform:scale(1.08);
background:#e91e63;
}

@keyframes flotar{
from{transform:translateY(0);}
to{transform:translateY(-15px);}
}

@keyframes aparecer{
from{
opacity:0;
transform:scale(.8);
}
to{
opacity:1;
transform:scale(1);
}
}

.confeti{
position:absolute;
width:12px;
height:12px;
border-radius:50%;
top:-20px;
animation:caer linear infinite;
}

@keyframes caer{
0%{
transform:translateY(-20px) rotate(0deg);
}
100%{
transform:translateY(110vh) rotate(720deg);
}
}
</style>
</head>

<body>

<div class="card">

<div class="flores">
🌷🌹🌺🌸💐
</div>

<h1>🎉 ¡Feliz Cumpleaños Suegrita! 🎉</h1>

<div class="pastel">🎂</div>

<h2>Con mucho cariño ❤️</h2>

<p>
Hoy celebramos a una persona muy especial.
Gracias por su cariño, sus consejos, su alegría
y por siempre recibirnos con una sonrisa.
</p>

<br>

<p>
Le deseo un año lleno de salud,
felicidad, bendiciones,
amor y momentos inolvidables.
Que todos sus sueños se hagan realidad.
</p>

<br>

<p>
🌹 Que Dios la bendiga siempre.
Disfrute muchísimo este hermoso día.
¡Muchas felicidades, suegrita! ❤️
</p>

<button onclick="felicitar()">
🎁 Abrir sorpresa
</button>

</div>

<script>

function felicitar(){

alert("🎂 ¡Feliz Cumpleaños Suegrita! Que tenga un día lleno de amor, salud, alegría y muchas bendiciones. ❤️");

lanzarConfeti();

}

function lanzarConfeti(){

for(let i=0;i<200;i++){

const c=document.createElement("div");

c.className="confeti";

c.style.left=Math.random()*100+"vw";

c.style.animationDuration=(Math.random()*3+2)+"s";

c.style.background=`hsl(${Math.random()*360},100%,50%)`;

document.body.appendChild(c);

setTimeout(()=>{
c.remove();
},6000);

}

}

</script>

</body>
</html>
