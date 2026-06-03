<!DOCTYPE html>
<html lang="pl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Zaproszenie Ślubne</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    display:flex;
    justify-content:center;
    align-items:center;
    min-height:100vh;
    overflow:hidden;
    font-family:Arial, sans-serif;
}

/* Film w tle */
#bg-video{
    position:fixed;
    top:0;
    left:0;
    width:100%;
    height:100%;
    object-fit:cover;
    z-index:-2;
}

/* Przyciemnienie filmu */
.overlay{
    position:fixed;
    inset:0;
    background:rgba(0,0,0,0.35);
    z-index:-1;
}

.container{
    position:relative;
    width:350px;
    height:230px;
    cursor:pointer;
}

/* Koperta */
.envelope{
    position:absolute;
    width:100%;
    height:100%;
    background:url("koperta.jpg") center/cover no-repeat;
    border-radius:12px;
    overflow:hidden;
    transition:transform 1s ease;
}

/* Klapa */
.flap{
    position:absolute;
    top:0;
    left:0;
    width:100%;
    height:50%;
    background:url("koperta.jpg") center top/cover no-repeat;
    transform-origin:top;
    transition:transform 1s ease;
    z-index:2;
}

.envelope.open .flap{
    transform:rotateX(-180deg);
}

/* Zaproszenie */
.card{
    position:absolute;
    top:50%;
    left:50%;
    width:320px;
    height:450px;
    background:url("zaproszenie.jpg") center/cover no-repeat;
    border-radius:15px;
    transform:translate(-50%,-50%) scale(0);
    transition:0.8s;
    box-shadow:0 0 30px rgba(255,255,255,0.3);
}

.card.show{
    transform:translate(-50%,-50%) scale(1);
}

.info{
    position:absolute;
    bottom:-60px;
    width:100%;
    text-align:center;
    color:white;
    font-size:18px;
}
</style>
</head>
<body>

<!-- Film MP4 w tle -->
<video id="bg-video" autoplay muted loop playsinline>
    <source src="tlo.mp4" type="video/mp4">
</video>

<div class="overlay"></div>

<div class="container" onclick="openEnvelope()">

    <div class="envelope" id="envelope">
        <div class="flap"></div>
    </div>

    <div class="card" id="card"></div>

    <div class="info">
        Kliknij kopertę 💍
    </div>

</div>

<audio id="bg-music">
    <source src="muzyka.mp3" type="audio/mpeg">
</audio>

<script>
let opened = false;

function openEnvelope(){

    if(opened) return;
    opened = true;

    document.getElementById("envelope").classList.add("open");

    setTimeout(() => {
        document.getElementById("card").classList.add("show");
    }, 700);

    const music = document.getElementById("bg-music");
    music.play();
}
</script>

</body>
</html>
