---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: SOCProjet
---

Hello, my name is Johanan Seeruthen and this is my SoC VGA driver Project report. For my project I began with attempting to create the Batman symbol however, the design did not turn out the way I expexcted, as you will see below, the images came out as randomly placed pxels across the middle of the middle of the screen, so after countless trial and error I decided to changed it to a smily face that blinks that was made, using a modified version of Colour Stripes provided by my lecturer.

## **Template VGA Design**
### **Project Set-Up**
The first template design was a good introduction to signal generation in VGA. This first template that we were given was a vga colour cycle. Instead of a still image, it would cycle through the colours that are normally shown in an old vga display. This in turn demonstrated to us hpw to cycle through image, which is a technique I used to create the 'blinking' effect that is shown in my project.

The second template design was a pretty straightforward demo on how to implement the VGA signal generation. It displayed vertical stripes of colors similar to an old VGA screen that produced a colourful image when no picture was being provided to them, this greatly increased my understanding of the ground work for how I was going to attempt the recreate a VGA timing and signal synchronization.

I set up the project in Vivado, and I ensured all the design files were correctly integrated and ready to simulate, synthesise and implement it into my project. I utizlised all the tools provided to me via the software Vivado to check the design flow, resource usage, and timing requirements for the project. This was useful to see the different parts of the FPGA work flow to see how they connect to the design to see how they run on the Basys 3 Artix 7 board provided to me by Michelle Lynch. 


Below is a screenshot of my project summary, showing the inital setup and design flow:

<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/Overview.png">


### **Template Code**
The main key module's in this project were:
- **VGASync.v:** This module makes the horizontal (hsync) and vertical (vsync) sync signals, this tracks the current position of each pizels that is being displayed on the screen screen, we can then ensure that the display is being updated row by row and frame by frame by using a horizontol count(hcount) and vertical count(vcount).
- 
- **VGAColourStripes.v:** This module controls the colors that are being outputted based on the position of the pixels. The default design was dividing the screen into multiple vertical stripes, with each having a different color.
For example part of the original code was assiging colors like this: `if (col >= 0 && col < 210) begin` `red_next <= 4'b0000;   // Red stripe` `green_next <= 4'b1111;` `blue_next <= 4'b0000;` `end else if (col >= 220 && col < 430) begin` `red_next <= 4'b1111;   // Green stripe` `green_next <= 4'b0000; blue_next <= 4'b1111; end`
This logic was simplistic yet effective in splitting the screen into multiple vertical stripes with different colours. This aided me in understanding the relationship between the pixels co-ordinates and screen outputs.
### **Simulation**
Next step was to make a simulation, the process helped me to understand how the template design worked. I used the simulator thats included with Vivado to check the hsync and the vsync and the color signals over time. The waveform output that was produced by the simulator showed me the timing of the pulses, this made it clear to me that the design was following the VGA's specifications.

<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/init sim.png">

For this template the simulation it had to verify that the color regions were mapped correctly to the sections of the screen. The timing diagram shown above shows how it transitions between the multiple color zones, this confirmed that the counters were incrementing as they were told to do.

### **Synthesis**
Next step was synthesis, for this process we had an initial design template that we translated the code into the a netlist which could then be used on the FPGA hardware. I used the synthesis tool on Vivado to do this process, this gave me detailed and informative insights into how this design used it's recources, logic mapping and the timing. These reports confiremed that the template design we were using had been utilized with minimal logic and memory which was within the capabilities of the Basys 3 Artix 7 development board. This means that it indicated the basic design that my teacher had provided was a straightforward combinational logic sequence with counters and were efficient and ready for the FPGA programming.

<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/init report.png">

### **Implementation**
The next step after synthesis was the implementation and it programmed the designing onto the FPGA hardware successfully. This involved mapping the bitstream that was generated to the development board provided, from this we can then connect the board to the VGA port on our monitor in our labs. The design also passes hold and pulse width checks but fails the setup timing check (WNS = -5.449 ns), meaning further optimization is required. The central window displays the physical layout of logic blocks and connections, helping identify timing-critical areas. When this is completed we should see the color stripes start displaying on the monitor. This shows that the design is functioning correctly as it displays on the monitor, we can also see that the image is displaying smnoothly showing the VGA timing signals are synced. The process shows the effectiveness and how modular the design is, it also shows its ready for real world applications. An example of this can be seen from the image bellow.

<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/Implementation design.png">


### **Demonstration**
Finally, once the board was programmed and connected to the VGA port on the monitor, The screen displayed the coloured vertical stripes. It was amazing to see some image finally displaying to the monitor

<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/TempDisplay.png">


## **My VGA Design Edit**
### **Code Adaptation**
The verilog code bellow is what i adapted to alter the demo template to generates my own personal code. It generates a simple face with blinking eyes on the VGA display. The logic for blinking is controller with a counter we made prior, this toggles the blink signal used for the face every so often based on the defined `BLINK_PERIOD`. The face was darwn by assigning color values to areas on the screen using the display grid. The face itself is yellow with black eyes and the eyes visibility are toggled based on the `blink` signal. The nose is also a small black rectangle within the face area. This code is made to make a visual representation of a face that is blinking.

<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/What I changed in VGATOP.png">
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/FaceCode.png">

This image isn't as complex as it seems to display but it does take an understanding of how to cycle the images to make the face wink and how to allign the images to make sure it also fits on the display. This design can be created by experimenting with the code until you understand and see the desired result you were hoping for
### **Simulation**
I then simulated the design on my blinking face design to confirm my color assignments and my transitions between the sections were correct. The waveform that was shown by the simulation also showed that the hcount values were alligned with what I put in my code to allign the boundaries of each pixel on the blinking face, the colors also matched what I expected to show up (white, yellow and black).

<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/Working Demo Sim.png">

The simulation also helps me if I needed to debug an issue in which the colors were overlapping because of incorrect boundary values. After adjusting the values within the if statements, the simulation looked perfect.
### **Synthesis**
next step was the synthesis, this process converted my Verilog code into a neetlist, this made it more usable for the FPGA hardware. I used the tools that are included with Vivado to generate a synthesis report, this told me there were no significant increses in the resource usage against my initial template shown above, I think this is becauase they both had very similar codes and relied on on the simple combinational logic for the assigning of the colors and counters for the pixel tracking. The key metrics like logic cell usage and the timing of it were shown to be within the limits for the board. This told me the design could be implemented in a real world application on the board.

<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/synthesis report.png">

Also included in this is the useful and helpful insights the synthesis gave me into what optimizations could be added like some logic to reduce delays and also improve the timing performance. Vivado also gave me some pointers on areas to improve on and refine on, it told me I can maybe add some timing constraints for the pixel clock. This mad sure my hardware was compatiable, it also taught me why I should keep using the value synthesis as this could play a critical step when i'm trying to improve my designs before I implement them into real world applications. 
### **Demonstration**
After I finished all these steps I can finally implment the design onto my board to use the VGA driver to display it onto a monitor. What I saw on the monitor was the smiley face blinking at me as it transitoned between the two switch cases. This was a great success as it shows all my code worked and the simluation proved to be right.
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/face blinking.jpg">
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/ActualDisplay.png">

## **Heirarchy Layout**
The hierarchy layout in the images shows me how the code is structred, it starts with the main components at the top and their related parts below it. This helps me keep the code clear to understand and east to work with by showing how everything is connected together. This structer make it easier for me to understand, fix and possibly even expand in the future.
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/Source.png">

## **Failed Tests**
There was a lot of trial and error during the duration of this project the following images outline the errors in the code as the images were not displaying a bat symbol. The original image i was supposed to make was the batman symbol however under intense trials and error it wouldn't work and time was against me so i decided to create a smiley face hat blinks instead.
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/error 1.jpg">
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/error2.jpg">
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/error3.jpg">
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/error4.jpg">
<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/error5.jpg">
