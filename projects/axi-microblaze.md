# AXI4-Lite 주변장치 설계 및 MicroBlaze 연동

[전체 프로젝트](../README.md#프로젝트) · [노션 상세·시연 자료](https://app.notion.com/3d423ec941b78121b0b0fb1912eee9e2)

> AXI 기반 I2C 제어 · LCD 출력 · I2C IP FC 90%

<p align="center"><img src="../assets/axi-microblaze.png" alt="AXI4-Lite 주변장치·MicroBlaze 대표 자료" width="680"></p>

| 구분 | 내용 |
| --- | --- |
| 기술 분야 | RTL·FPGA 시스템 설계 |
| 수행 기관 | 대한상공회의소 온디바이스AI 시스템반도체 설계교육 |
| 수행 형태 | 팀 |
| 담당 역할 | GPIO·Timer·UART·I2C Master 구현 · I2C 선택 범위 100% |
| 기간 | 2026.06.01 – 2026.06.30 |
| 구성·범위 | 대한상공회의소 · 2인 구성 · SPI/I2C 선택·분담 · I2C 구현 범위 기여도 100% |

## 개요

GPIO·Timer·UART·I2C Master IP를 직접 구현하고 AXI4-Lite를 통해 MicroBlaze와 연결해 C 코드로 제어했습니다. 2인 구성에서 SPI와 I2C를 선택·분담하는 방식이었으며, 저는 공통 주변장치 구현과 함께 I2C를 선택해 I2C Master IP와 LCD 연동을 수행했습니다. 기여도 100%는 본인이 선택한 I2C 구현 범위를 기준으로 합니다.

## 본인 역할

- GPIO·Timer·UART와 I2C Master IP 직접 구현
- AXI 레지스터 명령과 I2C Master의 START·WRITE·READ·STOP 제어 연결
- ACK/NACK, BUSY, DONE, RX_VALID 등 상태 처리
- I2C IP의 프로토콜 동작을 UVM으로 검증
- 실제 I2C LCD 통신과 미출력 원인 점검

## 시스템 구성

MicroBlaze, AXI Interconnect, AXI Interrupt Controller, Local BRAM과 직접 구현한 GPIO·Timer·UART·I2C 주변장치를 연결했습니다. Timer로 시간을 계산하고 GPIO와 I2C를 통해 FND·LCD에 표시하며, UART 명령으로 상태를 제어하도록 구성했습니다.

## I2C 설계·검증

AXI 레지스터에 기록한 명령에 따라 I2C 전송을 수행하고 완료·수신 상태를 소프트웨어에서 확인하도록 구성했습니다. UVM Monitor는 SCL·SDA에서 START, BYTE, ACK/NACK, STOP을 복원하고, Scoreboard에서 기대 이벤트와 실제 이벤트의 종류·데이터·9번째 비트를 순서대로 비교했습니다.
Random Test에서 누락된 Read ACK/NACK 조건을 Directed Sequence로 보완해 100회 테스트에서 Functional Coverage 90%를 기록했습니다. Master 단독 환경에서 Read Data가 `8'hFF`로 제한되는 조건을 확인하고, Slave BFM 추가를 후속 과제로 정리했습니다.

## 문제 해결

LCD가 출력되지 않을 때 RTL·드라이버·슬레이브 주소·배선·Contrast 설정을 나눠 점검했습니다. I2C Scanner로 실제 주소가 0x27인 것을 확인해 기존 0x3F 설정을 수정하고, SCL·SDA 배선과 Contrast를 조정해 출력을 확인했습니다.
I2C를 AXI 레지스터 제어에 연결하고 시뮬레이션의 프로토콜 동작과 실제 LCD 통신을 함께 확인했습니다. I2C Master IP 검증과 별도의 SPI·I2C Master–Slave 검증 프로젝트는 DUT·환경·Coverage가 다르므로 결과를 합치지 않습니다.

## 코드·결과 자료

- [AXI Custom IP 모음](https://github.com/Min-star-prog/ondeviceai/tree/main/window/OndeviceAI2/ip_repo)
- [I2C Master IP](https://github.com/Min-star-prog/ondeviceai/tree/main/window/OndeviceAI2/ip_repo/i2c_1.0)
- [MicroBlaze·Timer·I2C 시스템](https://github.com/Min-star-prog/ondeviceai/tree/main/window/OndeviceAI2/260628_microblaze_timer_i2c)
- [파형·상세 그림·시연 자료 — 노션](https://app.notion.com/3d423ec941b78121b0b0fb1912eee9e2)

[← 전체 프로젝트](../README.md#프로젝트)
