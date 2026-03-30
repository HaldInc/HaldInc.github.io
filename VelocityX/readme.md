[Back to main](https://haldinc.github.io/)

# VelocityX 2026

<p align="center">
  <a href="https://www.youtube.com/watch?v=v8qwdybPl3o" target="_blank">
    <img src="https://img.youtube.com/vi/v8qwdybPl3o/maxresdefault.jpg" width="800" alt="VelocityX">
  </a>
</p>

<p align="center">
  <small><i>Click to check out the video on YouTube</i></small>
</p>

---


One of the kids got a Nerf gun for Christmas. Not one of those that looks like a killer machine, but a unicorn blaster.

This one: <br>
<img src="./IMG-4987_lowRes.jpg" width="600">  <!--  gun    -->

After a few shots, the question from my kids arose: How fast is it actually shooting?

I quickly asked the kids back, “Good question—how could you find out?”

Suggestions: <br>
- 1st suggestion: We can record the sound of firing it into a wall at a known distance and measure the time between the shot and it hitting the wall. <br>
- 2nd suggestion: We can record a video of the dart passing by and count the frames. <br>
- 3rd suggestion: We can shoot it past two switches and measure the time difference. <br>

All good suggestions, mainly from my 9- and 13-year-olds.

We decided to proceed with the 3rd suggestion, but use optical sensors instead of switches, as they will be a non-invasive measurement—and I already had a bag of old H21A1 sensors.


PcC circuit setup - just some resistors for current limit of the sensors. All the other stuff on the board was for another project. <br>

<div style="display:flex; gap:10px; flex-wrap:wrap; justify-content:center;">
  <img src="./IMG-4774_lowRes.jpg" width="300">
  <img src="./IMG-4772_lowRes.jpg" width="600">
</div>

We made a quick proof of concept and printed a holder for the two optical sensors with a spacing of 100 mm. This was really a "dirty setup," but that’s how PoCs sometimes are, and it was good enough to show the kids that we could measure it with our "standard household tools."

The two optical sensors were hooked up to their respective oscilloscope channels with rising edge triggering. Even with this simple setup, we could clearly see that the time between the dart passing the first and last sensor was 4.66 ms. As the flight distance is 100 mm, this corresponds to 21.46 m/s. We got our first speed measurement!

---



<!-- ---------------------------------------------------------------------------------------------------------------------------------------------------------  -->


<img src="./BatBox.JPG" width="600">   <!-- render of battery pack  -->

<img src="./Box 1.JPG" width="600">    <!-- Render version of the final     -->

<img src="./Fusion1.JPG" width="600">   <!--  in Fusion     -->






<img src="./IMG-4830_lowRes.jpg" width="600">  <!--  battery pack IRL    -->

<img src="./IMG-4909_lowRes.jpg" width="600">  <!--  optical sensor    -->

<img src="./IMG-4972_lowRes.jpg" width="600">  <!--  switch and leaver IRL    -->

<img src="./IMG-4988_lowRes.jpg" width="600">  <!--  First light test    -->

<img src="./IMG-5007_lowRes.jpg" width="600">  <!--  light connection    -->

<img src="./IMG-5036_lowRes.jpg" width="600">  <!--  shutter IRL    -->

<img src="./IMG-5069_lowRes.jpg" width="600">  <!--  Ociliscope after gates    -->

<img src="./IMG-5146_lowRes.jpg" width="600">  <!--  Final IRL    -->

<img src="./SensorHub.JPG" width="600">  <!-- Sensors as drawing     -->

<img src="./SideView.JPG" width="600">  <!-- Render of sensors and velocity tube     --> 

<img src="./SideView_CAD.JPG" width="600"> <!-- Render of sensors and velocity tube  - from Fusion    --> 

<img src="./Switch assembly.JPG" width="600">  <!-- Shutter assembly     -->

<img src="./VelocityX_1.PNG" width="600">  <!-- Final rander     -->

# Time to start printing:



