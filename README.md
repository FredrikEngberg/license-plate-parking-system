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
