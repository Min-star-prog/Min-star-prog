# DDI 구성 블록 트랜지스터 수준 설계·시뮬레이션

[전체 프로젝트](../README.md#프로젝트) · [노션 상세·시연 자료](https://app.notion.com/3e123ec941b781a48a16f467e40bd690)

> 8-bit DAC 출력 · Level Shifter 약 0–5 V 전환

<p align="center"><img src="../assets/ddi-circuit.png" alt="DDI 구성 블록 회로 설계 대표 자료" width="680"></p>

| 구분 | 내용 |
| --- | --- |
| 기술 분야 | 트랜지스터 수준 회로 설계 |
| 수행 기관 | 성남시-가천대 반도체 팹리스 아카데미 |
| 수행 형태 | 개인 |
| 담당 역할 | Schematic·Sizing·테스트 회로·파형 분석 |
| 기간 | 2024.04.18 – 2024.06.06 |
| 구성·범위 | 성남시·가천대학교 · 개인 프로젝트 · 교육 실습 |

## 개요

교육 과정에서 디스플레이 구동 IC의 구성 블록을 트랜지스터 수준으로 설계하고 시뮬레이션했습니다. Cadence Virtuoso로 Schematic과 테스트 회로를 구성하고 Spectre에서 DC·TRAN 결과를 확인하며 소자 Width를 조정했습니다.

## 설계 범위

INV·NAND·NOR, Transmission Gate, Reset 기능을 포함한 DFF, 8단 Shift Register, 8-bit Decoder·DAC와 Level Shifter를 구성했습니다. 설계와 검증은 Schematic 시뮬레이션을 기준으로 진행했습니다.

## 블록별 확인

- 논리 게이트: 입력 조합별 동작과 VTC를 확인하고, Switching Point가 0.5 VDD 부근에 오도록 Width 조정
- DFF·Shift Register: ResetB 조건과 Clock에 따른 데이터 저장·8단 전달 파형 확인
- DAC: 입력 코드 증가에 따른 출력 증가와 최대 코드 이후 순환 동작 확인; 최대 출력 약 2.99066 V
- Level Shifter: 1 V 입력에 대해 약 0–5 V 범위의 출력 전환 확인

## 문제 해결

직렬·병렬 구조로 예상한 Width와 실제 VTC가 달라 게이트별 Width를 조정했습니다. Transmission Gate의 VDD를 넘는 출력은 스위칭에 따른 전하 주입·Clock Feedthrough 가능성과 연결해 해석했습니다. 별도의 원인 분리 실험은 수행하지 않았습니다.
Level Shifter가 중간 전압에 머물러 NMOS Width를 1.05–1.08 μm 범위에서 5 nm 간격으로 Sweep했습니다. 1.07 μm 조건에서 출력 전환을 확인했습니다.

## 결과와 범위

기본 게이트를 DFF·Shift Register·DAC로 확장하며 회로 구성과 Sizing·파형 분석을 실습했습니다. 결과는 Schematic 시뮬레이션 기준으로 정리했으며, Layout·PEX·PVT Corner 분석은 후속 과제로 남겼습니다.
입력 코드 증가에 따른 출력 증가를 관찰했습니다. DNL은 코드별 출력 간격과 이상적인 1 LSB의 차이로 별도 평가할 항목입니다.
<details>
<summary>세부 확인 항목</summary>

| 비교 항목 | 조정 전 | 조정 후 |
| --- | --- | --- |
| NMOS Width | 500 nm | 1.07 μm |
| 출력 상태 | 목표 전압에 도달하지 못하고 불완전하게 전환 | 약 0~5 V 범위의 출력 전환 확인 |

</details>

## 코드·결과 자료

- [파형·상세 그림·시연 자료 — 노션](https://app.notion.com/3e123ec941b781a48a16f467e40bd690)

[← 전체 프로젝트](../README.md#프로젝트)
