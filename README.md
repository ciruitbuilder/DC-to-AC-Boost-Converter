# DC-to-AC-Boost-Converter
DESCRIPTION:

This can be considered as a continuation/addition to the previous project of building a step up transformer. In this project, instead of rubbing the wires to create varying voltage accross primary coil of transformer(and hence generating varying magnetic flux), A 555 timer in astable mode is used to generate a high frequency square wave signal which is fed into a switching transistor(used transistor instead of MOSFET as this transformer is used in low voltage applications here) which is connected similar to a switch to the main primary coil and battery circuit loop. This setup applies time varying potential difference accross transformer primary coil
and hence creating a induced emf in secondary coil which is used to power the output load.

CIRCUIT DIAGRAM:

<img width="620" height="300" alt="main circuit converter" src="https://github.com/user-attachments/assets/8d58fb4f-78db-474e-8a5f-4415df70f6df" />


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

PROBLEM 1:

Before connecting the 555 timer to the switching circuit(the transformer and transistor loop) i tested the switching circuit. I used an LED for output.The test approximated the frequency of square wave at the base of the transistor for which the LED glowed the brightest. I used an Arduino Nano to provide the square wave, because the frequency from a digital pin can be altered to our needs through the sketch ran by Arduino. The code is the blink sketch in examples section of arduino ide, the output pin is changed to D2 and the frequency can be changed using delay() [the time inside delay() is the time period of square wave generated] :

                                             f = 1/T (f ---> frequency, T ---> time period)

Setup to test it:

<img width="828" height="453" alt="image" src="https://github.com/user-attachments/assets/1e86504c-fc6a-44de-b887-cfac0f196fec" />


(No flyback diodes used as the application is low powered and the power required to burn the transistor is much higher than what can be provided by the 1.5v cell)

I observed that the brightness was noticable from 500Hz onwards. The testing video(1kHz):

https://github.com/user-attachments/assets/e74684e5-2cc3-40ca-9b57-63ca90ea6b40

(mild yellow glow in LED when square wave source(arduino) is powered)

The relation of frequency to resistance and capacitance of a 555 timer astable circuit is given by:

                          f = 1/3RC*ln2

                          f = 1.44/3RC 
To make the 555 timer to produce frequencies nearly 1kHz, we need to use appropriate resistors and capacitors. Since i only had 1K ohm resistors and 1 microfarad capacitors, my solutions to this problem were:

1. reduce the resistance:
   i tried reducing the resistance by using a graphite tip of a pencil to replace the resistors of astable 555 circuit, but it was more conductive than whats    needed and may burn the 555 chip

2. reduce the capacitance:
   since resistance is constant(1K ohm), for a frequency of 1KHz, as per calculations:
   
             1/C = 3R*f*ln2
   
             1/C = 3*1000*1000*ln2
   
              C = 0.48 microfarads(approx)
   
   this cappacitance can approximately be obtained by connecting two capacitors of 1 microfarad in series (0.5 microfarad equivalent capacitance)

By this way i was able to generate grequencies neary 1KHz through the 555 timer. But still the LED didnt glow, when i tried testing wheather the 555 timer was producing the square wave using a speaker(salvaged from a old toy) , it gave a beeping sound confirming that the timer was producing the necessary square wave.  


PROBLEM 2:

Initially i thought the transistor was burnt, i tried confirming by isolating the transistor, putting it in a simple led switching circuit :

<img width="303" height="166" alt="image" src="https://github.com/user-attachments/assets/e1a9b7ec-dd52-4675-b673-d87549bc73fe" />

It did work, but i noticed that the transistor was connected in a wrong way in the main circuit(flipped).

After flipping the transistor and checking if it switched, the speaker's beep confirmed that the transistor switches, by beeping when connected its terminals to the transistor's collector and positive terminal.


PROBLEM 3:

Though the transistor switching was working now, when i connected the transformer again, placed the LED accross secondary coil and powered the arduino, The LED didnt glow. Then i had an idea to get output using the speaker instead of the LED. Unlike an LED, speaker doesnt have a specific set voltage below which it doesnt work.

When connected the speaker to the secondary coil, i heard a faint beep sound from the speaker , indicating the converter worked. but the sound obtained was lesser than what is heard when directly rubbing the wires from the 1.5v battery, showing that the converter didnt boost. This can be accounted to factors like:

1. Tranformer inefficiency(loss of flux as it is air cored)

2. square wave - the square wave has di/dt very high when it transistions from high to low and low to high, but this lasts only for a very short period of time. also i suspect the the discharge time of 555 astable mode(time for which the out put is low) is half the time the charging time(time for which the output is high), which gives a 66% duty cycle unlike the arduino tests which did make the LED glow with a 50% duty cycle with 1KHz frequency


OUTPUT:

https://github.com/user-attachments/assets/f0a8b322-630b-4026-a191-c4775bfb37be

There is an audible mild beeping sound made by speaker connected to secondary coil(output).


This project is an effort to make a DC - AC boost converter, though it didnt step up propery, it proved the concept that the transformer can be driven with automatic wave generators which is a upgrade from the last project.


ADDITIONAL OBSERVATION:

I also built a core for the transformer to reduce the losses due to air core. 

<img width="1600" height="1353" alt="image" src="https://github.com/user-attachments/assets/f680dcc4-3c44-433b-9ded-725884c584d8" />

This is built by using bunch of 1cm pieces of metallic wire from a clothing hanging wire(used a magnet to verify its ferromagnetic) placed parallel to eachother an fixed with playdough. 

In the OUTPUT video, one can observe that when the core was inserted(into the transformer in background), the intensity of beep sound increases, this also demonstrated the use of a ferromagnetic core in transformers to reduce flux loss. 


THANK YOU
