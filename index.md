---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---
I'm Anthony Johnson and this is my blog for my SoC 3rd year project. I will recreate a Yin-Yang as a VGA image using Vivado code

## **Template VGA Design**
### **Project Set-Up**
Summarise the project set-up and design flow. Include a screenshot of your own set-up, for example see the image of my Project Summary window below. Guideline 1 short paragraph.


<img src="">
### **Template Code**
Outline the structure and design of the Verilog code templates you were given. What do they do? Include reference to how a VGA interface works. Guideline: 2/3 short paragraphs, consider including screenshot(s).

The verilog code that was give to us was a colour cycle code, this code cycled through
### **Simulation**
Explain the simulation process. Reference any important details, include a well-selected screenshot of the simulation. Guideline: 1/2 short paragraphs.
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.

## **My VGA Design Edit**
Introduce your own design idea. Consider how complex/achievabble this might be or otherwise. Reference any research you do online (use hyperlinks).

The design I choose for my VGA design is a Yin-Yang. Ying and Yang is a chinese concept describing an opposite but interconnected, self-perpetuating cycle. Yin and yang can be thought of as complementary and at the same time opposing forces that interact to form a dynamic system in which the whole is greater than the assembled parts and the parts are important for cohesion of the whole.  //ENTER REFERENCE , WIKI 
<img src="https://github.com/Antoj2000/SoCReport/blob/main/docs/assets/images/YinYangGoogle.png">

At first glance this design is complex due to it's circular nature and seemingly abstract swirls inside the circle. I asked ChatGPT to give me code for a Yin-Yang VGA image but to no avail.

<img src="https://raw.githubusercontent.com/Antoj2000/SoCReport/blob/main/docs/assets/images/GPT%20Image.jpeg">


Although this was no success it was some help. (col - C3_X) * (col - C3_X) + (row - C3_Y) * (row - C3_Y)) <= C3_R * C3_R). This equation was littered through the code it gave me.
From this equation (equation of a circle) I was able to learn how to colour every pixel that resided inside the cicle what ever colour I wanted. (x,y) are the co-ordinated of the center of the circle and the 'r' is the desired radius.

Upon further inspection of the Yin-Yang on my screen and the new found knowledge fresh in my mind, I was able to deduce that the Yin-Yang symbol could easily be drawn by 5 circles in 3 layers. 


<img src="https://github.com/Antoj2000/SoCReport/blob/main/docs/assets/images/Copy.jpg">


The 5th Circle is just one large circle split into black and white.

### **Code Adaptation**
Briefly show how you changed the template code to display a different image. Demonstrate your understanding. Guideline: 1-2 short paragraphs.

Layers are added top to bottom using if else statements. 


### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.

### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.

### **Demonstration**
Below is my final Ying-Yang design. 

<img src="https://github.com/Antoj2000/SoCReport/blob/main/docs/assets/images/Yinyang%20completed.jpeg">

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
