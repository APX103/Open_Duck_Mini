> Not finalized yet

# Training policies that transfer to the real robot (sim2real)

We want to train policies that transfer well to the real robot. This is the sim2real problem. It's a hard problem, especially for us since we are using cheap servomotors that are hard to model and not overly powerful. 

Below, I'll roughly explain the steps we went through to get there, but you won't have to do everything again yourself since we provide the results of each process.

## Make an accurate model of the robot (URDF/MJCF)

### Robot structure

In the [Onhape document](https://cad.onshape.com/documents/64074dfcfa379b37d8a47762/w/3650ab4221e215a4f65eb7fe/e/0505c262d882183a25049d05), we specify the material of each part. But to be more accurate, because we print with infill we override the mass of the parts with the (pretty accurate) estimation of the slicer. 

We use [onshape-to-robot](https://github.com/Rhoban/onshape-to-robot) to export URDF/MJCF descriptions. For MJX, we have to make a lightweight model, see our [config.json](https://github.com/apirrone/Open_Duck_Playground/blob/main/playground/open_duck_mini_v2/xmls/config.json). 

This gives us a MJCF (Mujoco format) [description of the robot](https://github.com/apirrone/Open_Duck_Playground/blob/main/playground/open_duck_mini_v2/xmls/open_duck_mini_v2.xml) which describes the masses and moments of inertia of the full robot. 

### Motors

Another very important part of having an accurate model is modeling the motors's behavior. We use [BAM](https://github.com/Rhoban/bam/) for that. You don't have to go through the identification process yourself, we provide the results [here](https://github.com/Rhoban/bam/tree/main/params/feetech_sts3215_7_4V)

It's critical that the simulator simulates the motors accurately, because we will train a policy (a neural network) to output motor positions based on sensory inputs (motors positions/speeds, imu and feet sensors). If the motors behave differently in the simulation than in the real world, the policy won't work, or at worst, produce chaotic movements.

`BAM` allows us to export the main identified parameters to mujoco units (using `bam.to_mujoco`). These values are the ones we set in out mjcf model for the actuators and joints properties. 

- damping
- kp
- frictionloss
- armature
- forcerange

## Training policies 

We use our own [mujoco playground](https://github.com/google-deepmind/mujoco_playground) based framework, [Open Duck Playground](https://github.com/apirrone/Open_Duck_Playground)

In the [joystick](https://github.com/apirrone/Open_Duck_Playground/blob/main/playground/open_duck_mini_v2/joystick.py) env, you can try to enable/disable different rewards, write your own, play with the weights, noise, randomization etc. 

We obtained good results by implementing the imitation reward described by Disney in their [BDX paper](https://github.com/apirrone/Open_Duck_Playground/blob/main/playground/open_duck_mini_v2/joystick.py). 

To use this reward, we need reference motion. We made [this repo](https://github.com/apirrone/Open_Duck_reference_motion_generator) to generate such motion using a parametric walk engine. Following the instructions there, you can generate a `polynomial_coefficients.pkl` file which contains the reference motions. There is already such a file in the playground repo under the `data/` directory. 

Once your policy is trained, you can try to run it on the real robot using [this script](https://github.com/apirrone/Open_Duck_Mini_Runtime/blob/v2/scripts/v2_rl_walk_mujoco.py) in the runtime repo. Make sure you completed all the steps in the [checklist](https://github.com/apirrone/Open_Duck_Mini_Runtime/blob/v2/checklist.md) before running this.


