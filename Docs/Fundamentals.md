# Fundamentals

--- 

#### Configurations

Explaining configurations sounds like a major pain in the ass, so I'm gonna have this guy explain it to you:

[FTC Programming Tutorial (Episode 4: Configuring and Telemetry)](https://www.youtube.com/watch?v=22ZIoU6r0LI)

Watch the first two minutes.

#### Dashboard

1. Open up your Android Studio project. On the sidebar, scroll down to Gradle Scripts. Navigate to build.dependencies.gradle:
   
   **Gradle Scripts > build.dependencies.gradle**. 

2. Scroll through the file and ensure that there's a line like
   
   **implementation 'com.bylazar:fullpanels:1.0.12'**
   
   You can update it to the most recent version, which can be found in the Panels documentation.

3. Connect to the CHub (short for control hub) and push your code to it. Now your dashboard should be installed.

4. To access the dashboard, connect to your CHub and open '[192.168.43.1:8001](http://192.168.43.1:8001/)' in your browser. This is a very important feature for optimizing your programming, as it allows you to modify variables without re-pushing code to the robot, and as such, I highly recommend you bookmark this tab for easy access.

#### HardwareMap

The hardwareMap is the Object that we use to tell the CHub to relate code to hardware. Basically, you assign a piece of hardware a name in the configuration, which corresponds to the port that its hooked up to. You then use this assigned name to link a Object to the hardware. For example:

```java
private final DcMotorEx leftFront, leftBack, rightBack, rightFront;

public MecanumDrive(HardwareMap hardwareMap){
    leftFront = hardwareMap.get(DcMotorEx.class, "leftFront");
    leftBack = hardwareMap.get(DcMotorEx.class, "leftRear");
    rightBack = hardwareMap.get(DcMotorEx.class, "rightRear");
    rightFront = hardwareMap.get(DcMotorEx.class, "rightFront");
}
```

This fragment of code from the MecanumDrive subsystem declares and substantiates the drive motors for the drivetrain. Keep in mind, the hardware should be declared as the proper class, which, in this case, is DcMotorEx. The same class should be passed to the hardwareMap.get() method as the first argument, and the configured name should be passed as a String to the second argument. Also, the name of the Object in code does not have to be the same as the configured name.

#### Motors

A motor is a very high-power, high-speed component. You will only be given 8 motor slots, 4 of which will most likely be used on the drivetrain, so make sure a motor is absolutely necessary for whatever you're using it for.

- Most Used Methods
  
  - setZeroPowerBehavior() - tells the motor what to do when supplied with no power.
  
  - setMode() - tells the motor how to move, use RUN_WITHOUT_ENCODER when  running with power, RUN_WITH_ENCODER when using PID, and RUN_TO_POSITION when using an encoder to get to a specific position. 
  
  - setPower() - sets the motor to run at a specific power level from 0-1, has varying speeds.
  
  - setVelocity() - sets the motor to run at a specific speed, based on encoders.

(More on encoders later, but basically it requires another cable going from the motor)

More methods here: [DcMotorEx](https://ftctechnh.github.io/ftc_app/doc/javadoc/index.html).

#### Servos

A servo serves a similar function as a motor, acting as a device for applying torque, but it typically runs in a mode with a constrained range of motion, which can be swapped to continuous rotation mode. It's a lot weaker and slower than a motor, but is more power and space efficient. 

- Most Important Method
  
  - setPosition() - sets the position to a position from 0-1. Might wanna check the range of motion on the servo first.

#### IMU

The IMU, short for inertial measurement unit, is an internal device within the control hub, as well as a part of the Pinpoint computer that you might be using for auto. It allows you to know where the robot physically is relative to the starting position (as long as it doesn't get hit).

#### Telemetry
