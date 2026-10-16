# FPGA 지휘 동작 인식 게임 — 제어 RTL 설계·UVM 검증

[전체 프로젝트](../README.md#프로젝트) · [노션 상세·시연 자료](https://app.notion.com/3d423ec941b781d2a2a5fcb84437ab55)

> Scoreboard 657,780건 PASS · FAIL 0건 · FC 98.96%

<p align="center"><img src="../assets/vga-conductor.svg" alt="FPGA 지휘 동작 인식 게임 대표 자료" width="680"></p>

| 구분 | 내용 |
| --- | --- |
| 기술 분야 | RTL·FPGA 시스템 설계 |
| 수행 기관 | 대한상공회의소 온디바이스AI 시스템반도체 설계교육 |
| 수행 형태 | 팀 |
| 담당 역할 | 지휘 상태 FSM·Tick/Valid·점수 계산, 제어부 UVM 검증 |
| 기간 | 2026.08.31 – 2026.09.08 |
| 구성·범위 | 대한상공회의소 · 7인 팀 프로젝트 |

## 개요

OV7670 카메라로 지휘봉 좌표를 추출하고, 지휘 동작에 따라 BPM·볼륨·점수를 계산해 VGA 화면과 UART로 출력하는 팀 프로젝트입니다. 저는 지휘 상태 판정 FSM, Tick·Valid 제어, 점수 계산 RTL과 Game Logic 제어부 UVM 검증을 담당했습니다.

## 본인 역할

- 지휘봉 X·Y 좌표에 따른 ZONE 판정과 상태 전이 구현
- `ZONE1 → 2 → 3 → 4` 전이에 따른 Pattern Tick 생성과 유효 데이터 전달 제어
- 지휘 속도 수집·평균 계산·원곡 BPM 비교에 따른 점수 계산
- 제어부 상태와 출력을 관측하는 UVM 검증 환경과 테스트 시나리오 구성

## 설계

게임의 시작·준비·지휘·정지 흐름은 `IDLE / START / READY / PATTERN_1~4 / STOP` 상태로 나눴습니다. 점수 모듈은 1/4박자마다 지휘 속도를 수집하고 4개 값의 평균과 원곡 BPM의 차이를 계산해 +10점부터 -10점까지 반영했습니다. 수집·계산·전송 시점은 `IDLE / COLLECT / CALC / SEND` 상태로 구분했습니다.

## 검증과 결과

`Conduct_fsm_test`, `bpm_calc_test`, `score_test`, `full_game_scenario_test`로 FSM 전이, BPM 계산, 점수 증감과 게임 진행을 확인했습니다. Scoreboard에서 제어부 6개 모듈의 실제 값과 기대값을 비교해 657,780건 PASS, FAIL 0건을 기록했습니다. Functional Coverage는 75.0%에서 98.96%로 높였습니다.
미도달 조건은 Directed Test로 보완했고, 설계에서 발생할 수 없는 상태 전이와 의미 없는 상위 비트는 Coverage 범위를 검토해 정리했습니다. 이 결과는 구성한 제어부 검증 환경의 비교 건수와 Coverage이며, 전체 영상 경로의 검증 결과와 구분합니다.

## 코드·결과 자료

- [지휘 패턴 FSM](https://github.com/Min-star-prog/fpga-vga-conductor-game/blob/integration/rtl/game/pattern_stick.sv)
- [점수 계산 RTL](https://github.com/Min-star-prog/fpga-vga-conductor-game/blob/integration/rtl/game/game_score.sv)
- [Game Logic UVM](https://github.com/Min-star-prog/fpga-vga-conductor-game/tree/integration/tb/uvm/uvm_game_logic)
- [파형·상세 그림·시연 자료 — 노션](https://app.notion.com/3d423ec941b781d2a2a5fcb84437ab55)

[← 전체 프로젝트](../README.md#프로젝트)
