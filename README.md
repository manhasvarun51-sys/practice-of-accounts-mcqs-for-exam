<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Accounts Master 12</title>

<style>
body{
font-family:Arial,sans-serif;
background:#f5f5f5;
margin:0;
padding:20px;
}

.container{
max-width:700px;
margin:auto;
background:white;
padding:20px;
border-radius:15px;
box-shadow:0 0 20px rgba(0,0,0,.15);
}

h1{
text-align:center;
color:#1a73e8;
}

#score{
font-size:20px;
font-weight:bold;
margin-bottom:20px;
}

button{
width:100%;
padding:15px;
margin:10px 0;
font-size:18px;
cursor:pointer;
border:none;
border-radius:8px;
background:#1a73e8;
color:white;
transition:.3s;
}

button:hover{
background:#1558b0;
}

.correct{
background:green!important;
}

.wrong{
background:red!important;
}

#result{
font-size:22px;
font-weight:bold;
margin-top:20px;
text-align:center;
}

#next{
display:none;
}
</style>

</head>

<body>

<div class="container">

<h1>📚 Accounts Master 12</h1>

<div id="score">
Score : 0
</div>

<h2 id="question"></h2>

<div id="options"></div>

<button id="next" onclick="nextQuestion()">Next Question</button>

<div id="result"></div>

</div>

<script>

const questions=[

{
q:"Goodwill is a...",
o:["Current Asset","Intangible Asset","Fixed Asset","Liability"],
a:1
},

{
q:"Current Ratio =",
o:["Current Assets / Current Liabilities",
"Sales / Assets",
"Profit / Sales",
"Debt / Equity"],
a:0
},

{
q:"Debentures are...",
o:["Owner's Capital","Long-term Borrowings","Reserve","Asset"],
a:1
},

{
q:"Cash Flow Statement is prepared under...",
o:["AS-2","AS-3","AS-10","AS-26"],
a:1
},

{
q:"Sacrificing Ratio is calculated during...",
o:["Retirement","Admission","Dissolution","Death"],
a:1
},

{
q:"Inventory is excluded in...",
o:["Current Ratio","Quick Ratio","Debt Ratio","Net Profit Ratio"],
a:1
},

{
q:"Issue of Shares comes under...",
o:["Operating","Investing","Financing","None"],
a:2
},

{
q:"Realisation Account is prepared at...",
o:["Admission","Retirement","Dissolution","Issue of Shares"],
a:2
},

{
q:"Interest on Drawings is...",
o:["Income","Expense","Asset","Reserve"],
a:0
},

{
q:"Minimum Subscription is...",
o:["80%","90%","95%","100%"],
a:1
}

];

let score=0;
let current=0;

questions.sort(()=>Math.random()-0.5);

loadQuestion();

function loadQuestion(){

document.getElementById("next").style.display="none";

let q=questions[current];

document.getElementById("question").innerHTML=(current+1)+". "+q.q;

let options="";

q.o.forEach((opt,index)=>{

options+=`<button onclick="check(this,${index})">${opt}</button>`;

});

document.getElementById("options").innerHTML=options;

}

function check(btn,index){

let answer=questions[current].a;

let buttons=document.querySelectorAll("#options button");

buttons.forEach(b=>b.disabled=true);

if(index==answer){

btn.classList.add("correct");

score++;

document.getElementById("score").innerHTML="Score : "+score;

}else{

btn.classList.add("wrong");

buttons[answer].classList.add("correct");

}

document.getElementById("next").style.display="block";

}

function nextQuestion(){

current++;

if(current>=questions.length){

document.querySelector(".container").innerHTML=`
<h1>🎉 Test Completed</h1>

<h2>Your Score : ${score} / ${questions.length}</h2>

<button onclick="location.reload()">Practice Again</button>

`;

return;

}

loadQuestion();

}

</script>

</body>
</html># practice-of-accounts-mcqs-for-exam
