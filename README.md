# 이민 | FPGA·RTL 설계 및 UVM 검증

Verilog·SystemVerilog로 디지털 회로를 설계하고, 시뮬레이션과 FPGA 보드에서 동작을 확인해 왔습니다. AXI 주변장치와 MicroBlaze 연동, UVM 검증을 경험했으며, 로봇팔 프로젝트에서는 스테레오 좌표·사람 팔 각도 계산과 UART·시스템 통합을 맡았습니다.

[노션 포트폴리오](https://app.notion.com/p/09623ec941b782e6a750819f197c7713) · [이메일](mailto:h456456@naver.com)

## 대표 프로젝트

<table>
<tr>
<td width="50%" valign="top">
<h3>스테레오 비전 동작 추종 로봇팔</h3>
<a href="https://github.com/Min-star-prog/ondeviceai/blob/main/robot_arm/PORTFOLIO.md">
<img src="https://raw.githubusercontent.com/Min-star-prog/ondeviceai/main/robot_arm/docs/diagrams/robot_control_flow.png" alt="스테레오 입력과 사람 목표각에서 로봇 명령·PWM 출력으로 이어지는 제어 구조" width="100%">
</a>
<p><strong>Zybo Z7-20 · Zynq · C · Python · UART</strong></p>
<p>좌우 카메라 관측으로 3D 좌표를 복원하고 전완·손목·그리퍼의 5개 목표값으로 연결했습니다.</p>
<p><strong>담당:</strong> 스테레오 3D 좌표, 사람 팔 각도 계산, UART 설계, 시스템 통합</p>
<p><a href="https://github.com/Min-star-prog/ondeviceai/blob/main/robot_arm/PORTFOLIO.md">코드·구현 설명</a> · <a href="https://app.notion.com/p/3f723ec941b7816881c9fe81751f1529">시연·문제 해결</a></p>
</td>
<td width="50%" valign="top">
<h3>Maestro — FPGA 지휘게임</h3>
<a href="https://github.com/Min-star-prog/fpga-vga-conductor-game">
<img src="https://raw.githubusercontent.com/Min-star-prog/fpga-vga-conductor-game/integration/docs/images/demo-pattern-playing.jpg" alt="카메라 기반 지휘 패턴과 BPM·점수를 표시하는 실제 게임 화면" width="100%">
</a>
<p><strong>Basys 3 · SystemVerilog · VGA · UVM</strong></p>
<p>지휘봉 움직임으로 음악을 제어하는 시스템에서 패턴 판정과 점수 RTL, 제어부 검증을 맡았습니다.</p>
<p><strong>담당:</strong> 지휘 패턴 FSM, Tick·Valid 제어, 점수 계산, Game Logic UVM</p>
<p><a href="https://github.com/Min-star-prog/fpga-vga-conductor-game">코드·시연</a> · <a href="https://app.notion.com/p/3d423ec941b781d2a2a5fcb84437ab55">설계·검증 결과</a></p>
</td>
</tr>
</table>

| 프로젝트 | 직접 수행한 내용 | 결과·자료 |
| --- | --- | --- |
| **AXI4-Lite 주변장치·MicroBlaze** | GPIO·Timer·UART·I2C Master IP 구현, AXI 레지스터와 C 제어 연동 | [I2C LCD 출력 · I2C IP FC 90%](https://app.notion.com/p/3d423ec941b78121b0b0fb1912eee9e2) |
| **UBUS Master–Slave UVM VIP** | Master Agent·Sequence 구현, Slave 환경과 통합, 미도달 조건 보완 | [Transaction·Data Beat·Protocol Covergroup 각 100%](https://app.notion.com/p/3d423ec941b78182aeb4c9d63174fe7d) |

VGA Game Logic의 당시 제어부 검증 결과입니다.

**Scoreboard 657,780건 PASS / FAIL 0건 · Functional Coverage 98.96%**

Coverage는 각 프로젝트에서 정의한 DUT·시나리오 범위를 기준으로 하며, 상세 범위는 연결된 검증 설명에 정리했습니다.

## 기술 스택

| 분야 | 사용 기술·경험 |
| --- | --- |
| RTL·FPGA | Verilog, SystemVerilog, Vivado · Basys 3, Zybo Z7-20 |
| 설계 검증 | UVM, VCS, Verdi · Driver/Monitor/Scoreboard, Random·Directed Test, Coverage 분석 |
| SoC·임베디드 제어 | C, Zynq ARM Cortex-A9, MicroBlaze, STM32 · AXI4-Lite, UART, I2C, SPI, 인터럽트 |
| On-Device AI·영상 인식 | Python, OpenCV, Jetson Orin Nano · 영상·관절 좌표 처리와 시스템 연동 |

## 교육·프로젝트 경험

- **대한상공회의소 온디바이스AI 시스템반도체 설계교육** — RTL·통신 IP·AXI 주변장치, FPGA 영상 시스템, 임베디드 제어 및 통합 프로젝트
- **서강대 글로벌반도체설계 전문가과정** — SystemVerilog·UVM 기반 설계 검증, UBUS VIP
- **성남시·가천대학교 팹리스 아카데미** — 반도체 회로와 DDI 구성 블록 설계·시뮬레이션

[전체 프로젝트와 교육·수상 이력은 노션에서 확인할 수 있습니다.](https://app.notion.com/p/09623ec941b782e6a750819f197c7713)

