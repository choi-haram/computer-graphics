# Computer graphics summary for the first semester of the second grade

## 프로세싱 소프트웨어 익히기

###  - java언어를 이용하여 원, 펜 만들기

###  - p5.js이용하여 vertex(), beginShape(), noise() 함수 사용

## 팀프로젝트 1

###  - 3차원 지형을 Light와 Camera, Material을 활용하여 창의적으로 변형하기

> ### 컴퓨터 그래픽스 12팀 구성
* 팀장: _20191007 최하람_
* 팀원: _20211078 김조은_ , _20210832 허윤_ , _20210812 박현서_,  _20191126손정우_

> #### 3차원 지형 변형 (최종코드)

```p5.js
var cols, rows;
var scl = 20;
var w = 1200; 
var h = 1000;
var i=0;

var flying = 0;

var terrain = [];
let camera;

function preload() {

img = loadImage('https://previews.123rf.com/images/viaire/viaire1502/viaire150200005/36643763-modelo-lindo-con-los-corazones-fresas-y-flores.jpg');}

function setup() {
  createCanvas(600, 600, WEBGL);
  cols = w / scl;
  rows = h / scl;
  camera = createCamera();

  for (var x = 0; x < cols; x++) {
    terrain[x] = []; //1D
    for (var y = 0; y < rows; y++) {
      terrain[x][y] = 0; //specify a default value for now //2D
    }
  }

}
let time=10;
function draw() {
  normalMaterial();
  flying -= 0.009;
  var yoff = flying;
  for (var y = 0; y < rows; y++) {
    var xoff = 0;
    for (var x = 0; x < cols; x++) {
      terrain[x][y] = map(noise(xoff, yoff), 0, 1, -10, 100);
      xoff += 0.2;
    }
    yoff += 0.2;
  }


  background(0);
  translate(0, 50);
  rotateX(PI / 2.5);
  translate(-w / 2, -h / 2);
  for (var y = 0; y < rows - 1; y++) {
    beginShape(TRIANGLE_STRIP);
    for (var x = 0; x < cols; x++) {
      let v = terrain[x][y];
      v = map(v, -100,100,0,255);
      fill(v-64,v-32,v);
      vertex(x * scl, y * scl, terrain[x][y]);
      vertex(x * scl, (y + 1) * scl, terrain[x][y + 1]);
    }
    endShape();
  }

    translate(500, -2000);

    rotate(PI/5);
    push();
    camera.lookAt(10, -100,-100);
    camera.setPosition(sin(millis() / 1000) * 50, -100, 300);
    if(time>0){time=time -2390;}
    if(time<0){time =time +2400;}
    translate(time-700,100,time-900);
    noStroke();
    lights();
    fill(270,330,0);
    sphere(150);
    if (time>2000) time=-2390;
    pop();
    push();
    if(frameCount>10) rotateY(frameCount =0);
    if(frameCount<-10) rotate(frameCount * 0.1);

    translate(1450, 1800 ,i+50);
    texture(img);
    torus(100, 30);
    pop();
    pointLight(2500, 250, 250, mouseX, mouseY, 50);
}
```
### before/after
![before](https://user-images.githubusercontent.com/50861700/161380645-49ca05a4-97f4-41b4-960c-ed5db20f9ccc.gif)   ![after](https://user-images.githubusercontent.com/50861700/161380650-4cde1d61-baa7-4f62-8ccb-01495354e62f.gif)   

> ### 변경한 점

* 달과 튜브를 추가
* 튜브 색,사이즈,위치 조정,튜브 구멍 조정
* 튜브 이미지 추가
* 카메라 위치와 각도 조정

## 팀프로젝트2
### - 논문 작성
### 논문 ppt 제작

## 팀프로젝트3
### - Snake Game 분석 

## 팀프로젝트4
### - faceApi를 이용한 미용 프로그램의 구현

## 팀프로젝트5
### - 얼굴 그물망모델링을 활용한 가상현실 가면
### - 논문 작성
### - ppt 제작
### - 유튜브 제작
### - 리플릿 제작

