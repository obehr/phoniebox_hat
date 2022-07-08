# phoniebox_hat
Raspberry Pi HAT for [RPi-Jukebox-RFID](https://github.com/MiczFlor/RPi-Jukebox-RFID)

In 2021 I built a Raspberry PI based Jukebox with RFID reader (see [here](https://github.com/MiczFlor/RPi-Jukebox-RFID/discussions/1331#discussioncomment-433065)). I used a breadboard for buttons and LEDs, USB sound card, ground loop isolator, PAM8403 amplifier.

This is a Raspberry Pi HAT for the 40W GPIO header. It integrates all of those functions on a single custom PCB:
 - DAC (pcm5102a)
 - Amplifier (PAM8406)
 - LED open drain buffers
 - Switch inputs with hardware debounce
 - Screw clamps for connecting button and LEDs
 - Pin headers for RFID-RC522 and Pimoroni [OnOff SHIM](https://shop.pimoroni.com/products/onoff-shim)

The PCB is larger than the PI board itself. In this point it fails the official HAT [specification](https://github.com/raspberrypi/hats). Schematic and layout are done in KiCad 6.0.
