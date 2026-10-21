# 소스 코드 안내

[전체 프로젝트](README.md#프로젝트)

프로젝트 설명과 연결되는 코드의 진입점을 정리했습니다.

## RTL·FPGA 시스템 설계

| 프로젝트 | 코드·자료 |
| --- | --- |
| [FPGA 지휘 동작 인식 게임](projects/vga-conductor.md) | [지휘 패턴 FSM](https://github.com/Min-star-prog/fpga-vga-conductor-game/blob/integration/rtl/game/pattern_stick.sv)<br>[점수 계산 RTL](https://github.com/Min-star-prog/fpga-vga-conductor-game/blob/integration/rtl/game/game_score.sv)<br>[Game Logic UVM](https://github.com/Min-star-prog/fpga-vga-conductor-game/tree/integration/tb/uvm/uvm_game_logic) |
| [AXI4-Lite 주변장치·MicroBlaze](projects/axi-microblaze.md) | [AXI Custom IP 모음](https://github.com/Min-star-prog/ondeviceai/tree/main/window/OndeviceAI2/ip_repo)<br>[I2C Master IP](https://github.com/Min-star-prog/ondeviceai/tree/main/window/OndeviceAI2/ip_repo/i2c_1.0)<br>[MicroBlaze·Timer·I2C 시스템](https://github.com/Min-star-prog/ondeviceai/tree/main/window/OndeviceAI2/260628_microblaze_timer_i2c) |
| [RV32I Single-Cycle CPU](projects/rv32i-cpu.md) | [RV32I RTL·Testbench](https://github.com/Min-star-prog/ondeviceai/tree/main/linux/20260527_RV32I_singlecycle_source_code) |
| [UART 시계·센서 통합 시스템](projects/uart-sensor.md) | [센서·UART 통합 RTL](https://github.com/Min-star-prog/ondeviceai/tree/main/window/OndeviceAI2/fifo_sensor/fifo_sensor.srcs/sources_1/new) |

## SystemVerilog·UVM 검증

| 프로젝트 | 코드·자료 |
| --- | --- |
| [UBUS Master–Slave UVM VIP](projects/ubus-uvm.md) | [UBUS 프로젝트 설명](https://github.com/Min-star-prog/Segong/tree/main/LM/lk)<br>[Master 구현·Sequence](https://github.com/Min-star-prog/Segong/tree/main/LM/lk/lk_project/master-week6)<br>[Master–Slave 통합 코드](https://github.com/Min-star-prog/Segong/tree/main/LM/lk/lk_project/ex-week5) |
| [SPI·I2C 통신 IP UVM 검증](projects/spi-i2c-uvm.md) | [SPI RTL·UVM](https://github.com/Min-star-prog/ondeviceai/tree/main/linux/0616_spi)<br>[I2C RTL·UVM](https://github.com/Min-star-prog/ondeviceai/tree/main/linux/0616_i2c) |
| [UART·FIFO·ASCII Decoder 검증](projects/uart-fifo-sv.md) | [관련 UART·FIFO RTL](https://github.com/Min-star-prog/ondeviceai/tree/main/window/OndeviceAI2/uart_fifo/uart_fifo.srcs) |

## 임베디드 제어

| 프로젝트 | 코드·자료 |
| --- | --- |
| [스테레오 비전 3D 동작 추종 로봇팔](projects/stereo-robot-arm.md) | [로봇팔 소스·운영 문서](https://github.com/Min-star-prog/ondeviceai/tree/main/robot_arm)<br>[담당 구현·코드 읽는 순서](https://github.com/Min-star-prog/ondeviceai/blob/main/robot_arm/PORTFOLIO.md)<br>[전완 목표각 계산](https://github.com/Min-star-prog/ondeviceai/blob/main/robot_arm/robot_arm/src/app/robot/vision/human_target/forearm_mapping.c)<br>[UART 계약](https://github.com/Min-star-prog/ondeviceai/blob/main/robot_arm/robot_arm/docs/uart_protocol_unity.md) |
| [STM32 스마트 주차장 차단기](projects/stm32-parking.md) | [차단기 제어 C 소스](https://github.com/Min-star-prog/ondeviceai/tree/main/%EC%9E%84%EB%B2%A0%EB%94%94%EB%93%9C%20%EC%8B%9C%EC%8A%A4%ED%85%9C/1602.project) |

## 로봇팔 코드 읽는 순서

1. [담당 역할과 전체 구조](https://github.com/Min-star-prog/ondeviceai/blob/main/robot_arm/PORTFOLIO.md)
2. [스테레오 좌표·각도 계약](https://github.com/Min-star-prog/ondeviceai/blob/main/robot_arm/robot_arm/docs/stereo_absolute_angles.md)
3. [전완 목표각 계산](https://github.com/Min-star-prog/ondeviceai/blob/main/robot_arm/robot_arm/src/app/robot/vision/human_target/forearm_mapping.c)
4. [통합 파이프라인](https://github.com/Min-star-prog/ondeviceai/blob/main/robot_arm/robot_arm/src/app/main.c)

[← 포트폴리오 첫 화면](README.md)

