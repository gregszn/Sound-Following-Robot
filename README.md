# Sound-Following Robotic Car

## Overview

A sound-following robotic car developed as the final project for EEC 10 at the University of California, Davis (Winter 2025).

The robot uses two microphones to detect sound, processes the incoming audio signals through an MSP432 microcontroller, and controls two DC motors to navigate toward the detected sound source.

This project combines embedded C programming, digital signal processing, analog electronics, and hardware debugging.

## Technologies & Tools

- **Microcontroller:** Texas Instruments MSP432
- **Programming Language:** Embedded C
- **Development Environment:** Code Composer Studio
- **Hardware:** Dual microphones, PCB, DC motors
- **Signal Processing:** ADC, high-pass and low-pass digital filters
- **Motor Control:** PWM and GPIO
- **Testing:** Digital multimeter, oscilloscope, continuity and voltage measurements

## System Architecture

The robot follows a signal-processing and motor-control pipeline:

1. **Audio Detection:** Two microphones capture incoming sound signals.
2. **Analog-to-Digital Conversion:** The MSP432 samples the microphone inputs using its ADC.
3. **Digital Filtering:** High-pass and low-pass filters process the sampled signals.
4. **Signal Comparison:** The program calculates average peak values from each microphone.
5. **Direction Selection:** The controller determines the robot's next movement based on the processed signals.
6. **Motor Control:** PWM and GPIO signals control the robot's two motors.

## Key Features

- Dual-microphone sound detection
- Digital high-pass and low-pass filtering
- Average peak amplitude comparison for sound localization
- PWM-based DC motor control
- Forward, backward, left, right, and stop functions
- Alternating sampling and running modes

## Technical Implementation

### Audio Sampling and Processing

The MSP432 collects microphone signals through two ADC channels.

The program processes blocks of 1,000 samples and applies digital high-pass and low-pass filters to reduce unwanted frequency components.

Each processed signal is divided into ten groups of 100 samples. The maximum value from each group is identified, and the ten peak values are averaged to estimate the relative sound intensity at each microphone.

### Direction Control

The controller compares the processed microphone signals to determine the robot's movement.

- **Left:** Turn toward the left sound source.
- **Right:** Turn toward the right sound source.
- **Forward:** Move forward when microphone readings are sufficiently similar.
- **Stop:** Stop when the sound detection condition is not satisfied.

The motors are controlled through GPIO direction signals and PWM outputs.

### Hardware Integration

The project required soldering components onto a PCB and verifying the functionality of multiple circuit sections, including microphone inputs, amplifier stages, and filters.

Continuity and voltage measurements were used to troubleshoot electrical connections and verify circuit operation.

## Challenges and Troubleshooting

One of the main challenges was achieving consistent sound-following behavior.

During testing, the robot occasionally moved in unintended directions instead of approaching the sound source.

To investigate this behavior, we experimented with different software parameters and tested multiple types of audio inputs, including different sounds and music.

These experiments helped us better understand how the robot's movement depended on microphone readings, signal processing, and the characteristics of the sound source.

The project also required troubleshooting PCB connections and soldering quality to ensure reliable hardware operation.

## Results

The completed robot demonstrated the ability to detect sound using two microphones and control its movement based on the processed signals.

The project provided practical experience integrating analog circuitry, digital signal processing, embedded software, and motor control into a functional robotic system.

## Future Improvements

- Improve sound detection reliability under varying noise conditions.
- Refine direction-selection thresholds and filtering parameters.
- Optimize the sampling and motor-control routines.
- Improve PCB soldering quality and hardware reliability.
- Evaluate performance using repeatable sound-source tests.

## Contributors

- Gregory Ceron
- Rebeka Hang

**Course:** EEC 10 — University of California, Davis

**Completed:** March 2025
