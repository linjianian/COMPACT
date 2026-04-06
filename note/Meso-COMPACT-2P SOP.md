# System Operation Protocol

This document describes how to operate the COMPACT system after optical and mechanical alignment is completed. It focuses on hardware setup, control software, and imaging procedures.

---

## Pre-Operation Checklist

- Verify air bearing pressure is between 60 and 70 psi
- Confirm alignment has been completed according to the alignment protocol
- Ensure all required software is available on the control computers

---

## Hardware Power-On Sequence

1. Turn on the laser.
2. Turn on EOM power.
3. Confirm SLM power and verify connection to the control computer.
4. Power on the resonant scanner (12 V supply behind the setup).
5. Power on the Y galvo (left side shelf of the setup).
6. Turn on air flow for the air bearings (60–70 psi required).
7. Turn on the motor controller.
8. Turn on the PI stage controller and confirm connection to the control computer via the white cable.

---

## Hardware Connections and Configuration

### EOM Calibration
- Performed in the small setup behind ringCOMPACT.
- Place the flip mirror vertically for calibration.

### Resonant Scanner and Y Galvo
- Both require DC signal inputs.
- Resonant scanner: 1.3 V for a 310 µm scanning range.
- Y galvo: 0 V input.

### Motor Controller
- Motor software is located on the taskbar.
- Autodetect the motor.
- Open the jog window.
- Enable servo for TTL input during controller drive.
- Disable servo when manually adjusting phase.

### PI Translation Stage
- PI stage software is available on the taskbar.
- Connect the stage and enable control.
- Use software control for initial positioning.
- Use analog input for position control during imaging.
- Lock the stage position with the plate and screw on the right side when computer control is disabled.
- Ensure clearance to prevent collision with the magnetic disc.

---

## SLM Configuration

- Turn on the SLM and load the desired wavefront profile.
- Typically, one working-distance profile is used.
- For volumetric imaging:
  - Preload four wavefront profiles.
  - The SLM waits for an external trigger from the ScanSignal script to update wavefronts.

---

## Phase and Optical Component Verification

- Confirm phase alignment between the Dove prism and the GRIN lens (right-angle prism).
- Use the arrows on the magnetic coupling disc as alignment indicators.
- For GRIN lens and capillary alignment, refer to the dedicated alignment file.

---

## Imaging Preparation

1. Turn on the analog input for the resonant scanner.
   - Feedback frequency should be approximately 12 kHz.
2. The resonant scanner feedback is sent to:
   - Phase meter (for multiplied clock generation)
   - ScanImage (for synchronization)
3. Configure the phase meter:
   - Input signal around 12.035 kHz
   - Output in sync mode with a multiplier of 72
4. Enable the PI precision stage.
   - Ensure the mechanical block is engaged when the stage is not in use.
   - Position the stage so the disc is centrally located for optimal drive strength.
5. Position the animal motorized stage according to the clamps on the optical table.

---

## Motor Ramp-Up Procedure

1. Autodetect the motor in the control software.
2. Open the jog window.
3. Check phase alignment between the two discs with the servo disabled.
4. Enable the servo after phase alignment is verified.
5. Use the center computer to run the MATLAB script `rampup2`.
   - Multiplier value of 1 corresponds to a spinning rate of 20 Hz.
   - Ramp-up time should be set to 120 seconds.
   - Ramp-down time should be similar to avoid slipping.
6. Do not proceed until ramp-up is complete.

---

## Imaging Operation

- Complete any remaining alignment steps before GRIN lens rotation.
- For ScanImage:
  - Use two channels: green and red.
  - Spinning imaging trigger: PFI1
  - Large field-of-view imaging with stage translation: PFI2
  - Line number is calculated as:
    ```
    (24 kHz / spinning rate) - 26
    ```
- Control insertion depth carefully to avoid collisions or damage.
- Initially, use PI stage software for axial positioning during spinning imaging.
- After confirming the ideal axial location:
  - Use MATLAB to generate an analog waveform for PI stage translation.
  - The stage moves from the current position through the defined travel range.
- A digital output can be added to trigger SLM wavefront updates during imaging.
  - Ensure wavefront files are loaded in advance by running the appropriate MATLAB script.

---

## Shutdown Procedure

1. After imaging is complete:
   - Command the PI stage to output all-zero control signals.
2. Gradually slow down the motor via software.
3. Turn off the resonant scanner.
4. Lower the animal stage before removing the animal.
5. Ensure all hardware is under control and collision-free throughout shutdown.

---

## Notes

- This document assumes all alignment steps are completed beforehand.
- Refer to separate alignment documentation for optical and mechanical calibration procedures.
