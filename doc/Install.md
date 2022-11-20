
# Software installation

## OS

Tested with Raspberry Pi OS Lite

## Jukebox

Install RPi-Jukebox-RFID from https://github.com/MiczFlor/RPi-Jukebox-RFID/

The RC522 reader uses SPI0 and the default pin configuration. To configure, run ./run_register_reader.py in src/jukebox and submit the following inputs:

	Reader module number? -> 2 (MFRC522 via SPI)
	Install Python dependencies? -> y
	Auto-configure system settings? -> y
	SPI CEx (CE0=GPIO08, CE1=GPIO7)? -> 0
	IRQ GPIO pin (BCM numbering)? -> 24
	Reset GPIO pin (BCM numbering)? -> 25
	4-byte only legacy mode? -> n
	Do you want to add another RFID reader? -> n
	


## Battery disconnect circuit

The battery disconnect circuit is compatible with OnOffSHIM. Just run 
	
	curl https://get.pimoroni.com/onoffshim | bash

## Sound card
	
The sound card is compatible with HifiBerry MiniAmp. 

Remove the line

	dtparam=audio=on

from /boot/config.txt if it exists.

If your system uses the vc4-fkms-v3d overlay, make sure, audio is also disabled on this:

	dtoverlay=vc4-fkms-v3d,audio=off

Edit /boot/config.txt and add the following line:

	dtoverlay=hifiberry-dac

Edit or create /etc/asound.conf:

	pcm.hifiberry {
			  type softvol
			  slave.pcm "plughw:0"
			  control.name "Master"
			  control.card 0
	  } 
	pcm.!default {
			  type plug
			  slave.pcm "hifiberry"
	  }