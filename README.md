# tracker4R101

A simple mobile device tracker based on Python, MQTT and QGIS.
==============================================================

The motivation is to have a simple way to be tracked while running, walking or trekking. In my case, I'm going to run (well, I think I should say *walk*) the ultratrail
101 Km of Ronda in Malaga, South Spain. I want to have some way to be tracked from home (just recording the track
is not a problem with nice pieces of software like ORUX MAPS) and this is a simple, yet functional proof of concept.
USE IT AT YOUR OWN RISK, AS IT IS A EXPERIMENTAL AND EDUCATIONAL SOFTWARE NOT INTENDED FOR ANY SAFETY/EMERGENCY APPLICATION

La motivación es tener una manera sencilla de ser seguido desde casa mientras se corre, pasea o hace senderismo.
En mi caso, voy a correr (bueno, yo diría *andar*) la prueba de ultratrail 101 Km de Ronda. Me interesa tener un medio para 
poder ser seguido desde casa y esta es una prueba de concepto simple aunque funcional.
ESTE ES UN SOFTWARE EXPERIMENTAL Y EDUCACIONAL, SIN INTENCIÓN DE SER USADO PARA NINGUNA APLICACIÓN DE SEGURIDAD/EMERGENCIA. ÚSALO BAJO TU PROPIA RESPONSABILIDAD


LICENSE
=======
This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or
distribute this software, either in source code form or as a compiled
binary, for any purpose, commercial or non-commercial, and by any
means.

In jurisdictions that recognize copyright laws, the author or authors
of this software dedicate any and all copyright interest in the
software to the public domain. We make this dedication for the benefit
of the public at large and to the detriment of our heirs and
successors. We intend this dedication to be an overt act of
relinquishment in perpetuity of all present and future rights to this
software under copyright law.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR
OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

For more information, please refer to <http://unlicense.org/>

Requisites and dependences
==========================
To be able to track, you need:

1) Account in a MQTT broker site like cloudMQTT
2) QPython installed in your mobile devie (MUST BE ANDROID), as well as paho-mqtt module
3) Python 2.7, paho-mqtt and QGIS installed in your system

Small How-to
============

First you must modify the script according to your server, port, etc. configuration
Then run the DEVICE.py script in your cell phone. I suggest you to use QPython QRCode service to get the code in:

http://qpython.com/#qrcode

Yo can do it by copy-pasting the code. I suggest you to remove the license information, generate the QRCode with ECC set to L and Size to 10 and open the resulting QRCode in a new browser tab to be able to scan it with the phone

On tracker side, you must run TRACKER.py script to get the data from the mqtt broker.
The script saves the received data to a file called tracking.csv. You could create a file before with a suitable
header. Now the fields are:
mobile_id;point_id;lat;lon

To show the tracked points over a map, just load the file tracking.csv
as a CSV layer in QGIS enabling file whatching, so everytime a new point is appended by TRACKER.py it is shown on the map.

If you want to track many runners/vehicles at the same time, in priciple it should be as easy as running the
DEVICE.py script in each of the devices, ensuring they have properly set the mobile_id variable to something meaningful
(of course, the mobile_id MUST be different to make sense) and then set layer style in QGIS to categorized, categorizing by joining mobile_id and last field.

TODO:
=====
A lot, and for instance
- Because all data tranmsission will be through GSM connections, and because high chances of 
  running into no coverage zones, store-and-send procedures for positions.
- Convert the track points to line automagically
  



