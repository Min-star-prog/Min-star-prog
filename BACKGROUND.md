# 학력·교육·경험

[포트폴리오 첫 화면](README.md) · [전체 프로젝트](README.md#프로젝트)

## 학력

| 학교 | 내용 | 기간 |
| --- | --- | --- |
| 분당 서현고등학교 이과계열 졸업 | 졸업 | 2009.03.01 – 2012.02.29 |
| 경희대학교(서울) 정보디스플레이학과 학사 졸업 | 졸업 | 2013.03.04 – 2024.02.29 |

## 교육·실무 경험

### 대한상공회의소 온디바이스AI 시스템반도체 설계교육

CPU와 통신 주변장치를 RTL로 설계하고, SystemVerilog/UVM으로 검증했습니다. 이후 MicroBlaze 시스템, STM32 제어, Jetson 영상 인식, Zybo 로봇팔 연동 프로젝트를 수행했습니다.

#### 개요

| 기간 | 2026.03.24 ~ 2026.10.23 (980시간) |
| --- | --- |
| 주관 | 대한상공회의소 서울기술교육센터 (경기도 팹리스 아카데미, 온디바이스AI 2기) |
| 교육 내용 | CPU 및 AMBA Bus Interface, UART·I2C 등 프로토콜 중심의 HW 설계, ARM Cortex-M 기반 임베디드 펌웨어 개발 |

#### 수행 프로젝트

- [UART·FIFO·ASCII Decoder 검증](projects/uart-fifo-sv.md)
- [UART 시계·센서 통합 시스템](projects/uart-sensor.md)
- [RV32I Single-Cycle CPU](projects/rv32i-cpu.md)
- [SPI·I2C 통신 IP UVM 검증](projects/spi-i2c-uvm.md)
- [AXI4-Lite 주변장치·MicroBlaze](projects/axi-microblaze.md)
- [STM32 스마트 주차장 차단기](projects/stm32-parking.md)
- [Jetson 보드게임 인식·분석](projects/jetson-board-game.md)
- [FPGA 지휘 동작 인식 게임](projects/vga-conductor.md)
- [스테레오 비전 3D 동작 추종 로봇팔](projects/stereo-robot-arm.md)

#### 다룬 범위

UART·I2C RTL과 RV32I CPU를 설계한 뒤, AXI4-Lite 주변장치를 MicroBlaze에 연결했습니다. 시뮬레이션 결과와 실제 보드 동작을 대조했고, C 드라이버로 레지스터와 인터럽트를 제어했습니다. Zybo에서는 영상 입력과 로봇팔 제어를 연동했습니다.
VDMA와 DDR 프레임 버퍼를 활용하는 영상 전송 구조도 실습했습니다.

[노션 기록](https://app.notion.com/3d423ec941b7814e9416c158e7fb8e51)

### 팹리스 실무형 일경험 프로그램 2기

한국팹리스산업협회의 차량용 반도체 실습 프로그램에 참여했습니다. 제공된 AI SoC 보드와 예제 코드를 바탕으로 센서·통신 연동을 확인하고, YOLO 기반 NPU 후처리 코드를 수정했습니다. 수료 시 우수상을 받았습니다.

#### 개요

| 기간 | 2025.12.10 ~ 2026.01.16 |
| --- | --- |
| 주관 | 한국팹리스산업협회 |
| 사용 기술 | C, 임베디드 Linux(Ubuntu), 넥스트칩 AI SoC, NPU, 카메라 |
| 수상 | 팹리스 실무형 일경험 프로그램 우수상 (2026.01.16) |

#### 수행 내용

Ubuntu 환경에서 보드·센서 연결과 CAN 송수신을 실습했습니다. Sensing, Control, HPC Zone 간 상태 데이터 전달을 확인하고 시뮬레이터와 연결했습니다.
NPU 후처리는 제공된 YOLO 기반 C 코드를 분석하고 실습에 필요한 부분을 수정했습니다. 기존 모델을 새로 설계한 작업과는 구분하며, 출력 데이터가 인식 결과로 바뀌는 과정과 보드 연동을 중심으로 수행했습니다.

#### 교육 자료

[https://github.com/topst-development/Education/tree/edu/Fabless/LectureNote](https://github.com/topst-development/Education/tree/edu/Fabless/LectureNote)

#### 배운 점

FPGA와 MCU 중심이던 개발 환경에서 벗어나 임베디드 Linux 보드 위에서 동작하는 코드를 다뤄봤습니다. 기존 후처리 코드의 입력·출력을 따라가며 NPU 출력과 화면 표시 사이의 데이터 형식을 확인했습니다.

#### 관련 항목

[관련 기록](https://app.notion.com/p/3d423ec941b781aaa71dfe4abffc80a9)

[노션 기록](https://app.notion.com/3d423ec941b78123a136f859fbb80fe6)

### 서강대 글로벌반도체설계 전문가과정

SystemVerilog 설계·검증과 함께 합성, STA, DFT까지 백엔드 플로우를 다룬 20주 과정입니다. 

#### 개요

| 기간 | 2025.07.07 ~ 2025.11.28 (20주, 8시간/일) |
| --- | --- |
| 주관 | 서강대학교 판교 디지털혁신캠퍼스 시스템반도체 설계교육센터 · 성남시 시스템반도체 인재양성사업 |
| 구성 | 디지털 회로설계 기술과정 12주 + 전문화과제 팀프로젝트 8주 |
| 환경 | Synopsys · Cadence 정식 라이선스 EDA 환경 |

#### PI 및 백엔드 플로우

- **Logic Synthesis (Design Compiler)** — RTL을 게이트 레벨로 합성하고, 제약 조건에 따라 결과가 어떻게 달라지는지 확인했습니다.
- **Static Timing Analysis (PrimeTime)** — 타이밍 리포트를 읽고 위반 경로와 원인을 분석하는 흐름을 익혔습니다.
- **DFT Technology (TetraMax)** — 테스트 가능한 설계 개념과 DFT 플로우를 학습했습니다.
- **Low Power Design Methodology** — UPF 작성법을 배우며 저전력 설계 기법을 다뤘습니다.
Design Compiler와 PrimeTime 실습에서 합성 제약과 타이밍 리포트를 다뤘습니다. 이후 FPGA 지휘 게임에서는 조합 경로의 지연을 분석하고 갱신 주기에 맞는 타이밍 제약을 검토했습니다.

#### 수행 프로젝트

- [UBUS Master–Slave UVM VIP](projects/ubus-uvm.md) (2인 팀, 기여도 60%)
Master Agent의 Driver, Monitor, Sequencer와 검증 Sequence를 구현하고, Virtual Sequence로 Master와 Slave 시나리오를 함께 제어했습니다. 3개 Functional Covergroup에서 각각 100%를 달성했습니다.

#### 그 외 교육 범위

SystemVerilog Design / Verification / Assertion (VCS), ARM-based Modern SoC Architecture와 APB·AXI 버스 구조, SoC 설계 플로우와 Linux 기반 EDA 툴 구동 환경, 반도체 Device Physics, Python을 함께 다뤘습니다.

[노션 기록](https://app.notion.com/3d423ec941b7816bac0ef766dd9ad6d6)

### 윈스펙 반도체실무 온라인 실습과정

노션에 기록된 교육 기간: 2025.02.01 – 2025.03.31

[노션 기록](https://app.notion.com/3d423ec941b78158a13bd9c546623f44)

### 성남시·가천대학교 팹리스 아카데미

디지털 RTL과 트랜지스터 수준 회로 설계를 실습한 과정입니다. 아날로그 회로 기초와 디지털 RTL 설계를 함께 배웠고, 수료 시 최우수상을 받았습니다.

#### 개요

| 기간 | 2024.04.01 ~ 2024.08.19 (400시간) |
| --- | --- |
| 주관 | 가천대 팹리스 사업단 (성남시 지원) |
| 교육 내용 | 회로 이론 등 디지털·아날로그 회로 기초, UART·SPI 등 프로토콜 RTL 설계 및 합성, FPGA 설계 실무 |
| 수상 | 성남시-가천대 팹리스 아카데미 최우수상 · 성남시장 표창장 (2024.07.31) |

#### 수행 프로젝트

- **16-bit Ripple Carry Adder** — 가산기 구조를 설계하고 자리올림 전파 경로를 확인했습니다.
- **FPGA 기반 UART Tx & Rx** — UART 송수신 로직을 RTL로 설계하고 FPGA에서 동작을 확인했습니다.
- **16-bit SPI Master/Slave (Memory)** — SPI 마스터와 슬레이브를 설계하고 메모리 연동 동작을 구현했습니다.
- [DDI 구성 블록 회로 설계](projects/ddi-circuit.md) — Virtuoso로 DAC, Shift Register, Level Shifter 등 DDI 구성 블록을 트랜지스터 레벨에서 설계하고 시뮬레이션으로 검증했습니다.

#### 설계 실습

아날로그 회로를 트랜지스터 레벨에서 설계해보면서 학부에서 배운 회로 이론을 실제 설계와 연결했습니다. 동시에 UART, SPI를 RTL로 작성하고 합성해 FPGA에서 확인하며 디지털 설계로 방향을 잡게 된 과정입니다. 여기서 처음 다룬 UART와 SPI는 이후 대한상공회의소 과정에서 UVM 검증 대상으로 다시 다루게 됩니다.

[노션 기록](https://app.notion.com/3d423ec941b781d994cbf01d6595c4e1)

### ADRC 연구실 인턴

학부 연구실에서 차세대 디스플레이 소자의 전기적 특성과 신뢰성을 측정하고 평가했습니다.

#### 개요

| 기간 | 2024.01.02 ~ 2024.02.27 (200시간) |
| --- | --- |
| 소속 | ADRC (Advanced Display Research Center) |

#### 수행 내용

차세대 디스플레이 소자의 전기적 특성을 측정하고 신뢰성을 평가했습니다. 측정 결과를 소자 물리 관점에서 해석하며 소자 동작 원리에 대한 이해를 넓혔고, 디스플레이 구동회로와 인터페이스, 프로토콜, 회로 이론을 함께 학습했습니다.

#### 배운 점

패널을 구동하는 회로가 어떤 소자 특성 위에서 동작하는지 확인한 경험입니다. 이후 DDI 회로 설계와 디지털 설계로 관심을 넓히는 출발점이 되었습니다.

[노션 기록](https://app.notion.com/3d423ec941b781fb8510cd2f58850f7b)

### KIDS Display School 구동 및 회로

한국정보디스플레이학회 KIDS Display School에서 디스플레이 Backplane과 구동 회로 두 과목을 수강했습니다.

#### 개요

| 기간 | 2023.07.17 ~ 2023.08.14 |
| --- | --- |
| 수강 과목 | 디스플레이 Backplane · 디스플레이 구동 및 회로 |
| 성적 | 두 과목 모두 교육성적 A (과목별 상위 30% 성적우수자) |

#### 수강 내용

전공에서 다룬 디스플레이 Backplane 구조와 디스플레이 구동 회로를 다시 점검하고 한 단계 더 깊게 학습했습니다. 두 과목 모두 상위 30%에 해당해 교육성적 A를 받았습니다.
두 과목 모두 성적우수자에  해당해 상장을 받았습니다.

[노션 기록](https://app.notion.com/3d423ec941b7815b96f1e1874a8614a2)

### IDEC 온라인교육 (3개 과정, 총 7일)

노션에 기록된 교육 기간: 2022.06.01 – 2022.07.31

[노션 기록](https://app.notion.com/3d423ec941b781419526e31af058a297)

## 수상

| 수상 | 기록 |
| --- | --- |
| 성남시 반도체 팹리스 아카데미 최우수상 | [수상 자료](https://app.notion.com/3d423ec941b7810d9217d2f449dc3db7) |
| 팹리스 실무형 일경험 프로그램 우수상 | [수상 자료](https://app.notion.com/3d423ec941b781aaa71dfe4abffc80a9) |

## 자격·어학 기록

| 항목 | 취득·응시 기록 | 자료 |
| --- | --- | --- |
| 1종대형운전면허증 | 2016.12.12 | [노션 기록](https://app.notion.com/39c23ec941b782fb9e0801d2ef0c2911) |
| OPIc IH | 2023.07.16 | [노션 기록](https://app.notion.com/3d423ec941b7816aa76cf25088cf366a) |
| OPIc IM2 | 2025.08.31 | [노션 기록](https://app.notion.com/3d423ec941b781cea6f0f575f776d883) |
| 기타 인증서 및 수료증 | — | [노션 기록](https://app.notion.com/3e123ec941b78019b347f1e320ef99ec) |

[← 포트폴리오 첫 화면](README.md)
