# IMGDfinalproject
A short clip/film made with shaders
# Flatline: A Generative Audio-Visual Descent

 1. Inspiration & Goals
This project began as an exploration of visual complexity and mathematical rendering,
but quickly evolved into a generative cinematic short film. My primary goal was to bridge the gap between abstract computational art and linear narrative storytelling.
I wanted to see if I could evoke specific emotional responses (tension, panic, clinical detachment) using only math, lighting algorithms, and pure audio synthesis. 

A secondary goal was technical performance: moving away from CPU-heavy p5.js drawing commands and pushing the entire visual pipeline to the GPU via a custom GLSL Fragment Shader,
ensuring a locked 60fps experience regardless of visual density. Finally, I wanted to break the fourth wall by integrating the viewer directly into the final frame of the film using live webcam data.

 2. What I Made 
The project consists of two parallel systems running live in the browser: a visual engine built in p5.js  and an audio synthesis engine built in Strudel.

 The Visual Engine (GLSL Shader)
The visuals are driven by a single 40-second GLSL Fragment Shader timeline, utilizing the time uniform to branch the math into five distinct acts:
 Act 1 (The Rain): Uses a pseudo-random hash function N21 and  sine waves to simulate gravity affected water droplets. The drops distort the background UV coordinates, visualizing
 the out-of-focus "bokeh" traffic lights behind them.
 Act 2 (The Ambulance): Manipulates the global coordinate space with sine/cosine waves to simulate camera shake. Uses fract() to build geometric ceiling tiles and smoothstep to create beveled plastic edges.
 The flashing siren lights use clamped sine waves max(sin(time), 0.0)) combined with alpha blending (mix()) to cast light on our grid.
 Act 3 & 4 (The Hospital): Manipulates the Y-axis over time to create the illusion of forward motion down a hallway. Uses Signed Distance Functions (SDFs) and inverted multiplication to draw massive,
 looming silhouettes of surgeons blocking a pure white surgical light.
 Act 5 (The Vector Ghost): Samples the user's live webcam feed. It converts the RGB pixels to grayscale brightness,
 maps that brightness to an angle, and uses a 2D rotation matrix to draw a responsive, vector-field contour of the user's face trapped behind a geometric blue prison grid.

 The Audio Engine Strudel 
Rather than using static audio files, the soundscape is generated live using Strudel
I was not able to integrate the piece into the code so this should be treated as a seperate project only to be used in a live performance.

 3. User Evaluation
To evaluate the success of the narrative pacing and the technical execution, I playtested the 40-second experience with 5 of my classmates  :

The Narrative Test: Without explaining the code beforehand, I asked users what story they just watched to see if the abstract math effectively conveyed a physical reality.
    Results: Users clearly understood the transition from the rainy street to the ambulance crash. However, the operating room scene (Act 4) was too abstract.
    Several users noted the imagery was vague and did not realize the looming, animated circles were meant to be surgeons leaning over a table until I explained the context. 
   Pacing and Duration: 
   Results: The  feedback from all 5 testers was a desire for the experience to be longer. While the 40-second timeline kept the technical performance tight,
   the rapid succession of scenes didn't give viewers quite enough time to process the emotional weight of each environment before moving to the next.
   
  The Fourth-Wall Stinger: I tracked physical reactions at the 40-second mark when their own face was suddenly vectorized into the grid.
     Results:This was highly successful. The webcam threshold held up perfectly in the classroom lighting, and the sudden shift from abstract geometry to a live 
     vectorized reflection of themselves elicited genuine surprise and effectively landed the final tone of the piece.



My take on this project:
By treating the shader like a camera rig and the math like a lighting department, I learned that computational art doesn't have to be purely abstract.
Pushing the limits of WebGL and live audio synthesis allowed me to create a tightly controlled, performative narrative experience that directly involves the viewer in its final moments.
