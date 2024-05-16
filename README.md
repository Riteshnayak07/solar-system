# solar-system
<!DOCTYPE html>
<html>
<head>
<title>Solar System Model</title>
<style>
canvas {
background-color:rgb(0, 0, 0); }
</style>
</head>
<body>
<canvas id="canvas" width="1350" height="600"></canvas>
<script>
var canvas=document.getElementById('canvas');
var ctx=canvas.getContext('2d');
var sun= {
x:canvas.width/2,y:canvas.height/2,radius:35,color:'orange' };
var earth= {
x:canvas.width/2,y:canvas.height/2-150,radius:15,color:'green',orbitRadius:150,angle:0,speed:0.04 };
var moon= {
x:earth.x+50,y:earth.y,radius:5,color:'white',orbitRadius:50,angle:0,speed:0.10 };
function draw() {
//Clear the canvas
ctx.clearRect(0,0,canvas.width,canvas.height);

//Draw the sun
ctx.fillStyle=sun.color;
ctx.beginPath();
ctx.arc(sun.x,sun.y,sun.radius,0,Math.PI*2);
ctx.fill();

//Draw the earth's orbit
ctx.strokeStyle='white';
ctx.beginPath();
ctx.arc(canvas.width/2,canvas.height/2,earth.orbitRadius,0,Math.PI*2);
ctx.stroke();

//Draw the earth
ctx.fillStyle=earth.color;
ctx.beginPath();
ctx.arc(earth.x,earth.y,earth.radius,0,Math.PI*2);
ctx.fill();

//Draw the moon
ctx.fillStyle=moon.color;
ctx.beginPath();
ctx.arc(moon.x,moon.y,moon.radius,0,Math.PI*2);
ctx.fill();

//Update the earth's position
earth.x=canvas.width/2+earth.orbitRadius*Math.cos(earth.angle);
earth.y=canvas.height/2+earth.orbitRadius*Math.sin(earth.angle);
earth.angle+=earth.speed;

//Update the moon's position
moon.x=earth.x+moon.orbitRadius*Math.cos(moon.angle);
moon.y=earth.y+moon.orbitRadius*Math.sin(moon.angle);
moon.angle+=moon.speed;
requestAnimationFrame(draw);
}
requestAnimationFrame(draw);
</script>
</body>
</html>
