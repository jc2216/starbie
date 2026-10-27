## Starbie
A tiny motion-controlled digital pet, built for HackClub Halflife because I really want a 3D printer and also because I want to get better at electronics since I am an absolute noob.
I added a buzzer so that twinkle twinkle little star plays when the sprite is napping. I also added a rain animation when the humidity is greater than a certain threshold. We'll see if that works. 

Next Steps: 
* Change up some of the animations.
* implement sound during other actions/when using the selection thing.

---
## Features
* 1 XIAO ESP-32 C3 Microcontroller
* 2 Push buttons
* 1 MPU6050 IMU
* 1 DHT11 Environment Sensor
* 1 OLED Display

This starbie has a display with a sprite. The sprite has 3 values: joy, energy, and fullness. These three values change depending on the actions it does, such as whether it is napping or playing. Additionally, there are some neat animations, like some with hearts and sparkles. 

## Process
1. Designed the Schematic. This wasn't too hard since it was just following the Starbie guide for the most part. The buttons are wired to the ESP-32 through some of the pins, and so is the OLED, MPU6050, environment sensor, and the buzzer that I added. They are also all wired to GND. 

   <img width="589" height="539" alt="Screenshot 2026-10-11 at 2 21 05 AM" src="https://github.com/user-attachments/assets/0975e67d-5d53-4338-9e3f-77da17382c48" />

2. PCB routing. This was really annoying to do since there were some cases when I did half of the routing, but the other half was impossible to do, so I had to do it all over again. I also had to redo the PCB routing when I added the buzzer, so that was really annoying, too. Some things I learned are vias, which allow you to switch between the front and back copper layer, and ground pours, which you could draw by adding a board outline. The layout was done similar to the guide, which I assume tried to minimize the rat's nest. 

   <img width="686" height="445" alt="Screenshot 2026-10-11 at 2 21 29 AM" src="https://github.com/user-attachments/assets/29db1449-9d8d-4267-9938-bcdd2f5bfb9f" />

   <img width="881" height="497" alt="Screenshot 2026-10-11 at 2 21 41 AM" src="https://github.com/user-attachments/assets/aa6cb764-304f-4fb7-a7c9-ded4167f3668" />

3. Firmware! I added sparkles like in the guide, and I also created my own sprite using Clip Studio Paint. Some new features that I have added to the firmware is a rain animation when the humidity that the Environment Sensor detects is over a certain amount and a buzzer that plays twinkle twinkle little star when the sprite is napping. I had a pitches.h file that I copy pasted from somewhere since it just contained the default values for each note, and I also had a rain_frames.h file that I got from oledanimationmaker. In my main code, I had an array containing the notes and a parallel array containing the durations that correspond to each note. 

   <img width="32" height="32" alt="sprite" src="https://github.com/user-attachments/assets/2b233861-0f77-491d-aa6b-13b382f68789" />

4. Building + Uploading Firmware. I haven't gotten to this step yet, but I am pretty sure that you connect a USB cable from the ESP-32 to your computer. Then, in the Arduino IDE, you can verify the code with the check button, and then upload it with the arrow pointing right button. As for assembling the PCB, it will probably have some soldering involved, which I don't know how to do yet because I am an absolute beginner at PCBs. 

## BOM
[BOM.csv](https://github.com/user-attachments/files/33997758/BOM.csv)

Part,	Qty,	Unit,Total,	Vendor
XIAO ESP32-C3,1,$4.99,$4.99,seeed studio
0.96 OLED,1,$2.78,$2.78,Aliexpress
MPU6050,1,$2.10,$2.10,	Aliexpress
DHT11,1,$1.05,$1.05,	Aliexpress
MX Switches,4,$0.05,$0.20,Aliexpress
Keycaps,1,$0.01,$0.01,	Aliexpress
10k Resistor,1,$0.05,$0.05,Amazon
PCB,1,$9.20,$9.20,jlcpcb
passive piezo buzzer,1,$0.64,$0.64,	aliexpress
