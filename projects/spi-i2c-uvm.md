# SPI·I2C 통신 IP UVM 검증

[전체 프로젝트](../README.md#프로젝트) · [노션 상세·시연 자료](https://app.notion.com/3d423ec941b781efae15feac9005b06a)

> SPI FC 96% · I2C FC 100%

<p align="center"><img src="../assets/spi-i2c-uvm.png" alt="SPI·I2C 통신 IP UVM 검증 대표 자료" width="680"></p>

| 구분 | 내용 |
| --- | --- |
| 기술 분야 | SystemVerilog·UVM 검증 |
| 수행 기관 | 대한상공회의소 온디바이스AI 시스템반도체 설계교육 |
| 수행 형태 | 개인 |
| 담당 역할 | SPI·I2C 모두 UVM 환경 구성 · 송수신 자동 비교 |
| 기간 | 2026.05.01 – 2026.06.30 |
| 구성·범위 | 대한상공회의소 · 개인 프로젝트 · SPI와 I2C 모두 검증 · 기여도 100% |

## 개요

SPI와 I2C Master–Slave를 각각 대상으로 UVM 검증 환경을 구성한 개인 프로젝트입니다. 두 프로토콜 모두 직접 검증했으며, Sequence·Driver·Monitor·Scoreboard·Coverage를 연결해 구동·관측 시점과 송수신 데이터를 확인했습니다.

## 본인 역할

- SPI·I2C 각각 Sequence·Driver·Monitor·Scoreboard·Coverage 구성
- Master와 Slave의 송수신 데이터 자동 비교
- 프로토콜별 전송 구간과 Monitor Sampling 시점 점검
- 검증 시나리오 실행과 Functional Coverage 확인

## 프로토콜별 검증 범위와 결과

| 대상 | 확인 내용 | 결과 |
| --- | --- | --- |
| SPI | 8 SCLK의 양방향 Byte 전송, Master TX↔Slave RX와 Slave TX↔Master RX 비교 | WR Sequence 500회 · FC 96% |
| I2C | START·주소/RW·ACK·Data·ACK/NACK 구간, Read/Write 수신 값 비교 | WR Sequence 200회 · FC 100% |

SPI에서 MISO 값이 0x80으로 반복 수집되던 문제는 Monitor의 전송 종료 관측을 점검하고 `ss_n` 상승 시점과 종료 조건을 추가해 수정했습니다. I2C Read Monitor는 `pending_read`로 데이터 구간을 구분했습니다.

SPI는 WR Sequence 500회에서 Functional Coverage 96%, I2C는 WR Sequence 200회에서 100%를 기록했습니다. 서로 다른 프로토콜의 전송 구간과 데이터 수집 시점을 구분하고, Master–Slave 데이터 경로를 자동 비교하는 검증 환경을 구성했습니다.

## 결과

AXI의 SPI/I2C 선택·분담과 별개로 이 프로젝트에서는 두 프로토콜 모두 직접 검증했습니다. AXI 프로젝트의 I2C Master 단독 검증과 이 Master–Slave 검증은 DUT와 환경이 달라, 해당 Coverage는 프로젝트별로 표시합니다.

## 코드·결과 자료

- [SPI RTL·UVM](https://github.com/Min-star-prog/ondeviceai/tree/main/linux/0616_spi)
- [I2C RTL·UVM](https://github.com/Min-star-prog/ondeviceai/tree/main/linux/0616_i2c)
- [파형·상세 그림·시연 자료 — 노션](https://app.notion.com/3d423ec941b781efae15feac9005b06a)

[← 전체 프로젝트](../README.md#프로젝트)
