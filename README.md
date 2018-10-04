# Computer-Science
//Halloween garden
//x coordinates of objects x y z and a
int x=1440;
int y=1440;
int z=1440;
int a=1440;

//y coordinate of objects x y z and a
int y1=600;
//determines what type of obstacles x y z and a will be
int nex=0;
int next=0;
int next2=0;
int next3=0;

//if launcher is 1, object is spawned from the right, proceeds to travel to the left
int xlauncher=1;
int ylauncher=0;
int zlauncher=0;
int alauncher=0;

int difficultyLevel= 2; //reduction of x coordinates
//difficultyLevel components
int start=0;
int gap=0;
int stopper=0;

// front page
int gameStart=0;
  

void setup(){
  size(1440,850);
  //fill(#A91BD1);
  //rect(0, 0, width, 600);
  //fill(#E87D25);
  //rect(0, y1, width, 200);
  frameRate(300);
  
  if (difficultyLevel==2) {
    start=500; 
    gap= 150; //checkpoints
    stopper=start-gap*6;
    println(stopper);
    
  }
}

void draw(){
  background (255);
  size (1440, 850);
  fill(#A91BD1);
  rect(0, 0, width, 600);
  fill(#E87D25);
  rect(0, y1, width, 400);
 
  FrontPage("x");
  //obstacle(next,y);
 obstacle(nex,"x");
 if (gameStart==1){
   //game
 } else if (gameStart==2){
   instruction();
 } else if (gameStart==3){
   score();
 }
  

  //determines obstacle position
  
 //x coordinate restart
  if (x==stopper) {
    xlauncher=0;
    x=1440;
  }
  if (y==stopper) {
    ylauncher=0;
    y=1440;
  }
  if (z==stopper) {
    zlauncher=0;
    z=1440;
  }
  if (a==stopper) {
    alauncher=0;
    a=1440;
  }
  
  
}





void obstacle(int type, String position){
   
  int x1=900;
  int blockSz=20;
  
if ( position== "x") {
    x1=x;
    x=x-difficultyLevel;
  }
  if ( position== "y") {
    x1=y;
    y=y-difficultyLevel;
  }
  if ( position== "z") {
    x1=z;
    z=z-difficultyLevel;
  }
  if ( position== "a") {
    x1=a;
    a=a-difficultyLevel;
  }
  
  
  
  noFill();
  noStroke();
    rect(x1, y1-blockSz*6, blockSz*5, blockSz*6);
    float p=10;
    translate(x1, 0);
    translate(0, y1-p*12);
    noStroke();
    rectMode(RADIUS);
    //head
    fill(#389B3F);
    arc(p*3, p*3, p*6, p*6, radians(-135), radians(135), PIE);
    //upper lip
    fill(#F5487F);
    rotate(radians(-45));
    translate(0, p*3);
    rect(0, 0, p/2, p*2, 100);
    translate(0, -p*3);
    rotate(radians(-315));
    //lower lip
    rotate(radians(45));
    translate(p*4.5, p*1.5);
    rect(0, 0, p/2, p*2, 100);
    translate(-p*4.5, -p*1.5);
    rotate(radians(-45));
    //upper teeth
    fill(255);
    triangle(p, p*1.7, p*.8, p*3, p*1.2, p*1.9);
    translate(p*.8, p*.8);
    triangle(p, p*1.7, p*.8, p*3, p*1.2, p*1.9);
    translate(-p*.8, -p*.8);
    //lower teeth
    triangle(p, p*4.7, p*.8, p*3.4, p*1.2, p*4.5);
    //spots
    fill(#306734);
    ellipse (p*4, p*1.5, p*1.4, p*1.5);
    ellipse (p*5, p*3.5, p*.8, p);
    ellipse (p*3, p*5, p*.8, p);
    //stem
    rectMode(CORNER);
    rect(p*8, p*4, p*2, p*8);
    rect(p*6, p*2, p*2, p*2);
    strokeWeight(100);
    arc(p*8, p*4, p*4, p*4, radians(-90), radians(0), PIE);
    translate(-x1, 0);
    translate(0, -y1+p*12);
}

void FrontPage(String position){
  
 int xStart=width/2-100/2;
   int yStart=y1+40;
   
  //fill(255);
   noFill();
  noStroke();
  rect(xStart,yStart,100,50);//start
  
  fill(0);
  textAlign(CENTER);
  textSize(30);
  text("START",xStart+50,yStart+40);
  
  
  //fill(255);
  noFill();
  noStroke();
  
  rect(xStart-70,yStart+60,250,50);
  
  fill(0);
  textAlign(CENTER);
  textSize(30);
  text("INTRODUCTION",xStart+60,yStart+95);
  
   //fill(255);
  noFill();
  noStroke();
  rect(xStart,yStart+120,100,50);
  
  fill(0);
  textAlign(CENTER);
  textSize(30);
  text("SCORE",xStart+50,yStart+150);
  
  
}

void mouseClicked(){
  int xStart=width/2-100/2;
   int yStart=y1+40;
  if(mouseX>=(xStart) && mouseX<=(xStart)+100 && mouseY>=(yStart) && mouseY<=(yStart)+50){
    gameStart=1;
  }else if (mouseX>=xStart-70 && mouseX<=(xStart-70)+250 && mouseY>=yStart+60 && mouseY<=(yStart+60)+50){
   gameStart=2;
    
  }else if(mouseX>(xStart) && mouseX<=(xStart)+1000 && mouseY>=(yStart+120) && mouseY<=(yStart+120)+50){
    gameStart=3;
  }
  // for going back from ins
    if(mouseX>=0 && mouseX<=width/90 && mouseY>=0 && mouseY<=width/90){
      gameStart=0;
    }
    
    
  
 
}

void instruction(){
 
  background (255);
  size (1440, 850);
  fill(#A91BD1);
  rect(0, 0, width, 600);
  fill(#E87D25);
  rect(0, y1, width, 400);
  
  fill(0);
  text(" The 'RIGHT' key is pressed to  move forward " ,width*1/2,height*1/2);
  text(" The 'UP' key is pressed to jump across the obstacle" , width*1/2,(height*1/2)+50);
  
  fill(#FF0320);
  rect(0,0,width/90,width/90);
  fill(0);
  textAlign(LEFT);
  text("x",0,0+width/90);
  
  
}

void score(){
   background (255);
  size (1440, 850);
  fill(#A91BD1);
  rect(0, 0, width, 600);
  fill(#E87D25);
  rect(0, y1, width, 400);
  
  for (int y=100; y<=width-700; y=y+width/35) {
    fill(255);
    strokeWeight(2);
  rect(width*1/2-100, y, 200, height/21);
}

fill(#FF0320);
  rect(0,0,width/90,width/90);
  fill(0);
  textAlign(LEFT);
  text("x",0,0+width/90);

}
