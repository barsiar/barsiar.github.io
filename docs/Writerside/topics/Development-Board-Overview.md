# Development Board Overview

First Version of Schematic is complete but still subject to review.

In particular I am not sure if I have interpreted the details correctly for the SKYWORKS module as I have no access to full documentation. 
Please check for any obvious errors and let me know !

The Development board is a collection of circuits which can be configured in various ways to aid code development and testing.
Many configurations are possible including connections to external hardware and development modules. The aim is to provide as much flexibility as possible in selecting parts for the final design.

Each circuit block has top level interface connections brought out to pins which must be connected to build a workable system.
Most connections are made using wire-wrap pins and so you will need a tool like this .....

<img height="300" src="MFG_WSU-30M.jpg" title="Manual Wire Wrapping Tool" width="300"/>

e.g. DIGIKEY - K105-ND   or RS COMPONENTS 605-239

Also 30AWG Solid Core wire with Kynar or Tefzel insulation.

<img height="300" src="WWWire.jpg" title="Wire Wrapping Wire Spool" width="300"/>

Available from Digikey/RS

Note that it is also possible to use DUPONT wires to make connections but not recommended as the reliability is often an issue.

Some common connections e.g. Power Supply Lines, I2C Bus and SPI Bus can be made using 2pin jumper links....

<img height="200" src="Jumper Link.jpg" title="Jumper Link" width="300"/>

All connections will be labelled on the PCB silkscreen but please refer to schematics.




