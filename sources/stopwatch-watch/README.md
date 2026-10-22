# Stopwatch·Watch 제출 소스

2026.04.20 프로젝트 제출 ZIP의 소스를 변경 없이 보관한 스냅샷.

- **이민 담당:** Watch Control Unit·Datapath·Testbench
- **팀원 담당:** Stopwatch 설계·검증
- **진입점:** `toptop.v` → `top_stopwatch_watch.v` / `watch.v`
- **Watch:** `watch_control_unit.v`, `watch_datapath.v`
- **검증:** `tb_watch.v`
- **공통 입출력:** `button_debounce.v`, `fnd_controller.v`, `Basys-3-Master.xdc`

동시 증가 입력의 `+2` 분기는 일반 카운트 구간의 처리 내용. 해당 분기에서 상한 경계·자리올림을 별도 처리하지 않으므로 전체 경계조건 검증 완료를 뜻하지 않음.

[프로젝트 설명·파형·실물 시연](../../projects/stopwatch-watch.md)
