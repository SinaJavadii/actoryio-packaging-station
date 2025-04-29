# Automated Packaging and Sorting Line with Quality Control – Factory IO Project

This project simulates an automated packaging and sorting factory line using **Factory IO**. It features the classification and segregation of plastic and metal doors, along with detection and handling of defective products (Bad Boxes).

---

## 🏭 Scenario Description

The factory produces two types of products:
1. **Plastic doors (Blue Lid)**
2. **Metal doors (Metal Lid)**

Additionally, defective products (**Bad Boxes**, represented as cardboard boxes) are identified and separated early in the production line to improve operational efficiency.

---

## 🔧 System Functionality

The factory layout includes a **main conveyor line** supported by pushers and multiple sensors:

### 1. **Bad Box Removal**
- **Sensor:** Retroreflective sensor positioned at a specific height.
- **Behavior:**
  - Normal condition: Sensor output = 1
  - When a Bad Box passes: Sensor output = 0 (inverted using a NOT gate).
- **Logic:**
  - An `SR Latch` stores the detection signal.
  - A `TON` (Timer ON Delay) delays the pusher activation to match the box's travel time from sensor to pusher.
  - A second `TON` returns the pusher to its original position after pushing the box onto a curved side conveyor.

### 2. **Metal Lid Sorting**
- **Sensor:** Vision sensor capable of detecting metallic objects.
- **Behavior:**
  - Normal condition: Sensor output = 0
  - Detection of metal: Sensor output = 1
- **Logic:** Similar to Bad Box handling but with adjusted timing based on the speed of the conveyor.

### 3. **Plastic Doors (Blue Lid) Handling**
- After defective and metallic products are separated, the remaining products (Blue Lids) continue on the main conveyor to the end.

---

## 🔢 Control Logic (PLC)

- **CTU Counters**: Used to count the number of each detected product type.
- **INT Outputs**: Display counts via CONTROL I/O.
- **Reset Functionality**: Toggle switches are provided to reset each counter.

### Additional Vision Sensor
A secondary Vision sensor at the end of the conveyor counts the Blue Lids to ensure accurate tracking.

---

## ▶️ Startup Procedure

- A **toggle switch** (two-position switch: 0/1) is installed next to the main conveyor.
- Turning it on (position 1) starts the factory operations.

---

## 📁 Project Structure

- `CA`: Factory IO simulation file containing the complete 3D environment and logic.
- `Diagram1`: Block diagram illustrating the system's structure and data flow.
- `Documentation`: PDF file containing detailed project reports, explanations, and technical notes.
- `README.md`: This file explaining the project setup, logic, and structure.

---

## 💡 Important Notes

- Pushers' activation timing must be fine-tuned based on conveyor speed and object size.
- Proper placement of sensors is critical for reliable and accurate detection.
- The use of timers (`TON`) and `SR Latch` ensures synchronization between detection and physical actuation.

---

## 🔗 License

This project is for educational purposes. Feel free to use, modify, or improve it with appropriate credit.

---

If you encounter any issues or have suggestions for improvements, feel free to open an issue or pull request!
