# dzhe0035_individial_DongZheng
## Instructions on how to interact with the work
Moving the mouse up, down, left and right changes the number and distribution of rectangles, and mouse clicks change the color.

## Detailed information on animating group codes
In the draw() function, the code uses a for loop to iterate over each rectangle in the rectangles array (recta). The drawRectangle() function is then called to draw the rectangles. drawRectangle() takes as its arguments the position and size of the rectangles, as well as their internal color.
The mouseClicked() function is an event handler that is triggered when the mouse clicks on the canvas. In this function, the code regenerates the color palette (palette) and the main color (mainCol). First, the code empties the palette array. Then, a for loop generates 12 random hexadecimal colors and adds them to the palette. Next, a random mainCol is generated. Finally, all the colors in the palette, except the first one, and the mainCol, are merged into a new array, allColors.

**_Modify the code as follows:_**

```
// plotting function
function draw() {
  // Drawing background color
  background(backCol);
  // No Stroke
  noStroke()
  randomSeed(2)
  
  // Move the ball to be bigger or smaller
  translate(width/2-mouseX, height/2-mouseY)
  scale(map(mouseX, 0, width, 0, 2))


  // Iterate over all the cubes
  for (let recta of rectangles) {
    // Drawing small squares    
    drawRectangle(recta.i * u, recta.j * u, map(mouseX,0,width,0,recta.si * u), map(mouseY,0,height,0,recta.sj * u), recta.insideCol);
  }
}
```

```
function  mouseClicked(){
  palette = []
  createComposition();
  for (let i = 0; i < 12; i++) {
    // Generate random colours (16)
    let randomColor = '#' + Math.floor(Math.random()*16777215).toString(16);
    // Add the generated color to the array
    palette.push(randomColor); 
  }
  
  mainCol = '#' + Math.floor(Math.random()*16777215).toString(16)
  allColors = [...palette.slice(1), mainCol]

}
```
