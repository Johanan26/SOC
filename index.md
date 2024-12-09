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

<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/Overview.png">


### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.

## **My VGA Design Edit**
Introduce your own design idea. Consider how complex/achievabble this might be or otherwise. Reference any research you do online (use hyperlinks).
### **Code Adaptation**
Briefly show how you changed the template code to display a different image. Demonstrate your understanding. Guideline: 1-2 short paragraphs.
### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

## **More Markdown Basics**
This is a paragraph. Add an empty line to start a new paragraph.

Font can be emphasised as *Italic* or **Bold**.

Code can be highlighted by using `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list can be rendered as follows:
- vectors
- algorithms
- iterators

Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSrcs.png">
