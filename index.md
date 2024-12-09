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

I set up the project in Vivado, and I ensured all the design files were correctly integrated and ready to simulate, synthesise and implement it into my project. Vivado's enviorment gave me all the tools I needed for checking the design flow, resource usage, and timing requirements. This was important because I needed to see how the different parts of the FPGA workflow and how they connect to ensure the design could run on the Basys 3 board provided to me.

Below is a screenshot of my project summary, showing the inital setup and design flow:



<img src="https://raw.githubusercontent.com/Johanan26/SOC/main/docs/assets/images/Overview.png">
### **Template Code**
Outline the structure and design of the Verilog code templates you were given. What do they do? Include reference to how a VGA interface works. Guideline: 2/3 short paragraphs, consider including screenshot(s).
### **Simulation**
Explain the simulation process. Reference any important details, include a well-selected screenshot of the simulation. Guideline: 1/2 short paragraphs.
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
