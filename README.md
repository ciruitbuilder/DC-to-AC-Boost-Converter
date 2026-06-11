# DC-to-AC-Boost-Converter
DESCRIPTION:

This can be considered as a continuation/addition to the previous project of building a step up transformer. In this project, instead of rubbing the wires to create varying voltage accross primary coil of transformer(and hence generating varying magnetic flux), A 555 timer in astable mode is used to generate a high frequency square wave signal which is fed into a switching transistor(used transistor instead of MOSFET as this transformer is used in low voltage applications here) which is connected similar to a switch to the main primary coil and battery circuit loop. This setup applies time varying potential difference accross transformer primary coil
and hence creating a induced emf in secondary coil which is used to power the output load.

CIRCUIT DIAGRAM:

<img width="581" height="415" alt="image" src="https://github.com/user-attachments/assets/09fa6208-bca4-4e86-98d2-332fea959932" />

The 1.5v cell is connected to the input + and input -. To power the square wave generating 555 timer circuit, an arduino is used in this case. 

FINISHED IMAGE:

