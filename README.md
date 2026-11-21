# stworkbench

A working ST Motor Control Workbench project (MCSDK v6.2.0): **sensorless six-step drive in voltage mode** on the P-NUCLEO-IHM03 kit, built and debugged in STM32CubeIDE (May 2024).

## Hardware

| Item | Part |
| --- | --- |
| Control board | NUCLEO-G431RB (STM32G431RB) |
| Power board | X-NUCLEO-IHM16M1 (2.12 A max board current) |
| Motor | GimBal GBM2804H-100T: 7 pole pairs, Rs 5.29 Ω, Ls 1.058 mH, Ke 5.0 V rms/krpm, 2.16 A nominal, 1572 rpm max |
| Bus | 12 V nominal |

## Drive settings

- PWM 30 kHz (60 kHz reference)
- Default target speed 236 rpm, limited to 1572 rpm

## Layout

| Path | Purpose |
| --- | --- |
| `6STEP-P-NUCLEO-IHM03_SensorlessVoltageMode.wbdef` / `.ioc` | Workbench and CubeMX project; open these to change motor or drive parameters |
| `Inc/`, `Src/` | Generated application and motor-control code (`mc_*`, `drive_parameters.h`, `pmsm_motor_parameters.h`, `power_stage_parameters.h`) |
| `STM32CubeIDE/` | IDE project, launch profile, linker script and startup |
| `Drivers/`, `MCSDK_v6.2.0-Full/` | HAL, CMSIS and the motor-control SDK library |
| `[ATT]12095.reg.txt` | Windows registry entry that registers a manually installed STM32CubeMX so Workbench can find it |

## Build and run

1. Open `STM32CubeIDE/` in STM32CubeIDE, build `Debug`, and flash with the included launch profile.
2. Start and stop the motor with the blue user button, or connect Motor Pilot over the ST-LINK COM port (ASPEP protocol) to set speed and watch the drive.

To change the motor, power stage or speed loop, edit the `.wbdef` in MC Workbench and regenerate.
