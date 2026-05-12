# Algal Bloom IoT Monitoring System

This repository contains the technical documentation, firmware, and machine learning models for an inexpensive, IoT-based water quality monitoring system designed to predict harmful algal blooms (HABs).

---

## Project Overview

Harmful Algal Blooms (HABs) pose significant risks to recreational water quality and aquatic ecosystems. This project demonstrates a low-cost, field-deployable solution that uses physical water sensors to predict chlorophyll-a (Chla) levels, a key indicator of algal growth, using Random Forest and Gradient Boosting machine learning models.

---

## Features

### Real-Time Monitoring
- Collects:
  - pH
  - Conductivity
  - Temperature
  - Turbidity

### Active Sampling System
- Uses a reservoir and pump system for consistent sample acquisition.

### Automated Alerting
- Sends Gmail email alerts when high-risk algal growth is detected.

### Predictive Analytics
- Uses supervised machine learning with surrogate thresholds to classify bloom risk into:
  - `algae_absent`
  - `algae_may_be_present`
  - `algae_present`

---

## Repository Structure

```text
/Diagrams
    Wiring diagrams of system

/Documentation
    Formal IEEE report and presentation files

/Code
    Python scripts for machine learning model training and inference. Driver code for arduino

/3D Models
    Fusion Model of complete system
```

---

## Bill of Materials (BOM)

| Component | Description | Function |
|---|---|---|
| Microcontroller | IoT-enabled board (Arduino / ESP32) | Manages sensors and connectivity |
| pH Probe | Analog pH measurement probe | Monitors chemical spikes |
| Conductivity Sensor | Proxy indicator for nutrient levels | Detects high nutrient concentration (>300) |
| Turbidity Sensor | Measures water cloudiness | Low-cost surrogate for chlorophyll-a |
| Temperature Sensor | Waterproof DS18B20 probe | Tracks thermal growth conditions |
| Vacuum Pump | Micro 370 motor pump | Pulls water samples into the reservoir |
| Solenoid Valve | 12V valve | Responsible for draining the system |
| Boost Converter | XL6009 module | Converts 3.3V to 12V for solenoid operation |

---

## Machine Learning Performance

The system utilizes a surrogate threshold approach based on chlorophyll-a (Chla) guidelines from Health Canada using a **33 µg/L cutoff** for primary-contact water safety.

### Performance Metrics

- **Model Agreement Rate:** `84.74%`
  - Agreement between Random Forest and Gradient Boosting models on test data.

- **Primary Optimization Metric:** `Precision`
  - Designed to minimize false alarms while maintaining high sensitivity.

---

## Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/DorkyJuice/algalbloom_IOT.git
```

### 2. Initialize Submodules

```bash
git submodule update --init --recursive
```

### 3. Install Python Requirements

```bash
pip install -r requirements.txt
```

---

## Known Constraints & Future Recommendations

### Optimization
The current reservoir design is oversized for practical field deployment, leading to unnecessary energy consumption.

### Power Efficiency
The use of a 12V solenoid with a boost converter introduces substantial power losses. A native 3.3V solenoid is recommended for future revisions.

### Sensor Maintenance
The low-cost pH probe used in the prototype is highly sensitive and requires frequent recalibration and maintenance.

---

## References

This project was developed using guidance and threshold recommendations from:

- BC Ministry of Environment
- Health Canada

Additional references and citations are included in the Technical Report.
