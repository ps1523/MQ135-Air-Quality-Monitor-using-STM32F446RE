# MQ135-Air-Quality-Monitor-using-STM32F446RE

# MQ135 Air Quality Monitor using STM32F446RE

This project demonstrates how to interface the **MQ135 Air Quality Sensor** with the **STM32F446RE (Nucleo Board)** to monitor air quality parameters like **CO2, NH3, Alcohol, and Smoke levels**. The analog signal from the MQ135 is processed through the STM32's ADC and displayed via **UART (Minicom/TeraTerm)**.

---

## 📂 Project Folder Structure



ps1523/-MQ135-Air-Quality-Monitor-using-STM32F446RE/
├── Core/
│   ├── Inc/               # Header files
│   └── Src/               # Source files (main.c, stm32f4xx_it.c, etc.)
├── Drivers/                # STM32 HAL Drivers
├── .ioc                    # STM32CubeMX Configuration File
├── Makefile                # Project Build Makefile (optional)
├── README.md                # This Documentation
└── ...                     # Other CubeIDE config files


---

## 🛠️ Components Required

| Component                    | Quantity |
|-------------------------------|----------|
| STM32F446RE Nucleo Board       | 1        |
| MQ135 Air Quality Sensor Module| 1        |
| Jumper Wires                   | As needed|
| USB Cable                      | 1        |
| Breadboard (Optional)          | 1        |
| PC with STM32CubeIDE & Minicom | 1        |

---

## 🔌 Circuit Connections

| MQ135 Pin | STM32F446RE Pin | Description              |
|-----------|-----------------|--------------------------|
| VCC       | 3.3V             | Power Supply              |
| GND       | GND              | Ground                    |
| AOUT      | PA0              | Analog Output (ADC Input) |

---

## ⚙️ STM32CubeMX Configuration Steps

1. **ADC1 Configuration**:
   - Channel: IN0 (PA0)
   - Mode: Continuous Conversion
   - Resolution: 12-bit
2. **USART2 Configuration**:
   - Baud Rate: 9600
   - TX Pin: PA2
   - RX Pin: PA3 (optional)
3. **Clock Configuration**: Default settings.
4. Generate code and open in **STM32CubeIDE**.

---

## 📝 Code Workflow (main.c)

1. Initialize HAL, System Clock, GPIO, ADC, UART.
2. Start ADC in Polling Mode.
3. Read ADC value and convert it to voltage:


Voltage = (ADC_Value / 4095.0) * 3.3V

4. Determine air quality level based on voltage ranges.
5. Print ADC Value, Voltage, and Air Quality Status via UART.
6. Delay and repeat.

### Example UART Output:

ADC: 152 | Voltage: 1.22 V | GOOD AIR QUALITY | LOW CO2
ADC: 146 | Voltage: 1.17 V | MODERATE AIR QUALITY | MODERATE CO2
ADC: 220 | Voltage: 1.77 V | BAD AIR QUALITY | HIGH CO2


---

## 🧪 Calibration Note

- MQ135 is sensitive to environmental conditions.
- This project gives a **relative indication** (Good, Moderate, Bad Air Quality).
- For accurate ppm values, proper calibration with Rs/RL resistance formulas is required.

---

## 🖥️ UART Output via Minicom/TeraTerm

1. Connect USB to Nucleo Board.
2. Open Minicom or TeraTerm with **9600 Baud Rate**.
3. Observe live ADC readings, voltages, and air quality status.

---

## 🚀 How to Run

1. Connect MQ135 sensor to STM32 as per circuit diagram.
2. Flash the code to the STM32F446RE using STM32CubeIDE.
3. Open Minicom/TeraTerm at 9600 baud.
4. Observe real-time air quality readings.

---

## 📚 References

- [MQ135 Datasheet](https://www.winsen-sensor.com/d/files/PDF/MQ135.pdf)
- [STM32F446RE Nucleo Documentation](https://www.st.com/en/microcontrollers-microprocessors/stm32f446re.html)
- [STM32CubeIDE Documentation](https://www.st.com/en/development-tools/stm32cubeide.html)

---

## 📝 Future Enhancements

- Accurate ppm calculation using Rs/RL formulas.
- OLED or LCD display for standalone display.
- Add buzzer/alarm for high CO2 levels.
- IoT Data Logging (Cloud Integration).

---

## 📷 Sample Output Screenshot

*(You can upload a UART output screenshot here for reference.)*

---

## ✍️ Author

**PS1523**

---

git pull
ps1523/-MQ135-Air-Quality-Monitor-using-STM32F446RE  
git add README.md
git commit -m "Added detailed README for MQ135 Air Quality Monitor"
git push

