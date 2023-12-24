# canvas

1. Creating and resizing your canvas.

```javascript

let canvas = document.querySelector("canvas");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let c= canvas.getContext("2d");
c.fillStyle="red";
c.fillRect(200,400,200,200);
c.fillStyle="pink";
c.fillRect(100,300,900,200);
c.fillRect(300,200,500,200);


```



2. Drawing Elements.(canvas objects:)

1. Rectangle.
2. Lines.
3. Arcs/Circles.
4. Bezier Curves.
5. Images.
6. Text.

```javascript

// Line

c.beginPath();
// c.moveTo(x,y);
c.moveTo(600,600);
// c.lineTo(x,y);
c.lineTo(0,0);
c.lineTo(200,800);
c.strokeStyle="red";
c.stroke();

```

Arc circle

```javascript

for(var i= 0;i<300;i++){
          var x= Math.random()*window.innerWidth;
          var y = Math.random()*window.innerHeight;
          c.beginPath();
          c.arc(x,y,30,0,Math.PI*2,false);
          c.strokeStyle="blue"
          c.stroke();
}

```
```javascript

x=200;
y=300;

function animate(){
          requestAnimationFrame(animate);
          c.beginPath();
                    c.arc(x,y,30,0,Math.PI*2,false);
                    c.strokeStyle="blue"
                    c.stroke();
                    x+=5;
                    y+=5;
}

animate();




//remove copy on every call
x=200;
y=300;

function animate(){
          requestAnimationFrame(animate);
          c.clearRect(0,0,innerWidth,innerHeight);
          c.beginPath();
                    c.arc(x,y,30,0,Math.PI*2,false);
                    c.strokeStyle="blue"
                    c.stroke();
                    x++;
}

animate();


//bounce back from wall

x = 200;
dx = 4;
radius=50;

function animate() {
  requestAnimationFrame(animate);
  c.clearRect(0, 0, innerWidth, innerHeight);
  c.beginPath();
  c.arc(x, 200, radius, 0, Math.PI * 2, false);
  c.strokeStyle = "blue";
  c.stroke();
  if (x+radius > innerWidth || x-radius<0) {
    dx = -dx;
  }
  x += dx;
}

animate();

//bounce back from wall

x = Math.random()*innerWidth;;
y = Math.random()*innerHeight;
dx = (Math.random()-0.5)*8;
dy =(Math.random()-0.5)*8;
radius=30;

function animate() {
  requestAnimationFrame(animate);
  c.clearRect(0, 0, innerWidth, innerHeight);
  c.beginPath();
  c.arc(x, y, radius,0, Math.PI * 2, false);
  c.strokeStyle = "red";
  c.stroke();
  if (x+radius > innerWidth || x-radius<0) {
    dx = -dx;
  }
  if (y+radius > innerHeight || y-radius<0) {
    dy = -dy;
  }
  x += dx;
  y+=dy;
}

animate();

```



Create an object function for circle

```javascript

function Circle(x,y,dx,dy,radius){
          this.x=x;
          this.y=y;
          this.dx=dx;
          this.dy=dy;
          this.radius=radius;

          this.draw=function(){
                    c.beginPath();
                    c.arc(this.x, this.y, this.radius,0, Math.PI * 2, false);
                    c.strokeStyle = "red";
                    c.stroke();
          }

          this.update=function(){
                    if (this.y+this.radius > innerWidth || this.x-this.radius<0) {
                              this.dx = -this.dx;
                            }
                            if (this.y+this.radius > innerHeight || this.y-this.radius<0) {
                              this.dy = -this.dy;
                            }
                            this.x += this.dx;
                            this.y+=this.dy;
                            this.draw();
          }

}

var circle=new Circle(200,200,3,3,30);




function animate() {
  requestAnimationFrame(animate);
  c.clearRect(0, 0, innerWidth, innerHeight);
circle.update();
}

animate();


```


```javascript

function Circle(x, y, dx, dy, radius) {
  this.x = x;
  this.y = y;
  this.dx = dx;
  this.dy = dy;
  this.radius = radius;

  this.draw = function () {
    c.beginPath();
    c.arc(this.x, this.y, this.radius, 0, Math.PI * 2, false);
//     c.strokeStyle = "yellow";
    c.stroke();
    c.fill();
  };

  this.update = function () {
    if (this.x + this.radius > innerWidth || this.x - this.radius < 0) {
      this.dx = -this.dx;
    }
    if (this.y + this.radius > innerHeight || this.y - this.radius < 0) {
      this.dy = -this.dy;
    }
    this.x += this.dx;
    this.y += this.dy;
    this.draw();
  };
}

var circle = new Circle(200, 200, 3, 3, 30);

let circleArray = [];

for (var i = 0; i < 50; i++) {
          radius = 30;
  x = Math.random() * (innerWidth - radius*2)+radius;
  y = Math.random() *(innerHeight- radius*2)+radius;
  dx = (Math.random() - 5);
  dy = (Math.random() - 5);

  circleArray.push(new Circle(x, y, dx, dy, radius));
}

console.log(circleArray);

function animate() {
  requestAnimationFrame(animate);
  c.clearRect(0, 0, innerWidth, innerHeight);
for(var i=0;i<circleArray.length;i++){

          circleArray[i].update();
}

}

animate();


```











  
8. Animating Elements.
9. Interacting with the Elements.
   


