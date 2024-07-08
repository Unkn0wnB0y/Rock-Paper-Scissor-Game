# Rock-Paper-Scissor-Game
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rock Paper Scissors</title>
<style>
  *{
    margin: 0;
    padding: 0;
}
body{
    background-color:#EDC6A4 ;
}
h1{
    text-align: center;
    justify-content: center;
    padding: 30px;
    font-size: 60px;
    color:#212529;
    margin-top: 50px;
}
.score-board{
 display: flex;
 flex-direction: row;
 justify-content: center;
 align-items: center;
 font-size: 2rem;
 gap: 3rem;
 background-color:#F77472 ;
 margin-top: 100px;
 
}
.choice{
    height: 250px;
    width: 250px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center ;
}
.choice:hover {
    cursor: pointer;
    background-color: black;
}
img{
    height: 200px;
    width: 200px;
    object-fit: cover;
}
.choices{
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 150px;
    gap: 2rem;
}
.msg-container {
margin-top: 3rem;
display: flex;
align-items: center;
justify-content: center;
}
#msg{
    background-color: #081b31;
    color: aliceblue;
    font-size: 2rem;
    display: inline;
    padding: 1rem;
    border-radius: 1rem;
}
#user-score,
#comp-score{
    font-size: 4rem;
}
</style>
</head>
<body>
<h1>Rock Paper Scissors</h1>
   
    <div class="score-board">
        <div class="score">
            <p>Player </p>
            <p id="user-score"> 0</p>
        </div>
        <div class="score">
            <p>Computer </p>
            <p id="comp-score">0</p> 
        </div>
    </div>
    <div class="choices">
        <div class="choice" id="rock">
        <img src="https://nehalhazem.github.io/rockPaperScissors.io/img/rock.png" alt=""></div>
       <div class="choice" id="paper">
        <img src="https://nehalhazem.github.io/rockPaperScissors.io/img/paper.png" alt=""></div>
        <div class="choice" id="scissors">
        <img src="https://nehalhazem.github.io/rockPaperScissors.io/img/scissors.png" alt=""></div>
    </div>
    <div class="msg-container">
        <p id="msg">Play your move</p>
    </div>
<script>
  let userScore = 0;
let compScore = 0;
const choices = document.querySelectorAll(".choice");
const msg = document.querySelector("#msg");
const userScorepara = document.querySelector("#user-score");
const compScorepara = document.querySelector("#comp-score");
const genCompChoice = () => {
    const options = ["rock","paper","scissors"];
   const randIdx = Math.floor(Math.random() * 3);
   return options[randIdx];
};
const drawGame = () => {
    msg.innerText ="Game was Draw.";
    msg.style.backgroundcolor =" #081b31";
};
const showWinner = (userWin, userChoice ,compChoice) => {
 if(userWin) {
    userScore++;
    userScorepara.innerText = userScore ;
    msg.innerText =`You win! Your ${userChoice} beats ${compChoice}`;
    msg.style.backgroundcolor = "green";
 } else {
    compScore++;
    compScorepara.innerText = compScore;
    msg.innerText =`You lose. ${compChoice} beats Your ${userChoice}`;
    msg.style.backgroundcolor = "red";
 }
};
const playGame = (userChoice) => {
    const compChoice = genCompChoice();
    if (userChoice === compChoice) {
        drawGame();
    } else {
        let userWin = true ;
        if (userChoice === "rock") {
           userWin =compChoice === "paper" ? false : true ;
        } else if (userChoice === "paper") {
        userWin = compChoice === "scissors" ? false : true;
        } else {
         userWin =  compChoice === "rock" ? false : true ;
        }
        showWinner(userWin, userChoice, compChoice );
    }
};
choices.forEach((choice) => {
    choice.addEventListener( "click",() => {
     const userChoice = choice.getAttribute("id");
     playGame(userChoice);
    });
});
</script>
</body>

</html>
