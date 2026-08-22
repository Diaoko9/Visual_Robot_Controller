# Visual_Robot_Controller

**Author:** Ahmad Poureskandari  
**Domain:** Computer Vision | Robotics (Visual Servoing) | Edge Computing | Embedded Linux

## 📌 Project Overview
This repository contains a complete closed-loop "visual servoing" pipeline. It utilizes a Raspberry Pi 4 to capture real-time video, process frames to identify object coordinates using OpenCV, and dynamically calculate the inverse kinematics required to command a 4-DOF meArm2 robotic arm to grasp the target.

By handling both the high-level computer vision processing and the low-level hardware control on a single edge device, this project demonstrates a highly optimized approach to autonomous robotic interaction.

## 🔬 Academic & Research Value
This project serves as a foundational prototype for advanced intelligent systems and aligns with modern research in computer vision laboratories:
* **Visual Servoing at the Edge:** Demonstrates the viability of running continuous OpenCV object detection loops on resource-constrained hardware while minimizing control latency.
* **Kinematic Modeling:** Translates 2D pixel coordinates (Camera Frame) into a 3D spatial coordinate system, solving the Inverse Kinematics (IK) to generate precise shoulder, elbow, and base joint angles.
* **Benchmarking:** Establishes a framework for measuring the trade-offs between frame resolution, processing time, and physical positioning accuracy (error in mm).

## ⚙️ Engineering & Industrial Value
* **Hardware Abstraction:** Features a custom Python driver layer to bridge high-level algorithms with low-level PWM/I2C hardware protocols (e.g., driving PCA9685 servo controllers).
* **POSIX/Linux Environment:** Developed in a headless Linux environment, proving competency in edge device configuration, SSH deployment, and system resource management.
* **Python for Automation:** Showcases production-ready Python structuring, separating vision modules, mathematical calculation engines, and hardware execution threads.

## 🛠️ Hardware & Software Stack
* **Compute:** Raspberry Pi 4 Model B (Linux)
* **Vision:** Raspberry Pi Camera Module V2 (or standard USB Webcam)
* **Actuation:** meArm2 (4 Degrees of Freedom) + PCA9685 16-Channel PWM Driver
* **Software:** Python 3, OpenCV (cv2), NumPy

## 📂 Repository Structure
```text
mearm-vision-raspi/
├── src/                
│   ├── vision.py          # OpenCV object detection and pixel coordinate extraction
│   ├── kinematics.py      # Forward/Inverse kinematics math engine (NumPy)
│   ├── arm_control.py     # Hardware abstraction layer for I2C/PWM servo control
│   └── main.py            # Main execution loop integrating vision and motion
├── docs/               
│   ├── kinematic_equations.md # Mathematical breakdown of the IK model
│   └── wiring_diagram.png     # Pinout connections for Pi to PCA9685
├── tests/                 # Scripts for calibrating servos and camera focal length
├── requirements.txt       # Python dependencies
└── README.md              # Project overview and setup instructions
