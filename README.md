# actoryio-packaging-station
A Factory IO project for automated sorting and packaging.
# Automated Packaging and Sorting Line with Quality Control – Factory IO Project

This project simulates an automated packaging and sorting factory line using **Factory IO**. It features the classification and segregation of plastic and metal doors, along with detection and handling of defective products (Bad Boxes).

---

## 🏭 Scenario Description

The factory produces two types of products:
1. **Plastic doors (Blue Lid)**
2. **Metal doors (Metal Lid)**

Bad products (**Bad Boxes**, represented as cardboard boxes) are detected and removed at the beginning of the conveyor line to improve efficiency.

---

## 🔧 System Functionality

The factory consists of a **main conveyor line** equipped with two types of pushers and sensors:

### 1. **Bad Box Removal**
- **Sensor:** Retroreflective sensor mounted at a fixed height.
- **Logic:**
  - Normal state: Signal = 1
  - Detection (Box passes): Signal = 0 → Inverted → Stored in an `SR Latch`
- **Delay Handling:** Uses a `TON` (Timer ON Delay) to delay the activation of the pusher until the box reaches it.
- **Pushback Control:** Another `TON` returns the pusher to its original position after pushing.

### 2. **Metal Lid Sorting**
- **Sensor:** Vision sensor that sends a signal if a metal object is detected.
- **Logic:**
  - Normal state: Signal = 0
  - Metal detected: Signal = 1 → Triggers the sorting logic.
- The same pusher logic (with timing adjustments) as Bad Box removal is used.

### 3. **Blue Lid Handling**
- Remaining objects (after removal of Bad Boxes and Metal Lids) are assumed to be plastic doors (Blue Lid).
- These are sent to the end of the main conveyor.

### Conveyor System
- Uses **Curved Belt Conveyors** to direct pushed items to side lines.

---

## 🔢 Control Logic (PLC)

- **CTU Counters**: Count the number of detections for each product type.
- **INT Outputs**: Show counts via CONTROL I/O.
- **Reset Switches**: Connected to each CTU to allow reset functionality.

### Additional Vision Sensor
A secondary Vision sensor at the end of the conveyor counts Blue Lids for more accurate results.

---

## ▶️ Startup Procedure

- A **toggle switch** (0/1) is provided next to the conveyor.
- Turning it on starts the factory operation.

---

## 📁 Project Structure

- `.factoryio` file: The complete simulation model.
- `.pdf` or `.docx`: Full project documentation.
- `README.md`: This file.

---

## 💡 Notes

- Timing of pushers must be adjusted based on conveyor speed.
- Sensor positioning is critical for accurate detection.
- Realistic logic design improves performance and simulation reliability.

---

## 🔗 License

This project is intended for educational purposes. Feel free to fork, use, or improve it with credit.

---

If you need help with automation, control logic, or simulation, feel free to open an issue or reach out!
