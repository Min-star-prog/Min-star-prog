# RV32I Single-Cycle CPU 설계 및 Bubble Sort 실행 검증

[전체 프로젝트](../README.md#프로젝트) · [Notion 상세·시연](https://app.notion.com/p/3d423ec941b7815d9825ccf432bcf0bf)

대한상공회의소 온디바이스AI 시스템반도체 설계교육 · 개인 · 2026.05.19 – 2026.05.27

![프로젝트 대표 자료](../assets/rv32i-cpu.png)

> **대한상공회의소 · 개인 프로젝트 · Bubble Sort 선택 과제**
>
> **핵심 결과:** 37개 명령어 동작 확인 · 6개 원소 정렬 · 함수 호출·복귀와 메모리 변화 추적

## 개요

- **과제:** 32-bit RV32I Single-Cycle CPU 설계·명령어 시뮬레이션
- **선택 프로그램:** Bubble Sort 실행으로 반복문·조건문·함수 호출·메모리 접근 확인

## 담당 역할

- PC·Register File·ALU·Immediate Generator·Control Unit 및 메모리 인터페이스 구성
- 명령어 형식에 따른 제어 신호·데이터 경로 설계와 시뮬레이션
- Bubble Sort의 C·Assembly 분석 및 PC·레지스터·스택·배열 값 추적

## CPU 구조 및 명령어 설계

- **메모리:** Instruction/Data Memory를 분리한 Harvard 구조
- **제어:** 명령어에 따른 ALU 피연산자·Write Back 데이터·다음 PC 선택

**Single-Cycle CPU Datapath 구성도**

[상세 그림 — Notion](https://app.notion.com/p/3d423ec941b7815d9825ccf432bcf0bf#fbb662fb458747b1b80a4eacb1a42ac8)

PC·제어부·Register File·ALU·메모리·Write Back의 연결

<details>
<summary>Single-Cycle 실행 흐름과 모듈별 역할</summary>

명령어 Fetch → Decode 및 레지스터 읽기 → ALU 연산·주소 계산 → 메모리 접근 → Write Back 데이터 선택을 한 클록 주기 안에서 처리하고, 상태 변경은 클록 에지에 반영하도록 구성했습니다.

| 구성 요소 | 구현 내용 |
| --- | --- |
| PC | 순차 실행, 조건 분기, JAL·JALR의 다음 주소 선택 |
| Instruction Memory | PC에 해당하는 32비트 명령어 제공 |
| Register File | rs1·rs2 조합 읽기와 rd 동기 쓰기, x0 특성 유지 |
| Immediate Generator | 명령어 형식별 비트 재배치와 32비트 확장 |
| ALU | 산술·논리·시프트 연산과 Signed/Unsigned 비교 |
| Control Unit | Opcode·funct3·funct7에 따른 제어 신호 생성 |
| Data Memory | 주소·접근 폭에 따른 Load/Store |
| Write Back MUX | ALU 결과, Load 데이터, Immediate, PC 상대 주소, PC+4 중 선택 |

Register File 읽기는 조합 경로로 두어 같은 주기 안에 ALU 입력을 제공했습니다. 명령어별로 사용하는 경로가 달라도 연산 결과와 PC가 올바른 클록 에지에 반영되는지 파형으로 확인했습니다.

</details>

<details>
<summary>37개 명령어 구성과 제어 신호</summary>

| 분류 | 명령어 | 개수 |
| --- | --- | --- |
| R-Type | ADD, SUB, SLL, SLT, SLTU, XOR, SRL, SRA, OR, AND | 10 |
| I-Type 산술·논리 | ADDI, SLTI, SLTIU, XORI, ORI, ANDI, SLLI, SRLI, SRAI | 9 |
| Store | SB, SH, SW | 3 |
| Load | LB, LH, LW, LBU, LHU | 5 |
| Branch | BEQ, BNE, BLT, BGE, BLTU, BGEU | 6 |
| Upper Immediate | LUI, AUIPC | 2 |
| Jump | JAL, JALR | 2 |
| 합계 | 산술·논리, 메모리 접근, 조건 분기 및 점프 | 37 |

Load는 발표자료에서 IL-Type으로 구분한 명령어군이며, 인코딩은 I 형식을 사용합니다.

| 제어 신호 | 역할 |
| --- | --- |
| rf\_we | Register File 쓰기 허용 |
| alusrc\_sel | ALU의 두 번째 피연산자를 rs2 또는 Immediate로 선택 |
| alu\_control | 산술·논리·시프트 연산 및 분기 비교 조건 선택 |
| rfsrc\_sel | rd에 기록할 Write Back 데이터 선택 |
| mem\_mode / dwe | 메모리 접근 폭·부호 처리와 Store 쓰기 제어 |
| branch / jal / jalr | 조건 분기·직접 점프·간접 점프 경로 선택 |

- **Write Back 경로 선택**

| rfsrc\_sel | 선택 데이터 | 사용 예 |
| --- | --- | --- |
| 0 | ALU 결과 | ADD·ADDI 등 |
| 1 | Data Memory 읽기 데이터 | LB·LW 등 |
| 2 | 확장된 Immediate | LUI |
| 3 | PC + Immediate | AUIPC |
| 4 | PC + 4 | JAL·JALR의 복귀 주소 |

Immediate Generator는 I·S 형식의 12비트 상수를 부호 확장하고, B·J 형식은 분리된 비트를 재배치해 하위 0비트를 붙였습니다. U 형식은 상위 20비트를 배치하고 하위 12비트를 0으로 구성했습니다.

</details>

## 명령어 동작 검증

- 명령어군별 입력·기대 동작을 정한 Directed Simulation
- ALU 결과·rd 저장·메모리 주소/데이터·분기 조건·PC 변화 대조

<details>
<summary>ALU 연산·Signed/Unsigned·시프트 검증</summary>

| 확인 항목 | 입력·조건 | 확인 결과 |
| --- | --- | --- |
| SUB | 2 - 3 / 2 - 4 | -1 / -2 저장 |
| SLT / SLTU | 0xFFFF\_FFFF와 1 비교 | Signed는 1, Unsigned는 0 |
| SRL / SRA | 0xFFFF\_FFFF를 1비트 우측 시프트 | 0x7FFF\_FFFF / 0xFFFF\_FFFF |
| SLL | 2를 4비트 좌측 시프트 | 0x0000\_0020 |

- **R-Type 연산 및 Register File 저장 파형**

[상세 그림 — Notion](https://app.notion.com/p/3d423ec941b7815d9825ccf432bcf0bf#95179c462b324cca92d442b1375ffb51)

목적 레지스터에 저장된 값으로 연산 결과를 확인했습니다. 동일한 비트 패턴도 Signed/Unsigned 해석에 따라 비교 결과가 달라지고, SRL과 SRA는 상위 비트를 채우는 방식이 다름을 확인했습니다. I-Type은 Immediate를 선택해 같은 연산 경로를 검증했습니다.

</details>

<details>
<summary>Load/Store 주소 계산과 Sign·Zero Extension</summary>

ALU에서 `rs1 + Immediate`로 접근 주소를 계산했습니다. Store는 rs2 데이터를 메모리에 기록하고, Load는 선택한 데이터를 확장해 rd에 저장하도록 연결했습니다.

| 명령어 | 접근 폭 | rd에 저장하는 데이터 |
| --- | --- | --- |
| LB | 8비트 | Sign Extension |
| LH | 16비트 | Sign Extension |
| LW | 32비트 | Word 데이터 |
| LBU | 8비트 | Zero Extension |
| LHU | 16비트 | Zero Extension |

Store는 SB·SH·SW에 대해 주소 Offset과 저장 위치를 확인했습니다. Load는 같은 0xFF·0xFFFF 데이터가 Signed 명령에서는 0xFFFF\_FFFF로, Unsigned 명령에서는 0x0000\_00FF·0x0000\_FFFF로 저장되는지 비교했습니다.

- **Load 접근 주소·데이터 선택·확장 결과 파형**

[상세 그림 — Notion](https://app.notion.com/p/3d423ec941b7815d9825ccf432bcf0bf#7ea34934a7aa4d3b9a5c38fc623ab808)

</details>

<details>
<summary>Branch·JAL·JALR의 PC 변경과 복귀 주소</summary>

| 동작 | 다음 PC | 함께 확인한 항목 |
| --- | --- | --- |
| 순차 실행 | PC + 4 | 다음 명령어 진행 |
| Branch 조건 성립 | PC + Immediate | branch와 b\_taken, 분기 목적지 |
| Branch 조건 불성립 | PC + 4 | 순차 경로 유지 |
| JAL | PC + Immediate | rd에 PC+4 저장 |
| JALR | (rs1 + Immediate) & \~1 | rd에 PC+4 저장, 목적지 bit 0 제거 |

- **Branch 비교 결과와 PC 변화 파형**

[상세 그림 — Notion](https://app.notion.com/p/3d423ec941b7815d9825ccf432bcf0bf#6a4bb5a82ea7471f924bb502430f4048)

Immediate를 8로 둔 시나리오에서 조건이 성립하면 PC가 8만큼, 불성립하면 4만큼 증가하는지 확인했습니다. 같은 0xFFFF\_FFFF와 1을 비교해 BLT와 BLTU의 Signed/Unsigned 차이도 확인했습니다.

JAL·JALR은 점프 목적지 선택과 PC+4 저장을 함께 확인하고, Bubble Sort의 실제 함수 호출·복귀 흐름에서도 추적했습니다.

</details>

## Bubble Sort 프로그램 검증

- C 코드를 RV32I Assembly로 변환해 Instruction Memory에서 실행
- `main → sort → swap → sort → main`의 인자 전달·원소 교환·스택 복구 추적

<details>
<summary>C 코드·배열 초기화·반복 범위 분석</summary>

- **원본 코드의 핵심 부분**

```c
int Num[6] = {3, 5, 9, 1, 7};
int a = 0;
sort(Num, 5);
a = 0x12345678;
while (1);
```

```c
void sort(int *pNum, int size)
{
    for (int i = 0; i < size; i++) {
        for (int j = 0; j < size - i; j++) {
            if (pNum[j] > pNum[j + 1]) {
                swap(&pNum[j], &pNum[j + 1]);
            }
        }
    }
}
```

`Num[6]`에 초기값 5개를 지정했으므로 마지막 원소는 0으로 초기화됩니다. 실제 초기 배열은 `3, 5, 9, 1, 7, 0`입니다.

이 코드의 반복 조건은 `j < size - i`입니다. size가 5일 때 첫 번째 순회는 j=0\~4가 되어 Num\[0\]부터 Num\[5\]까지 인접한 여섯 원소를 비교합니다. 따라서 `sort(Num, 5)`와 최종 여섯 원소의 정렬 결과가 연결됩니다.

배열 접근에서는 인덱스를 2비트 좌측 시프트해 4바이트 Offset을 만들고 시작 주소에 더했습니다. 배열 값 자체와 원소의 주소를 구분해 Load/Store와 swap 인자 전달을 분석했습니다.

</details>

<details>
<summary>ABI 레지스터와 Stack Frame·메모리 배치</summary>

| 레지스터 | ABI 이름 | 이 프로그램에서의 용도 |
| --- | --- | --- |
| x1 | ra | 함수 복귀 주소 |
| x2 | sp | 스택 공간 확보·복구 |
| x8 | s0 / fp | 지역 변수 접근의 기준 주소 |
| x10 | a0 | 배열 또는 원소의 시작 주소 전달 |
| x11 | a1 | 반복 상한 또는 두 번째 원소 주소 전달 |

- **함수별 Stack Pointer 변화**

| 함수 | sp 진입 전 → 확보 후 | 설정한 s0 / fp |
| --- | --- | --- |
| main | 0x100 → 0x0D0 (256 → 208) | 0x100 (256) |
| sort | 0x0D0 → 0x0A0 (208 → 160) | 0x0D0 (208) |
| swap | 0x0A0 → 0x070 (160 → 112) | 0x0A0 (160) |

main의 배열 24바이트, 변수 a 4바이트, ra·s0 8바이트를 합하면 36바이트이며, 원본 Assembly는 48바이트 프레임을 확보했습니다. sort와 swap도 각각 48바이트 프레임에 ra·s0·인자·지역 변수를 저장했습니다. 함수 복귀 시 저장한 레지스터와 sp가 이전 값으로 복원되는지 확인했습니다.

- **main의 48바이트 스택 확보와 sp·s0 변화 파형**

[상세 그림 — Notion](https://app.notion.com/p/3d423ec941b7815d9825ccf432bcf0bf#61fed19e488e489b9c1a14832521bcc8)

- **관찰한 주요 Data Memory 주소**

| 주소 / Word 인덱스 | 저장 내용 |
| --- | --- |
| 0xD4\~0xE8 / 53\~58 | Num\[0\]\~Num\[5\], 4바이트 간격 |
| 0xEC / 59 | main의 지역 변수 a |
| 0xA8 / 42 | sort의 size = 5 |
| 0xAC / 43 | sort의 pNum = 0xD4 |
| 0xB8 / 46, 0xBC / 47 | sort의 j, i |
| 0x78 / 30, 0x7C / 31 | swap으로 전달한 두 원소의 주소 |
| 0x8C / 35 | swap의 temp |

파형의 `data_ram[index]`는 Word 인덱스이며, 바이트 주소는 인덱스에 4를 곱한 값으로 해석했습니다.

</details>

<details>
<summary>sort 호출·인자 전달·swap·복귀 파형</summary>

- **sort 호출 시 a0·a1 전달과 JAL·ra·sp 변화**

[상세 그림 — Notion](https://app.notion.com/p/3d423ec941b7815d9825ccf432bcf0bf#6dd0beff77e9420582dab91a984e9c61)

배열 시작 주소 212(0xD4)를 a0에, 반복 상한 5를 a1에 전달했습니다. PC가 100에서 sort 시작 주소 120으로 이동하고, 복귀 주소 104가 ra에 저장되는지 확인했습니다.

중첩 반복문의 비교 결과에 따라 swap을 호출했습니다. 값 비교에는 Load한 데이터를 사용하고, swap에는 `&pNum[j]`, `&pNum[j+1]`의 주소를 전달했습니다.

- **swap의 원소 주소·메모리 교환 및 스택 복구 파형**

[상세 그림 — Notion](https://app.notion.com/p/3d423ec941b7815d9825ccf432bcf0bf#3e5b2562d748478bbdeef50d699a81b0)

위 사례에서 두 원소 주소 220(0xDC), 224(0xE0)를 전달하고 temp를 거쳐 Num\[2\]와 Num\[3\]의 9와 1을 교환했습니다. swap 중 sp는 160→112로 변하고, sort로 복귀하면 160으로 복구되는지 확인했습니다.

</details>

## 실행 결과

- **정렬:** `3, 5, 9, 1, 7, 0` → `0, 1, 3, 5, 7, 9`
- **함수 복귀:** sort 종료 후 PC 328→104, main 복귀와 a=`0x12345678` 저장
- **종료 흐름:** `while(1)` 자기 분기로 PC 116(0x74) 유지

**Bubble Sort 최종 배열·main 복귀·a 저장 결과 파형**

[상세 그림 — Notion](https://app.notion.com/p/3d423ec941b7815d9825ccf432bcf0bf#a3455adc329544f1b4e350b7406b181e)

정렬 배열·main 복귀·a 저장값을 실행 파형에서 대조

## 점검·수정

- **기능 점검:** JALR 목적지 bit 0 처리·x0 쓰기 보호 확인
- **구문 오류:** 명령어 추가 후 Include Header까지 점검해 Syntax Error 수정

<details>
<summary>JALR 목적지 bit 0 처리와 x0 보호</summary>

- **JALR 점프 주소 처리 코드**

[상세 그림 — Notion](https://app.notion.com/p/3d423ec941b7815d9825ccf432bcf0bf#524fe035ec3a49268d2c0e622706327a)

```verilog
assign pc_imm = (imm_extend + pc_jalr) & ~32'd1;
```

JALR 경로는 rs1을 기준 주소로 선택하고, Immediate를 더한 결과의 bit 0을 0으로 처리했습니다. 점프 목적지와 PC+4 복귀 주소 저장을 함께 확인했습니다.

- **x0 쓰기 차단 및 읽기 값 유지 코드**

[상세 그림 — Notion](https://app.notion.com/p/3d423ec941b7815d9825ccf432bcf0bf#8935ad95e5854051acf4eb2dd7406c69)

```verilog
always @(posedge clk) begin
    if (rf_we && (waddr != 5'd0)) begin
        register_file[waddr] <= wdata;
    end
end
assign rdata1 = (raddr1 != 0) ? register_file[raddr1] : 32'd0;
assign rdata2 = (raddr2 != 0) ? register_file[raddr2] : 32'd0;
```

x0을 목적 레지스터로 지정하면 쓰기를 차단하고, 읽기 주소가 0이면 상수 0을 출력하도록 구성했습니다.

</details>

<details>
<summary>명령어 추가 후 Syntax Error 점검</summary>

여러 명령어를 추가한 뒤 Syntax Error가 발생했습니다. 수정 중인 RTL만 확인하던 범위를 Include Header까지 넓혀 문법 오류를 찾아 수정했습니다.

`rv32i_datapath.sv`에서 사용하는 `define.vh`처럼 명령어·연산 코드 정의가 포함된 파일도 함께 점검하고, 명령어 추가 이후 시뮬레이션 결과를 다시 확인했습니다.

</details>


## 관련 링크

- [RV32I RTL·Testbench](https://github.com/Min-star-prog/ondeviceai/tree/main/linux/20260527_RV32I_singlecycle_source_code)

[← 전체 프로젝트](../README.md#프로젝트)

