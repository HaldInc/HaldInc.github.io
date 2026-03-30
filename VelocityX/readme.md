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

## Proof of concept:

We decided to proceed with the 3rd suggestion, but use optical sensors instead of switches, as they will be a non-invasive measurement — and I already had a bag of old H21A1 sensors.


PcC circuit setup - just some resistors for current limit of the sensors. All the other stuff on the board was for another project. <br>

<div style="display:flex; gap:10px; flex-wrap:wrap; justify-content:center;">
  <img src="./IMG-4774_lowRes.jpg" height="300">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="./IMG-4772_lowRes.jpg" height="300">
</div>

We made a quick proof of concept and printed a holder for the two optical sensors with a spacing of 100 mm. This was really a "dirty setup," but that’s how PoCs sometimes are, and it was good enough to show the kids that we could measure it with our "standard household tools."

The two optical sensors were hooked up to their respective oscilloscope channels with rising edge triggering. Even with this simple setup, we could clearly see that the time between the dart passing the first and last sensor was 4.66 ms. As the flight distance is 100 mm, this corresponds to 21.46 m/s. We got our first speed measurement!

---
## Product design:

Now that the PoC worked, we decided to turn this into a real product look and feel. _...naturally not for sale—unless someone wants to buy it :)_ We started with the requirements and the constraints:

### Requirements:
- Non-invasive measurement
- High accuricy measurement
- Show current, minimum, maximum and avrage speed
- Standalone tool - not need external power or phone or pc connection
- 3D printed case
- Some cool looking light
  
### Constraints
- This is a Christmas holiday project with the kids - only limited time.
- Use only components we have at home; no time to order anything.

---

### The velocity meter unit:

From the PoC, it became clear that the H21A1 phototransistor optical interrupt switch was producing some “noise” and was sensitive to the environment. The H21A1 is designed with a gallium arsenide infrared emitting diode paired with a silicon phototransistor inside a small plastic housing, with only 3 mm between the emitter and the transistor. For our project, I needed a gap of about 25 mm, so I removed the diode and transistor from their original housing and built my own setup.

Even though the sensor is designed for infrared, ambient light could still interfere and affect the signal. To solve this, I covered the transistor in black tape and built a channel-like cover to shield the entire pathway between the first and second sensors. This helped stabilize the signal and made the setup more ridgit.

<div style="display:flex; gap:20px; flex-wrap:wrap; justify-content:center;">
  <img src="./IMG-4909_lowRes.jpg" height="300">  <!--  optical sensor    -->
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="./SensorHub.JPG" height="300">  <!-- Sensors as drawing     -->
</div>

The design speeds up print time while maintaining a lightweight yet strong structure. I designed the octagonal tube using the sheet metal tool in Fusion and printed it as a thin, foldable structure.

<p float="middle">
  <img align="top" src="./SheetMetal.JPG"  width="45%"/>  
  <img align="top" src="./SideView_CAD.JPG"  width="45%"/>
</p>


### Improving the signal:


The fully covered channel turned out to have an even bigger benifit:  Making sure that no drats lands inside the unit. 

To improve the signal from the photo transistors I added a hex inverters with Schmitt-Trigger inputs (74HC14). This gave me a clean sharp level transision:

<img src="./IMG-5069_lowRes.jpg" width="600">  <!--  Ociliscope after gates    -->

This signal is perfect for a micro controller.

---

### Battery case:

If you can buy an off-the-shelf battery container, always do that! But if you really want to, print it.

<div style="display:flex; flex-wrap:wrap; justify-content:center;">
  <img src="./BatBox.JPG" height="300">   <!-- render of battery pack  -->  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="./IMG-4830_lowRes.jpg" height="300">  <!--  battery pack IRL    -->
</div>


---

### Power switch and the shutter assembly:

I wanted to have a mechanical power switch directly in serial with the battery pack, so we have zero standby power consumtion. As I would have a mechanical movement to power the unit on and off, I thought it would be cool to also make this cover the messuring pathway up - as a duft protection. *Actually, just to make it look cool.*

This turned out to be harder then expected, but I ended up with a design like this: 


| ![ShutterAssembly]("./SwitchAssembly.JPG"){height=500px} | ![In Fusion](./Fusion1.JPG){height=500px} |
|:--:|:--:|

<div style="display:flex; flex-wrap:nowrap; justify-content:center; align-items:center;">
  <img src="./SwitchAssembly.JPG" height="500">  <!-- Shutter assembly     -->
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="./Fusion1.JPG" height="500">   <!--  in Fusion     -->
</div>


<img src="./IMG-4972_lowRes.jpg" width="600">  <!--  switch and leaver IRL    -->


<!-- ---------------------------------------------------------------------------------------------------------------------------------------------------------  -->



<img src="./Box 1.JPG" width="600">    <!-- Render version of the final     -->









<img src="./IMG-4988_lowRes.jpg" width="600">  <!--  First light test    -->

<img src="./IMG-5007_lowRes.jpg" width="600">  <!--  light connection    -->

<img src="./IMG-5036_lowRes.jpg" width="600">  <!--  shutter IRL    -->

<img src="./SideView.JPG" width="600">  <!-- Render of sensors and velocity tube     --> 

<img src="./IMG-5146_lowRes.jpg" width="600">  <!--  Final IRL    -->


<img src="./SideView_CAD.JPG" width="600"> <!-- Render of sensors and velocity tube  - from Fusion    --> 


<img src="./VelocityX_1.PNG" width="600">  <!-- Final rander     -->

---
CAD design is done in Autodesk Fusion. Animations in Blender.



