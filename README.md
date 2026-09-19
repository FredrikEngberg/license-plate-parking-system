# license-plate-parking-system
License plate recognition and parking automation system using camera input, computer vision and system integrations.

# License Plate Parking System

A camera-based parking automation system designed to detect vehicle registration plates, determine whether a vehicle is entering or leaving, and automatically update parking information.

> Status: 🚧 In development

---

## Overview

The goal of this project is to build a practical parking management system using camera input, computer vision and system integrations.

The system is intended to:

- Detect vehicles at a shared entrance/exit
- Read registration plates
- Determine whether the vehicle is entering or leaving
- Identify or assign a parking space
- Store parking information automatically
- Send or display relevant updates through external services

The project is designed to run locally without requiring a paid cloud subscription for the camera.

---

## Planned System

```text
             Vehicle
                │
                ▼
        ┌───────────────┐
        │ Camera input  │
        │  Tapo camera  │
        └───────┬───────┘
                │
             RTSP/video
                │
                ▼
        ┌───────────────┐
        │   Mac mini    │
        │ Processing    │
        └───────┬───────┘
                │
                ▼
        ┌───────────────┐
        │ Plate         │
        │ recognition   │
        └───────┬───────┘
                │
                ▼
        ┌───────────────┐
        │ Direction     │
        │ logic         │
        │ IN / OUT      │
        └───────┬───────┘
                │
        ┌───────┴────────┐
        ▼                ▼
   ┌─────────┐      ┌─────────┐
   │ Airtable│      │  Slack  │
   └─────────┘      └─────────┘


The Direction Problem
The parking area uses the same access point for both entry and exit.
Because a registration plate can be visible from both directions, reading the plate alone is not enough to determine whether the vehicle is entering or leaving.
Possible solutions being evaluated include:
Two-camera approach
Two cameras can be positioned in opposite directions.

                    PARKING AREA

                         ▲
                         │
                    Vehicle IN
                         │

                ┌─────────────────┐
                │   Camera IN     │
                └─────────────────┘


==================== ROAD ====================


                ┌─────────────────┐
                │   Camera OUT    │
                └─────────────────┘

                         │
                    Vehicle OUT
                         ▼

The system can use the camera that detects the vehicle to determine direction.
Additional logic can also be used to prevent duplicate detections.


Hardware
Planned/current hardware:
- Tapo IP camera
- Mac mini M2
- Local network connection
The Mac mini acts as the processing computer for the system.

Software
Technologies being evaluated or used:
- Python
- OpenCV
- OCR / Automatic Number Plate Recognition
- RTSP camera stream
- Airtable API
- Slack API
- Git
- GitHub

Camera detects vehicle
        ↓
Capture frame
        ↓
Locate registration plate
        ↓
Read plate using OCR
        ↓
Validate registration number
        ↓
Determine direction
        ↓
Check current parking state
        ↓
Update parking database
        ↓
Send notification / update

Example
A vehicle with registration:
ABC123
is detected by the entry camera.
The system could create:
Registration: ABC123
Direction: IN
Parking space: 2
Time: 14:32
Status: Parked

When the same vehicle later passes the exit camera:
Registration: ABC123
Direction: OUT
Time: 17:48
Status: Left

Project Goals
The main goals are to learn and demonstrate:
- Computer vision
- Camera stream processing
- OCR
- Python development
- API integrations
- Automation
- State management
- Real-world system design
- Git and GitHub workflow

Development Roadmap
Phase 1 – Camera connection
- Connect to camera
- Verify local video stream
- Capture frames from the stream
- Test image quality
Phase 2 – Plate detection
- Detect vehicles
- Locate registration plates
- Extract plate image
- Test OCR
- Validate Swedish registration numbers
Phase 3 – Direction detection
- Test entry camera
- Test exit camera
- Create IN/OUT logic
- Prevent duplicate detections
Phase 4 – Parking logic
- Store detected vehicles
- Track parking state
- Add parking space handling
- Handle repeated detections
Phase 5 – Integrations
- Airtable integration
- Slack integration
- Logging
- Error handling
Phase 6 – Testing
- Daylight tests
- Low-light tests
- Different vehicle speeds
- Multiple vehicles
- Incorrect OCR results

license-plate-parking-system/
│
├── src/
│   ├── camera/
│   ├── detection/
│   ├── direction/
│   ├── parking/
│   └── integrations/
│
├── tests/
│
├── docs/
│   ├── images/
│   └── diagrams/
│
├── config/
│
├── .gitignore
├── requirements.txt
└── README.md

Privacy
The project will be designed with privacy in mind.
Registration plate data and camera images should only be stored when required for the functionality of the system.
Sensitive configuration such as API keys and passwords must never be committed to GitHub.
These will instead be stored using environment variables or local configuration files excluded through .gitignore.

Current Status
The project is currently in the planning and initial development phase.
The camera hardware has been selected and the architecture of the system is being designed.

Future Improvements
Possible future additions:
- Web dashboard
- Parking history
- Automatic parking-space assignment
- Vehicle statistics
- Improved OCR confidence handling
- Local database
- Docker deployment
- Automatic startup on the Mac mini
- Additional camera support

Author
Fredrik Engberg
Embedded Systems & IoT
- GitHub: FredrikEngberg
- Portfolio: fredrikengberg.github.io
