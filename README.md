# Humanoid Robot Stack

> **Showcase page.** This repository is a public showcase of a **private repository**:
> it contains a description of the work only, with **no source code**.

Embodied-AI software for a **humanoid service robot** (Jetson-based platform, ROS 2), built during my work as a Robotics and AI Engineer at Botifull.

The robot perceives the people in front of it, verifies who they are, navigates a shared indoor space safely, and holds a spoken conversation grounded in what it can actually see.

## What I built

**Person perception**
- RGB-D pipeline on an Orbbec Gemini 2 depth camera, YOLO person detection and MediaPipe landmarks
- Per-frame record: presence, distance, person and head position, horizontal and vertical angle, confidence
- Depth and angle utilities that turn pixels into metric, robot-frame geometry
- Runs first on a laptop for fast iteration, then the same modules move into the ROS 2 package on the robot

**Identity and interaction**
- Face-based identity, QR and ID-card recognition, and an identity-verification flow
- Head tracking so the robot holds eye contact as a person moves
- Handshake behaviour, touch-sensor handling, head-screen UI and an operator control panel
- ASL fingerspelling recognition

**Navigation**
- LiDAR-based navigation, stereo navigation and obstacle avoidance
- Semantic navigation: navigate by what a place *is*, not only by coordinates
- Semantic frame extraction linking perception output to the planner

**Scene understanding**
- Spill and trash detection for an indoor service environment
- Clothing VLM for open-vocabulary description of people

**Voice**
- Local text-to-speech, audio streaming, and an LLM dialogue pipeline connecting speech to grounded robot responses

## Stack

Python, ROS 2, PyTorch, YOLO, MediaPipe, SAM / CLIP-class models, Whisper, Orbbec Gemini 2 (RGB-D), LiDAR, stereo vision, MuJoCo (simulation before deployment), NVIDIA Jetson

## How it was developed

Simulation first: behaviour validated in MuJoCo before every hardware run, then iterated between simulation and the real robot. Each capability was built as a standalone module with its own tests, then integrated into the robot's ROS 2 runtime.

---

*Source code is private. This page documents the work; code can be shared on request.*
