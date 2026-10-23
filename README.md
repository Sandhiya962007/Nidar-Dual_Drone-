# NIDAR 2025 – Autonomous Agriculture Drone System

## Overview
This project is developed for the NIDAR 2025 competition. It focuses on a dual-drone system for precision agriculture, combining crop scanning, plant-stress identification, and targeted spraying with ground control and drone simulation using Software-in-the-Loop (SITL).

The system uses separate drones for scanning and spraying to support efficient agricultural monitoring and treatment.

## Project Structure

```text
NIDAR_2025/
├── dual_drone_simulation_in_SITL/
│   ├── scan1_drone.py
│   └── spray_drone1.py
├── GCS_STATION.py
├── README.md
├── gcs.py
├── jetson.py
├── test.py
└── two_drone.py
```

## 1. Dual-Drone Simulation in SITL

**Files:**
- `scan1_drone.py`
- `spray_drone1.py`

**Purpose:**
Simulates two drones using Software-in-the-Loop (SITL).

### Scanning Drone
The scanning drone is intended to:
- Follow predefined waypoints over the agricultural field.
- Collect crop images or sensor data.
- Identify potential crop-stress locations.
- Record GPS coordinates for detected targets.

### Spraying Drone
The spraying drone is intended to:
- Use target coordinates identified by the scanning drone.
- Navigate to the corresponding locations.
- Perform targeted spraying.
- Return to its launch location after completing the mission.

## 2. Ground Control Station

**File:** `GCS_STATION.py`

Provides the main ground control station functionality for managing drone missions and monitoring their operation.

Potential responsibilities include:
- Monitoring drone status.
- Managing mission information.
- Displaying telemetry and GPS data.
- Coordinating mission execution.

## 3. Ground Control System

**File:** `gcs.py`

Contains supporting ground control functionality for communicating with drones and handling mission-related information.

Possible functions include:
- Drone communication.
- Telemetry monitoring.
- Mission coordination.
- Receiving and processing drone data.

## 4. Jetson Integration

**File:** `jetson.py`

Provides a starting point for integrating onboard processing using an NVIDIA Jetson platform.

Potential applications include:
- Crop-image processing.
- Computer vision.
- Crop-stress detection.
- Processing sensor data and target coordinates.

## 5. Testing

**File:** `test.py`

Used to test individual functions, communication, or mission-related components during development.

## 6. Dual-Drone Coordination

**File:** `two_drone.py`

Contains the dual-drone coordination logic.

The intended workflow is:
1. Initialize both drone connections.
2. Start the scanning mission.
3. Collect crop-stress target coordinates.
4. Transfer the target information to the spraying workflow.
5. Start the spraying mission after the required scanning-stage completion conditions are met.
6. Monitor mission progress and return the drones safely.

## Technologies Used

- Python 3
- ArduPilot SITL
- MAVLink
- DroneKit, where used by the scripts
- GPS waypoint navigation
- Ground Control Station (GCS)
- NVIDIA Jetson platform
- Computer vision for crop monitoring

## System Workflow

1. **Simulation:** Launch the drones in SITL.
2. **Scanning:** The first drone surveys the agricultural field.
3. **Target Identification:** Crop-stress locations are identified and their coordinates recorded.
4. **Mission Coordination:** Ground control manages the mission information and drone status.
5. **Targeted Spraying:** The second drone visits the identified locations and performs the spraying operation.
6. **Mission Completion:** The drones complete their assigned missions and return according to the configured flight logic.

## Project Objective

The objective is to develop an autonomous precision-agriculture system that separates crop monitoring from targeted spraying. This approach aims to reduce unnecessary chemical application, improve monitoring efficiency, and demonstrate coordinated drone operations for the NIDAR 2025 competition.

## Important Note

This README describes the intended project architecture based on the provided filenames. Actual functionality, communication protocols, and mission sequencing depend on the implementation in each Python file. Test all flight operations in SITL before conducting real-world flights.
