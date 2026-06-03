<!DOCTYPE html>
<html lang="pl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Zaproszenie Ślubne</title>

<style>

body{
    margin:0;
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    background:#f5f1eb;
    overflow:hidden;
}

/* KONTENER */

.container{
    position:relative;
    width:500px;
    height:400px;
}

/* ZAPROSZENIE */

.card{
    position:absolute;
    width:280px;
    height:400px;
    left:50%;
    bottom:70px;
    transform:translateX(-50%) translateY(220px);
    background:url("zaproszenie.jpg") center/cover no-repeat;
    border-radius:8px;
    transition:1.5s;
    z-index:1;
    box-shadow:0 10px 30px rgba(0,0,0,.25);
}

.card.show{
    transform:translateX(-50%) translateY(-120px);
}

/* KOPERTA */

.envelope{
    position:absolute;
    width:400px;
    height:250px;
    left:50%;
    bottom:0;
    transform:translateX(-50%);
    cursor:pointer;
    z-index:10;
}

/* TYŁ */

.back{
    position:absolute;
    width:100%;
    height:100%;
    background:#e7d5b7;
    border-radius:6px;
}

/* LEWY TRÓJKĄT */

.left{
    position:absolute;
    width:0;
    height:0;
    border-top:125px solid transparent;
    border-bottom:125px solid transparent;
    border-right:200px solid #d9c29c;
    z-index:11;
}

/* PRAWY */

.right{
    position:absolute;
    right:0;
    width:0;
    height:0;
    border-top:125px solid transparent;
    border-bottom:125px solid transparent;
    border-left:200px solid #d9c29c;
    z-index:11;
}

/* DÓŁ */

.bottom{
    position:absolute;
    bottom:0;
    width:0;
    height:0;
    border-left:200px solid transparent;
    border-right:200px solid transparent;
    border-top:130px solid #cdb287;
    z-index:12;
}

/* KLAPKA */

.flap{
    position:absolute;
    top:0;
    width:0;
    height:0;
    border-left:200px solid transparent;
    border-right:200px solid transparent;
    border-top:130px solid #efdcbc;
    transform-origin:top;
    transition:1s;
    z-index:20;
}

.flap.open{
    transform:rotateX(180deg);
}

</style>
</head>

<body>

<div class="container">

    <div class="card" id="card"></div>

    <div class="envelope" onclick="openInvite()">

        <div class="back"></div>
        <div class="left"></div>
        <div class="right"></div>
        <div class="bottom"></div>
        <div class="flap" id="flap"></div>

    </div>

</div>

<script>

let opened = false;

function openInvite(){

    if(opened) return;

    opened = true;

    document.getElementById("flap").classList.add("open");

    setTimeout(()=>{
        document.getElementById("card").classList.add("show");
    },600);
}

</script>

</body>
</html>
