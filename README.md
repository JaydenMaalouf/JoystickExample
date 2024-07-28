# JoystickPlugin Example :joystick:

This repo is an example repository of how to make use of the [JoystickPlugin](https://github.com/JaydenMaalouf/JoystickPlugin) - written by [JaydenMaalouf](https://github.com/JaydenMaalouf)

The level and assets are from the Vehicle Template in Unreal Engine. This content is owned by Epic Games.

**NOTE:**  
This example plugin does not come with binaries included. You will need to download the latest release from [here](https://github.com/JaydenMaalouf/JoystickPlugin/releases) and copy the `Binaries/` and `Intermediate/` folders into this project.

## How it works

The example effects are located in [Content/Effects](https://github.com/JaydenMaalouf/JoystickExample/tree/main/Content/Effects)  
There are 4 effects included in the example - however, only 2 are enabled by default.

- **DampeningEffect**  
  This adds some friction to the steering axis to simulate steering stiffness.
- **RumbleEffect**  
  Static Haptic ForceFeedback Effect using the in-built controller force feedback asset.
- **SineEffect**  
  This reads a variable from the Owning Actor to determine what PhysicalMaterial surface the vehicle is currently on. If the vehicle is NOT driving on the track (material is named `NonSlippery`), then the effect will play; increasing in magnitude as the vehicle speeds up.
- **SpringEffect**
  This effect is intended to demonstrate how to centre the steering of the wheel when the vehicle accelerates. However, it does not currently work.

The Dampening and Sine effect are added to the player Pawn via the `JoystickForceFeedbackComponent`.  
This component handles creating, managing and destroying the effects for each (on `BeginPlay` by default) Joystick.

## Configuration

### Component

- **AutoInitialise**  
  Initialise the effect with the HapticDeviceManager.  
  _Required before starting an effect_
- **AutoStartOnInitialisation**  
  Start the effect immediately after initialisation.
- **OverrideEffectTick**  
  Useful for controlled the TickInterval and TickGroup of the effect.

### Effect

- **AutoInitialise**  
  Initialise the effect with the HapticDeviceManager.  
  _Required before starting an effect_
- **AutoStartOnInitialisation**  
  Start the effect immediately after initialisation.
- **AutoUpdatePostTIck**  
  Update the effect data every tick. Useful for effects that are affected by physics.
