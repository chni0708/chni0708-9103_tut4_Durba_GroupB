
# Individual-project
 In this project, I crafted a dynamic and interactive visual animation that focuses on rotating and scaling various circle patterns. My individual work builds upon the group’s codebase by adding unique animations that noise-based transformations. These additions introduce smooth rotations and subtle size variations to specific visual elements, such as the white and yellow dot layers, enhancing the animation's rhythm and visual depth.


**Link of group project:**
https://github.com/chni0708/chni0708-9103_tut4_Durba_GroupB.git


**My individual task:  Noise-based transformations for animation.**

1. Noise-Based Animations for Dots 

My primary focus was integrating Perlin noise to animate certain layers, particularly the white and yellow dot layers, giving them a combination of rotational movement and size variation. Using a randomOrNoiseArray, I created a scaling factor for each circle to enable slight size adjustments in sync with the animation’s timing. This approach not only keeps the visuals cohesive but also adds a rhythmic, organic flow to the expansions and contractions.

Technical Explanation:
To create this effect, I applied a slowDownFactor to control how often the size animations update, resulting in smooth, gradual transitions. The size change code activates every 8 frames, following a pattern in frameCount, which ensures the animations maintain a visually pleasing pace without appearing overwhelming.



2. Rotating White and Yellow Dot Layers

To add complexity and visual appeal to the animation, I introduced rotating layers of white and yellow dots. These dots rotate around the center at different speeds and directions, while also displaying subtle size changes. This layering effect enhances the animation's rhythm and depth.

Technical Explanation:
I implemented a rotationAngle variable that increments with each draw() call, creating the smooth rotation effect. This angle is added to the base angle for each dot’s position calculation, allowing the dot layers to rotate continuously around the center.

For natural, rhythmic size variations, I used a randomOrNoiseArray and a slowDownFactor. By checking if frameCount is a multiple of slowDownFactor, I controlled the frequency of size updates, so that dot sizes adjust only every few frames. This method leverages Perlin noise to achieve smooth transitions in size, creating a cohesive, visually pleasing effect without abrupt changes.


**Link of individual project-animation:**
https://www.youtube.com/watch?v=zLl5sZ54__E


3.Coding 

let whiteDotLayers = [];
let yellowDotLayers = [];

let randomOrNoiseArray = [0.2, 1.8, 0.6, 1.2, 1.6]; 
//chenlu:These values act as scaling factors that control the size of the circles, with each value used to adjust the circle size by multiplying it with a base value
let slowDownFactor = 8//chenlu2:slowDownFactor is set to 8, meaning that the size will only update every 8 frames, slowing down the animation.
let valueArrayLength = randomOrNoiseArray.length;
//chenlu:This line gets the length of the randomOrNoiseArray and stores it in valueArrayLength. In this example, valueArrayLength is 5 because the array has five elements.

whiteDotLayers = [
    new WhiteDotLayers(bigCircles[5], 3, 18),
    new WhiteDotLayers(bigCircles[7], 4, 12),
    new WhiteDotLayers(bigCircles[9], 4, 12)
  ]
 yellowDotLayers = [
    new YellowDotLayers(bigCircles[0], 3, 12),
    new YellowDotLayers(bigCircles[2], 3, 14),
    new YellowDotLayers(bigCircles[1], 4, 16),
    new YellowDotLayers(bigCircles[4], 3, 12),
    new YellowDotLayers(bigCircles[6], 4, 18),
    new YellowDotLayers(bigCircles[12], 3, 16),
    new YellowDotLayers(bigCircles[14], 4, 12),]

    
class WhiteDotLayers {
  constructor(bigCircle, numLayers, numDots) {
    this.bigCircle = bigCircle;
    this.numLayers = numLayers;
    this.numDots = numDots;
    this.rotationAngle = 0;//chenlu3 Initialize the rotation angle of the white point
  }
  
  display() {
    let x = width * this.bigCircle.xScale;
    let y = height * this.bigCircle.yScale;
    this.rotationAngle += 0.01;//chenlu 3 Increase rotation angle for animation
    for (let layer = 1; layer <= this.numLayers; layer++) {
      let radius = this.bigCircle.r * 0.2 + layer * 30;
      for (let i = 0; i < this.numDots; i++) {
        let angle = TWO_PI / this.numDots * i+this.rotationAngle;//chenlu3 adding rotation angle
        let dotX = x + radius * cos(angle);
        let dotY = y + radius * sin(angle);
        let size = 20;
        // chenlu2:This line checks if frameCount (which increases every frame) is a multiple of slowDownFactor (8 in this case).
      //By doing this, size will only update once every 8 frames, instead of every frame, which makes the animation slower.
        if (frameCount % slowDownFactor === 0) {
          size = 20 + randomOrNoiseArray[frameCount / slowDownFactor % valueArrayLength] * 10;}
        fill(255);
        noStroke();
        ellipse(dotX, dotY, size);
      }
    }
  }
}


class YellowDotLayers {
  constructor(bigCircle, numLayers, numDots) {
    this.bigCircle = bigCircle;
    this.numLayers = numLayers;
    this.numDots = numDots;
    this.rotationAngle = 0; // chenlu 3 Initialize rotation angle for yellow dots
  
  }

  display() {
    let x = width * this.bigCircle.xScale;
    let y = height * this.bigCircle.yScale;
    this.rotationAngle += 0.01; // chenlu 3 Increment rotation angle for animation
    fill('#fabd4d');
    noStroke();
    for (let layer = 1; layer <= this.numLayers; layer++) {
      let radius = this.bigCircle.r * 0.20 + layer * 30;
      for (let i = 0; i < this.numDots; i++) {
        let angle = TWO_PI / this.numDots * i+this.rotationAngle; // chenlu 3 Add rotation angle;
        let dotX = x + radius * cos(angle);
        let dotY = y + radius * sin(angle);
        let size = 20;
        // Rate of update of control size
        if (frameCount % slowDownFactor === 0) {
          size = 20 + randomOrNoiseArray[frameCount / slowDownFactor % valueArrayLength] * 10;
        }
        ellipse(dotX, dotY, size);
      }
    }
  }
}

  //Draw white dot layers
  for (let dotLayer of whiteDotLayers){ dotLayer.display();
  }
  // Draw yellow dot layers
  for (let dotLayer of yellowDotLayers) {dotLayer.display();
  }