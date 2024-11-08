
# Individual-project
 In this project, I crafted a dynamic and interactive visual animation that focuses on rotating and scaling various circle patterns. My individual work builds upon the group’s codebase by adding unique animations that noise-based transformations. These additions introduce smooth rotations and subtle size variations to specific visual elements, such as the white and yellow dot layers, enhancing the animation's rhythm and visual depth.


**Link of group project:**
https://github.com/chni0708/chni0708-9103_tut4_Durba_GroupB.git


**My individual task:  Noise-based transformations for animation.**

1.Noise-Based Animations for Dots and Layers
My primary focus was integrating Perlin noise to animate certain layers, particularly the white and yellow dot layers, giving them a combination of rotational movement and size variation. Using a randomOrNoiseArray, I created a scaling factor for each circle to enable slight size adjustments in sync with the animation’s timing. This approach not only keeps the visuals cohesive but also adds a rhythmic, organic flow to the expansions and contractions.

Technical Explanation:
To create this effect, I applied a slowDownFactor to control how often the size animations update, resulting in smooth, gradual transitions. The size change code activates every 8 frames, following a pattern in frameCount, which ensures the animations maintain a visually pleasing pace without appearing overwhelming.

2. Rotating White and Yellow Dot Layers

To add complexity and visual appeal to the animation, I introduced rotating layers of white and yellow dots. These dots rotate around the center at different speeds and directions, while also displaying subtle size changes. This layering effect enhances the animation's rhythm and depth.

Technical Explanation:

I implemented a rotationAngle variable that increments with each draw() call, creating the smooth rotation effect. This angle is added to the base angle for each dot’s position calculation, allowing the dot layers to rotate continuously around the center.

For natural, rhythmic size variations, I used a randomOrNoiseArray and a slowDownFactor. By checking if frameCount is a multiple of slowDownFactor, I controlled the frequency of size updates, so that dot sizes adjust only every few frames. This method leverages Perlin noise to achieve smooth transitions in size, creating a cohesive, visually pleasing effect without abrupt changes.
![coding 1](chni0708-9103_tut4_Durba_GroupB/picture/1.png)
![coding 2](chni0708-9103_tut4_Durba_GroupB/picture/2.png)
![coding 31](chni0708-9103_tut4_Durba_GroupB/picture/3.png)
![coding 4](chni0708-9103_tut4_Durba_GroupB/picture/4.png)

**Link of individual project-animation:**
https://www.youtube.com/watch?v=zLl5sZ54__E