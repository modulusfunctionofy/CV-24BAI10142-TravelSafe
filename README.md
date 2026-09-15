# TravelSafe — Driver Monitoring & Safety Analysis

TravelSafe is a **Computer Vision–based Driver Monitoring System (DMS)** designed to identify potentially unsafe driving behaviors from live webcam feeds and pre-recorded videos.

The project combines **YOLOv8, MediaPipe, OpenCV, and real-time video processing** to detect and analyze behaviors such as drowsiness, yawning, distraction, and phone usage.

The system is implemented as a full-stack application with a **FastAPI backend, Vue.js frontend, and SQLite database**, making it suitable for academic use, experimentation, and real-time computer vision analysis.

---

## Features

- **Drowsiness Detection**  
  Uses facial landmarks and Eye Aspect Ratio (EAR) to identify prolonged eye closure.

- **Yawn Detection**  
  Uses Mouth Aspect Ratio (MAR) to detect potential yawning and signs of fatigue.

- **Distraction Detection**  
  Analyzes head orientation using yaw and pitch to identify potential driver distraction.

- **Phone Detection**  
  Uses YOLOv8 object detection to identify mobile phone usage.

- **Real-Time Monitoring**  
  Supports live driver monitoring using a standard webcam.

- **Video Analysis**  
  Supports analysis of pre-recorded video files.

- **Risk Scoring**  
  Calculates an overall safety score based on the frequency and severity of detected events.

- **Session Management**  
  Stores completed sessions and detected incidents for later review.

- **Analytics Dashboard**  
  Provides a web-based dashboard for viewing session history, incidents, and analytics.

- **Headless CLI**  
  Allows video analysis without launching the web dashboard.

---

## Technology Stack

### Computer Vision

- Python
- OpenCV
- MediaPipe
- YOLOv8
- NumPy

### Backend

- Python
- FastAPI
- SQLAlchemy
- SQLite

### Frontend

- Vue.js 3
- Vite
- JavaScript
- Chart.js
- HTML/CSS

### Development & Testing

- Git
- Docker
- Docker Compose
- Pytest

---

## System Architecture

TravelSafe follows a client-server architecture consisting of a Vue.js frontend, FastAPI backend, computer vision engine, and SQLite database.

```text
                    ┌─────────────────────┐
                    │   Webcam / Video    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Video Processing  │
                    │       OpenCV        │
                    └──────────┬──────────┘
                               │
                ┌──────────────┴──────────────┐
                │                             │
                ▼                             ▼
       ┌──────────────────┐          ┌──────────────────┐
       │ MediaPipe Face   │          │  YOLOv8 Object   │
       │     Analysis     │          │    Detection     │
       └────────┬─────────┘          └────────┬─────────┘
                │                             │
                ▼                             ▼
       ┌──────────────────┐          ┌──────────────────┐
       │ EAR / MAR / Head │          │ Phone / Object   │
       │     Analysis     │          │    Detection     │
       └────────┬─────────┘          └────────┬─────────┘
                │                             │
                └──────────────┬──────────────┘
                               ▼
                    ┌─────────────────────┐
                    │    Event Engine     │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Risk Scoring      │
                    │      Engine         │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │    FastAPI Backend  │
                    └──────────┬──────────┘
                               │
                    ┌──────────┴──────────┐
                    ▼                     ▼
          ┌──────────────────┐   ┌──────────────────┐
          │ SQLite Database  │   │   Vue.js Web     │
          │                  │   │    Dashboard     │
          └──────────────────┘   └──────────────────┘