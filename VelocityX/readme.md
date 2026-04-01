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



## The sketch:

<img src="./Sketch.JPG" height="600">


---

### The velocity meter unit:

From the PoC, it became clear that the H21A1 phototransistor optical interrupt switch was producing some “noise” and was sensitive to the environment. The H21A1 is designed with a gallium arsenide infrared emitting diode paired with a silicon phototransistor inside a small plastic housing, with only 3 mm between the emitter and the transistor. For our project, I needed a gap of about 25 mm, so I removed the diode and transistor from their original housing and built my own setup.

Even though the sensor is designed for infrared, ambient light could still interfere and affect the signal. To solve this, I covered the transistor in black tape and built a channel-like cover to shield the entire pathway between the first and second sensors. This helped stabilize the signal and made the setup more ridgit.

<div style="display:flex; gap:20px; flex-wrap:wrap; justify-content:center;">
  <img src="./IMG-4909_lowRes.jpg" height="400">  <!--  optical sensor    -->
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="./SensorHub.JPG" height="300">  <!-- Sensors as drawing     -->
</div>

The design speeds up print time while maintaining a lightweight yet strong structure. I designed the octagonal tube using the sheet metal tool in Fusion and printed it as a thin, foldable structure.

<br>
<br>

<p float="middle">
  <img align="top" src="./SheetMetal.JPG"  width="45%"/>  
  <img align="top" src="./SideView_CAD.JPG"  width="45%"/>
</p>

The fully covered channel turned out to have an even big benifit:  Making sure that no drats lands inside the unit itself, but are guide thrugh it.

### Improving signal quality:

To improve the signal quality from the phototransistors, I added a hex inverter with Schmitt-trigger inputs (74HC14). This gives a clean, sharp level transition that is perfect for the microcontroller:

<img src="./IMG-5069_lowRes.jpg" width="600">  <!--  Ociliscope after gates    -->

<!-- ---------------------------------------------------------------------------------------------------------------------------------------------------------  -->
---

### Power switch and the shutter assembly:

I wanted to have a mechanical power switch directly in serial with the battery pack, so we have zero standby power consumtion. As I would have a mechanical movement to power the unit on and off, I thought it would be cool to also make this cover the messuring pathway up - as a duft protection. *Actually, just to make it look cool.*

This turned out to be harder then expected, but I ended up with a design like this: 


<p float="middle">
  <img align="top" src="./SwitchAssembly.JPG"  width="50%"/>  
  <img align="top" src="./Fusion1.JPG"  width="45%"/>
</p>


<br>
<br>
Here is the final printed version being installed.

<img src="./IMG-4972_lowRes.jpg" width="600">  <!--  switch and leaver IRL    -->

As a side note, the LCD display is a very old 2 × 20-digit Epson EA-D20025AR module that I salvaged from a fax machine years ago and have reused in several projects since.

<!-- ---------------------------------------------------------------------------------------------------------------------------------------------------------  -->


---

### Battery case:

If you can buy an off-the-shelf battery container, always do that! But if you really want to design it yourself and print it, that is naturally also an option. This is what I needed to do as I couldnt wait to get one delivered and I didint have any at home. 

<div style="display:flex; flex-wrap:wrap; justify-content:center;">
  <img src="./BatBox.JPG" height="300">   <!-- render of battery pack  -->  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="./IMG-4830_lowRes.jpg" height="300">  <!--  battery pack IRL    -->
</div>

Again, I ended up overengineering the front cover a bit too much :)

The first iteration had a screw locking the front cover. This design results in a bigger bump on the inner side that would collide with the moving shutters; therefore, I needed a new solution. I ended up with a solution that is more integrated into the rear panel itself.

<div style="display:flex; flex-wrap:wrap; justify-content:center;">
  <img src="./BatCover_firstVer.jpg" height="300">   <!-- battery cover 1st version  -->  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="./BatCover_backSide.jpg" height="300">  <!--  battery cover - back side    -->
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="./BatCover_2ndVer.jpg" height="300">  <!--  battery cover 2nd version    --> 
</div>

Here are some renderings of the final design, featuring a print-in-place rotating disk for locking the panel.

<!--  Renderes view of the rear panel with the battery cover   -->
<div style="display:flex; flex-wrap:nowrap; justify-content:center;">
  <img src="./BatCoverRender1.JPG" height="400">  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="./BatCoverRender2.JPG" height="400">  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="./BatCoverRender3.JPG" height="400">  
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="./BatCoverSectionView.JPG" height="400"> 
</div>

This is the final printed version: <br>
<img src="./BatCover_Final.jpg" height="400">    <!--  battery cover - final version    --> 



---


<!-- ---------------------------------------------------------------------------------------------------------------------------------------------------------  -->
## Light effect 

<img src="./Box1.JPG">    <!-- Render version of the final     -->

To enhance the design and avoid just having a plain box, I wanted to add ribs to the sides - *inspired by the M41A Pulse Rifle from Aliens.* This idea quickly evolved into a different shape, and I decided to print them in semi-transparent PLA so we could add light to it.


The light effect has two functions:
- When the unit is powered on, the light rolls from one side to the other.
- When you shoot a Nerf dart through the velocity meter, the ribs on the sides light up as the dart travels through the unit.


This is a rendering of the ribs: <br>
<img src="./SideView.JPG" width="600">  <!-- Render of sensors and velocity tube     --> 

<br>

The kids wanted blue light, so that’s what we went with. Unfortunately, I only had blue SMD LEDs, so I needed to solder them under my microscope.

<img src="./LED_2.JPG" width="600">  <!--  light connection    -->

Some hot glue to hold it in place...

<img src="./IMG-5007_lowRes.jpg" width="600">  <!--  light connection    -->

..and heres the first test:

<img src="./IMG-4988_lowRes.jpg" width="600">  <!--  First light test    -->

<!-- ---------------------------------------------------------------------------------------------------------------------------------------------------------  -->
---
## LCD display

As mentioned before, the LCD display is a very old 2 × 20-character Epson EA-D20025AR module that I salvaged from a fax machine years ago. Yep, it’s old 🙂 but still working.

Here, I used the LCD to show current, minimum, maximum, and average speed. As I only have two lines, the MCU updates the display every 4 seconds, alternating between showing current and average speed, and minimum and maximum speed.

<img src="./IMG-5139_lowRes.jpg"  width="500">  <!--  First light test    -->

---

## Final design

The dimentions: <br>
<img src="./Dimentions.JPG" >    <!--  Dimentions.jpg  -->

Render of the final design: <br>
<img src="./Final_Render1.JPG">  <!-- Final rander     -->

The real life working product:  <br>
<img src="./IMG-5146_lowRes.jpg">  <!--  Final IRL    -->

<!-- ---------------------------------------------------------------------------------------------------------------------------------------------------------  -->
---
## Conclusion on the speed:

When measuring the speed of a gun, the measurements are very stable, and you can see a clear difference between the two Nerf guns we have. The "Unicorn Blaster" has an average speed of around 21.5 m/s, while the other gun is around 26.8 m/s.

It is also clear that the largest impact on the speed is not actually the gun itself, but the dart. When it is old, stepped on a few times, and slightly bent, it reduces the speed significantly. 
In a video I recorded, I used a dart that was squeezed a bit and had a few markings. This resulted in an average speed reduction from 21.6 m/s to 4.6 m/s.

---
CAD design is done in Autodesk Fusion. Animations in Blender.



