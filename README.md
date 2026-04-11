# ATN-avionic-telemetry-system

* This project is divided into 2 parts! The main PCB and the other Avionic Bay Holder


## THE PCB PART!:


* Atn is a Flight computer which uses TVC(thrust vector control) to stabilze the rocket from its trajectory change.
* This also helps in trajectory control which is used for gravity turn or zero lift turn using the escape velocity --> 11.2 km/s
  
So we will be talking about different steps for making this!

I've used quite a few components here for this project, which are:

* STM32(F7 series)
* ICM 42688
* BMP390
* LoRa sx1278
* Antenna

So there are the main components used here, i didnt mention a few as they are not important which are usually the CP2102 and more stuffs!
- for the servo controlls i just added another usb connector which is connected to the power bank, this is because you cant supply power from the power bank which is used to supply power to the MCU because servos draw alot of power and it could damage the board! the thing is that i really dont wanna include a bug converter on the pcb for the LIPO connection... so i just used the normal Power Bank Supply!
- Ive made 8 versions of this pcb each with alot of changes! the primary one used a esp32 and a magnetometer which is not that god for ideal model rocketry.

* the Main PCB drawing software ive used is Easyeda! The screenshots of the schematic and PCB are linked below! 

### Main Schematic:

<img width="1163" height="710" alt="Screenshot 2026-04-11 195243" src="https://github.com/user-attachments/assets/d14fbba7-44b2-414f-93a6-6122b326e6a2" />

### The Main PCB routed:

<img width="872" height="483" alt="Screenshot 2026-04-04 195052" src="https://github.com/user-attachments/assets/24c784b8-78dd-455b-8c61-33a81ab57377" />


## The AVIONIC BAY:

- The avionic Bay is just a holder for the ATN but, specially designed to fit for a rocket I've been making!
- This Bay has 2 parts, the pad and the holder cup!

### The pad:

  - Its basically the supporting pad for the pcb, so that it wont break easily! all the pressure exerted on the PCB would be transfered(recieved) to this part! This part        has the screws to hold it down and fits perfectly in the holder cup

<img width="1919" height="1079" alt="Screenshot 2026-03-09 190935" src="https://github.com/user-attachments/assets/9ffa93ee-15a1-484e-beff-cd631cc3cd50" />

### The Holder Cup:

  - This part holds down the PCB inside it, with pathway for the wire connections, the TVC done beneath this part!

    <img width="1411" height="1010" alt="Screenshot 2026-03-09 190924" src="https://github.com/user-attachments/assets/6bb721a9-087d-426c-a7dc-214cf7a01e51" />

