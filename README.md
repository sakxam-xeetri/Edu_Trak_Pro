<div align="center">

# 🎓 Edu Track Pro
**Next-Generation IoT RFID Smart Attendance System**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![PHP](https://img.shields.io/badge/PHP-8.0+-777BB4?style=for-the-badge&logo=php&logoColor=white)](https://www.php.net/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0+-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![Arduino](https://img.shields.io/badge/Arduino-ESP8266-00979D?style=for-the-badge&logo=arduino&logoColor=white)](https://www.arduino.cc/)

*A production-ready, highly scalable IoT attendance management platform that seamlessly bridges specialized hardware with a powerful, comprehensive web dashboard.*

[Features](#-key-features) • [Architecture & Tech Stack](#-architecture--tech-stack) • [System Structure](#-system-structure) • [Installation](#-quick-start-guide) • [API](#-api-reference) • [Contributors](#-team)

</div>

---

## 🌟 Overview

**Edu Track Pro** automates the entire student attendance lifecycle. Using ESP8266 and MFRC522 RFID scanners, our hardware securely and instantly transmits tap-in and tap-out data to a custom PHP/MySQL backend. Administrators and students interact with a beautiful, fully responsive dashboard loaded with real-time analytics, automated logging, and easy-export capabilities.

---

## ✨ Key Features

### 🛡️ Enterprise-Grade Authentication & Roles
- **Admin Dashboard**: Full administrative control, student lifecycle management, and actionable analytics.
- **Student Portal**: Secure individual access to daily routines, historical attendance, and interactive calendar views.

### ⚡ Smart IoT Capabilities
- **Automated Check-In/Out**: Intelligent state detection (First scan = IN, Second scan = OUT).
- **Reject Logic**: Prevents duplicate entry spamming in a single day.
- **Instant Synchronization**: Real-time communication between hardware and the backend API over Wi-Fi.

### 📊 Powerful Analytics & UX
- **Interactive Visualizations**: Powered by **Chart.js** for actionable insights on dashboard.
- **Responsive Design**: Flawless experience across desktop, tablet, and mobile (Dark/Light mode native UX).
- **One-Click Exports**: Generate CSV and Excel reports instantly.
- **Timezone Aware**: Robust timezone handling (Default: GMT+5:45 Nepal).

---

## 🏗️ Architecture & Tech Stack

### Software Engineering
| Layer | Technologies | Description |
| :--- | :--- | :--- |
| **Frontend** | HTML5, CSS3, ES6+, Chart.js | Responsive, modern, state-driven UI interface. |
| **Backend** | PHP 8.0+, RESTful API | Secure data processing, authentication, sessions. |
| **Database** | MySQL / MariaDB | Relational architecture, built-in security. |
| **Security** | Bcrypt, Prepared Statements | Protection against SQLi, XSS, CSRF attacks. |

### Embedded Hardware
| Component | Specifications | Purpose |
| :--- | :--- | :--- |
| **ESP8266 NodeMCU** | Wi-Fi Microcontroller | Core logic, API communication via `ESP8266HTTPClient`. |
| **MFRC522 Module** | 13.56MHz RFID | Reads MIFARE RFID cards/tags. |
| **16x2 LCD (I2C)** | 0x27 Address | Real-time visual feedback to users at the gate. |
| **Buzzer & LEDs** | Active | Instant audio/visual success and error alerts. |

---

## 📂 System Structure

We enforce a modern, separated project structure for maximum maintainability:

```text
Edu_Trak_Pro/
├── frontend/             # 🎨 HTML, CSS, JS application layers
│   ├── index.html        # App landing and frontend routing
│   ├── admin-dashboard.html
│   ├── student-dashboard.html
│   ├── css/              # Modular stylesheets
│   └── js/               # Frontend logic & API interfacing
├── API/                  # ⚙️ PHP Backend RESTful Endpoints
│   ├── conn.php          # Database connectivity
│   ├── rfid-checkin.php  # Core IoT ingestion endpoint
│   └── ...               # Auth and CRUD controllers
├── arduino/              # 📡 Embedded C++ Firmware
│   └── audrino.ino       # ESP8266 implementation code
├── database/             # 💾 Data schemas
│   └── schema.sql        # Table structures & seeds
└── docs/                 # 📚 Extensive documentation
```

---

## 🚀 Quick Start Guide

### 1. Database Initialization
1. Ensure your local server environment (e.g., XAMPP, LAMP, or Docker) is running.
2. Initialize a new database named `edutrack`.
3. Import the schema file located at `database/schema.sql`.

### 2. API & Environment Setup
Update configuration files to match your local network:
- Modify `API/conn.php` with your MySQL credentials if they vary from default root.
- Update the `arduino/audrino.ino` sketch with your backend host settings:
  ```cpp
  const char* serverHost = "192.168.1.100";  // Your backend Server IP
  const char* apiEndpoint = "/projects/iot/IoT-RFID-Attendance-System-/API/rfid-checkin.php"; // Update to your directory path
  ```

### 3. Hardware Deployment
Wire your ESP8266 to the MFRC522 and peripherals as outlined in the hardware documentation.
1. Select **NodeMCU 1.0 (ESP-12E Module)** in the Arduino IDE.
2. Compile and upload the firmware.
3. Connect to the auto-generated Wi-Fi AP ("AutoConnectAP") to configure local network credentials.

### 4. Admin Setup
Navigate to the frontend application (e.g., `http://localhost/Edu_Trak_Pro/frontend/`):
- **Default Admin Login**:
  - **User**: `admin`
  - **Pass**: `admin123`
- *Mandatory: Immediately change the admin password upon your first login.*

---

## 🔌 API Reference

Our backend exposes a clean HTTP REST layer. Comprehensive documentation can be found in `API/API.md`.

| Method | Endpoint | Action | Parameters |
|:---|:---|:---|:---|
| `POST` | `/API/rfid-checkin.php` | Hardware tap ingestion | `uid` (RFID signature) |
| `POST` | `/API/login.php` | User authentication | `username`, `password`, `role` |
| `POST` | `/API/add-student.php` | Register a new card | `uid`, `name`, `roll` |
| `GET`  | `/API/fetch-attendance.php`| Retrieve logs | *(Optional filters)* |

---

## 👨‍💻 Team

Developed with passion by experts in embedded systems and web architecture.

<div align="center">
  <table>
    <tr>
      <td align="center">
        <a href="https://github.com/they-call-me-electronerd">
          <img src="https://github.com/they-call-me-electronerd.png" width="100px;" alt="Sakshyam Bastakoti" style="border-radius:50%"/>
          <br />
          <b>Sakshyam Bastakoti</b>
          <br />
          <small>Hardware Engineer</small>
        </a>
      </td>
      <td align="center">
        <a href="https://github.com/zenithkandel">
          <img src="https://github.com/zenithkandel.png" width="100px;" alt="Zenith Kandel" style="border-radius:50%"/>
          <br />
          <b>Zenith Kandel</b>
          <br />
          <small>Software Engineer</small>
        </a>
      </td>
    </tr>
  </table>
</div>

---

<div align="center">
  <sub>Built under the <a href="LICENSE">MIT License</a>. Open source, robust, and ready for deployment.</sub>
</div>
