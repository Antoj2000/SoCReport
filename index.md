---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---
I'm Anthony Johnson and this is my blog for my SoC 3rd year project. I will recreate a Yin-Yang as a VGA image using Vivado code

## **Template VGA Design**
### **Project Set-Up**
The Vivado project SoCProject targets the Artix-7 xc7a35tcpg236-1 FPGA and uses Verilog as the top-level design language. The project includes synthesis and implementation phases, both of which have completed successfully, despite a couple of warnings. 


 <img src="https://raw.githubusercontent.com/Antoj2000/SoCReport/main/docs/assets/images/ProSum.png"> 
 
 
### **Template Code**

A VGA interface works by transmitting analog signals to a monitor to display images. It uses three primary color channels (Red, Green, Blue) for color information and two synchronization signals: horizontal sync (HSYNC) and vertical sync (VSYNC). The pixel clock determines the timing of individual pixels, while the sync signals define the start and end of each line and frame, ensuring proper alignment of the displayed image. The VGA controller in the design generates these signals based on a predefined resolution and refresh rate, creating the desired image on the screen.

For this System on Chip project we were given two code templates that both demostrated different VGA images.
The first verilog code that was given to us was a colour cycle code. This code cycled through 8 different colours that switched the colour of the screen accordingly. 

The second code, and the the one I used for the base of my project, was Colour Stripes. Colour Stripes split the screen into rows and columns and uses if else statements to colour each column accordingly. This showed me how to section off areas of the screen and also set pixels to black and white.


### **Simulation**
Simulation involves verifying the functionality of your design before deploying it to hardware. 

This process begins with writing a testbench that simulates input signals such as pixel clock, horizontal sync (ROW), and vertical sync (COL). These signals drive your design, allowing the simulation to produce outputs for verification. The simulation ensures that the design splits the VGA display into columns and rows.

### **Synthesis and Implementation**
Synthesis converts your HDL code into a gate-level representation, optimizing it for the target FPGA. During this step, the tool checks for syntax correctness, maps the design to logical components, and ensures compatibility with the FPGA's architecture. Synthesis ensures the timing and logic for generating sync signals and RGB outputs are correctly translated into FPGA resources.

After synthesis, implementation maps the design to the physical resources of the FPGA. This includes placing and routing the logic to ensure the design meets timing constraints, particularly for the VGA's pixel clock and synchronization requirements. Once implementation is complete, a .bit file is generated, which can be programmed onto the FPGA to verify the VGA display functionality on hardware.

## **My VGA Design Edit**

The design I choose for my VGA design is a Yin-Yang. Ying and Yang is a chinese concept describing an opposite but interconnected, self-perpetuating cycle. Yin and yang can be thought of as complementary and at the same time opposing forces that interact to form a dynamic system in which the whole is greater than the assembled parts and the parts are important for cohesion of the whole.   [Yin-Yang Wiki](https://en.wikipedia.org/wiki/Yin_and_yang) 

<img src="https://raw.githubusercontent.com/Antoj2000/SoCReport/main/docs/assets/images/YinYangGoogle.png">

At first glance this design is complex due to it's circular nature and seemingly abstract swirls inside the circle. I asked ChatGPT to give me code for a Yin-Yang VGA image but to no avail.

<img src="https://raw.githubusercontent.com/Antoj2000/SoCReport/main/docs/assets/images/GPT%20Image.jpeg">

Although this was no success it was some help. (col - C3_X) * (col - C3_X) + (row - C3_Y) * (row - C3_Y)) <= C3_R * C3_R). This equation was littered through the code it gave me.
From this equation (equation of a circle) I was able to learn how to colour every pixel that resided inside the cicle what ever colour I wanted. (x,y) are the co-ordinated of the center of the circle and the 'r' is the desired radius.

Upon further inspection of the Yin-Yang on my screen and the new found knowledge fresh in my mind, I was able to deduce that the Yin-Yang symbol could easily be drawn by 5 circles in 3 layers. 


<img src="https://raw.githubusercontent.com/Antoj2000/SoCReport/main/docs/assets/images/Copy.jpg">


The 5th Circle is just one large circle split into black and white.

I think GPT sometimes takes its tasks too literal. When it seen the Yin-Yang it tried to caluclate every pixel exactly and in the end overengineered the code to the point of disaster. This reminds me of a youtube video I recently watched covering Moravec's paradox.

[Moravec's Paradox](https://youtu.be/raHM3k-uR0E?si=W4r_KTrS3OoV3b70).


Moravec's Paradox highlights the surprising difficulty AI and computational systems face with tasks humans find simple, while excelling at complex calculations. For instance, in drawing a yin-yang symbol, an overly engineered solution might involve intricate algorithms or complex logic. In contrast, I deduced a simpler approach using just five circles. This illustrates how humans often solve problems by reframing them in simpler terms, while AI or engineered solutions may lack the creativity or flexibility to see the easier path.

### **Code Adaptation**

Here is a snippet of my final code.

<img src="https://raw.githubusercontent.com/Antoj2000/SoCReport/main/docs/assets/images/VGACode.png">

At first I encountered a problem where the circles werent prioritising properly. I quickly realised that they need to be coded from top to bottom using if else statements. 
I replaced the if else checking columns with an equation checking if a pixel is within a circles boundaries. 
The colour grey is then called if a pixel is not used in the above equations. This is to close the bigger circle off and make the design clearer.


### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
//PUT IN MY SIMULATED DESIGN PIC 

### **Synthesis**
Here is my Synthesized Design 
<img src="https://raw.githubusercontent.com/Antoj2000/SoCReport/main/docs/assets/images/VGASynthesizedDesign.jpg">

Here is my Implemented Design 
<img src="https://raw.githubusercontent.com/Antoj2000/SoCReport/main/docs/assets/images/VGAImplementedDesign.jpg">

### **Demonstration**
Below is my final Ying-Yang design. 

<img src="https://raw.githubusercontent.com/Antoj2000/SoCReport/main/docs/assets/images/Yinyang%20completed.jpeg">

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
