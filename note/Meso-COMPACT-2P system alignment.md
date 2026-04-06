# System Alignment Protocol

## Overview

This protocol describes the alignment of optical, rotation, and mechanical axes for a rotating two‑photon imaging system. The alignment proceeds from defining the optical axis to aligning rotating components, the imaging probe, translation stages, and the animal motion system.

**Key axes to be aligned:**
- Optical axis  
- Rotation axis  
- Mechanical axis of each element  

---

## Optical Path Alignment

### SLM and Beam Conditioning

The laser is first incident on the spatial light modulator (SLM), which updates the wavefront for defocus control and corrects on‑axis aberrations.

- Beam diameter: **8.25 mm**
- Purpose:
  - Fully utilize the SLM aperture
  - Employ sufficient pixels for wavefront manipulation

A relay system reduces the beam size to match the resonant scanner aperture.

### Scanner and Relay Optics

- A single‑axis galvo mirror provides static beam tilt.
- A 1:2 relay system matches the pupil size of the objective lens.
- The resulting numerical aperture is approximately **0.4**, suitable for two‑photon imaging.

A Dove prism is used to rotate the scanning axis of the resonant scanner to match the rotation angle of the imaging probe.

---

## Air Bearing 1 Alignment (Rotation Axis to Optical Axis)

### Rotation Axis Alignment

An air bearing is used to provide rotational motion. Its rotation axis must coincide with the optical axis.

**Procedure:**
1. Mount a mirror on the air bearing to retroreflect the incoming beam.
2. Rotate the air bearing while adjusting the mirror tip‑tilt.
3. Stop when the reflected beam remains stationary during rotation.
4. Adjust the tip‑tilt of the air bearing mechanical housing.

**Principle:**
- The observed beam motion corresponds to twice the angular misalignment between the rotation axis and the optical axis.

### Lateral Position Alignment

After rotational alignment, the lateral positions of the axes are aligned.

**Procedure:**
1. Place a pinhole at the center of the rotation axis.
2. Verify the pinhole position by rotating the air bearing:
   - The pinhole should remain stationary.
3. Adjust the lateral position of the air bearing until the pinhole is centered on the optical axis.

Tip‑tilt and lateral adjustments are implemented via screws in the air bearing housing.

---

## Dove Prism Mounting and Alignment

The Dove prism is mounted on the air bearing. The on‑axis beam leaving the prism must remain colinear with the original optical axis.

**Observations:**
- Near‑field beam displacement indicates lateral positioning error.
- Far‑field beam displacement indicates angular (tilt) error.

**Procedure:**
- Iteratively adjust lateral position and tilt of the Dove prism.
- Continue until the beam remains stationary in both near and far field during rotation.

---

## Imaging Probe Alignment

### Translation Stage Alignment

The imaging probe must be aligned with the travel axis of a precision translation stage.

**Procedure:**
1. Place a camera on the translation stage.
2. Move the stage over its full travel range.
3. Observe beam position on the camera.

**Criterion:**
- If the travel axis coincides with the optical axis, the beam position remains constant during motion.

### Alignment to Air Bearing 2

The imaging probe is aligned to the rotation axis of a second air bearing.

**Procedure:**
1. Rotate the imaging probe.
2. Record its position using two orthogonally placed imaging systems.
3. Identify the rotation axis by averaging the observed positions.
4. Adjust lateral position and tip‑tilt using fine adjustment screws.

**Result:**
- Runout of the imaging probe is reduced to within several microns over its full length.

---

## Alignment of Probe Axis and Travel Axis

After aligning the mechanical and rotation axes of the imaging probe, the probe axis must coincide with the translation stage travel axis.

**Procedure:**
1. Track the lateral position of the imaging probe during long‑range stage motion.
2. Analyze lateral deviation as a function of travel.
3. Adjust the mounting interface between the air bearing and the translation stage.

If the axes coincide, the lateral probe position remains unchanged throughout travel.

---

## Objective Lens Alignment

The objective lens is mounted on the same housing using a Thorlabs XYZ translation mount.

**Procedure:**
- Adjust the objective lens position in X, Y, and Z.
- Align the optical axis of the objective to the system optical axis.

---

## Animal Translation Stage Alignment

A precision three‑axis stage capable of group motion is used to move animals.

**Procedure:**
1. Attach a glass rod to the three‑axis stage.
2. Observe the rod using two orthogonal cameras.
3. Adjust the rod orientation to match the reference axis.
4. Move the stage vertically.
5. Tune group‑move coefficients until lateral displacement remains within tolerance.

---

## Notes

- This document can serve as:
  1. A methods reference
  2. A setup description for results
  3. A finalized alignment protocol after proofreading
