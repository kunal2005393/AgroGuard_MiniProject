# 🌱 AGROGUARD — Smart Agriculture Decision Support System

**An IoT-Based Multi-Parameter Precision Agriculture Decision Support System for Sustainable Farming**

AGROGUARD is a low-cost smart agriculture project designed to help farmers make informed decisions about farm conditions, irrigation, and pesticide spraying. It combines environmental sensors, an Arduino-based monitoring device, a FastAPI backend, a Supabase database, and a web dashboard to transform field measurements into actionable recommendations.

## 🎯 Problem Statement

Farmers face challenges such as inefficient water use, limited access to real-time field information, uncertain irrigation timing, and unsuitable pesticide spraying conditions. AGROGUARD aims to address these challenges through affordable monitoring and decision-support technology.

## ✨ Key Features

- **Multi-Parameter Monitoring:** Measures soil moisture, temperature, humidity, rainfall, and water-tank level.
- **AFHI — Adaptive Farm Health Index:** Combines monitored parameters into a weighted farm-condition score.
- **CAII — Crop Adaptive Irrigation Intelligence:** Provides irrigation and water-availability recommendations.
- **SPAE — Smart Pesticide Advisory Engine:** Provides spraying-condition recommendations based on environmental readings.
- **Web Dashboard:** Presents sensor readings, farm-health information, and recommendations.
- **Local Status Display:** Uses an OLED display and status LEDs for on-device feedback.
- **Database Integration:** Uses Supabase and PostgreSQL for structured data storage.
- **Modular Architecture:** Separates sensor acquisition, backend processing, decision logic, storage, and visualization.

> **Note:** The current prototype uses rule-based and weighted decision logic. Machine learning and computer vision are potential future enhancements.

## 🧰 Technology Stack

| Component | Technology |
|---|---|
| Microcontroller | Arduino UNO R4 WiFi |
| Sensors | Soil moisture, DHT11, rain sensor, water-level sensor |
| Local display | SSD1306 OLED |
| Backend | Python, FastAPI |
| Database | Supabase, PostgreSQL |
| Frontend | HTML, CSS, JavaScript |
| Communication | Wi-Fi, HTTP/REST APIs |
| Decision support | AFHI, CAII, SPAE |

## 🏗️ System Architecture


Field Sensors
     ↓
Arduino UNO R4 WiFi
     ↓ Wi-Fi / HTTP
FastAPI Backend
     ↓
Validation and Decision Engine
     ├── AFHI: Farm Health Assessment
     ├── CAII: Irrigation Advisory
     └── SPAE: Pesticide Advisory
     ↓
Supabase / PostgreSQL
     ↓
Web Dashboard

Arduino → OLED Display and Status LEDs


## 📊 Decision-Support Modules

### 1. AFHI — Adaptive Farm Health Index

AFHI calculates a weighted score from normalized soil moisture, temperature, humidity, rainfall, and water availability.

The prototype uses the following weights:

- Soil moisture: 30%
- Temperature: 20%
- Humidity: 15%
- Rainfall: 20%
- Water availability: 15%

The resulting score supports an overall assessment of monitored farm conditions. The weights and thresholds are prototype settings and require field validation before agricultural deployment.

### 2. CAII — Crop Adaptive Irrigation Intelligence

CAII considers soil moisture, rainfall, water availability, and crop context to provide irrigation-related recommendations. It is intended to support water-conscious decisions rather than replace farmer judgment.

### 3. SPAE — Smart Pesticide Advisory Engine

SPAE evaluates environmental conditions to advise whether spraying should be avoided, delayed, or considered under the prototype's rules. Its output is advisory only and does not establish pesticide safety or replace product-label instructions and agricultural expert guidance.

## 🔌 Hardware Components

- Arduino UNO R4 WiFi
- DHT11 temperature and humidity sensor
- Soil moisture sensor
- Rain sensor
- Water-level sensor
- SSD1306 I²C OLED display
- Green, yellow, and red LEDs
- Push buttons for user interaction
- Buzzer (optional, depending on the current hardware configuration)
- Connecting wires and breadboard

## 📁 Project Structure

`text
AgroGuard_MiniProject/
├── arduino/
│   ├── agroguard_device_telemetry/
│   └── agroguard_wifi_test/
├── backend/
│   ├── app/
│   ├── routes/
│   ├── services/
│   └── requirements.txt
├── database/
│   ├── README.md
│   └── supabase_schema.sql
├── frontend/
│   ├── assets/
│   ├── css/
│   ├── js/
│   ├── locales/
│   └── index.html
├── .gitignore
└── README.md
`

## 🚀 Setup and Installation

### Prerequisites

- Python 3.10 or a compatible version supported by the project dependencies
- Git
- Arduino IDE
- Required Arduino libraries
- A Supabase project if database integration is enabled

### 1. Clone the repository

```bash
git clone https://github.com/kunal2005393/AgroGuard_MiniProject.git
cd AgroGuard_MiniProject
```

### 2. Set up the backend

```bash
cd backend
python -m venv venv
```

Activate the virtual environment on Windows:

```powershell
.\venv\Scripts\Activate.ps1
``'

Install the dependencies:

```bash
pip install -r requirements.txt
```

Configure the required environment variables using the provided `.env.example` as a guide. Use your own credentials and never commit real secrets.

Run the backend from the backend directory using the entry point documented in the project. For an application exposed as `app.main:app`, the command is:

```bash
python -m uvicorn app.main:app --host 127.0.0.1 --port 5000
```

### 3. Configure the database

1. Create a Supabase project.
2. Review `database/supabase_schema.sql`.
3. Apply the schema using the Supabase SQL Editor if it matches your current backend configuration.
4. Configure database connection details through environment variables.

Refer to [`database/README.md`](database/README.md) for database-specific instructions.

### 4. Configure the Arduino device

1. Open the required `.ino` file from the `arduino/` directory in Arduino IDE.
2. Install the libraries required by the sketch.
3. Create your own local `arduino_secrets.h` using the provided example template, if available.
4. Configure your Wi-Fi credentials, device ID, backend host, port, and device API key locally.
5. Ensure the device and computer can communicate over the same network when using a local backend.
6. Select the correct board and port, then upload the sketch.

**Security:** Never publish Wi-Fi passwords, device API keys, Supabase service-role keys, or other private credentials.

### 5. Run the frontend

Open `frontend/index.html` in a browser or use a local development server. Configure the API base URL in the frontend settings or source code to match the running backend.

## 🌍 Sustainable Development Goals

AGROGUARD aligns with the objectives of:

- **SDG 2 — Zero Hunger:** Supporting informed and sustainable agricultural practices.
- **SDG 6 — Clean Water and Sanitation:** Encouraging efficient water management.
- **SDG 9 — Industry, Innovation and Infrastructure:** Applying affordable technology to agricultural challenges.
- **SDG 12 — Responsible Consumption and Production:** Supporting more informed resource use.
- **SDG 13 — Climate Action:** Encouraging climate-aware agricultural decisions.

These are intended contributions; their real-world impact requires evaluation.

## 🔮 Future Scope

- Machine-learning-based irrigation prediction
- Crop recommendation using soil and environmental information
- Fertilizer advisory
- Computer-vision-based crop-health assessment
- Advanced weather integration
- Automated irrigation hardware
- Mobile application and notifications
- Multi-farm monitoring and field trials

## ⚠️ Limitations

AGROGUARD is a prototype decision-support system. Sensor calibration, environmental variability, crop-specific requirements, and local agricultural conditions can affect recommendations. Field testing and expert validation are required before relying on its outputs for operational farming decisions.

## 👨‍💻 Project Information

**Project Name:** AGROGUARD  
**Category:** IoT, Smart Agriculture, Precision Agriculture  
**Repository:** [AgroGuard_MiniProject](https://github.com/kunal2005393/AgroGuard_MiniProject)

## 📄 License

A license has not yet been specified. Add an appropriate license file if you want to define how others may reuse, modify, or distribute this project.
