# CS 3338 Final Project - Group 2 - EagleNav

**Jira Project URL:** https://cs3338-group-2.atlassian.net/jira/for-you

---

## Team 2

- Anna Guerrero-Leon
- Jose Mateo Ayala
- Justin Ho
- Min Park

---

## Overview

EagleNav is a mobile campus navigation application designed to improve accessibility and navigation for students, staff, and visitors at California State University, Los Angeles. The app focuses on supporting students with disabilities by providing accessible route guidance, voice-guided directions, augmented reality overlays, and real-time obstacle detection using the device camera.

The system comprises:

- **A Mobile Application (Android & iOS):** For students and campus visitors to navigate the CSULA campus using GPS, voice guidance, AR overlays, and haptic feedback.
- **A Routing Backend:** A self-hosted Valhalla routing engine running on Google Cloud Platform, serving pedestrian routes computed from a custom CSULA campus map built with OpenStreetMap data.
- **An Events Service:** A Node.js service that provides campus event data, allowing users to browse, bookmark, and receive notifications for upcoming events.

---

## System Architecture

The application follows this general workflow:

1. **Route Request:** The user opens the app, searches for a destination, and the app resolves the closest accessible building entrance.
2. **Route Generation:** The app sends a routing request to the Valhalla backend, which computes a pedestrian route using the custom CSULA campus map.
3. **Live Navigation:** The app's guidance loop runs on every GPS tick, tracking the user's position, advancing navigation steps, and detecting route deviation.
4. **Voice & Haptic Guidance:** The app delivers turn-by-turn instructions as body-relative spoken directions (e.g., "turn slightly to your right") along with haptic feedback on each turn.
5. **Obstacle Detection:** In parallel with navigation, the object detection module processes the device camera feed and alerts the user to nearby obstacles via text-to-speech.

---

## Features

- **Mobile Application (Android & iOS):**
  - GPS-based turn-by-turn campus navigation
  - Body-relative voice guidance and orientation coaching
  - Augmented reality navigation overlays
  - Real-time obstacle detection using YOLOv11n
  - Haptic feedback on turns and step advancement
  - Campus events browser with bookmarking and notifications
  - Accessibility settings: high contrast mode, text size, caption mode

---

## Technologies Used

- **Mobile Application:**
  - Flutter (Dart)
  - OpenStreetMap / flutter_map
  - geolocator, flutter_compass, flutter_tts
  - YOLOv11n (object detection and segmentation)
  - Core ML (iOS) / TFLite (Android)

- **Backend & Infrastructure:**
  - Valhalla (open-source routing engine)
  - Google Cloud Platform (VM hosting)
  - Cloudflare R2 (campus map storage)
  - JOSM (campus map editing)
  - Node.js (events service)
  - Docker
