# Design of an elevator using CODESYS - Control System Technologies

Project of the course "Control System Technologies", Alma Mater Studiorum UniBO (Spring 2020). Design of an elevator using PLC programming on CODESYS, using both SFC and ST languages.

<p align="center">
  <img src="https://user-images.githubusercontent.com/64502909/140430440-6710bbed-7c59-4eb3-8a2b-84fc8c641798.png">
</p>

#

The whole implementation is mostly based on the frequent use of steps, transitions, synchronizations, parallelisms and IF instructions, which are the basic elements of the SFC and ST languages.

First of all, the design is based on the *Generalized Actuator* approach, which uses Function Blocks to guarantee modularity and reusability and to organize the control program in a readable way. This approach also relies on the definition of a *Policy*, the code that defines the sequence of actions of the mechanism. The Policy first sends an event to trigger the GA, and then the GA executes the action. Later on, a GA sends an acknowledge to communicate to the Policy that the action is completed.

<p align="center">
  <img src="https://user-images.githubusercontent.com/64502909/140430707-76bb5acc-cbcb-4b72-b0fe-fe60c7aadb39.JPG">
</p>

The variables used to control the elevator are divided into **input variables**, both sensors and HMI variables, and **output variables**, the actuators. In total, there are 7 sensors and 5 actuators, and to control the overall system it was enough to use 3 GAs in total.

Each GA has a specific task to fulfill. Generally speaking, the **Door GA** manages the opening and the closing of the door, the **Motor GA** regulates the upward and downward movement of the cab, while the **Led GA** manages instead the LED graphical interface (when a button is pushed the corresponding LED has to turn on) and the ordering sequence of the calls.
