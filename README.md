# Microcontroller-based Robotic Car

An intelligent robotic car system using STM32 microcontrollers and OpenMV vision modules for autonomous navigation and visual recognition.

## Tasks

- **Task 1 - Line Following**: Sensor-based line tracking
- **Task 2 - Labyrinth**: Autonomous maze navigation
- **Task 3 - Comprehensive**: Multi-task, including line following, ball kicking, and obstacle avoidance
- **Task 4 - AprilTag Tracking**: Visual marker detection and tracking

## Hardware

### Controllers
- **STM32F103** (ARM Cortex-M3, 72MHz) - Sensor processing and motor control
- **STM32H743** (ARM Cortex-M7, 480MHz) - Vision processing with OpenMV
- **LongQiu** control board with three-wheel omnidirectional chassis

### Sensors & Peripherals
- **HC-SR04** ultrasonic sensors (2x) - Distance measurement
- **Photoelectric sensors** (4x) - Line detection array
- **OpenMV camera** - RGB565 vision processing (160x120)
- **Rotary encoders** (3x) - Motor feedback via Timer 12/13/14
- **0.96" OLED display** (I2C) - Status visualization
- **SPI LCD** (80x60) - Real-time image display

### Motor Control
- **DC motors** (3x) with DRV8701 driver
- PWM control at 10kHz via Timer 4
- Speed range: ±6000 PWM units

### Communication Protocols
- **UART** (115200 baud) - Inter-board communication
- **I2C** (software) - OLED display
- **SPI** (software) - LCD display

## Project Structure

```
microcontroller-based-robotic-car/
├── Task1 Line_Following/              # Photoelectric sensor-based tracking
│   └── STM32F103/                     # HAL-based control code
├── Task2 Labyrinth/                   # Ultrasonic maze navigation
│   ├── STM32F103/                     # Sensor data processing
│   └── STM32H743/                     # OpenMV coordination
├── Task3 Comprehensive_Task/          # Multi-mode vision control
│   ├── STM32F103/                     # Sensor integration
│   └── STM32H743/                     # OpenMV vision processing
└── Task4 April Tracking/              # AprilTag detection
    └── STM32H743/                     # TAG36H11 marker tracking
```

## Features

### Task 1 - Line Following
- PID-controlled line tracking with 4-channel photoelectric sensor array
- HC-SR04 ultrasonic obstacle detection
- MPU6050 IMU-based stabilization
- Adaptive speed control for intersections and sharp turns

### Task 2 - Labyrinth Navigation
- Dual HC-SR04 ultrasonic sensors for wall-following
- State machine navigation with dead-end detection
- Real-time distance-based path adjustment (12cm threshold)
- UART communication between STM32F103 and STM32H743

### Task 3 - Comprehensive Task
- OpenMV camera with HSV color detection and blob tracking
- Multi-mode operation: line following, ball kicking, obstacle avoidance
- Sensor fusion: photoelectric + ultrasonic + vision
- Real-time image display on SPI LCD

### Task 4 - AprilTag Tracking
- TAG36H11 marker detection and recognition
- Vision-based autonomous tracking with position feedback
- Motor speed adjustment based on tag distance and angle

## Technical Stack

**Control Algorithms**: PID control, state machines, sensor fusion, encoder feedback
**Vision Processing**: HSV color space, blob detection, template matching, AprilTag (TAG36H11)
**Motion Control**: 3-wheel omnidirectional drive, 10kHz PWM, DRV8701 motor driver
**Communication**: UART (115200 baud), I2C, SPI, ADC

## Development

**STM32**: Keil MDK-ARM, HAL Library, C
**OpenMV**: OpenMV IDE, MicroPython
