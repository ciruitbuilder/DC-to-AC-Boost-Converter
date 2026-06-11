# DC-to-AC-Boost-Converter
DESCRIPTION:

This can be considered as a continuation/addition to the previous project of building a step up transformer. In this project, instead of rubbing the wires to create varying voltage accross primary coil of transformer(and hence generating varying magnetic flux), A 555 timer in astable mode is used to generate a high frequency square wave signal which is fed into a switching transistor(used transistor instead of MOSFET as this transformer is used in low voltage applications here) which is connected similar to a switch to the main primary coil and battery circuit loop. This setup applies time varying potential difference accross transformer primary coil
and hence creating a induced emf in secondary coil which is used to power the output load.

CIRCUIT DIAGRAM:

<img width="581" height="415" alt="image" src="https://github.com/user-attachments/assets/09fa6208-bca4-4e86-98d2-332fea959932" />

The 1.5v cell is connected to the input + and input -. To power the square wave generating 555 timer circuit, an arduino is used in this case. 

COMPONENTS USED:

1. 20:5 (secondar : primary) step up transformer (built previously)

2. 1.5v cell

3. bc547 NPN transistor

4. 1 microfarad capacitors

5. battery holder

6. copper wires

7. single cored breadboard wires

8. 1k ohm resistors

9. 555 timer ic

10. Arduino Nano

11. Breadboard

FINISHED IMAGE:

<img width="1600" height="1200" alt="finished image" src="https://github.com/user-attachments/assets/7f540c43-de78-49ab-8686-26d98aabe7ce" />

This build was done in multipe attempts, i faced various issues which i tried solving. Those issues and my solutions are given as further topics

ATTEMPT 1:

Before connecting the 555 timer to the switching circuit(the transformer and transistor loop) i tested the switching circuit. I used an LED for output.The test approximated the frequency of square wave at the base of the transistor for which the LED glowed the brightest. I used an Arduino Nano to provide the square wave, because the frequency from a digital pin can be altered to our needs through the sketch ran by Arduino. The code is the blink sketch in examples section of arduino ide, the output pin is changed to D2 and the frequency can be changed using delay() [the time inside delay() is the time period of square wave generated] :

                                             f = 1/T (f ---> frequency, T ---> time period)

Setup to test it:

<img width="828" height="453" alt="image" src="https://github.com/user-attachments/assets/1e86504c-fc6a-44de-b887-cfac0f196fec" />


(No flyback diodes used as the application is low powered and the power required to burn the transistor is much higher than what can be provided by the 1.5v cell)

I observed that the brightness was noticable from 500Hz onwards. The testing video(1kHz):


