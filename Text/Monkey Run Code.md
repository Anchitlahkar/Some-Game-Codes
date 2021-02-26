# Monkey Run Code

-----------

````javascript
var PLAY = 1
var END = 0
var gameState = PLAY
var monkey , monkey_running
var banana ,bananaImage, obstacle, obstacleImage
var FoodGroup, obstacleGroup
var score = 0

function preload(){
  
  
  monkey_running =            loadAnimation("sprite_0.png","sprite_1.png","sprite_2.png","sprite_3.png","sprite_4.png","sprite_5.png","sprite_6.png","sprite_7.png","sprite_8.png")
  
  bananaImage = loadImage("banana.png");
  obstacleImage = loadImage("obstacle.png");
  jungleImage = loadImage("jungle.png")
 
}



function setup() {
  createCanvas(600, 200);
  
  monkey = createSprite(50,150,20,50);
  monkey.addAnimation("running", monkey_running);
  monkey.scale = 0.1;
  monkey.debug = true;
  
  backgroundImage = createSprite(200,100,600,200);
  backgroundImage.addImage(jungleImage)
  backgroundImage.depth = monkey.depth
  monkey.depth = monkey.depth +1
  
  backgroundImage1 = createSprite(650,100,600,200);
  backgroundImage1.addImage(jungleImage)
  backgroundImage1.depth = monkey.depth
  monkey.depth = monkey.depth +1
  
  backgroundImage.velocityX = -2
  backgroundImage1.velocityX = -2
 
  
  invisibleGround = createSprite(200,190,400,10);
  invisibleGround.visible = false;
  
  wall= createSprite(300,10,600,5)
  
  //create Obstacle and Cloud Groups
  obstaclesGroup = createGroup();
  
  score = 0
}

function draw() {
  background("skyBlue");
  
  if(backgroundImage.x < 0){
    backgroundImage.x = 200
    backgroundImage1.x = 650
  }
  
  //displaying score
  text("Score: "+ score, 500,50);
  
  if(keyDown("space")){
    monkey.velocityY = -8
    console.log(monkey.velocityY)
  }
  if(monkey.isTouching(wall)){
    monkey.velocityY = 8
    console.log(monkey.velocityY)
  }
  
    
  monkey.collide(invisibleGround);
  
  
  
  spawnObstacles();
  spawnBanana();
  

  
  drawSprites();
}

function spawnObstacles(){
 if (frameCount % 90 === 0){
   obstacle = createSprite(800,165,10,40);
   obstacle.addImage(obstacleImage);
 
   
   obstacle.velocityX = -2;
   
    //assign scale and lifetime to the obstacle           
    obstacle.scale = 0.1;
    obstacle.lifetime = 600;
   
   //add each obstacle to the group
    obstaclesGroup.add(obstacle);
 }
}

function spawnBanana(){
 if (frameCount % 90 === 0){
   banana = createSprite(800,100,10,40);
   banana.addImage(bananaImage);
 
   
   banana.velocityX = -2;
   
    //assign scale and lifetime to the obstacle           
    banana.scale = 0.1;
    banana.lifetime = 600;
   
 }
}
````

--------

----------

---------



# Monkey Run code 2

````javascript
var PLAY = 1
var END = 0
var gameState = PLAY
var monkey , monkey_running
var banana ,bananaImage, obstacle, obstacleImage
var FoodGroup, obstacleGroup
var score = 0

function preload(){
  
  
  monkey_running =            loadAnimation("sprite_0.png","sprite_1.png","sprite_2.png","sprite_3.png","sprite_4.png","sprite_5.png","sprite_6.png","sprite_7.png","sprite_8.png")
  
  bananaImage = loadImage("banana.png");
  obstacleImage = loadImage("obstacle.png");
  jungleImage = loadImage("jungle.png")
 
}



function setup() {
  createCanvas(600, 200);
  
  monkey = createSprite(50,150,20,50);
  monkey.addAnimation("running", monkey_running);
  monkey.scale = 0.1;
  monkey.debug = true;
  
  backgroundImage = createSprite(200,100,600,200);
  backgroundImage.addImage(jungleImage)
  backgroundImage.depth = monkey.depth
  monkey.depth = monkey.depth +1
  
  backgroundImage1 = createSprite(650,100,600,200);
  backgroundImage1.addImage(jungleImage)
  backgroundImage1.depth = monkey.depth
  monkey.depth = monkey.depth +1
  
  backgroundImage.velocityX = -2
  backgroundImage1.velocityX = -2
 
  
  invisibleGround = createSprite(200,190,400,10);
  invisibleGround.visible = false;
  
  wall= createSprite(300,10,600,5)
  
  //create Obstacle and Cloud Groups
  obstaclesGroup = createGroup();
  
  score = 0
}

function draw() {
  background("skyBlue");
  
  if(backgroundImage.x < 0){
    backgroundImage.x = 200
    backgroundImage1.x = 650
  }
  
  //displaying score
  text("Score: "+ score, 500,50);
  
  if(keyDown("space")){
    monkey.velocityY = -8
    console.log(monkey.velocityY)
  }
 monkey.velocityY = monkey.velocityY +8
  
    
  monkey.collide(invisibleGround);
  
  
  
  spawnObstacles();
  spawnBanana();
  

  
  drawSprites();
}

function spawnObstacles(){
 if (frameCount % 90 === 0){
   obstacle = createSprite(800,165,10,40);
   obstacle.addImage(obstacleImage);
 
   
   obstacle.velocityX = -2;
   
    //assign scale and lifetime to the obstacle           
    obstacle.scale = 0.1;
    obstacle.lifetime = 600;
   
   //add each obstacle to the group
    obstaclesGroup.add(obstacle);
 }
}

function spawnBanana(){
 if (frameCount % 90 === 0){
   banana = createSprite(800,100,10,40);
   banana.addImage(bananaImage);
 
   
   banana.velocityX = -2;
   
    //assign scale and lifetime to the obstacle           
    banana.scale = 0.1;
    banana.lifetime = 600;
   
 }
}
````

