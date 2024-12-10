---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: SOCProjet
---

Hi my name is Johanan Seeruthen and this is my VGA driver Project, For my project I started off with trying to make a bat symbol however it wouldn't work so i changed it to a smily face that blinks that was made, using a modified version of Colour Stripes provided by my teacher.

## **Template VGA Design**
### **Project Set-Up**
The template design was a pretty straightforward demo on how to implement the VGA signal generation. It displayed vertical stripes of colors similar to an old VGA screen that produced a colourful image when no picture was being provided to them, this greatly increased my understanding of the ground work for how I was going to attempt the recreate a VGA timing and signal synchronization.

I set up the project in Vivado, and I ensured all the design files were correctly integrated and ready to simulate, synthesise and implement it into my project. I utizlised all the toold provided to me via the software Vivado to check the design flow, resource usage, and timing requirements for the project. This was useful to see the different parts of the FPGA work flow to see how they connect to the design to see how they run on the Basys 3 Artix 7 board provided to me by Michelle Lynch. 


Below is a screenshot of my project summary, showing the inital setup and design flow:



<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/Overview.png">


### **Template Code**
The main key module's in this project were:
- **VGASync.v:** This module makes the horizontal (hsync) and vertical (vsync) sync signals, this tracks the current position of each pizels that is being displayed on the screen screen, we can then ensure that the display is being updated row by row and frame by frame by using a horizontol count(hcount) and vertical count(vcount).
- **VGAColourStripes.v:** This module controls the colors that are being outputted based on the position of the pixels. The default design was dividing the screen into multiple vertical stripes, with each having a different color.
For example part of the original code was assiging colors like this: `if (col >= 0 && col < 210) begin` `red_next <= 4'b0000;   // Red stripe` `green_next <= 4'b1111;` `blue_next <= 4'b0000;` `end else if (col >= 220 && col < 430) begin` `red_next <= 4'b1111;   // Green stripe` `green_next <= 4'b0000; blue_next <= 4'b1111; end`
This logic was simplistic yet effective in splitting the screen into multiple vertical stripes with different colours. This aided me in understanding the relationship between the pixels co-ordinates and screen outputs.
### **Simulation**
Next step was to make a simulation, the process helped me to understand how the template design worked. I used the simulator thats included with Vivado to check the hsync and the vsync and the color signals over time. The waveform output that was produced by the simulator showed me the timing of the pulses, this made it clear to me that the design was following the VGA's specifications.

<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/Working Demo Sim.png">

For this template the simulation it had to verify that the color regions were mapped correctly to the sections of the screen. The timing diagram shown above shows how it transitions between the multiple color zones, this confirmed that the counters were incrementing as they were told to do.
### **Synthesis**
Next step was synthesis, for this process we had an initial design template that we tranlated the code into the a netlist which could then be used on the FPGA hardware. I used the synthesis tool on Vivado to do this process, this gave me a detailed and informative insights into how this design used it's recources, logic mapping and the timing. These reports confiremed that the template design we were using had been utilized with minimal logic and memory which was within the capabilities of the Basys 3 Artix 7 development board. This means that it indicated the basic design that my teacher had provided was a straightforward combinational logic sequence with counters and were efficient and ready for the FPGA programming.

add photo of report (temp one for now)
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/synthesis report.png">

The next step after synthesis was the implementation and it programmed the designing onto the FPGA hardware successfully. This involved mapping the bitstream that was generated to the board provided by Michelle Lynch, from this we can then connect the board to the VGA port on our monitor in our labs. When this is completed we should see the color stripes start displaying on the monitor. This shows that the design is functioning correctly as it displays on the monitor, we can also see that the image is displaying smnoothly showinf the VGA timing signals are synced. The process shows the effectiveness and how modular the design is, it also shows its ready for real world applications.

### **Demonstration**
Finally, once the board was programmed and connected to the VGA port on the monitor, The screen displayed the coloured vertical stripes. It was amazing to see some image finally displaying to the monitor
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/TempDisplay.png">


## **My VGA Design Edit**
### **Code Adaptation**
After doing the template display, I decided to try it myself, I made a smiley face that blinks. This involved adjusting the code within `VGAColourCycle.v` module.

<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/What I changed in VGATOP.png">
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/FaceCode.png">

This image isn't as complex as it seems to display but it does take an understanding of how to cycle the images to make the face wink and how to allign the images to make sure it also fits on the display. This design can be created by experimenting with the code until you understand and see the desired result you were hoping for
### **Simulation**
I then simulated the design on my blinking face design to confirm my color assignments and my transitions between the sections were correct. The waveform that was shown by the simulation also showed that the hcount values were alligned with what I put in my code to allign the boundaries of each pixel on the blinking face, the colors also matched what I expected to show up (white, yellow and black).

<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/Working Demo Sim.png">

The simulation also helps me if I needed to debug an issue in which the colors were overlapping because of incorrect boundary values. After adjusting the values within the if statements, the simulation looked perfect.
### **Synthesis & Implementation**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/face blinking.jpg">
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/ActualDisplay.png">

## **Heirarchy Layout**
The following image shows use how the heirarchy of the code should be displayed
<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/Source.png">

## **Failed Tests**
This is a paragraph. Add an empty line to start a new paragraph.
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/error 1.jpg">
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/error2.jpg">
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/error3.jpg">
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/error4.jpg">
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/error5.jpg">
