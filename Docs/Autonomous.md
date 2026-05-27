# Auto

---

At this point of the process, you should already have a fleshed out supersystem, and at least a (semi-)functional Teleop. Furthermore, I'll be explaining how to do an Auto given a pinpoint computer with 2 odometry wheels, as that is what I'm familiar with and will also be the most accurate and convenient way for you as well. 

#### Tuning

Now this is probably gonna be the longest part of the process, but it is absolutely crucial that you get this right. The people at PedroPathing have already set up a teleop that streamlines this process. Navigate to the [Tuning](https://pedropathing.com/docs/pathing/tuning) page on the PedroPathing docs. You should see a sidebar that contains all the steps for tuning. 

Go through these from top to bottom, making sure to thoroughly understand what's on these pages and follow the instructions as they'll fully guide you through the tuning process. Throughout the tuning process, the tuner will either give you a number, or you'll need to manually tune a PID controller. These numbers all need to be recorded and put into the Constants.java file as the docs say. If you're confused about where certain constants go, refer to the '25-'26 docs on the resources page. Also, as my version of Pedro may be outdated by the time you're working on this, there may be new or removed constants.  

#### Pathing

The pathing system can be rather hard to understand starting off. The easiest way for you to make use of it and begin to understand it is to use the [PedroPathing Visualizer](https://visualizer.pedropathing.com/). Essentially, it allows you to draw up a virtual path on a map of the field and then port that path into java, allowing for a direct copy paste into your code. I hope you can use this without too much explanation as this is the easiest, most comprehensive feature to use. It also creates the Paths class, containing the paths you've constructed, a setPathState() method, and an autonomousPathUpdate() method.

Now, to actually utilize the path that you've constructed in the visualizer and intertwine it with your own supersystem code, you're gonna add to the autonomousPathUpdate() method in the Paths class (which should've been created along with your paths if you used the visualizer correctly). 

```java
public void autonomousPathUpdate() {
        switch (pathState){
            case 0:
                follower.followPath(paths.toShoot);
                setPathState(1);
                break;
            case 1:
//                if(!follower.isBusy() && pathTimer.getElapsedTimeSeconds() > 0.5) {
//                    superSystem.shoot();
//                    setPathState(2);
//                }
                setPathState(2);
                break;
            case 2:
//                if(superSystem.isEmpty() && pathTimer.getElapsedTimeSeconds() > 0.25){
                if(!follower.isBusy() && pathTimer.getElapsedTimeSeconds() > 0.25){
                    follower.followPath(paths.toPickup);
                    setPathState(3);
                }
                break;
            case 3:
                if(!follower.isBusy()){
                    follower.followPath(paths.toShoot2);
                    setPathState(-1);
                }
                break;
        }
} 
```

This is where all the other action besides the driving goes, as you can't use outside methods within the path builder. In the example above, Auto is split into stages, each with a corresponding path or action. The setPathState() method will allow you to switch between stages. You'll most likely want to use some getter methods from the follower or other conditions so that you don't start acting while the robot's still zipping around the field. 
