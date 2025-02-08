# Game
let userScore = 0;
let computerScore = 0;

const choices = document.querySelectorAll(".choice");
const msg = document.querySelector("#msg");

const useerScorePara = document.querySelector("#user-score");
const computerScorePara = document.querySelector("#computer-score");

const genComputerChoice = () => {
    const options = ["rock","paper","scissors"];
    const randIdx = Math.floor(Math.random() * 3);
    return options[randIdx];
    //rock, paper, scissors
}

const drawGame = () => {
    console.log("Ouch!!, Game Drawn try Agai");
    msg.innerText = "Ouch!!, Game Drawn try Again";
    msg.style.backgroundColor = "#081b31";
}

const showWinner = (userWin, userChoice, computerChoice) => {
    if(userWin){
        userScore++;
        useerScorePara.innerText = userScore;
        console.log("Hurray!!, You Win");
        msg.innerText = `You Win ${userChoice} beats ${computerChoice}`;
        msg.style.backgroundColor = "green";
    }else{
        computerScore++;
        computerScorePara.innerText = computerScore;
        console.log("Oops!!, You Lose rome wasn't built in a day");
        msg.innerText = `You Lose ${computerChoice} beats ${userChoice}`;
        msg.style.backgroundColor = "red";
    }
}

const playGame = (userChoice) => {
    const computerChoice = genComputerChoice();

    if(userChoice == computerChoice){
        //Draw Game
        drawGame();
    }else{
        let userWin = true;
        if(userChoice === "rock"){
            //scissors, paper
            userWin = computerChoice === "paper" ? false:true;
        }else if(userChoice === "paper"){
            //rock, scissors
            userWin = computerChoice === "scissors" ? false : true;
        }else{
            //rock , paper
            computerChoice === "rock" ? false : true;
        }
        showWinner(userWin, userChoice, computerChoice);
    }
};

choices.forEach((choice) => {
    choice.addEventListener("click", () => {
        const userChoice = choice.getAttribute("id");
        playGame(userChoice);
    });
});
