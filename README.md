# 🪖 IoT Smart Helmet — Industrial Worker Safety Monitoring System

<p align="center">
  <b>SiWx917 Wi-Fi 6 + Bluetooth LE | IoT | Edge Monitoring | Cloud Dashboard</b>
</p>

<p align="center">
  An IoT-enabled industrial safety helmet designed to monitor hazardous conditions, detect worker impacts, and transmit real-time safety information through wireless connectivity.
</p>

---

## 📌 Project Overview

The **IoT Smart Helmet** is an embedded safety-monitoring system developed for industrial environments where workers may be exposed to **gas leakage, excessive temperature, and accidental impacts/falls**.

The system combines multiple sensors with the **Silicon Labs SiWx917 Wi-Fi 6 + Bluetooth LE platform** to collect safety-related parameters and communicate the data to a cloud-connected monitoring system.

A web dashboard provides a centralized interface for viewing helmet status and sensor information.

### 🎯 Objective

To develop a compact and connected worker-safety system capable of:

* Monitoring environmental conditions
* Detecting abnormal impacts or falls
* Identifying potentially hazardous gas levels
* Processing sensor information at the edge
* Transmitting safety data wirelessly
* Providing real-time monitoring through a web dashboard

---

## 🚀 Key Features

### 🛡️ Worker Safety Monitoring

* Impact / fall detection using **MPU6050**
* Gas-level monitoring using **MQ-135**
* Temperature and humidity monitoring using **DHT22**
* Hazard-status evaluation

### 📡 Wireless Connectivity

* **Wi-Fi 6** connectivity using SiWx917
* **Bluetooth Low Energy (BLE)** capability
* Wireless transmission of safety information

### ☁️ Cloud & Data Layer

* Sensor data preparation for cloud transmission
* Python-based data uploader
* REST-based communication architecture
* Structured sensor data format

### 📊 Monitoring Dashboard

* Helmet identification
* Current safety status
* Gas-level visualization
* Impact-force information
* Temperature monitoring
* Web-based monitoring interface

---

# 🏗️ System Architecture

```text
                 ┌─────────────────────────┐
                 │      SMART HELMET        │
                 │                         │
                 │  MPU6050  → Impact      │
                 │  MQ-135   → Gas         │
                 │  DHT22    → Environment  │
                 └────────────┬────────────┘
                              │
                              ▼
                 ┌─────────────────────────┐
                 │       SiWx917 SoC       │
                 │                         │
                 │ Sensor Processing       │
                 │ Hazard Evaluation       │
                 │ Wi-Fi 6 / BLE           │
                 └────────────┬────────────┘
                              │
                         Wi-Fi / BLE
                              │
                              ▼
                 ┌─────────────────────────┐
                 │     Cloud / Server      │
                 │                         │
                 │ Data Reception           │
                 │ Data Storage             │
                 └────────────┬────────────┘
                              │
                              ▼
                 ┌─────────────────────────┐
                 │    Web Dashboard        │
                 │                         │
                 │ Status                  │
                 │ Gas Level               │
                 │ Impact                  │
                 │ Temperature             │
                 └─────────────────────────┘
```

---

# 🔧 Hardware Components

| Component                         | Purpose                                                   |
| --------------------------------- | --------------------------------------------------------- |
| **Silicon Labs SiWx917 BRD2605A** | Main controller, Wi-Fi 6 & BLE connectivity               |
| **MPU6050**                       | Accelerometer / gyroscope for impact and motion detection |
| **MQ-135**                        | Gas / air-quality monitoring                              |
| **DHT22**                         | Temperature and humidity measurement                      |
| **Li-ion Battery**                | Portable power source                                     |
| Smart Helmet                      | Physical safety platform                                  |

---

# 💻 Software & Technologies

| Technology                          | Usage                              |
| ----------------------------------- | ---------------------------------- |
| **C**                               | Embedded firmware                  |
| **Python**                          | Cloud/data communication           |
| **HTML**                            | Dashboard structure                |
| **CSS**                             | Dashboard styling                  |
| **JavaScript**                      | Dashboard interaction              |
| **Wi-Fi 6**                         | Wireless communication             |
| **Bluetooth LE**                    | Short-range wireless communication |
| **REST API**                        | Data transmission architecture     |
| **SiWx917 SDK / Development Tools** | Embedded development               |

---

# 📂 Project Structure

```text
IoT-Smart-Helmet/
│
├── 📁 firm/
│   └── main.c
│
├── 📁 cloud/
│   ├── data_uploader.py
│   └── firebase_config.json
│
├── 📁 dashboard/
│   ├── index.html
│   ├── script.js
│   └── style.css
│
├── 📦 Industry-based-Smart-Helmet.zip
│
└── 📄 README.md
```

---

# ⚙️ Firmware Architecture

The embedded firmware follows a simple monitoring cycle:

```text
        START
          │
          ▼
   Initialize SiWx917
          │
          ▼
   Initialize Sensors
          │
          ▼
    Read Sensor Data
          │
          ▼
   Evaluate Conditions
          │
      ┌───┴────┐
      │        │
    SAFE     HAZARD
      │        │
      │        ▼
      │   Generate Alert
      │        │
      │        ▼
      │   Send Data
      │        │
      └────┬───┘
           ▼
     Continue Monitoring
```

---

# 🧠 Hazard Detection Concept

The system evaluates multiple sensor parameters to determine the current helmet condition.

### Example parameters

```text
Gas Level
    ↓
MQ-135
    ↓
Hazard Evaluation

Impact / Motion
    ↓
MPU6050
    ↓
Fall / Impact Evaluation

Temperature & Humidity
    ↓
DHT22
    ↓
Environmental Monitoring
```

The resulting information can be classified into states such as:

```text
🟢 SAFE
🟡 WARNING
🔴 HAZARD
```

---

# ☁️ Cloud Data Flow

Sensor information is structured before being transmitted to the cloud layer.

Example data:

```json
{
  "helmet_id": "HLT_01",
  "gas_level": 145,
  "impact_force": 2.8,
  "temperature": 33.2,
  "status": "SAFE"
}
```

The current repository includes a Python-based uploader for demonstrating the cloud communication layer.

> **Note:** The repository currently contains prototype/simulated cloud communication. The placeholder cloud endpoint should be replaced with the deployment server/Firebase endpoint before production use.

---

# 📊 Web Dashboard

The dashboard provides a simple monitoring interface for the smart helmet.

### Dashboard Parameters

* 🪖 Helmet ID
* 🟢 Current safety status
* 🌫️ Gas level
* 💥 Impact force
* 🌡️ Temperature

The dashboard is implemented using:

```text
HTML
 ↓
CSS
 ↓
JavaScript
 ↓
Sensor / Cloud Data
```

---

# 🔄 Complete Data Flow

```text
Sensors
   │
   ▼
SiWx917
   │
   ├── Sensor Processing
   │
   ├── Hazard Evaluation
   │
   └── Wi-Fi / BLE Communication
             │
             ▼
        Cloud / Server
             │
             ▼
       Web Dashboard
             │
             ▼
      Safety Monitoring
```

---

# 🧪 Current Prototype Status

| Module                       | Status               |
| ---------------------------- | -------------------- |
| SiWx917 development platform | 🟢 Implemented       |
| Sensor architecture          | 🟢 Defined           |
| MPU6050 integration          | 🟡 Prototype         |
| MQ-135 integration           | 🟡 Prototype         |
| DHT22 integration            | 🟡 Prototype         |
| Firmware architecture        | 🟡 Prototype         |
| Cloud communication          | 🟡 Prototype         |
| Web dashboard                | 🟢 Implemented       |
| End-to-end deployment        | 🔵 Under development |

> 🟢 Implemented    🟡 Prototype    🔵 Under Development

---

# 🎯 Applications

The system can be adapted for:

* 🏭 Manufacturing industries
* ⛏️ Mining environments
* 🏗️ Construction sites
* 🧪 Chemical industries
* ⚡ Industrial maintenance
* 🚧 Hazardous work zones

---

# 🔮 Future Enhancements

The prototype can be extended with:

* 🚨 Emergency SOS button
* 📍 GPS-based worker location
* 📱 Mobile notifications
* 🔔 Buzzer / vibration alerts
* 📈 Historical sensor analytics
* ☁️ Real-time cloud database
* 🤖 ML-based accident prediction
* 🔋 Battery-level monitoring
* 👷 Worker identification
* 📡 OTA firmware updates

---

# 🏆 Project Highlights

### Why SiWx917?

The **SiWx917** provides an integrated wireless platform combining:

```text
              SiWx917
                 │
        ┌────────┴────────┐
        │                 │
     Wi-Fi 6             BLE
        │                 │
        └────────┬────────┘
                 │
          IoT Connectivity
```

This enables the smart helmet to communicate with connected systems without requiring a separate Wi-Fi and Bluetooth controller.

---

# 👨‍💻 Project Team

**Project:** IoT Smart Helmet – Industrial Worker Safety Monitoring System

**Institution:** KPR Institute of Engineering and Technology (KPRIET)

**Domain:** Embedded Systems • IoT • Wireless Communication • Industrial Safety

---

# 📜 License

This project is developed for **academic, research, and educational purposes**.

---

<p align="center">
  <b>🪖 Building Safer Connected Workplaces with IoT</b>
</p>
