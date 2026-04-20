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

# PID CONTROLLER CODE:

*This code is done in simulink and converted into C and C++ for stm32.
## Explaination:
* So matlab is basically a programming software used for simulations! it uses math and physics primarly and uses fortran! A Advantage of matlab is that it has something called simulink! which basically uses blocks for all those linear equations!.
* Lets get into our code, first we get a desired angle which is 0 degrees! its because we want our rocket to be straight not to be slanted, when its slanted it usually goes down and crashes! so we use desired angle as 0, now we use a simple logic! so find a error angle which is basically the angle which is away from normal line (0 degress) for this we use the formula ( Desired angle -  mesured angle =  error angle) this error angle is put into the PID which is Propotion, integral and derivative! I cant explain their functions but we do all these functions with our error angle and then sum it! we use a gain value which is basically Kp, Ki and Kd! and then the output is summed! this summed output is a corrected angle but! it should be less than 15 degrees! this is because if its more than 15.. it will make your rocket turn more! so yeah we limit this angle and then we use vector resolution!
* With vector resolution we divide this thrust into 2 components! which are Vertical (Tsin) and Horizontal (Tcos) the thetha is same and the T is also same, now we are supposed to plug this values into our 2 servos! which one moves in X axis and other moves in Z axis!, But we need to simulation it (i.e.) getting the output on a virtuall rocket! for this we plug those values into 3DOF ( 3 degree of freedom) which takes all the values/data of a rocket and convert those input thrust into other many required stuffs like angle, angular momentum, pos and -etc! now that we have Fx and Fz we need moment arm!
* [ Moment arm =  T .  Sin(thetha) . L ] 
*  Now we can get our angle! which is basically the position of our virtual rocket! and then we feed it into our mesured angle once again! and again and again till the step time runs out!
* this output is also feeded into scope which is basically a graph!
* So we just finished our PID Controll and ive made some changes from the diagram im pasting here and ive got a really good output! so here ya go!

## Photos:

### PID FORMULA:

<img width="600" height="79" alt="image" src="https://github.com/user-attachments/assets/8a62cc5c-af21-4c2d-8c88-5cee925fadc5" />


### Main Diagram Simulink:

<img width="1508" height="699" alt="image" src="https://github.com/user-attachments/assets/fec32cb9-fdcd-454d-841d-ad697ea8841e" />



### Output: 

<img width="681" height="525" alt="Screenshot 2026-04-21 001327" src="https://github.com/user-attachments/assets/9a96629b-f9d4-448c-ba44-c544eb541e86" />
* the output will not be same as the diagram given as ive made some changes!
