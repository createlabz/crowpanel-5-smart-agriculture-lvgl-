# 🌾 CrowPanel 5.0 – Smart Agriculture Dashboard (LVGL)

<p align="center">
  <img src="https://github.com/createlabz/website_createlabz_picsv2/blob/main/3.5spi.jpg?raw=true" alt="CrowPanel 5.0 Dashboard Preview" width="400"/>
</p>

<p align="center">
  <strong>A fully working LVGL 8.3.10 + LovyanGFX setup for:</strong>
</p>

<p align="center">
  🖥 <strong>CrowPanel ESP32 Display 5.0" V3 (800×480 RGB)</strong><br>
  ⚡ <strong>ESP32-S3-WROOM-1-N4R8 (4MB Flash / 8MB PSRAM)</strong>
</p>

---

## 📋 Table of Contents

- [🛠 Software Setup Guide (Arduino IDE)](#-software-setup-guide-arduino-ide)
- [📦 Required Libraries](#-required-libraries)
- [⚙️ Board Configuration](#️-board-configuration)
- [📁 Project Structure](#-project-structure)
- [🚀 Features in This Demo](#-features-in-this-demo)
- [🧠 Common Problems & Fixes](#-common-problems--fixes)
- [🌱 Want to Explore?](#-want-to-explore)
- [📜 License](#-license)

---

## 🛠 Software Setup Guide (Arduino IDE)

### ✅ Arduino IDE

| Recommendation | Version |
|----------------|---------|
| **Recommended** | Arduino IDE 2.x |
| **Tested With** | 2.3.7 |

---

### ✅ Install ESP32 Board Package

**Step 1 — Add Board Manager URL**

Go to **File → Preferences**

In the **"Additional Boards Manager URLs"** field, add: https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json


Click **OK** to save.

---

**Step 2 — Install ESP32 Package**

Go to **Tools → Board → Boards Manager**

In the Boards Manager window that opens:
- Type `esp32` in the search box
- Look for **"esp32 by Espressif Systems"**
- Click **Install** (version 3.3.7 recommended)

Wait for the installation to complete.

---

### 🎯 Recommended Core Version

| Version | Status |
|---------|--------|
| **3.3.7** | ✅ Tested & Confirmed Working |
| **2.0.14** | ✅ Alternative Stable |

> ⚠ **WARNING:** Do NOT randomly mix versions. LVGL + LovyanGFX are sensitive to core versions.

---

## 📦 Required Libraries

Go to **Sketch → Include Library → Manage Libraries**

This will open the Library Manager. Search for and install each of the following:

| Library | How to Find | Tested Version | Notes |
|---------|-------------|----------------|-------|
| **LovyanGFX** | Type "LovyanGFX" in search | 1.2.19 | Graphics driver for RGB panels |
| **LVGL** | Type "LVGL" in search | **8.3.10** | ⚠ DO NOT use LVGL 9.x |

> ⚠ **CRITICAL:** This project is built specifically for **LVGL 8.3.x**. Version 9.x will NOT work.

---

## ⚙️ Board Configuration

### Select Board

Go to **Tools → Board → ESP32 Arduino → ESP32S3 Dev Module**

---

### 🔧 Core Settings

Go to **Tools** and set the following:

| Setting | Value |
|---------|-------|
| **USB CDC On Boot** | Enabled |
| **CPU Frequency** | 240MHz (WiFi) |
| **Core Debug Level** | None |

---

### 💾 Flash Settings (VERY IMPORTANT)

Go to **Tools** and set the following:

| Setting | Value |
|---------|-------|
| **Flash Mode** | QIO 80MHz |
| **Flash Size** | 4MB (32Mb) |
| **Partition Scheme** | Huge APP (3MB No OTA / 1MB SPIFFS) |

> ⚠ If incorrect, you will see: `Detected size(4096k) smaller than the size in the binary image header(16384k)`

---

### 🧠 PSRAM Settings (REQUIRED)

Go to **Tools → PSRAM** and set:

| Setting | Value |
|---------|-------|
| **PSRAM** | **OPI PSRAM** |

> ⚠ **REQUIRED** for 800×480 LVGL projects. Without PSRAM → crash / freeze / bootloop.

---

### 🔌 USB Settings

Go to **Tools** and set the following:

| Setting | Value |
|---------|-------|
| **USB Mode** | Hardware CDC and JTAG |
| **Upload Mode** | USB-OTG CDC (TinyUSB) |
| **Upload Speed** | 921600 |

---

### 🧹 First Upload Recommendation

Go to **Tools → Erase All Flash Before Sketch Upload** and set:

| Setting | Value |
|---------|-------|
| **Erase All Flash Before Sketch Upload** | **Enabled** |

After successful upload, you may disable it.

---

## 📁 Project Structure

Your Arduino sketch folder MUST look like this:

final-crowpanel/
│
├── final-crowpanel.ino
├── gfx_conf.h
└── lv_conf.h
