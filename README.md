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
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    overflow:hidden;
    font-family:Georgia, serif;
}

/* FILM W TLE */
#bg-video{
    position:fixed;
    inset:0;
    width:100%;
    height:100%;
    object-fit:cover;
    z-index:-2;
}

.overlay{
    position:fixed;
    inset:0;
    background:rgba(0,0,0,0.35);
    z-index:-1;
}

/* GŁÓWNY BLOK */
.container{
    position:relative;
    width:420px;
    height:500px;
}

/* ZAPROSZENIE */
.card{
    position:absolute;
    left:50%;
    bottom:120px;
    width:320px;
    height:450px;
    transform:translateX(-50%) translateY(240px);
    background:url("zaproszenie.jpg") center/cover no-repeat;
    border-radius:12px;
    box-shadow:0 15px 35px rgba(0,0,0,.35);
    transition:1.5s ease;
    z-index:1;
}

.card.show{
    transform:translateX(-50%) translateY(-80px);
}

/* KOPERTA */
.envelope{
    position:absolute;
    bottom:0;
    left:50%;
    transform:translateX(-50%);
    width:420px;
    height:260px;
    z-index:5;
}

/* DÓŁ KOPERTY */
.envelope-body{
    position:absolute;
    width:100%;
    height:100%;
    background:url("koperta.jpg") center/cover no-repeat;
    border-radius:10px;
    overflow:hidden;
}

/* KLAPKA */
.flap{
    position:absolute;
    top:0;
    left:0;
    width:100%;
    height:130px;
    background:url("koperta.jpg") center top/cover no-repeat;
    transform-origin:top center;
    transition:1.2s ease;
    z-index:10;
}

.flap.open{
    transform:rotateX(-180deg);
}

/* NAPIS */
.text{
    position:absolute;
    width:100%;
    top:-60px;
    text-align:center;
    color:white;
    font-size:22px;
    text-shadow:0 0 10px black;
}
</style>
</head>
<body>

<video autoplay muted loop playsinline id="bg-video">
    <source src="tlo.mp4" type="video/mp4">
</video>

<div class="overlay"></div>

<div class="container">

    <div class="text">
        Kliknij kopertę 💍
    </div>

    <div class="card" id="card"></div>

    <div class="envelope" onclick="openInvitation()">

        <div class="flap" id="flap"></div>

        <div class="envelope-body"></div>

    </div>

</div>

<audio id="music">
    <source src="muzyka.mp3" type="audio/mpeg">
</audio>

<script>
let opened = false;

function openInvitation(){

    if(opened) return;
    opened = true;

    document.getElementById("flap").classList.add("open");

    setTimeout(() => {
        document.getElementById("card").classList.add("show");
    }, 700);

    document.getElementById("music").play();
}
</script>

</body>
</html>
