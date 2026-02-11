# Jimenita--
Carta de cumpleaños 
index.html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Recuerdos con Ezequiel</title>

<style>
body{
  margin:0;
  background:radial-gradient(circle,#111,#000);
  overflow:hidden;
  font-family:Arial, sans-serif;
}

#scene{
  width:100vw;
  height:100vh;
  perspective:1200px;
  display:flex;
  align-items:center;
  justify-content:center;
  position:relative;
}

#sphere{
  position:relative;
  width:420px;
  height:420px;
  transform-style:preserve-3d;
  animation:rotate 35s linear infinite;
}

/* TEXTOS 3D */
#topText{
  position:absolute;
  top:30px;
  font-size:28px;
  color:#ff69b4;
  transform:translateZ(200px);
  animation:float 6s ease-in-out infinite;
}

#centerText{
  position:absolute;
  font-size:32px;
  color:white;
  transform:translateZ(120px);
  animation:float 5s ease-in-out infinite reverse;
}

/* FOTOS */
.photo{
  position:absolute;
  width:120px;
  height:160px;
  border-radius:10px;
  overflow:hidden;
  box-shadow:0 0 20px rgba(255,255,255,.4);
  transition:transform .4s;
}

.photo img{
  width:100%;
  height:100%;
  object-fit:cover;
}

.photo:hover{
  transform:scale(1.5);
  z-index:10;
}

@keyframes rotate{
  from{transform:rotateY(0deg);}
  to{transform:rotateY(360deg);}
}

@keyframes float{
  0%,100%{transform:translateY(0) translateZ(150px);}
  50%{transform:translateY(-15px) translateZ(180px);}
}
</style>
</head>

<body>

<div id="scene">
  <div id="topText">Feliz cumpleaños Jimena 💕</div>
  <div id="centerText">Recuerdos con Ezequiel</div>
  <div id="sphere"></div>
</div>

<audio id="music" src="musica.mp3" loop></audio>

<script>
const sphere = document.getElementById("sphere");
const total = 30;
const radius = 240;

for(let i=0;i<total;i++){
  const y = (360/total)*i;
  const x = (i%6)*30 - 75;

  const div = document.createElement("div");
  div.className = "photo";
  div.style.transform = `
    rotateY(${y}deg)
    rotateX(${x}deg)
    translateZ(${radius}px)
  `;

  const img = document.createElement("img");
  img.src = `foto${i+1}.jpg`;

  div.appendChild(img);
  sphere.appendChild(div);
}

// música al tocar
document.body.addEventListener("click",()=>{
  document.getElementById("music").play();
},{once:true});
</script>

</body>
</html>
