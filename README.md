# 이민

**FPGA·RTL 설계 · SystemVerilog/UVM 검증**

디지털 회로를 설계하고, 시뮬레이션과 실제 보드에서 동작을 확인해 왔습니다. RTL·UVM부터 AXI 주변장치, 임베디드 제어와 영상 입력의 시스템 연동까지 경험을 쌓았습니다.

[노션 포트폴리오](https://app.notion.com/p/09623ec941b782e6a750819f197c7713) · [이메일](mailto:h456456@naver.com)

[기술 스택](#기술-스택) · [프로젝트](#프로젝트) · [교육·경험](#교육경험) · [수상](#수상)

## 기술 스택

| 분야 | 언어·도구·플랫폼 | 다룬 내용 |
| --- | --- | --- |
| RTL·FPGA | Verilog, SystemVerilog, Vivado · Basys 3, Zybo Z7-20 | CPU, 통신 IP, AXI 주변장치, VGA 시스템 |
| 설계 검증 | UVM, VCS, Verdi | Agent·Sequence·Scoreboard, Random/Directed Test, Coverage |
| SoC·임베디드 제어 | C · MicroBlaze, ARM Cortex-A9, STM32 | 레지스터·인터럽트, UART·I2C·SPI, 모터·센서 연동 |
| 합성·타이밍 | Design Compiler, PrimeTime | RTL 합성·제약 조건·타이밍 리포트 실습 |
| 회로 설계·분석 | Virtuoso, Spectre, MATLAB, Tcl | Schematic, Sizing, DC/TRAN 분석 |
| On-Device AI·영상 인식 | Python, OpenCV, Jetson Orin Nano | 좌표·국면 인식, 후처리, ONNX/TensorRT 배포 |

## 프로젝트

**12개 프로젝트**의 담당 역할과 결과를 분야별로 정리했습니다. 프로젝트명을 누르면 설계·검증, 문제 해결과 상세 자료를 볼 수 있습니다.

[교육·기관별 보기](projects/README.md) · [소스 코드 안내](SOURCE_CODE.md)

### RTL·FPGA 시스템 설계

| 프로젝트 | 담당 역할 | 핵심 결과 |
| --- | --- | --- |
| [FPGA 지휘 동작 인식 게임](projects/vga-conductor.md) | 패턴 FSM · Tick/Valid · 점수 RTL · UVM | FC 98.96% · Scoreboard 657,780건 PASS |
| [AXI4-Lite 주변장치·MicroBlaze](projects/axi-microblaze.md) | GPIO·Timer·UART·I2C Master · AXI 연동 | I2C LCD 출력 · I2C IP FC 90% |
| [RV32I Single-Cycle CPU](projects/rv32i-cpu.md) | CPU RTL · 명령어·프로그램 실행 검증 | 37개 명령어 · Bubble Sort 실행 확인 |
| [UART 시계·센서 통합 시스템](projects/uart-sensor.md) | SR04 Datapath·CU·Testbench · Top 통합 | 30 ms Timeout · 4개 모드 동작 |
| [FPGA VGA 두더지 게임](projects/vga-mole.md) | 화면 생성 · RGB 합성 | 배경·캐릭터·시작 화면 합성 · DE2 동작 |

### SystemVerilog·UVM 검증

| 프로젝트 | 담당 역할 | 핵심 결과 |
| --- | --- | --- |
| [UBUS Master–Slave UVM VIP](projects/ubus-uvm.md) | Master Agent·Sequence · Slave 연동 | 3개 Functional Covergroup 각 100% |
| [SPI·I2C 통신 IP UVM 검증](projects/spi-i2c-uvm.md) | Master–Slave 자동 비교 · Coverage | SPI FC 96% · I2C FC 100% |
| [UART·FIFO·ASCII Decoder 검증](projects/uart-fifo-sv.md) | Class 기반 모듈·통합 경로 자동 비교 | Full/Empty·데이터 순서 확인 · Sampling 수정 |

### 임베디드 제어

| 프로젝트 | 담당 역할 | 핵심 결과 |
| --- | --- | --- |
| [스테레오 비전 3D 동작 추종 로봇팔](projects/stereo-robot-arm.md) | 스테레오 3D · 사람 각도 · UART · 통합 | 실물 추종 · 동작 녹화·재생 시연 |
| [STM32 스마트 주차장 차단기](projects/stm32-parking.md) | 센서 · 상태 제어 · 타이머 인터럽트 · 모터 | 1 ms 모터 제어 · 500 ms 미감지 판정 |

### 트랜지스터 수준 회로 설계

| 프로젝트 | 담당 역할 | 핵심 결과 |
| --- | --- | --- |
| [DDI 구성 블록 회로 설계](projects/ddi-circuit.md) | Schematic · Sizing · DC/TRAN 분석 | 8-bit DAC · 약 0–5 V Level Shifter |

### On-Device AI·영상 인식

| 프로젝트 | 담당 역할 | 핵심 결과 |
| --- | --- | --- |
| [Jetson 보드게임 인식·분석](projects/jetson-board-game.md) | 장기·바둑 인식 · 국면 안정화 · 엔진·GUI | 장기 CNN Val. 99.14% · 바둑 170개 패치 정분류 |

## 교육·경험

**경희대학교 정보디스플레이학과 학사**

| 과정·활동 | 주요 내용 |
| --- | --- |
| 대한상공회의소 온디바이스AI 시스템반도체 설계교육 | RTL·UVM, AXI·MicroBlaze, STM32, Jetson, Zybo 로봇팔 |
| 팹리스 실무형 일경험 프로그램 2기 | 차량용 AI SoC, CAN·센서 연동, YOLO 기반 NPU 후처리 |
| 서강대 글로벌반도체설계 전문가과정 | SystemVerilog·UVM, UBUS VIP, 합성·STA·DFT |
| 윈스펙 반도체실무 온라인 실습과정 | 반도체 실무 온라인 실습 |
| 성남시·가천대학교 팹리스 아카데미 | RTL·FPGA 및 트랜지스터 수준 회로 설계 |
| ADRC 연구실 인턴 | 디스플레이 소자의 전기적 특성·신뢰성 측정·평가 |
| KIDS Display School 구동 및 회로 | 디스플레이 Backplane·구동회로, 두 과목 교육성적 A |
| IDEC 온라인교육 | 3개 과정, 총 7일 교육 |

[학력·교육·경험·자격 상세](BACKGROUND.md)

## 수상

| 시기 | 수상 |
| --- | --- |
| 2026.01 | 팹리스 실무형 일경험 프로그램 우수상 |
| 2024.07 | 성남시 반도체 팹리스 아카데미 최우수상 · 성남시장 표창 |

---

[전체 프로젝트](#프로젝트) · [교육·기관별 프로젝트](projects/README.md) · [노션 포트폴리오](https://app.notion.com/p/09623ec941b782e6a750819f197c7713)
