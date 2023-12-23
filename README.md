# canvas

1. Creating and resizing your canvas.

```javascript

let canvas = document.querySelector("canvas");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let c= canvas.getContext("2d");
c.fillRect(200,400,200,200);
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
c.stroke();

```
















  
8. Animating Elements.
9. Interacting with the Elements.
   


