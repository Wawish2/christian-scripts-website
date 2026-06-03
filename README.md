# christian-scripts-website
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FaithStage - Christian Scripts</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial, sans-serif;
}

body{
    background:#f4f4f4;
    color:#333;
}

header{
    background:#1f4e5f;
    color:white;
    padding:20px;
    position:sticky;
    top:0;
}

nav{
    display:flex;
    justify-content:space-between;
    align-items:center;
}

.logo{
    font-size:1.5rem;
    font-weight:bold;
}

nav ul{
    list-style:none;
    display:flex;
    gap:20px;
}

nav a{
    color:white;
    text-decoration:none;
}

.hero{
    background:linear-gradient(rgba(0,0,0,.6),rgba(0,0,0,.6)),
    url('https://images.unsplash.com/photo-1504052434569-70ad5836ab65?w=1200');
    background-size:cover;
    background-position:center;
    color:white;
    text-align:center;
    padding:100px 20px;
}

.hero h1{
    font-size:3rem;
    margin-bottom:20px;
}

.hero p{
    font-size:1.2rem;
    max-width:700px;
    margin:auto;
}

.btn{
    display:inline-block;
    margin-top:25px;
    background:#f9b233;
    color:black;
    padding:12px 25px;
    text-decoration:none;
    border-radius:5px;
    font-weight:bold;
}

section{
    padding:60px 20px;
    max-width:1200px;
    margin:auto;
}

.section-title{
    text-align:center;
    margin-bottom:30px;
    color:#1f4e5f;
}

.about{
    text-align:center;
    line-height:1.8;
}

.search-box{
    text-align:center;
    margin-bottom:30px;
}

.search-box input{
    width:100%;
    max-width:500px;
    padding:12px;
    border:1px solid #ccc;
    border-radius:5px;
}

.scripts-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
    gap:20px;
}

.card{
    background:white;
    padding:20px;
    border-radius:10px;
    box-shadow:0 3px 10px rgba(0,0,0,.1);
}

.card h3{
    color:#1f4e5f;
    margin-bottom:10px;
}

.card p{
    margin-bottom:15px;
}

.card button{
    background:#1f4e5f;
    color:white;
    border:none;
    padding:10px 15px;
    cursor:pointer;
    border-radius:5px;
}

.contact-form{
    max-width:600px;
    margin:auto;
}

.contact-form input,
.contact-form textarea{
    width:100%;
    padding:12px;
    margin-bottom:15px;
    border:1px solid #ccc;
    border-radius:5px;
}

.contact-form button{
    background:#1f4e5f;
    color:white;
    border:none;
    padding:12px 20px;
    cursor:pointer;
}

footer{
    background:#1f4e5f;
    color:white;
    text-align:center;
    padding:20px;
}

.modal{
    display:none;
    position:fixed;
    inset:0;
    background:rgba(0,0,0,.7);
}

.modal-content{
    background:white;
    width:90%;
    max-width:800px;
    margin:5% auto;
    padding:30px;
    border-radius:10px;
    max-height:80vh;
    overflow:auto;
}

.close{
    float:right;
    cursor:pointer;
    font-size:28px;
    color:red;
}
</style>
</head>
<body>

<header>
<nav>
<div class="logo">FaithStage</div>

<ul>
<li><a href="#home">Home</a></li>
<li><a href="#about">About</a></li>
<li><a href="#scripts">Scripts</a></li>
<li><a href="#contact">Contact</a></li>
</ul>
</nav>
</header>

<section class="hero" id="home">
<h1>FaithStage</h1>
<p>
Bringing Bible stories to life through drama,
storytelling and Christian scripts.
</p>

<a href="#scripts" class="btn">Browse Scripts</a>
</section>

<section id="about">
<h2 class="section-title">About</h2>

<div class="about">
<p>
Welcome to FaithStage.
This platform shares Christian drama scripts,
Bible plays, youth ministry content and gospel storytelling resources.
</p>

<p>
Created by Emmanuel Mbiru to inspire faith,
creativity and evangelism through drama.
</p>
</div>
</section>

<section id="scripts">

<h2 class="section-title">Script Library</h2>

<div class="search-box">
<input
type="text"
id="searchInput"
placeholder="Search scripts..."
>
</div>

<div class="scripts-grid" id="scriptsContainer">

<div class="card">
<h3>David and Goliath</h3>
<p>Youth Drama • 15 Minutes</p>

<button onclick="openScript(
'David and Goliath',
'Scene 1: David arrives at the battlefield...'
)">
Read Script
</button>
</div>

<div class="card">
<h3>The Prodigal Son</h3>
<p>Church Play • 20 Minutes</p>

<button onclick="openScript(
'The Prodigal Son',
'Scene 1: The younger son requests his inheritance...'
)">
Read Script
</button>
</div>

<div class="card">
<h3>Faith Over Fear</h3>
<p>Youth Drama • 10 Minutes</p>

<button onclick="openScript(
'Faith Over Fear',
'Scene 1: A young believer struggles with fear...'
)">
Read Script
</button>
</div>

</div>

</section>

<section id="contact">

<h2 class="section-title">Contact</h2>

<form class="contact-form">

<input
type="text"
placeholder="Your Name"
required
>

<input
type="email"
placeholder="Your Email"
required
>

<textarea
rows="5"
placeholder="Your Message"
required
></textarea>

<button type="submit">
Send Message
</button>

</form>

</section>

<footer>
<p>
© 2026 FaithStage | Christian Scripts by Emmanuel Mbiru
</p>
</footer>

<div class="modal" id="scriptModal">

<div class="modal-content">

<span class="close" onclick="closeModal()">
&times;
</span>

<h2 id="scriptTitle"></h2>

<hr style="margin:15px 0;">

<p id="scriptContent"></p>

</div>

</div>

<script>

const searchInput =
document.getElementById("searchInput");

searchInput.addEventListener("keyup", () => {

const filter =
searchInput.value.toLowerCase();

const cards =
document.querySelectorAll(".card");

cards.forEach(card => {

const title =
card.querySelector("h3")
.textContent
.toLowerCase();

card.style.display =
title.includes(filter)
? "block"
: "none";

});

});

function openScript(title, content){

document.getElementById("scriptTitle")
.textContent = title;

document.getElementById("scriptContent")
.textContent = content;

document.getElementById("scriptModal")
.style.display = "block";
}

function closeModal(){
document.getElementById("scriptModal")
.style.display = "none";
}

window.onclick = function(event){

const modal =
document.getElementById("scriptModal");

if(event.target === modal){
closeModal();
}

}

</script>

</body>
</html>
