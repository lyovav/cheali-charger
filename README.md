Welcome to cheali-charger!

This project is an alternative firmware for the G.T. POWER A6-10 200W Lipo charger.

Don't use it if You don't need to!
(not everything is implemented yet).  
This is a early version so be very careful.
Use it only if You can not calibrate your
charger with the original firmware.

Any feedback is very welcome!  
https://github.com/stawel/cheali-charger

Features
--------
- Li-ion, LiPo and LiFe:
  - charging
  - fast charging
  - charging + balancing at the same time (not implemented yet)
  - discharging 
  - balancing
  - storage
  - storage + balancing
- Ni-Cd and NiMH - not well tested!
  - charging, method: -dV/dT
  - discharging 
  - cycling (not implemented yet)
- Pb (not implemented yet)
- Internal resistance display
  - single cell resistance
  - whole battery resistance
  - battery leads resistance
- Internal and external temperature monitoring
- Overcharge and overdischarge monitoring
- Input voltage monitoring
- Memory for 32 batteries 
- CALIBATION!


WARNING
-------
Please CALIBRATE the charger before use!
Always use the external temperature probe!  
(if You like your house ;) )


Hardware
--------
- G.T. POWER A6-10 200W (http://www.hobbyking.com/hobbyking/store/__7386__GT_A_6_10_200W_Balance_charger_discharger.html)
- IMAX B6 Charger/Discharger 1-6 Cells (comming soon)
- .... - any suggestions are very welcome


Building from Source
--------------------
dependencies: cmake, avrdude, avr-libc, gcc-avr

<pre>
user@~$ sudo apt-get install cmake avrdude avr-libc gcc-avr git

user@~$ git clone https://github.com/stawel/cheali-charger.git
user@~$ cd cheali-charger

user@~/cheali-charger$ ./bootstrap
user@~/cheali-charger$ make

flashing with USBasp:
 
user@~/cheali-charger$ cd src/hardware/GTPowerA6-10
edit file: progUSBasp.sh, replace "TTY=/dev/ttyUSB0" to match your configuration.
user@~/cheali-charger/src/hardware/GTPowerA6-10$ ./progUSBasp.sh
</pre>
 
Now You should see a "ChealiCharger welcome" screen.

Done.

Flashing: G.T. POWER A6-10 200W
-------------------------------

- Connect a standard AVR ISP 10-pin cable to the board: https://github.com/stawel/cheali-charger/blob/master/docs/GTPowerA6-10/front.jpg
- set "Device" to: atmega32
- use the cheali-charger/hex/cheali-charger-0.10.hex file as "Flash"



Calibration
-----------
Connect a NOT fully charged LiPo battery to the main leads
and the balance port.

go to: "options"->"calibrate":
- balance port calibration: go to "B0-2", "B3-5"  
   - use a voltmeter to measure the voltage of all cells  
     and set the values in the appropriate fields.  
- output voltage calibration: go to "B0-5 to Vout"  
   - press the "start" button for a few seconds  
     (this will copy the voltage from the balance port)
- charge current calibration: go to "Icharge"  
  connect your amperemeter in series with the battery  
  - go to: "50mA"  
    press "Inc", "Dec" buttons until the amperemeter shows 50mA  
    press "start" button for a few seconds  
  - go to: "1000mA"  
    press "Inc", "Dec" buttons until the amperemeter shows 1000mA  
    press "start" button for a few seconds  
    WARNING: the battery will be charged with high current!  
- discharge current calibration: go to "Idischarge"  
    Repeat the same steps as before  
    WARNING: the battery will be discharged with high current!  

Done.



Have fun! 



