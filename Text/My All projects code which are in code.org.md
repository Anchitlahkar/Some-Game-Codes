

# My All projects code which are in code.org







# My project on  Air hockey online game

###### Today I have submitted my Air hokey project in Whitehat Jr I had made this game in code.org

the code is here

``` javascript
//create the ball, playerPaddle and computerPaddle as sprite objects
var time = 0;
var opstical1 = 0; 

var wall1 = createSprite( 20,200,5,400);
wall1.shapeColor = "white";

var wall1 = createSprite( 380,200,5,400);
wall1.shapeColor = "white";

var op1 = createSprite(-10,-10,20,20);
op1.shapeColor = "White";
var op2 = createSprite(-20,-20,20,20); 
op2.shapeColor = "White";
var op3 = createSprite(-30,-30,20,20);
op3.shapeColor = "White";
var op4 = createSprite(-40,-40,20,20);
op4.shapeColor = "White";
var op5 = createSprite(-50,-50,20,20);
op5.shapeColor = "White";

var ball = createSprite(200,200,15,15);
ball.shapeColor = "yellow";


var playerPaddle = createSprite(200, 370,70,10);
playerPaddle.shapeColor = "brown";

var computerPaddle = createSprite(200,30,70,10);
computerPaddle.shapeColor = "brown";

var player = createSprite(200, 390,100,15);
player.shapeColor = "BLACK";

var computer = createSprite(200, 10,100,15);
computer.shapeColor = "BLACK";

//variable to store different state of game
var gameState = "serve";
var playerScore = 0;
var computerScore = 0;


function draw() {
  //clear the screen
  background("blue");
  // playerPaddle.x = ball.x;
  
  createEdgeSprites();
  
  if (ball.isTouching(edges) || ball.isTouching(playerPaddle) || ball.isTouching(computerPaddle)) {
      playSound("sound://category_jump/arcade_game_jump_1.mp3");
  }
  if (time >1500) {
    time = 0;
  }
  
  sound();
  extraDrawings();
  speed();
  player1();
  bounceOff();
  gameServe();
  gamePlay();
  roundOver();
  gameOver();
  restart();
  removeOp();
  startOp();
  opstical1restart();
  start();
  
  drawSprites();
}
function extraDrawings() {
  textSize(18 + 2); 
  fill("black");
  text( playerScore ,35, 220);
  text( computerScore , 35,180);
  
  computerPaddle.x = ball.x;

  for (var i = 0; i < 400 ; i = i + 20) {
    line(i,200, i + 10, 200);
  }
  
  fill("red");
  arc(200, 200, 50, 50, 0, 360);
  
  
  noFill();
  stroke("White");
  arc(200, 200, 100, 100, 0, 360);
  
  noFill();
  stroke("White");
  arc(200,0, 200, 200, 0, 360);
  arc(200,400, 200, 200, 0, 360);
}
function bounceOff() {
  ball.bounceOff(edges);
  ball.bounceOff(playerPaddle);
  ball.bounceOff(computerPaddle);
  ball.bounceOff(op1);
  ball.bounceOff(op2);
  ball.bounceOff(op3);
  ball.bounceOff(op4);
  ball.bounceOff(op5);
  
  playerPaddle.bounceOff(leftEdge);
  playerPaddle.bounceOff(rightEdge);
  
  computerPaddle.bounceOff(leftEdge);
  computerPaddle.bounceOff(rightEdge);
}
function serve() {
  ball.velocityX = 3;
  ball.velocityY = 4;
}
function reset() {
  ball.x = 200;
  ball.y = 200;
  ball.velocityX = 0;
  ball.velocityY = 0;
}
function player1() {
    if (keyDown(LEFT_ARROW)) {
    playerPaddle.x = playerPaddle.x - 10; 
  }
  
  if (keyDown(RIGHT_ARROW)) {
    playerPaddle.x = playerPaddle.x + 10; 
  }
}
function gameServe() {
  if (gameState === "serve") {
    textFont('Arial Black');
    fill("White");
    textSize(23);
    text("Press Space to Serve",80,180);
  }
}
function gamePlay() {
    if (keyDown("space") && gameState === "serve") {
    serve();
    gameState = "play";
  }   
}
function roundOver() {
  if(ball.isTouching(player) || ball.isTouching(computer)) {
    if (ball.isTouching(player)) {
      computerScore = computerScore + 1;
      playSound( "sound://category_alerts/retro_game_long_fall_2.mp3");
    }
    if (ball.isTouching(computer)) {
      playerScore = playerScore + 1;
      playSound("sound://category_hits/vibrant_game_big_game_horn_hit.mp3");
    }    
    reset();
    time = 0; 
    gameState = "serve";
  }
}
function gameOver() {
    if (computerScore === 3 || playerScore === 3 ) {
    gameState = "over";
    if (gameState === "over") {
    fill("white");
    text("Game Over" , 140,150);
    text("Press R to restart the game", 100, 180);
    time = 0;
    opstical1 = 0;
    }
    
  }
}
function restart() {
      if (keyDown("R") && gameState === "over") {
      computerScore = 0;
      playerScore = 0;
      time = 0;
      gameState = "serve";
    }
}
function speed() {
  if (time === 400) {
    ball.velocityX = 5;
    ball.velocityY = 6;
  }
  if (time === 800) {
    ball.velocityX = 7  ;
    ball.velocityY = 8  ;
  }
  
}
function startOp() {
  if (opstical1 === 100 || opstical1 === 500){
    op1.y = (randomNumber(30, 370));
    op1.x = (randomNumber(30, 370));
    
    op2.y = (randomNumber(30, 370));
    op2.x = (randomNumber(30, 370));
    
    op3.y = (randomNumber(30, 370));
    op3.x = (randomNumber(30, 370));
    
    op4.y = (randomNumber(30, 370));
    op4.x = (randomNumber(30, 370));
    
    op5.y = (randomNumber(30, 370));
    op5.x = (randomNumber(30, 370));
  }
  
  
}
function opstical1restart() {
  if (opstical1 === 700) {
    opstical1 = 0;
    
    op1.y = (randomNumber(-30, -370));
    op1.x = (randomNumber(-30, -370));
    
    op2.y = (randomNumber(-30, -370));
    op2.x = (randomNumber(-30, -370));
    
    op3.y = (randomNumber(-30, -370));
    op3.x = (randomNumber(-30, -370));
    
    op4.y = (randomNumber(-30, -370));
    op4.x = (randomNumber(-30, -370));
    
    op5.y = (randomNumber(-30, -370));
    op5.x = (randomNumber(-30, -370));
  
  }
  
}
function removeOp() {
  if (opstical1 === 0 || opstical1 === 300 ){
    op1.y = (randomNumber(-30, -370));
    op1.x = (randomNumber(-30, -370));
    
    op2.y = (randomNumber(-30, -370));
    op2.x = (randomNumber(-30, -370));
    
    op3.y = (randomNumber(-30, -370));
    op3.x = (randomNumber(-30, -370));
    
    op4.y = (randomNumber(-30, -370));
    op4.x = (randomNumber(-30, -370));
    
    op5.y = (randomNumber(-30, -370));
    op5.x = (randomNumber(-30, -370));
  
}
}
function start() {
  
  if (gameState === "serve") {
    time = 0;
    opstical1 = 0;
  }
  
  
  if (gameState === "play") {
    time = time + 1;
    opstical1 = opstical1 + 1;
  }
  
}
function sound() {
  if (ball.isTouching(op1) || ball.isTouching(op2)|| ball.isTouching(op3) || ball.isTouching(op4) || ball.isTouching(op5)) {
    playSound("sound://category_pop/retro_game_counter_ping_2.mp3");
  }
}

```



-----------------------------------------

------------------------------

















































# My project on pong game Advance

the code is here

```javascript
//create the ball, playerPaddle and computerPaddle as sprite objects
var ball = createSprite(200,200,10,10);
ball.setAnimation("ball");

var playerPaddle = createSprite(370,200,10,70);
playerPaddle.setAnimation("player");

var computerPaddle = createSprite(40,200,10,70);
computerPaddle.setAnimation("robot");

//variable to store different state of game
var gameState = "serve";

//variables to keep the score
var compScore = 0;
var playerScore = 0;


function draw() {
  //clear the screen
  background("Green");
  
  fill("white");
  arc(200, 200, 100, 100, 0, 360);
  
  
  if(ball.isTouching(computerPaddle) || ball.isTouching(playerPaddle)) {
   playSound("hit.mp3");
  }
  
   
  //place info text in the center
  if (gameState === "serve") {
    fill("Black");
    textSize(20);
    text("Press Space to Serve",110,140);
  }
   
  //display scores
  fill("Black");
  textSize(20);
  text(compScore, 170,20);
  text(playerScore, 230,20);
  
  //make the player paddle move with the mouse's y position
  playerPaddle.y = World.mouseY;
  
  //AI for the computer paddle
  //make it move with the ball's y position
  computerPaddle.y = ball.y;
  
  //draw line at the centre
  for (var i = 0; i < 400; i=i+20) {
    line(200,i,200,i+10);
  }
  
  if (keyWentDown("K")) {
    playerPaddle.setAnimation("player_kick");
  }
  
  if (keyWentUp("k")) {
    playerPaddle.setAnimation("player");
   }
  
  
  //create edge boundaries
  //make the ball bounce with the top and the bottom edges
  createEdgeSprites();
    if(ball.isTouching(bottomEdge) || ball.isTouching(topEdge)){
    playSound("wall_hit.mp3");
    }
  ball.bounceOff(topEdge);
  ball.bounceOff(bottomEdge);
  ball.bounceOff(playerPaddle);
  ball.bounceOff(computerPaddle);
 
  
  //serve the ball when space is pressed
  if (keyDown("space") &&  gameState === "serve") {
    serve();
    gameState = "play";
  }
  
 
  //reset the ball to the centre if it crosses the screen
  if(ball.x > 400 || ball.x <0) {
    
    if(ball.x > 400) {
      compScore = compScore + 1;
      playerPaddle.setAnimation("player_fall");
    }
    
    if(ball.x < 0) {
      playerScore = playerScore + 1;
    }
    
    playSound("score.mp3");
    
    reset();
    gameState = "serve";
  }
  
  if (playerScore === 5 || compScore === 5){
    gameState = "over";
    fill("Black");
    text("Game Over!",170,160);
    text("Press 'R' to Restart",150,180);
  }
  
  if (keyDown("r") && gameState === "over") {
    gameState = "serve";
    compScore = 0;
    playerScore = 0;
  }
  
  drawSprites();
}

function serve() {
  ball.velocityX = 3;
  ball.velocityY = 4;
  playerPaddle.setAnimation("player");
}

function reset() {
  ball.x = 200;
  ball.y = 200;
  ball.velocityX = 0;
  ball.velocityY = 0;
}
```

-----------------------------

---------------------------------------

























































# My Security System

``` js
var time = 0;
var lifeCount = 3;

var thief = createSprite(20,380,20,20);

var laser1 = createSprite(320,110,200,5);
laser1.shapeColor = "red";
var laser2 = createSprite(320,100,5,200);
laser2.shapeColor = "red";

var wall1 = createSprite(375,130,100,5);

var wall2 = createSprite(300,55,5,100);  

var gameState = "serve";


function draw() {
  
  background('White');

  
  fill("White");
  shape(390,0,380,10,390,20,400,10);

  
  createEdgeSprites();
  
  bounceOff1();
  gameStart();
  protecting();
  end();
  restart();
  gameOver();
  ifWin();
  
  drawSprites();
}
function bounceOff1() {
    thief.bounceOff(edges);
  }
function protecting() {
    if (thief.isTouching(laser1) && gameState === "play") {
      thief.velocityX = 0;
      thief.velocityY = 0;
      
    playSound("https://www.tones7.com/media/PoliceSirene.mp3");
      gameState = "over";
      lifeCount = lifeCount - 1;
    }
    
    if (thief.isTouching(laser2) && gameState === "play") {
      thief.velocityX = 0;
      thief.velocityY = 0;
      
    playSound("https://www.tones7.com/media/PoliceSirene.mp3");  
      gameState = "over";
      lifeCount = lifeCount - 1;
    
    }
    
    
}
function dicection() {
  
  if (keyDown(LEFT_ARROW)) {
    thief.velocityX = -5;
    thief.velocityY = 0;
  }
  
  if (keyDown(RIGHT_ARROW)) {
    thief.velocityX = 5;
    thief.velocityY = 0;
  }
  
  if (keyDown(UP_ARROW)) {
    thief.velocityX = 0;
    thief.velocityY = -5;
  }
  
  if (keyDown(DOWN_ARROW)) {
    thief.velocityX = 0;
    thief.velocityY = 5;
  }
  
}
function gameStart() {
  
  if (keyDown("space") && gameState === "serve") {
    gameState = "play";
  }

  if (gameState === "play"){
  dicection();
  randomLasers();
  background("Blue");
  wall1.shapeColor = "blue";
  wall2.shapeColor = "blue";
  fill("White");
  shape(390,0,380,10,390,20,400,10);
  time = time + 1;
}
}
function randomLasers() {
  if (time >= 50 && time < 100) {
    laser1.x = randomNumber(100, 300);
    laser1.y = randomNumber(20, 380);
    
    laser2.x = randomNumber(100, 300);
    laser2.y = randomNumber(20, 380);
  }
  
    if (time >= 0 && time < 50) {
    laser1.x = 320;
    laser1.y = 110;
    
    laser2.x = 320;
    laser2.y = 100;
  }
  
  if (time >=100) {
    time = 0;
  }
  
}
function end() {
  if (gameState === "over") {
    background("Red");
    
    wall1.shapeColor = "red";
    wall2.shapeColor = "red";
    
    laser1.x = 320;
    laser1.y = 110;
    
    laser2.x = 320;
    laser2.y = 100; 
    
    fill("White");
    shape(390,0,380,10,390,20,400,10);
    
    fill("black");
    textSize("20");
    text("The Thief is caught",120, 200);
    text("Press 'R' to restert the game",90,240);
    
    fill("Black");
    textSize(20);
    text("Life Count = ",250,380);
    text(lifeCount ,370,380);

    if (keyDown("R") && gameState === "over") {
    gameState = "serve";
    time = 0;
    }
    
    if (lifeCount === 0 && gameState === "over") {
    gameState = "Final Death";
    time = 0;
    }
  }
}
function restart() {
  if (gameState === "serve") {
    thief.x = 20;
    thief.y = 380;
    
    laser1.x = 320;
    laser1.y = 110;
    
    laser2.x = 320;
    laser2.y = 100;
    
    wall1.shapeColor = "white";
    wall2.shapeColor = "white";
    
  fill('Black');
  textSize(20);
  text("Press SPACE to start the game", 80,220);
  
    fill("Black");
    textSize(20);
    text("Life Count = ",250,380);
    text(lifeCount ,370,380);

  }
  
}
function gameOver() {
  if (gameState === "Final Death") {
  background("Red");
  fill('Black');
  textSize(20);
  text("The Thief is caught",120, 200);
  text("Game Over!!!", 150,240);
  
  }
  
}
function ifWin() {
  if (thief.isTouching(wall1) || thief.isTouching(wall2)) {
      time = 0;
  }
}
```

---------------------------------

---------------------------------



































# My fun game

the code is here

```javascript
console.log("Hi This game is made by Anchit Lahkar");
console.log("hi");

var score = 0;
var time = 0;


var Squariad = createSprite(196,57,20,20);
Squariad.shapeColor = "White";

  Squariad.velocityX = 0;
  Squariad.velocityY = 0;
  
var Golden = createSprite(200,30,500,10);
Golden.shapeColor = "black";

var Pin1 = createSprite(200,300,20,20);
Pin1.shapeColor = "yellow";

var Pin2 = createSprite(180,320,20,20);
Pin2.shapeColor = "yellow";

var Pin3 = createSprite(220,320,20,20);
Pin3.shapeColor = "yellow";

var Pin4 = createSprite(160, 340, 20, 20);
Pin4.shapeColor = "yellow";

var Pin5 = createSprite(200, 340, 20, 20);
Pin5.shapeColor = "yellow";

var Pin6 = createSprite(240, 340, 20, 20);
Pin6.shapeColor = "yellow";


var wall1 = createSprite(200,40,500,10);
wall1.shapeColor = "red";

var wall2 = createSprite(30,130,70,10);
wall2.shapeColor = "red";


var wall3 = createSprite(370,130,70,10);
wall3.shapeColor = "Red";

var wall4 = createSprite(370,170,70,10);
wall4.shapeColor = "Red";


var wall5 = createSprite(30,170,70,10);
wall5.shapeColor = "Red";

var square = createSprite(395,150,10,30);
square.shapeColor = "GReen";

var square1 = createSprite(5,150,10,30);
square1.shapeColor = "GReen";


function draw(){
  background("black");
  
  fill("White");
  textSize(20);
  text(score, 365, 384);
  text("Score = ", 278, 384);
  
  createEdgeSprites();
  

  direction();
  score1();
  round2();
  round2Velocity();
  round3();
  round3Velocity();
  destroy();
  allBounceoff();
  Endgame();
  
  
  drawSprites();
  return ;
  
  
}


function direction() {
    if(keyDown(UP_ARROW)) {
    Squariad.velocityX = 0;
    Squariad.velocityY = -3;
    }
    
    if(keyDown(DOWN_ARROW)) {
    Squariad.velocityX = 0;
    Squariad.velocityY = 3;
    }
    
    if(keyDown(LEFT_ARROW)) {
    Squariad.velocityX = -3;
    Squariad.velocityY = 0;
    
    }
    if(keyDown(RIGHT_ARROW)) {
    Squariad.velocityX = 3;
    Squariad.velocityY = 0;
    }    
    
    if(keyDown(ENTER)) {
    
    Squariad.velocityX = 0;
    Squariad.velocityY = 0;
    }
}
function destroy() {
    if (Squariad.isTouching(Golden)) {
      wall1.destroy();
      wall2.destroy();
      wall3.destroy();
      wall4.destroy();
      wall5.destroy();
      Pin1.destroy();
      Pin2.destroy();
      Pin3.destroy();
      Pin4.destroy();
      Pin5.destroy();
      Pin6.destroy();
      square.destroy();
      square1.destroy();
      Squariad.destroy();
      background("white");
      text("the game is Destroyed!!!", 150,200);
      text("Please Reaload", 170, 250);
  }
}
function allBounceoff() {
  
  Squariad.bounceOff(edges);
  Squariad.bounce(Pin1);
  Squariad.bounce(Pin2);
  Squariad.bounce(Pin3);
  Squariad.bounce(Pin4);
  Squariad.bounce(Pin5);
  Squariad.bounce(Pin6);
  Squariad.bounceOff(wall1);
  Squariad.bounceOff(wall2);
  Squariad.bounceOff(wall3);
  Squariad.bounceOff(wall4);
  Squariad.bounceOff(wall5);
  
  
  
  Pin1.bounceOff(edges);
  Pin1.bounce(Squariad);
  Pin1.bounce(Pin2);
  Pin1.bounce(Pin3);
  Pin1.bounce(Pin4);
  Pin1.bounce(Pin5);
  // Pin1.bounce(Pin6);
  Pin1.bounceOff(wall1);
  // Pin1.bounceOff(wall2);
  Pin1.bounceOff(wall2);
  Pin1.bounceOff(wall3);
  Pin1.bounceOff(wall4);
  Pin1.bounceOff(wall5);
       
  
  Pin2.bounceOff(edges);
  Pin2.bounce(Squariad);
  Pin2.bounce(Pin3);
  Pin2.bounce(Pin4);
  Pin2.bounce(Pin5);
  Pin2.bounce(Pin6);
  Pin2.bounceOff(wall1);
  Pin2.bounceOff(wall2);
  Pin2.bounceOff(wall3);
  Pin2.bounceOff(wall4);
  Pin2.bounceOff(wall5);

  
  
  
  Pin3.bounceOff(edges);
  Pin3.bounce(Squariad);
  Pin3.bounce(Pin4);
  Pin3.bounce(Pin5);
  Pin3.bounce(Pin6);
  Pin3.bounceOff(wall1);
  Pin3.bounceOff(wall2);
  Pin3.bounceOff(wall3);
  Pin3.bounceOff(wall4);
  Pin3.bounceOff(wall5);
  
  
  
  Pin4.bounceOff(edges);
  Pin4.bounce(Squariad);
  Pin4.bounce(Pin5);
  Pin4.bounce(Pin6);
  Pin4.bounceOff(wall1);
  Pin4.bounceOff(wall2);
  Pin4.bounceOff(wall3);
  Pin4.bounceOff(wall4);
  Pin4.bounceOff(wall5);
  
  
  Pin5.bounceOff(edges);
  Pin5.bounce(Squariad);
  Pin5.bounce(Pin6);
  Pin5.bounceOff(wall1);
  Pin5.bounceOff(wall2);
  Pin5.bounceOff(wall3);
  Pin5.bounceOff(wall4);
  Pin5.bounceOff(wall5);
  
  
  
  Pin6.bounceOff(edges);
  Pin6.bounce(Squariad);
  Pin6.bounce(Pin1);
  Pin6.bounceOff(wall1);
  Pin6.bounceOff(wall2);
  Pin6.bounceOff(wall3);
  Pin6.bounceOff(wall4);
  Pin6.bounceOff(wall5);

}
function score1() {
  if (Pin1.isTouching(square)) {
    background("White");
    score = score + 30;
    Pin1.x = 17;
    Pin1.y = 12;
  } 
  
    if (Pin2.isTouching(square)) {
    background("Green");
    score = score + 30;
    Pin2.x = 17;
    Pin2.y = 12;
  }
  
    if (Pin3.isTouching(square)) {
    background("purple");
    score = score + 30;
    Pin3.x = 17;
    Pin3.y = 12;
  }
  
    if (Pin4.isTouching(square)) {
    background("orange");
    score = score + 30;
    Pin4.x = 17;
    Pin4.y = 12;
  }
  
    if (Pin5.isTouching(square)) {
    background("Blue");
    score = score + 30;
    Pin5.x = 17;
    Pin5.y = 12;
  }
  
    if (Pin6.isTouching(square)) {
    background("yellow");
    score = score + 30;
    Pin6.x = 379;
    Pin6.y = 12;

  }
    if (Squariad.isTouching(square)){
    Squariad.x = 17;
    Squariad.y = 12;
    Squariad.velocityY = 12;
    }
  
  
    if (Pin1.isTouching(square1)) {
        score = score + 30;
        Pin1.x = 379;
        Pin1.y = 12;
      } 
      
    if (Pin2.isTouching(square1)) {
        score = score + 30;
        Pin2.x = 379;
        Pin2.y = 12;
      }
      
    if (Pin3.isTouching(square1)) {
        score = score + 30;
        Pin3.x = 379;
        Pin3.y = 12;
}
      
    if (Pin4.isTouching(square1)) {
        background("White");
        score = score + 30;
        Pin4.x = 379;
        Pin4.y = 12;
}
      
    if (Pin5.isTouching(square1)) {
        score = score + 30;
        Pin5.x = 379;
        Pin5.y = 12;
}
      
    if (Pin6.isTouching(square1)) {
        score = score + 30;
        Pin6.x = 379;
        Pin6.y = 12;
    }       
    if (Squariad.isTouching(square1)) {
        Squariad.x = 370;
        Squariad.y = 9;
        Squariad.velocityY = 12;
        }
}

function round2() {
  if (score === 180) {
    time = time + 1;
   if (time >= 50) {
     text("Press 'SPACE' for continoue",20 , 200);
     text("20 Points bonous for round 2", 40, 260 );
   
    if (keyDown("space")) {
      
        time = 1;
        score = score +20;
        
        Pin1.x = 200;
        Pin1.y = 300;
        Pin1.velocityX = 0;
        Pin1.velocityY = 0;
        
        Pin2.x = 180;
        Pin2.y = 320;
        Pin2.velocityX = 0;
        Pin2.velocityY = 0;
        
        Pin3.x = 220;
        Pin3.y = 320;
        Pin3.velocityX = 0;
        Pin3.velocityY = 0;
        
        Pin4.x = 160;
        Pin4.y = 342;
        Pin4.velocityX = 0;
        Pin4.velocityY = 0;
        
        Pin5.x = 200;
        Pin5.y = 342;
        Pin5.velocityX = 0;
        Pin5.velocityY = 0;
        
        Pin6.x = 240;
        Pin6.y = 342;
        Pin6.velocityX = 0;
        Pin6.velocityY = 0;
  }
 }
}
  
}
function round2Velocity() {
  if (time === 1) {
    if (Squariad.isTouching(Pin1) || Squariad.isTouching(Pin2) || Squariad.isTouching(Pin3) || Squariad.isTouching(Pin4) || Squariad.isTouching(Pin5) || Squariad.isTouching(Pin6)) {
    
    Pin1.velocityX = -4;
    Pin1.velocityY = 4;
    
    Pin2.velocityX = 4;
    Pin2.velocityY = -4;
    
    Pin3.velocityX = -4;
    Pin3.velocityY = 4;
    
    Pin4.velocityX = 4;
    Pin4.velocityY = -4;
    
    Pin5.velocityX = -4;
    Pin5.velocityY = 4;
    
    Pin6.velocityX = 4;
    Pin6.velocityY = -4;
    time = time - 1;
    } 
  }
  
}
function round3() {
  if (score === 380) {
    time = time + 5;
    if (time >= 5) {
     text("Press 'SPACE' for continoue",20 , 200);
     text("20 Points bonous for round 2", 40, 260 );
    }
    if (keyDown("space")) {
        
        
      
        score = score +20;
        
        Pin1.x = 200;
        Pin1.y = 300;
        Pin1.velocityX = 0;
        Pin1.velocityY = 0;
        
        Pin2.x = 180;
        Pin2.y = 320;
        Pin2.velocityX = 0;
        Pin2.velocityY = 0;
        
        Pin3.x = 220;
        Pin3.y = 320;
        Pin3.velocityX = 0;
        Pin3.velocityY = 0;
        
        Pin4.x = 160;
        Pin4.y = 342;
        Pin4.velocityX = 0;
        Pin4.velocityY = 0;
        
        Pin5.x = 200;
        Pin5.y = 342;
        Pin5.velocityX = 0;
        Pin5.velocityY = 0;
        
        Pin6.x = 240;
        Pin6.y = 342;
        Pin6.velocityX = 0;
        Pin6.velocityY = 0;
  }
 }
}
function round3Velocity() {
    if (time >= 5) {
    if (Squariad.isTouching(Pin1) || Squariad.isTouching(Pin2) || Squariad.isTouching(Pin3) || Squariad.isTouching(Pin4) || Squariad.isTouching(Pin5) || Squariad.isTouching(Pin6)) {
    
    Pin1.velocityX = -8;
    Pin1.velocityY = 8;
    
    Pin2.velocityX = 8;
    Pin2.velocityY = -8;
    
    Pin3.velocityX = -8;
    Pin3.velocityY = 8;
    
    Pin4.velocityX = 8;
    Pin4.velocityY = -8;
    
    Pin5.velocityX = -8;
    Pin5.velocityY = 8;
   
    Pin6.velocityX = 8;
    Pin6.velocityY = -8;
    time = time - 5;
    } 
  }
}
function Endgame() {
  if (score === 580) {
    score = score + 20;
  }
  if (score === 600) {
    
    text("you won the game. Congratulations!!!" , 20,220);
    
    Pin1.velocityX = 0;
    Pin1.velocityY = 0;
    
    Pin2.velocityX = 0;
    Pin2.velocityY = 0;
    
    Pin3.velocityX = 0;
    Pin3.velocityY = 0;
    
    Pin4.velocityX = 0;
    Pin4.velocityY = 0;
    
    Pin5.velocityX = 0;
    Pin5.velocityY = 0;
   
    Pin6.velocityX = 0;
    Pin6.velocityY = 0;
  }
  
  
}
```

-----------------------

----------------------





























# My project 5

the code is here

```javascript
var time = 0;

var waterPipe = createSprite( 200,85,360,3);
waterPipe.shapeColor = "Brown";

var waterPipe1 = createSprite( 200,135,360,3);
waterPipe1.shapeColor = "Brown";

var waterPipe2 = createSprite( 200,185,360,3);
waterPipe2.shapeColor = "Brown";

var waterPipe3 = createSprite( 200,235,360,3);
waterPipe3.shapeColor = "Brown";

var waterPipe4 = createSprite( 200,285,360,3);
waterPipe4.shapeColor = "Brown";

var waterPipe5 = createSprite( 20,105,3,360);
waterPipe5.shapeColor = "Brown";

var waterPipe6 = createSprite( 380,260,3,350);
waterPipe6.shapeColor = "Brown";


function draw() {
  background("rgb(139,69,19)");
  
  time1();
  
  if (time >= 1) {
    time = time +1;
  }
  
  restartTime();
  water();
  pumpkin();
  tomato();
  mushroom();
  brinjal();
  carrot();
  spinach();
  Brown();
  
  drawSprites();

}

function pumpkin() {
  for (var  p = 50;  p < 400; p = p + 50) {
  var Pumpkin = createSprite(p, 60, 20, 20);
  Pumpkin.shapeColor = "#ff7518";
  }
}
function tomato() {
  for (var t = 50; t < 400; t = t + 50) {
  var Tomato = createSprite(t,110, 20, 20);
  Tomato.shapeColor = "red";
  }
}
function mushroom() {
  for (var m = 50; m < 400; m = m + 50) {
  var Mushroom = createSprite(m,160, 20, 20);
  Mushroom.shapeColor = "#d8ccc0";
  }
}
function brinjal() {
  for(var b = 50; b < 400; b = b + 50) {
  var Brinjal = createSprite(b,210, 20, 20);
  Brinjal.shapeColor = "Purple";
  }
}
function carrot() {
  for (var c = 50; c < 400; c = c + 50) {
  var  Carrot = createSprite(c,260, 20, 20);
  Carrot.shapeColor = "#EB8921";
  }
}
function spinach() {
  for (var s = 50; s < 400; s = s + 50) {
  var Spinach = createSprite(s,310, 20, 20);
  Spinach.shapeColor = "#698056";
  }
}
function time1() {
  if (time === 0) {
    time = time + 1;
  }
}

function Brown() {
   if (time === 71 || time === 72 || time === 73 || time === 74 || time === 75) {
     waterPipe5.shapeColor = "Brown";
   }
   if (time === 76 || time === 77 || time === 78 || time === 79 || time === 80) {
     waterPipe.shapeColor = "Brown";
     waterPipe1.shapeColor = "Brown";
     waterPipe2.shapeColor = "Brown";
     waterPipe3.shapeColor = "Brown";
     waterPipe4.shapeColor = "Brown";
     waterPipe6.shapeColor = "Brown";
   }
}
function water() {
  if (time === 41 || time === 42 || time === 43 || time === 44 || time === 45) {
    waterPipe5.shapeColor = "Blue";
  }
  if (time === 46 || time === 47 || time === 48 || time === 49 || time === 50) {
    waterPipe5.shapeColor = "Blue";
    waterPipe.shapeColor = "Blue";
    waterPipe1.shapeColor = "Blue";
    waterPipe2.shapeColor = "Blue";
    waterPipe3.shapeColor = "Blue";
    waterPipe4.shapeColor = "Blue";
    waterPipe6.shapeColor = "Blue";
  }
}

function restartTime() {
  if (time >= 80) {
    time = 0;
  }
  
}
```

--------

---------------







































# My maze

the code is here

```javascript
var sofia = createSprite(10,5,15,15);
sofia.shapeColor = "white";

var cup = createSprite(10,390,15,15);
cup.shapeColor = "YELLOW";

var wall1 = createSprite(40,90,10,200);
var wall2 = createSprite(220,185,280,10);
var wall3 = createSprite(80,125,10,130);
var wall4 = createSprite(260,30,205,10);
var wall5 = createSprite(95,30,40,10);
var wall6 = createSprite(115,90,10,130);
var wall7 = createSprite(360,230,10,340);
var wall8 = createSprite(190,120,50,10);
var wall9 = createSprite(140,80,50,10);
var wall10 = createSprite(280,120,50,10);
var wall11 = createSprite(164,100,10,50);
var wall12 = createSprite(300,100,10,50);
var wall13 = createSprite(210,100,10,50);
var wall14 = createSprite(260,110,10,155);
var wall15 = createSprite(180,220,360,10);
var wall16 = createSprite(230,75,50,10);
var wall17 = createSprite(140,145,5,75);
var wall18 = createSprite(163,137,5,45);
var wall19 = createSprite(210,165,5,40);
var wall20 = createSprite(214,122,40,5);
var wall21 = createSprite(233,140,5,40);
var wall22 = createSprite(328,90,5,130);
var wall23 = createSprite(310,153,40,5);
var wall24 = createSprite(170,54,100,2);


var wall25 = createSprite(5,365,70,5);
var wall26 = createSprite(70,343,5,115);
var wall27 = createSprite(113,340,5,160);
var wall28 = createSprite(50,260,130,5);
var wall29 = createSprite(50,340,40,5);
var wall30 = createSprite(20,310,40,5);
var wall31 = createSprite(50,287,40,5);
var wall32 = createSprite(195,260,5,70);
var wall33 = createSprite(227,294,70,5);
var wall34 = createSprite(260,343,5,95);
var wall35 = createSprite(135,270,50,5);
var wall36 = createSprite(170,295,50,5);
var wall37 = createSprite(170,320,120,5);
var wall38 = createSprite(210,345,100,5);
var wall39 = createSprite(170,370,120,5);
var wall40 = createSprite(320,300,5,150);
var wall41 = createSprite(275,345,30,5);
var wall42 = createSprite(305,320,30,5);
var wall43 = createSprite(275,295,30,5);
var wall44 = createSprite(305,372,30,5);
var wall45 = createSprite(289,276,5,40);
var wall46 = createSprite(259,245,5,40);
var wall47 = createSprite(229,276,5,40);



var transfer1 = createSprite(280,113,30,10);
transfer1.shapeColor = "Blue";

var transfer2 = createSprite(235,85,40,10);
transfer2.shapeColor = "Blue";

var transfer3 = createSprite(187,110,35,10);
transfer3.shapeColor = "Blue";

var transfer4 = createSprite(90,390,30,10);
transfer4.shapeColor = "Blue";

var transfer5 = createSprite(15,230,30,10);
transfer5.shapeColor = "Blue";

var transfer6 = createSprite(340,230,30,10);
transfer6.shapeColor = "Blue";


function draw() {
  background("black");
  
  createEdgeSprites();
  
  colorWalls();
  
  youWin();
  
  bounceOff();
  
  direction();
  
  transfer();
  
  changeTransper();
  
  
  drawSprites();
}



function direction() {
    if (keyDown(UP_ARROW)) {
    sofia.velocityX = 0;
    sofia.velocityY = -4;
  }
  
    if (keyDown(DOWN_ARROW)) {
    sofia.velocityX = 0;
    sofia.velocityY = 4;
  }
  
    if (keyDown(RIGHT_ARROW)) {
    sofia.velocityX = 4;
    sofia.velocityY = 0;
  }
  
    if (keyDown(LEFT_ARROW)) {
    sofia.velocityX = -4;
    sofia.velocityY = 0;
  }
  
    if (keyDown("ENTER")) {
    sofia.velocityX = 0;
    sofia.velocityY = 0;
  }
  
}
function bounceOff() {
  sofia.bounceOff(edges);
  sofia.bounceOff(wall1);
  sofia.bounceOff(wall2);
  sofia.bounceOff(wall3);
  sofia.bounceOff(wall4);
  sofia.bounceOff(wall5);
  sofia.bounceOff(wall6);
  sofia.bounceOff(wall7);
  sofia.bounceOff(wall8);
  sofia.bounceOff(wall9);
  sofia.bounceOff(wall10);
  sofia.bounceOff(wall11);
  sofia.bounceOff(wall12);
  sofia.bounceOff(wall13);
  sofia.bounceOff(wall14);
  sofia.bounceOff(wall15);
  sofia.bounceOff(wall16);
  sofia.bounceOff(wall17);
  sofia.bounceOff(wall18);
  sofia.bounceOff(wall19);
  sofia.bounceOff(wall20);
  sofia.bounceOff(wall21);
  sofia.bounceOff(wall22);
  sofia.bounceOff(wall23);
  sofia.bounceOff(wall24);
  sofia.bounceOff(wall25);
  sofia.bounceOff(wall26);
  sofia.bounceOff(wall27);
  sofia.bounceOff(wall28);
  sofia.bounceOff(wall29);
  sofia.bounceOff(wall30);
  sofia.bounceOff(wall31);
  sofia.bounceOff(wall32);
  sofia.bounceOff(wall33);
  sofia.bounceOff(wall34);
  sofia.bounceOff(wall35);
  sofia.bounceOff(wall36);
  sofia.bounceOff(wall37);
  sofia.bounceOff(wall38);
  sofia.bounceOff(wall39);
  sofia.bounceOff(wall40);
  sofia.bounceOff(wall41);
  sofia.bounceOff(wall42);
  sofia.bounceOff(wall43);
  sofia.bounceOff(wall44);
  sofia.bounceOff(wall45);
  sofia.bounceOff(wall46);
  sofia.bounceOff(wall47);
}
function transfer() {
   if (sofia.isTouching(transfer1)) {
     sofia.velocityY = 0;
     sofia.x = 90;
     sofia.y = 370;
  }
  
  if (sofia.isTouching(transfer2)) {
     sofia.velocityY = 0;
     sofia.x = 335;
     sofia.y = 250;
  }
  
  if (sofia.isTouching(transfer3)) {
     sofia.velocityY = 0;
     sofia.x = 15;
     sofia.y = 250;
  }
  
 }
function changeTransper() {
     if (sofia.isTouching(transfer4)) {
     sofia.x = 275;
     sofia.y = 90;
     sofia.velocityY = 0;
   }
   
   if (sofia.isTouching(transfer5)) {
     sofia.x = 180;
     sofia.y = 80;
     sofia.velocityY = 0;
   }
   
   if (sofia.isTouching(transfer6)) {
     sofia.x = 225;
     sofia.y = 90 + 15;
     sofia.velocityY = 0;
   }
}
function colorWalls() {
  wall1.shapeColor = "silver";
  wall2.shapeColor = "silver";
  wall3.shapeColor = "silver";
  wall4.shapeColor = "silver";
  wall5.shapeColor = "silver";
  wall6.shapeColor = "silver";
  wall7.shapeColor = "silver";
  wall8.shapeColor = "silver";
  wall9.shapeColor = "silver";
  wall10.shapeColor = "silver";
  wall11.shapeColor = "silver";
  wall12.shapeColor = "silver";
  wall13.shapeColor = "silver";
  wall14.shapeColor = "silver";
  wall15.shapeColor = "silver";
  wall16.shapeColor = "silver";
  wall17.shapeColor = "silver";
  wall18.shapeColor = "silver";
  wall19.shapeColor = "silver";
  wall20.shapeColor = "silver";
  wall21.shapeColor = "silver";
  wall22.shapeColor = "silver";
  wall23.shapeColor = "silver";
  wall25.shapeColor = "silver";
  wall26.shapeColor = "silver";
  wall27.shapeColor = "silver";
  wall28.shapeColor = "silver";
  wall29.shapeColor = "silver";
  wall30.shapeColor = "silver";
  wall31.shapeColor = "silver";
  wall32.shapeColor = "silver";
  wall33.shapeColor = "silver";
  wall34.shapeColor = "silver";
  wall35.shapeColor = "silver";
  wall36.shapeColor = "silver";
  wall37.shapeColor = "silver";
  wall38.shapeColor = "silver";
  wall39.shapeColor = "silver";
  wall40.shapeColor = "silver";
  wall41.shapeColor = "silver";
  wall42.shapeColor = "silver";
  wall43.shapeColor = "silver";
  wall44.shapeColor = "silver";
  wall45.shapeColor = "silver";
  wall46.shapeColor = "silver";
  wall47.shapeColor = "silver";
}
function youWin() {
  if (sofia.isTouching(cup)) {
  sofia.overlap(cup);
  sofia.velocityX = 0;
  sofia.velocityY = 0;
  fill("yellow");
  textSize(50);
  text("You Win", 120, 150);
  wall1.destroy();
  wall2.destroy();
  wall3.destroy();
  wall4.destroy();
  wall5.destroy();
  wall6.destroy();
  wall7.destroy();
  wall8.destroy();
  wall9.destroy();
  wall10.destroy();
  wall11.destroy();
  wall12.destroy();
  wall13.destroy();
  wall14.destroy();
  wall16.destroy();
  wall17.destroy();
  wall18.destroy();
  wall19.destroy();
  wall20.destroy();
  wall21.destroy();
  wall22.destroy();
  wall23.destroy();
  wall24.destroy();
  transfer1.destroy();
  transfer2.destroy();
  transfer3.destroy();
  }
}
```

--------

---------



























# My Project pong game

the code is here

```javascript
var time = 0;
var playerScore = 0;
var computerScore = 0;
var playerPaddle = createSprite(390,200,10,70);
playerPaddle.shapeColor = "red";
var computerPaddle = createSprite(10,200,10,70);
computerPaddle.shapeColor = "red";
var ball = createSprite(200,200,15,15);
ball.shapeColor = "red";



function draw() {
  
  background("Yellow");

  
  createEdgeSprites();

  textSize(20);
  fill("black");
  text(playerScore, 240, 20);
  text(computerScore, 160, 20);
  
  if (keyDown("space")) {
    ball.velocityX = 5;
    ball.velocityY = 2;
    
  }
  
  ball.bounceOff(playerPaddle);
  ball.bounceOff(computerPaddle);
  ball.bounceOff(topEdge);
  ball.bounceOff(bottomEdge);
  
  playerPaddle.y = World.mouseY;
  computerPaddle.y = ball.y;
  
  
  if (ball.x >400 || ball.x < 0) {
    computerPaddle.x = 10;
    computerPaddle.y = 200;
  }
  
    if (ball.x >400) {
    computerScore = computerScore + 10;
    ball.x = 200;
    ball.y = 200;
    ball.velocityY = 0;
    ball.velocityX = 0;
  }
  
    if (ball.x >400) {
    playerScore = playerScore + 10;
    ball.x = 200;
    ball.y = 200;
    ball.velocityY = 0;
    ball.velocityX = 0;
  }
  
    if (computerScore === 30) {
    fill("black");
    textSize(20);
    text("Sorry you lose the Game", 80, 120);
    text("Please click ENTER to restart the game", 20, 180);
    playerPaddle.y = 200;
    playerPaddle.x = 390;
    ball.x = 200;
    ball.y = 200;
    ball.velocityY = 0;
    ball.velocityX = 0;
    
    
     if (keyDown("ENTER")) {
    playerPaddle.x = 390;
    playerPaddle.y = World.mouseY;
    computerPaddle.x = 10;
    computerPaddle.y = ball.y;
    computerScore = 0;
    playerScore = 0;
    ball.velocityX = 4;
    ball.velocityY = 2;
  }
  }
  
    if (playerScore === 30) {
    fill("black");
    textSize(20);
    text("Great!!!  You won the game", 80, 120);
    text("Please click ENTER to restart the game", 20, 180);
    playerPaddle.y = 200;
    playerPaddle.x = 390;
    ball.x = 200;
    ball.y = 200;
    ball.velocityY = 0;
    ball.velocityX = 0;
  }
  

  
  if (ball.x >=360){
    time = time + 1;
  }
  
  drawSprites();
  
}
```

------------

--------







#                      -----------------------End-----------------------



