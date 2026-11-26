# 🛩️ ROTAX912_DIGITAL_TWIN — Módulo de Adquisición de Datos (DAQ / FADEC)

Este repositorio contiene el diseño electrónico (esquemáticos, layout de PCB, lista de materiales y documentación técnica) del **Módulo de Adquisición de Datos de Sensores** orientado al desarrollo de un **Gemelo Digital (Digital Twin)** y monitoreo tipo **FADEC** para motores aeronáuticos **Rotax 912**.

---

## 📐 Descripción del Proyecto

El objetivo principal es diseñar y fabricar una placa de circuito impreso (**PCB**) capaz de acondicionar, digitalizar y transmitir en tiempo real las variables físicas críticas del motor **Rotax 912**. Los datos adquiridos alimentarán el modelo de gemelo digital para diagnóstico, telemetría y análisis de rendimiento en banco de ensayos o aeronave.

### Funcionalidades Principales:
* **Acondicionamiento de Señales:** Filtrado analógico, protección contra sobretensiones/transitorios y adaptación de impedancias para sensores aeronáuticos estándar.
* **Adquisición Multicanal:** Lectura simultánea de temperaturas, presiones, régimen de giro y parámetros eléctricos.
* **Comunicaciones:** Interfaz robusta para envío de tramas de datos hacia la unidad de procesamiento del Gemelo Digital (CAN Bus / UART / USB).
* **Alimentación Aeronáutica:** Etapa de regulación con protección contra inversión de polaridad y picos de tensión propios del bus de 12V/14V.

---

## ⚙️ Arquitectura de Hardware y Sensores Soportados

*(Ajustar los canales y modelos específicos según el diseño final del esquemático)*

| Variable / Parámetro | Tipo de Sensor Típico (Rotax 912) | Acondicionamiento / Interfaz |
| :--- | :--- | :--- |
| **RPM (Régimen de Motor)** | Captor magnético / Trigger coil | Comparador / Schmitt Trigger + Optoacoplador |
| **EGT (Temp. Gases de Escape)** | Termocuplas Tipo K (x4 cilindros) | Amplificador compensado (ej. MAX31855 / AD8495) |
| **CHT (Temp. Cabeza de Cilindro)** | NTC / Termistor o Termocupla | Divisor resistivo de precisión + Filtro RC |
| **Temperatura de Aceite** | Sensor resistivo (NTC VDO / Rotax) | Puente / Divisor + Buffer operacional |
| **Presión de Aceite** | Transductor resistivo o 4-20 mA / 0-5V | Amplificador diferencial / Conversión I-V |
| **MAP (Presión de Admisión)** | Sensor piezorresistivo absoluto (0-5V) | Filtro pasa-bajos anti-aliasing |
| **Flujo / Presión de Combustible** | Sensor de efecto Hall / Transductor | Entrada digital por interrupción / Canal ADC |
| **Tensión de Bus / Batería** | Divisor de tensión aislado | Protección TVS + Filtro |

---

## 📂 Estructura del Repositorio

```text
ROTAX912_DIGITAL_TWIN/
├── hardware/               # Archivos fuente CAD (KiCad / Altium) - Esquemáticos y PCB
├── fabrication/            # Archivos Gerber, Drill, Pick & Place y planos de ensamblaje
├── bom/                    # Lista de materiales (Bill of Materials) y hojas de datos
├── firmware/               # Código embebido de prueba y calibración del MCU (si aplica)
├── docs/                   # Diagramas en bloques, pinout de conectores y notas de diseño
└── README.md               # Documentación principal del proyecto