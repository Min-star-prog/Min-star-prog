# UART 기반 시계·센서 통합 FPGA 시스템

[전체 프로젝트](../README.md#프로젝트) · [노션 상세·시연 자료](https://app.notion.com/3dc23ec941b7811f8fe9c1f251297953)

> 30 ms 센서 무응답 처리 · 4개 모드·UART 출력 확인

<p align="center"><img src="../assets/uart-sensor.png" alt="UART 시계·센서 통합 시스템 대표 자료" width="680"></p>

| 구분 | 내용 |
| --- | --- |
| 기술 분야 | RTL·FPGA 시스템 설계 |
| 수행 기관 | 대한상공회의소 온디바이스AI 시스템반도체 설계교육 |
| 수행 형태 | 팀 |
| 담당 역할 | SR04 Datapath·Control Unit·Testbench, Top 통합 |
| 기간 | 2026.05.01 – 2026.05.06 |
| 구성·범위 | 대한상공회의소 · 3인 팀 프로젝트 |

## 개요

Stopwatch, Watch, DHT11 온습도 센서와 SR04 초음파 센서를 UART·FIFO 경로와 하나의 FPGA 시스템으로 통합했습니다. 저는 SR04 Datapath·Control Unit과 Testbench를 작성하고, `top_4module`에서 통신부와 각 기능 모듈의 연결을 담당했습니다.

## 본인 역할

- SR04 Trigger 생성과 Echo 펄스 폭 측정
- 측정 시간의 거리 환산과 센서 무응답 처리
- SR04 상태·데이터 경로를 확인하는 Testbench 작성
- UART/FIFO·ASCII Decoder와 Stopwatch·Watch·DHT11·SR04의 Top 연결

## 통합 구조

PC의 ASCII 명령은 UART RX·FIFO·Decoder를 거쳐 각 기능을 제어하고, 선택한 모드의 결과는 FND에 표시했습니다. 시간·온습도·거리 데이터는 ASCII Sender·FIFO·UART TX를 통해 PC 터미널로 전송했습니다. 

## SR04 설계와 문제 해결

Trigger를 10 μs 이상 유지하고 Echo의 High 시간을 1 μs Tick으로 측정해 거리로 환산했습니다. Echo가 오지 않을 때 WAIT 상태에 머무르던 문제는 30,000 Tick, 즉 30 ms의 Timeout 조건으로 IDLE에 복귀하도록 수정했습니다.

## 결과

Basys3에서 4개 모드 전환과 FND 출력을 확인했고, PC 터미널에서 시간·온습도·거리 데이터를 수신했습니다. 32회 이상 연속 명령 입력 시 동일 데이터가 반복 출력되는 현상은 남은 이슈로 기록하고, FIFO Pop과 Decoder Valid의 연결을 후속 점검 항목으로 정리했습니다.

## 코드·결과 자료

- [센서·UART 통합 RTL](https://github.com/Min-star-prog/ondeviceai/tree/main/window/OndeviceAI2/fifo_sensor/fifo_sensor.srcs/sources_1/new)
- [파형·상세 그림·시연 자료 — 노션](https://app.notion.com/3dc23ec941b7811f8fe9c1f251297953)

[← 전체 프로젝트](../README.md#프로젝트)
