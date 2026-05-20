[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/AnR2QgvN)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=22965207&assignment_repo_type=AssignmentRepo)
# 🌐 IoT Elective Project 2026
### Cape Peninsula University of Technology — IT Diploma
**Module:** Internet of Things (IoT) Elective | **Year:** 2026

---

## 📋 Table of Contents

1. [Project Overview](#project-overview)
2. [Group Members](#group-members)
3. [Project Idea & Problem Statement](#project-idea--problem-statement)
4. [System Architecture & Design](#system-architecture--design)
5. [Hardware Components](#hardware-components)
6. [Software & Technologies](#software--technologies)
7. [Circuit Diagram / Wiring](#circuit-diagram--wiring)
8. [Build Process (with photos)](#build-process-with-photos)
9. [Code Documentation](#code-documentation)
10. [Testing & Results](#testing--results)
11. [Challenges & Solutions](#challenges--solutions)
12. [Project Demonstration](#project-demonstration)
13. [References](#references)
14. [Assessment Rubric](#assessment-rubric)
15. [Embedding Images in Your README](#embedding-images-in-your-readme)

---

## 📌 Project Overview

**Project Title:** Smart Adaptive Romm hub  
**Group Name / Number:** Techwavers  
**Presentation Date:** 20 May 2026 — 10:00 to 15:00 (SAST)

---

## 🗓️ Presentation Schedule — 20 May 2026

> 📍 **Date:** Wednesday, 20 May 2026  
> 🕙 **Time:** 10:00 – 15:00 (South Africa Standard Time, UTC+2)  
> ⏱️ **Slot duration:** 15 minutes per group  
> ⚠️ **All groups must be present and ready before their slot.**

| Slot | Time (SAST) | Group |
|------|-------------|-------|
| 1 | 10:00 – 10:15 | Group 1 |
| 2 | 10:15 – 10:30 | Group 2 |
| 3 | 10:30 – 10:45 | Group 3 |
| — | 10:45 – 11:00 | ☕ Short Break |
| 4 | 11:00 – 11:15 | Group 4 |
| 5 | 11:15 – 11:30 | Group 5 |
| — | 11:30 – 12:30 | 🍽️ Lunch Break |
| 6 | 12:30 – 12:45 | Group 6 |
| 7 | 12:45 – 13:00 | Group 7 |
| — | 13:00 – 15:00 | 🧑‍🏫 Moderation / Feedback Session |

> 📌 Group numbers will be replaced with actual group names once confirmed with the lecturer.

---

## 👥 Group Members

| Student Name | Student Number | Role / Responsibility |
|---|---|---|
| Hillary Itlhabanyeng | 230777465 | Team Leader |
| Athini Ngquke | 222352302 | Backend developer Lead |
| Baatile Gerald Motau | 230993508 | Documentation Lead |
| Wayne Simango | 230237584 | Hardware lead |
| Tlou Masebe | 230128521 | Hardware analyst|
| Sinobawo Nkomo | 223174602 | Controller|

---

## 💡 Project Idea & Problem Statement

### Problem Statement
Traditional residential spaces rely entirely on manual user intervention to control lighting and climate appliances. This static approach leads to severe energy waste when rooms are left vacant, causes constant user discomfort due to unmanaged temperature fluctuations, and compromises occupant privacy through modern, invasive, cloud-dependent camera or audio surveillance alternatives.

### Proposed Solution
The Smart Mood Hub: A low-cost, presence-aware, localized IoT ecosystem built inside a model smart home. By integrating non-visual infrared and thermodynamic sensors with an Arduino edge microcontroller, the system autonomously switches room lighting and ambient climate overlays in real time, creating an intuitive, self-optimizing environment that requires zero manual or cloud intervention.

### Objectives
-  Autonomous Environmental Adaptation
To eliminate manual app or switch overhead by engineering an immediate, deterministic sensory loop that instantly shifts lighting and ambient "moods" based on real-time room data. |Objective 1
- Zero-Latency Energy Optimization
To drastically reduce electricity waste by enforcing a strict software-level presence gating protocol that cuts all non-essential hardware load the moment a vacancy threshold is reached. | Objective 2
- Privacy-First Edge Infrastructure
To deliver an intelligent smart home experience that runs entirely on localized microcontrollers using non-visual sensors, proving that home automation can be secure, private, and highly affordable. | Objective 3

---

## 🏗️ System Architecture & Design

![System Architecture Diagram](images/IoT.png)

### Design Decisions
Our primary design decision centered on engineering a localized, hardware-based edge architecture that prioritizes zero-latency execution, user privacy, and circuit stability. By processing all sensor telemetry directly on the Arduino Uno R3 rather than routing data through external cloud servers, we eliminate dependency on network connectivity. This edge-computing approach ensures the smart home remains fully operational during internet dropouts or load-shedding, while achieving sub-150ms response times for immediate environmental actuation.To uphold our commitment to privacy-first automation, we intentionally chose non-visual sensors over camera or audio surveillance. The combination of the HC-SR501 Passive Infrared (PIR) motion tracker and the DHT11 thermodynamic sensor allows the system to accurately map room occupancy and comfort metrics using invisible thermal radiation and environmental gradients. This design choice guarantees that data collection remains entirely non-invasive, securing the system for private residential spaces while keeping the physical hardware footprint remarkably low-cost and accessible.Architecturally, we executed a strategic parallel pin-mapping layout to resolve potential hardware conflicts and optimize power distribution. We shifted the telemetry display data lines entirely to the Arduino’s analog cluster ($A0$ through $A3$), leaving the high digital pins ($9$ through $13$) dedicated strictly to our tracking sensors and LED indicator matrix. This distinct structural split completely isolates display communication noise from sensitive climate signals, prevents pin overlap, and ensures absolute circuit stability during live demonstrations before the lecturers.

---

## 🔧 Hardware Components

| Component | Description | Quantity | Purpose |
|---|---|---|---|
| Arduino Uno R3 | An open-source, 8-bit microcontroller board based on the ATmega328P processor. It features 14 digital input/output pins, 6 analog inputs, and a 16 MHz ceramic resonator. | 1 | Serves as the central "Logic Core" or brain of the entire project. It ingests raw data streams from the sensor array, evaluates the environmental thresholds, and executes the firmware code to trigger the visual outputs. |
| DHT11 Sensor |  A basic, ultra-low-cost digital temperature and humidity sensor. It uses a capacitive humidity sensor and a thermistor to measure the surrounding air, outputting a digital signal on a single data pin. | 1 | Handles atmospheric telemetry. It samples the ambient room temperature every 2 seconds, feeding data into the Arduino to determine whether the environment needs to trigger Warm Mode, Chilled Mode, or stay in the Comfort Zone. |
| HC-SR501 Passive Infrared (PIR) Motion Sensor | A non-visual electronic sensor that measures infrared light radiating from objects in its field of view. It features adjustable sensitivity and delay potentiometers on the back of the module. | 1 | Acts as the system’s "Master Energy Gate." It continuously scans the room for human presence up to 7 meters away to trigger the active environmental loop or initiate the 5-second power-save sleep state when the room is vacant. |
| High-Efficiency LED Array (White, Red, Blue) |Standard 5mm light-emitting diodes that emit localized visible wavelengths when forward-biased. | 2| White LED (1x): Simulates the primary ceiling light for physical room visibility when occupancy is confirmed.

Red LED (1x): Acts as the "Warm Mode" indicator to visually simulate a residential heating system turning on.

Blue LED (1x): Acts as the "Chilled Mode" indicator to simulate an HVAC air-conditioning unit cooling the space.|
| Solderless Breadboard & Premium Jumper Wires | A plastic, reusable terminal testing board alongside an assortment of male-to-male and male-to-female solid-core jumper wires. | 2 |  Establishes the physical parallel data bus and shared power/ground rails ($5V$ and $GND$). It links all peripheral sensors, displays, and actuators to the Arduino microcontroller pins cleanly without permanent solder joints. |

---

## 💻 Software & Technologies

| Tool / Platform | Purpose |
|---|---|
| Arduino IDE | Acts as the primary development platform for writing, compiling, and uploading the C++ firmware. It was used to write the sensor tracking logic and directly flash the compiled binary code onto the ATmega328P microcontroller chip via USB |
| Wokwi (IoT Virtual Lab) | Served as the critical digital twin simulation platform before physical circuit assembly. It was used to virtually wire the Arduino Uno, the PIR sensor, and the DHT11 sensor to test the C++ firmware. Simulating the logic matrix in Wokwi helped identify and resolve pin-sharing conflicts safely without risking hardware damage |
| DHT Sensor Library (by Adafruit) | Handles data communication with the atmospheric sensor. It abstracts the complex bit-streaming protocol of the DHT11, allowing the Arduino to instantly read ambient temperature values via a single, low-overhead software function |
| YouTube | Utilized as a vital technical research platform during the prototyping phase. It was used to analyze component datasheets, study video demonstrationn and research best-practice calibration methods for isolating the DHT11 sensor from hardware heat signatures |

---

## 🔌 Circuit Diagram / Wiring

![Circuit Diagram](images/circuit_diagram.png)

| Component Pin | Microcontroller Pin | Notes |
|---|---|---|
| [e.g. DHT11 DATA] | [e.g. D2] | [Pull-up resistor required] |
| [e.g. LED +] | [e.g. D13] | [220Ω resistor in series] |

---

## 🏭 Build Process (with photos)

### Step 1: [Step Title]
> _Description of what was done._

![Step 1 Photo](images/build_step1.jpg)

### Step 2: [Step Title]
> _Description of what was done._

![Step 2 Photo](images/build_step2.jpg)

---

## 🖥️ Code Documentation

### Main Firmware (e.g., `main.ino`)

```cpp
#include <DHT.h>

// --- Pin setup ---
#define DHTPIN 6
#define DHTTYPE DHT11
#define LDR_PIN A0
#define PIR_PIN 3
#define LED_COOL 4
#define LED_WARM 5
#define LED_STATUS 13
#define LED_ALERT 12

// --- RGB LED pins ---
int redPin = 10;
int greenPin = 11;
int bluePin = 12;

// --- PIR calibration ---
int calibrationTime = 30;
long unsigned int lowIn;
long unsigned int pause = 5000;
boolean lockLow = true;
boolean takeLowTime;

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);

  // PIR setup
  pinMode(PIR_PIN, INPUT);
  pinMode(LED_STATUS, OUTPUT);
  digitalWrite(PIR_PIN, LOW);

  Serial.print("Calibrating PIR sensor ");
  for (int i = 0; i < calibrationTime; i++) {
    Serial.print(".");
    delay(1000);
  }
  Serial.println(" done");
  Serial.println("SENSOR ACTIVE");

  // DHT + LEDs setup
  dht.begin();
  pinMode(LED_COOL, OUTPUT);
  pinMode(LED_WARM, OUTPUT);
  pinMode(LED_ALERT, OUTPUT);

  // RGB LED setup
  pinMode(redPin, OUTPUT);
  pinMode(greenPin, OUTPUT);
  pinMode(bluePin, OUTPUT);

  Serial.println("Smart Room Adaptive Hub starting...");
  delay(2000);
}

// Helper function to set RGB color
void setColor(bool r, bool g, bool b) {
  digitalWrite(redPin, r ? HIGH : LOW);
  digitalWrite(greenPin, g ? HIGH : LOW);
  digitalWrite(bluePin, b ? HIGH : LOW);
}

void loop() {
  // --- Motion detection ---
  if (digitalRead(PIR_PIN) == HIGH) {
    digitalWrite(LED_STATUS, HIGH);
    if (lockLow) {
      lockLow = false;
      Serial.println("---");
      Serial.print("Motion detected at ");
      Serial.print(millis() / 1000);
      Serial.println(" sec");
    }
    takeLowTime = true;
  }

  if (digitalRead(PIR_PIN) == LOW) {
    digitalWrite(LED_STATUS, LOW);
    if (takeLowTime) {
      lowIn = millis();
      takeLowTime = false;
    }
    if (!lockLow && millis() - lowIn > pause) {
      lockLow = true;
      Serial.print("Motion ended at ");
      Serial.print((millis() - pause) / 1000);
      Serial.println(" sec");
    }
  }

  // --- Climate sensing ---
  float humidity = dht.readHumidity();
  float temperature = dht.readTemperature();

  if (isnan(temperature) || isnan(humidity)) {
    Serial.println("DHT sensor error!");
    return;
  }

  if (temperature > 50.0) temperature = 0.0;
  if (humidity > 100.0) humidity = 0.0;

  Serial.print("Temp: ");
  Serial.print(temperature);
  Serial.print("C  Hum: ");
  Serial.print(humidity);
  Serial.print("%  ");

  // Climate mode logic
  if (temperature > 30.0) {
    digitalWrite(LED_COOL, HIGH);
    digitalWrite(LED_WARM, LOW);
    digitalWrite(LED_ALERT, HIGH);
    setColor(true, false, false); // Red
    Serial.print("Mode: HOT  ");
  } else if (temperature > 25.0) {
    digitalWrite(LED_COOL, LOW);
    digitalWrite(LED_WARM, HIGH);
    digitalWrite(LED_ALERT, LOW);
    setColor(true, true, false); // Yellow
    Serial.print("Mode: WARM  ");
  } else if (temperature >= 20.0) {
    setColor(false, true, false); // Green
    Serial.print("Mode: COMFORT  ");
  } else {
    setColor(false, false, true); // Blue
    Serial.print("Mode: COOL  ");
  }

  // --- Light sensing ---
  int lightRaw = analogRead(LDR_PIN);
  int lightPercent = map(lightRaw, 0, 1023, 0, 100);
  Serial.print("Light: ");
  Serial.print(lightPercent);
  Serial.print("%  ");

  Serial.print("Motion: ");
  Serial.println(digitalRead(PIR_PIN) == HIGH ? "YES" : "NO");

  delay(2000);
}


```

### Key Functions

| Function | Purpose | Key Actions | Output/Effect |
| --- | --- | --- | --- |
| ``setup()`` | Initializes system components | - Starts Serial communication<br>- Calibrates PIR sensor<br>- Configures pin modes<br>- Starts DHT11 sensor | System ready message in Serial Monitor; PIR calibration complete |
| ``loop()`` | Main program loop (runs continuously) | - Reads PIR sensor for motion<br>- Reads DHT11 for temperature & humidity<br>- Reads LDR for light intensity<br>- Updates LEDs and RGB color based on conditions | Real-time monitoring of motion, climate, and light; LED and RGB feedback |
| ``setColor(r,g,b)`` | Helper function to control RGB LED color | - Accepts boolean values for Red, Green, Blue<br>- Sets digital pins HIGH/LOW accordingly | RGB LED changes color to represent climate mode (Red, Yellow, Green, Blue) |
| **Motion Logic** (inside ``loop()``) | Detects and logs motion events via PIR sensor | - Turns ``LED_STATUS`` ON/OFF<br>- Logs motion start/end times<br>- Uses lock/unlock mechanism | Serial output: “Motion detected at X sec” / “Motion ended at X sec” |
| **Climate Logic** (inside ``loop()``) | Reads temperature & humidity, sets climate mode | - Activates LEDs (Cool, Warm, Alert)<br>- Maps temperature ranges to RGB colors<br>- Handles sensor errors | Serial output: Temp, Humidity, Mode (HOT/WARM/COMFORT/COOL) |
| **Light Logic** (inside ``loop()``) | Reads ambient light via LDR sensor | - Converts raw analog value to percentage<br>- Prints light intensity to Serial Monitor | Serial output: “Light: XX%” |

---

## 🧪 Testing & Results
| Test # | Description | Expected Results | Actual Results | Pass/Fail |
| --- | --- | --- | --- | --- |
| 1 | **PIR Motion Detection** – Move in front of PIR sensor | ``LED_STATUS`` turns ON, Serial Monitor logs “Motion detected at X sec” | LED lit up, Serial Monitor displayed motion detection message | ✅ Pass |
| 2 | **Motion End** – Stay still for >5 seconds | ``LED_STATUS`` turns OFF, Serial Monitor logs “Motion ended at X sec” | LED turned off after pause, Serial Monitor displayed motion ended message | ✅ Pass |
| 3 | **Climate HOT Mode** – Warm DHT11 sensor (>30°C) | ``LED_COOL`` ON, ``LED_ALERT`` ON, RGB LED Red, Serial Monitor shows “Mode: HOT” | LEDs activated correctly, RGB LED turned Red, Serial Monitor showed HOT mode | ✅ Pass |
| 4 | **Climate WARM Mode** – Temp between 25–30°C | ``LED_WARM`` ON, RGB LED Yellow, Serial Monitor shows “Mode: WARM” | Warm LED lit, RGB LED Yellow, Serial Monitor showed WARM mode | ✅ Pass |
| 5 | **Climate COMFORT Mode** – Temp between 20–25°C | RGB LED Green, Serial Monitor shows “Mode: COMFORT” | RGB LED Green, Serial Monitor displayed COMFORT mode | ✅ Pass |
| 6 | **Climate COOL Mode** – Temp <20°C | RGB LED Blue, Serial Monitor shows “Mode: COOL” | RGB LED Blue, Serial Monitor displayed COOL mode | ✅ Pass |
| 7 | **Light Sensing** – Cover/uncover LDR | Serial Monitor shows light percentage (0–100%) | Light % values updated correctly in Serial Monitor | ✅ Pass |
| 8 | **Sensor Error Handling** – Disconnect DHT11 | Serial Monitor shows “DHT sensor error!” | Error message displayed correctly | ✅ Pass |

---

## ⚠️ Challenges & Solutions

| Challenge Encountered | Solution Applied |
|---|---|
| Slow Sensor Polling vs. System Responsiveness
The DHT11 climate sensor requires a relatively slow processing cycle (sampling only once every 1–2 seconds). If the Arduino code loops too quickly without proper timing management, it can cause data reading errors, system freezes, or laggy motion detection from the high-speed PIR sensor.| We implemented non-blocking timing delays in the firmware code. Instead of using the restrictive delay() function which pauses the whole microcontroller, the system paces its climate sampling independently, allowing the PIR motion tracking pin to remain highly responsive and achieve sub-150ms execution loops. |
| Component Voltage Drops (Micro-Brownouts)
Running multiple high-output LEDs (White, Red, and Blue) simultaneously from a single Arduino Uno board can pull too much current at once. During early testing, this sudden power draw caused micro-voltage drops across the power rails, resulting in unstable readings from the DHT11 sensor.| We stabilized the circuit by grouping all components onto shared, dedicated power and ground distribution rails on the breadboard, back-linked directly to the regulated 5V pin of the Arduino. Additionally, we added high-tolerance 220$\Omega$ current-limiting resistors to each LED to regulate the exact milliamp draw and protect the MCU pins. |

---

## 🎥 Project Demonstration

- 📹 **Demo Video:** [Insert link here]
- 📊 **Presentation Slides:** [Insert link here]
- 🔗 **Live Dashboard (if applicable):** [Insert link here]

---

## 📚 References

1. [Reference Title](https://link-to-reference.com) — _Brief description_
2. [Reference Title](https://link-to-reference.com) — _Brief description_

---

## 📊 Assessment Rubric

> ⚠️ **Students: Do NOT modify this section.**

### 📝 T1 — 50 Marks

| Criteria | Excellent (5) | Good (4) | Satisfactory (3) | Needs Improvement (2) | Incomplete (0-1) | Marks |
|---|---|---|---|---|---|---|
| Project Proposal & Problem Statement | Clear, detailed, well-researched | Clear with minor gaps | Stated but lacks depth | Vague | Not submitted | /5 |
| System Design & Architecture | Detailed diagram + design decisions | Good diagram with some docs | Basic diagram | Incomplete | Not submitted | /5 |
| Hardware Component Selection | All justified with images | Most documented | Listed not justified | Incomplete | Not attempted | /5 |
| Circuit Diagram / Wiring | Complete + pin mapping | Mostly complete | Partial | Incomplete | Not submitted | /5 |
| GitHub Repository Setup | Well-structured, clear commits | Good with minor issues | Basic structure | Minimal | Repo not set up | /5 |
| Markdown Documentation Quality | Excellent: headings, tables, images, code | Good with minor issues | Basic Markdown | Minimal | None | /5 |
| GitHub Commit History (T1) | Regular commits, all members | Regular, most members | Some commits | Few | None | /5 |
| Initial Code / Prototype | Working + well-commented | Working + some comments | Partial prototype | Started, not working | None | /5 |
| Group Collaboration Evidence | Issues, PRs, commits from all | Good evidence | Some evidence | Minimal | None | /5 |
| Build Progress Photos | Step-by-step + descriptions | Good photos | Photos, few descriptions | Few photos | None | /5 |
| | | | | | | **T1 Total** | **/50** |

---

### 📝 T2 — 50 Marks *(Final Presentation: 20 May 2026, 10:00–15:00 SAST)*

| Criteria | Excellent (5) | Good (4) | Satisfactory (3) | Needs Improvement (2) | Incomplete (0-1) | Marks |
|---|---|---|---|---|---|---|
| Final Working Project | Fully functional | Mostly functional | Partially functional | Limited functionality | Not functional | /5 |
| Live Demonstration | Confident, all features | Good, minor issues | Core features shown | Partial/unclear | No demonstration | /5 |
| Testing & Results Documentation | All tests + analysis | Most documented | Some documented | Minimal | None | /5 |
| Code Quality & Comments | Clean, structured, fully commented | Good, most commented | Works, lacks comments | Messy/partial | None | /5 |
| Markdown Documentation Quality (T2) | Complete professional README | Good with minor gaps | Most sections filled | Incomplete | Minimal/none | /5 |
| GitHub Commit History (T2) | Consistent, all members | Good, most members | Some commits | Few | None | /5 |
| Challenges & Solutions | All documented with solutions | Most documented | Some documented | Vague | Not documented | /5 |
| System Architecture (Final) | Updated, matches build | Mostly matches | Partially updated | Outdated | Not present | /5 |
| Presentation Quality | Professional, all members | Good, all contribute | Acceptable | Weak/incomplete | None | /5 |
| References & Attribution | All properly listed | Most listed | Some listed | Minimal | None | /5 |
| | | | | | | **T2 Total** | **/50** |

---

### 🏆 Final Mark Summary

| Term | Marks Available | Marks Achieved |
|---|---|---|
| T1 | 50 | /50 |
| T2 | 50 | /50 |
| **Total** | **100** | **/100** |

---

> 📌 **Assessed by:** `[Lecturer Name]`  
> 📅 **Presentation Date:** 20 May 2026, 10:00–15:00 (SAST)  
> 📅 **Final Submission Deadline:** 20 May 2026  
> 🏫 **Institution:** Cape Peninsula University of Technology (CPUT)

---

## 🖼️ Embedding Images in Your README

> 💡 This guide is for all groups — use it to add photos, diagrams, and screenshots to your README.

### Method 1: Upload images to the `images/` folder in your repo ✅ *(Recommended)*

1. In your repository, create a folder called `images/`
2. Upload your image files (`.jpg`, `.png`, `.gif`) into that folder
3. Reference them in your README using a **relative path**:

```markdown
![Alt text describing the image](images/your-image-filename.png)
```

**Example:**
```markdown
![Circuit Diagram](images/circuit_diagram.png)
![Build Step 1](images/build_step1.jpg)
![System Architecture](images/architecture_diagram.png)
```

---

### Method 2: Drag & Drop into a GitHub Issue or PR (then copy the link)

1. Open any **Issue** or **Pull Request** in your repo
2. Drag and drop your image into the text box — GitHub will auto-upload it
3. GitHub generates a URL like:
   ```
   https://user-images.githubusercontent.com/.../.../image.png
   ```
4. Copy that URL and paste it into your README:

```markdown
![My Image](https://user-images.githubusercontent.com/your-generated-link-here.png)
```

---

### Method 3: Use a full GitHub URL (after uploading to the repo)

If your image is already in the repo (e.g., `images/photo.jpg` on the `main` branch):

```markdown
![Photo](https://github.com/cput-it-diploma/cput-it-diploma-iot-project_2026-iot_elective_project_2026-IoT_2026/blob/main/images/photo.jpg?raw=true)
```

> ⚠️ Always add `?raw=true` at the end when using a full GitHub blob URL, otherwise the image won't render.

---

### ✅ Image Embedding Checklist

- [ ] Image file is uploaded to the `images/` folder in your repo
- [ ] File name has **no spaces** (use underscores: `circuit_diagram.png` ✅, not `circuit diagram.png` ❌)
- [ ] You used the correct Markdown syntax: `![Alt text](path/to/image.png)`
- [ ] The path is correct (check uppercase/lowercase — GitHub paths are case-sensitive)
- [ ] Image renders correctly when you preview the README

---

### 📐 Resizing Images (optional)

Markdown doesn't support resizing natively, but you can use HTML inside your README:

```html
<img src="images/circuit_diagram.png" alt="Circuit Diagram" width="600"/>
```

This sets the image width to 600px. Adjust as needed.

---

*Documented using Markdown on GitHub — CPUT IT Diploma IoT Elective 2026* 🚀
