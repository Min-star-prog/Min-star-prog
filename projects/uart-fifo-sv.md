# UART·FIFO·ASCII Decoder SystemVerilog 검증

[전체 프로젝트](../README.md#프로젝트) · [노션 상세·시연 자료](https://app.notion.com/3d423ec941b781a4b293d7d2a599bd54)

> FIFO Full/Empty·데이터 순서 확인 · Sampling 오류 수정

<p align="center"><img src="../assets/uart-fifo-sv.png" alt="UART·FIFO·ASCII Decoder 검증 대표 자료" width="680"></p>

| 구분 | 내용 |
| --- | --- |
| 기술 분야 | SystemVerilog·UVM 검증 |
| 수행 기관 | 대한상공회의소 온디바이스AI 시스템반도체 설계교육 |
| 수행 형태 | 개인 |
| 담당 역할 | Class 기반 자동 비교 · 자율 범위의 단위·통합 검증 |
| 기간 | 2026.03.01 – 2026.04.30 |
| 구성·범위 | 대한상공회의소 · 개인 프로젝트 · 자율 검증 과제 |

## 개요

교육 과정에서 각자가 검증 범위를 정하는 개인 과제로, UART 송수신과 FIFO, ASCII Decoder를 대상으로 Class 기반 SystemVerilog Testbench를 구축했습니다. 저는 모듈별 기능과 UART RX에서 FIFO·Decoder로 이어지는 데이터 경로를 확인했습니다.

## 검증 환경

Generator는 Random Transaction을 생성하고 Driver는 UART 프레임이나 FIFO 제어 입력으로 변환했습니다. Monitor는 실제 출력을 수집하고 Scoreboard는 기대값과 비교했습니다. 이 프로젝트는 SystemVerilog Class 기반 검증이며, UVM 프로젝트와 구분해 표시합니다.

## 확인한 시나리오

- FIFO Push only와 Pop only에서 Full·Empty 상태 확인
- Random Push/Pop에서 저장·출력 데이터 순서 비교
- UART TX 직렬 출력을 Bit 중앙에서 샘플링해 Byte 복원
- UART RX·FIFO·ASCII Decoder 사이의 데이터 전달과 명령 해석 비교

## 결과

입력 생성부터 실제 값 수집·자동 비교까지 검증 흐름을 직접 구성했습니다. 검증 결과는 모듈별 비교와 통합 경로의 데이터 전달 확인을 기준으로 정리했습니다.

## Race Condition 분석

출력 로그는 같지만 Scoreboard에서 FAIL이 발생했습니다. Monitor의 Sampling과 DUT의 Non-blocking Assignment 갱신이 겹치는 것을 확인해, 사용한 시뮬레이션 시간 단위에서 Capture를 `#1` 뒤로 이동했습니다. 데이터가 갱신된 이후에 비교하도록 바꿔 해당 테스트의 결과를 확인했습니다.

## 코드·결과 자료

- [관련 UART·FIFO RTL](https://github.com/Min-star-prog/ondeviceai/tree/main/window/OndeviceAI2/uart_fifo/uart_fifo.srcs)
- [파형·상세 그림·시연 자료 — 노션](https://app.notion.com/3d423ec941b781a4b293d7d2a599bd54)

[← 전체 프로젝트](../README.md#프로젝트)
