# DC-to-AC-Boost-Converter
DESCRIPTION:

This can be considered as a continuation/addition to the previous project of building a step up transformer. In this project, instead of rubbing the wires to create varying voltage accross primary coil of transformer(and hence generating varying magnetic flux), A 555 timer in astable mode is used to generate a high frequency square wave signal which is fed into a switching transistor(used transistor instead of MOSFET as this transformer is used in low voltage applications here) which is connected similar to a switch to the main primary coil and battery circuit loop. This setup applies time varying potential difference accross transformer primary coil
and hence creating a induced emf in secondary coil which is used to power the output load.
