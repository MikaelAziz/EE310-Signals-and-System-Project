# Acoustic Echo Cancellation (AEC) Project
**Names (ID):** Muhammad Sabeer Asad (27100179), Mirza Sarim Ahmed Beg (27100244) and Mikael Aziz (26100014)

## Overview 
This repository contains a Python implementation of an **Acoustic Echo Canceller (AEC)**. The system is designed to identify and remove acoustic echo from a microphone signal using the **Normalized Least Mean Squares (NLMS)** algorithm, integrated with a **Geigel Double-Talk Detector (DTD)**.### Adaptive Signal Processing with NLMS & Geigel DTD. This is the capstone project for the course EE310: Signals and Systems.

Do note that this read me file doesn't contain details of the algorithm that have been covered in the project report or jupyter notebook.

## Quick Start
Ensure you have the following packages installed:

pip install numpy sounddevice soundfile matplotlib scipy

## Project Structure
Our code can be divided into two main sections:
* **Synthetic Signal**: This section of the code is there to ensure that our `nlms` and `nlms_geigel` functions are performing as expected along with the relevant performance metrics (i.e. ERLE and Misalignment)
* **Live Signal**: Using the `mamdani.wav` we first did an "offline run" in which the prerecorded audio file with near and far-end speech was used followed by the "Live Echo Cancellation Setup" with the same .wav file.

## Usage 
The synthetic signal section can be run as is. For the live signal section, first the microphone must be setup correctly. The `print(sd.query_devices())` command was used to find the index of the microphone as following: 
![1](io_output.jpeg)
Since the index 1 corresponded with our laptop's microphone and 2 with our laptop's speaker, we configured the `MIC_DEV` and `SPK_DEV` to be set as 1 and 2 respectively. Ensure the same is done for your device before running the program otherwise the code will throw an error.

Once the offline code is being run it will prompt you to speak into the microphone while the audio is playing by display the `Recording from microphone (device index 0) for 10 seconds at 44100 Hz...` message. Note that the audio file is 1 minute 8 seconds long so make sure to note down at what times you were speaking to verify the DTD flag. The same applies for the live version which will prompt you to speak into the microphone by display `Starting live AEC... (Playing far_end.wav and recording mic)`