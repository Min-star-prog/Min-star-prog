# 산화물 TFT 전기적 특성 및 신뢰성 평가

[전체 프로젝트](../README.md#프로젝트) · [Notion 상세·시연](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7)

경희대학교 ADRC · 개인 · 2024.01.02 – 2024.02.27

> **산화물 TFT의 전기적 특성과 바이어스·온도에 따른 변화를 측정·비교한 ADRC 인턴 프로젝트**

## 프로젝트 개요

- **대상:** ZnO·IGZO 계열 TFT, 시료·채널 크기·위치별 특성 비교
- **평가:** Transfer·Output·Hysteresis, PBS/NBS, 온도 의존성

**측정 시료와 위치**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#a9cf9fd0feec4da387e5725bffb59ac8)

시료 영역·광학 이미지·개별 소자 위치를 구분해 측정 결과 관리

<details>
<summary>소자 구조·측정 위치 확인</summary>

ZnO·IGZO 계열 산화물 TFT와 MgZrOx Gate Insulator를 사용한 시료를 측정했습니다. 시료 구조와 제작 조건을 이해한 뒤, 같은 시료 안에서도 P1\~P4 영역 및 Left/Right 세부 위치를 구분했습니다.

구조 자료에는 Glass Substrate·Mo Gate·Gate Insulator·c-IGZO Active Layer·Mo S/D가 표시돼 있습니다. 이 구조도는 측정 대상의 제작 배경을 설명하는 자료입니다.

측정 위치 사진과 광학 이미지를 사용해 시료·영역·채널 크기를 기록하고, 서로 다른 위치의 곡선을 혼동하지 않도록 식별자를 유지했습니다.

**측정 대상 c-IGZO TFT 구조·제작 배경**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#110e80c2265646ffa166fb50fbf04c5f)

연구실에서 제작한 측정 시료의 소자 구조·제작 조건

</details>

## 담당 역할

- **소속·기간:** 경희대학교 ADRC · 2024.01.02 – 2024.02.27 · 200시간
- 제작된 소자의 전기적 측정·조건별 비교·연구 발표
- 이동도·문턱전압·SS·누설·Memory Window 지표 정리

## 기본 특성·채널 크기 비교

- **측정:** 채널 Width·Length와 위치별 Transfer·Output 비교
- **지표:** 이동도·문턱전압·SS·히스테리시스 정리

<details>
<summary>채널 길이 변화·기본 전기적 지표</summary>

Width를 20 µm로 두고 Length를 바꾼 TFT의 Transfer·Output과 전기적 지표를 비교했습니다.

| W/L (µm) | μFE (cm²/V·s) | Vth (V) | SS (V/dec) |
| --- | --- | --- | --- |
| 20/3 | 11.60 | 1.60 | 0.06 |
| 20/4 | 22.47 | -0.40 | 0.11 |
| 20/6 | 24.10 | 0.20 | 0.09 |
| 20/9 | 26.18 | 1.20 | 0.07 |
| 20/10 | 24.83 | 1.90 | 0.06 |

위 값은 1주차 측정 결과로 정리한 표입니다. 이후 다른 재료·시료의 결과와 구분해, 채널 크기별 특성을 비교하는 기초 자료로 활용했습니다.

**채널 Length별 Transfer·Output·지표**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#fdd474e43e5c4245b2317ea63334e2fc)

W=20 µm에서 Length를 바꿔 측정한 곡선과 전기적 지표를 함께 정리했습니다.

이동도·문턱전압·SS를 함께 확인하며, 한 지표만으로 소자의 전체 특성을 판단하지 않도록 했습니다.

</details>

<details>
<summary>Mg-doped ZnO TFT 특성 측정</summary>

2주차에는 10% Mg-doped ZnO TFT의 여러 지점을 측정했습니다. 원본 자료에 표시된 350°C Spray Pyrolysis는 시료의 제작 조건이며, 직접 담당한 범위는 제작된 소자의 특성 측정과 정리입니다.

W/L=20/10 µm 시료의 L/R 위치별 Transfer 곡선을 비교하고, 이동도·문턱전압·SS를 표로 정리했습니다.

측정 위치별 곡선과 지표를 함께 제시해, 같은 W/L 조건에서도 지점별 차이가 있음을 확인했습니다.

**10% Mg-doped ZnO TFT 지점별 측정**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#4ba1d5e247bc4b178262c9c8775a94f6)

W/L=20/10 µm 소자의 여러 위치에서 Transfer 곡선과 지표를 비교한 자료입니다.

</details>

<details>
<summary>짧은 채널·Width 변화 비교</summary>

2차 시료에서 L=6·8 µm 조건과 여러 Width의 TFT를 추가로 비교했습니다. L=8 µm 그룹의 원본 표는 다음과 같습니다.

| W/L (µm) | μFE (cm²/V·s) | Vth (V) | SS (V/dec) | Hysteresis (V) |
| --- | --- | --- | --- | --- |
| 10/8 | 20.06 | -0.10 | 0.075 | 0.05 |
| 20/8 | 17.24 | -0.15 | 0.085 | 0.00 |
| 50/8 | 14.95 | 0.00 | 0.093 | 0.00 |
| 100/8 | 11.52 | 0.05 | 0.097 | 0.00 |

동일 Length에서 Width를 바꾼 결과와 각 Transfer·Output을 함께 확인했습니다. 관찰한 차이를 채널 크기별 측정 결과로 기록하고, 하나의 원인으로 단정하지 않았습니다.

**L=8 µm에서 Width별 소자 특성**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#3a6204665c5942f1aa0e024e041c0607)

Width를 10·20·50·100 µm로 구분해 Transfer·Output과 지표를 비교한 원본입니다.

L=6 µm 그룹에는 미측정 항목도 있어, 측정한 값과 빠진 조건을 구분했습니다.

</details>

## IGZO 시료별 특성 비교

- **시료 구분:** IGZO·c-IGZO의 1차·2차 샘플 비교
- **확인 지표:** Memory Window·누설·이동도·문턱전압·SS

<details>
<summary>IGZO 시료별 Memory Window·누설 특성 비교</summary>

MgZrOx Gate Insulator를 사용한 IGZO TFT에서 정·역방향 Sweep에 따른 히스테리시스와 Memory Window를 비교했습니다.

원본의 1차·2차 샘플 비교표에는 VGS=±5 V 조건에서 그룹 평균 Memory Window가 0.43 V에서 1.06 V로 달라진 결과와 Ioff 비교가 정리돼 있습니다. Transfer 곡선의 기울기 변화도 함께 확인했습니다.

**비교 범위:** 1차·2차의 서로 다른 시료 측정값

시료별 평균과 개별 위치의 곡선을 함께 살펴보고, 이후에는 주사 시간을 바꿔 Memory Window가 어떻게 달라지는지 추가 비교했습니다.

**IGZO 1차·2차 시료 비교**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#f03e582cda204222b36d1991a7d6b58d)

Memory Window·Ioff 비교와 Transfer 기울기 변화를 정리한 원본입니다. 샘플 간 비교 결과로 제시합니다.

</details>

<details>
<summary>c-IGZO 1차 시료·지표 요약</summary>

5주차에는 50% Mg-doped ZrOx Gate Insulator 위의 c-IGZO TFT를 측정했습니다. W/L=20/10·50/10 µm와 L=8·20 µm 시료의 Transfer·Output·Hysteresis를 정리했습니다.

원본의 그룹 종합표에는 평균 μFE 14.39 cm²/V·s, Vth -2.10 V, SS 약 0.15 V/dec가 제시돼 있습니다. 각 그룹의 측정 지점 수와 개별 곡선을 함께 기록했습니다.

이 평균은 해당 주차에 측정한 그룹의 요약값이며, 이후 2차 시료나 온도·스트레스 조건의 결과와 구분했습니다.

**c-IGZO 1차 시료 그룹별 특성 요약**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#cee6dcf473994b8780272c263c957675)

W/L과 측정 지점 수를 구분해 이동도·문턱전압·SS·히스테리시스 등을 정리했습니다.

</details>

<details>
<summary>c-IGZO 2차 시료·W/L·위치별 비교</summary>

2차 시료에서는 W/L=20/10 µm와 50/10 µm 소자를 여러 위치에서 측정하고, Transfer·Output과 개별 지표를 함께 정리했습니다. Transfer 자료에는 VDS=0.1·0.3·0.6·1.0 V 조건의 곡선이 표시돼 있습니다.

| 2차 시료 그룹 | 측정 위치 수 | 평균 μFE (cm²/V·s) | 평균 Vth (V) | 평균 SS (V/dec) | 평균 Hysteresis (V) |
| --- | --- | --- | --- | --- | --- |
| W/L=20/10 µm | 15 | 17.44 | -0.18 | 0.116 | 0.02 |
| W/L=50/10 µm | 16 | 16.10 | -0.09 | 0.131 | 0.01 |

20/10 µm 그룹의 Transfer와 Output을 대응시키고, 50/10 µm 그룹에서는 위치별 차이와 평균을 함께 비교했습니다.

**c-IGZO 2차 시료 Transfer · W/L=20/10 µm**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#9737ed22f0464c5a8ab9d34e8e37c389)

15개 위치의 Transfer와 전기적 지표를 기록한 자료입니다.

**c-IGZO 2차 시료 Output · W/L=20/10 µm**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#3b8fee9e11614d08a6ae6b3217815426)

동일 소자 식별자에 대응하는 Output 곡선을 비교했습니다.

**c-IGZO 2차 시료 Transfer · W/L=50/10 µm**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#fe67f82432694c22a0d929536cc31b54)

16개 위치의 Transfer와 그룹 평균을 함께 정리했습니다.

</details>

## 주사 시간에 따른 Memory Window

- **조건:** Fast 0.64분·Slow 5분 비교
- **1차 샘플:** 평균 0.56 → 1.05 V
- **2차 샘플:** 평균 1.06 → 0.70 V

**주사 시간별 비교 결과**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#9526b11034e244c1a99f4c28edea6257)

동일한 조건 변화에도 샘플별 Memory Window 변화 방향이 다름을 관찰

<details>
<summary>주사 시간에 따른 Memory Window 변화</summary>

Fast 0.64분·Slow 5분 조건의 샘플별 Memory Window 비교

| 시료 | Fast · 0.64분 평균 MW | Slow · 5분 평균 MW | 변화 |
| --- | --- | --- | --- |
| 1차 샘플 | 0.56 V | 1.05 V | 증가 |
| 2차 샘플 | 1.06 V | 0.70 V | 감소 |

1차 샘플 P1\~P6·2차 샘플 P1\~P4의 평균값 비교

주사 시간이 늘어날 때 1차 샘플은 MW 증가, 2차 샘플은 감소했습니다.

</details>

## 바이어스 스트레스 평가

- **바이어스:** VGS=±5 V, 최대 3600 s 스트레스 전후 특성 비교

**PBS·NBS 시간별 Transfer 변화**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#35db1e6a7f5e4a77aeb6ea68b730bf38)

측정 지점별 곡선·문턱전압 이동 방향·크기를 함께 비교

<details>
<summary>PBS·NBS 바이어스 스트레스 평가</summary>

c-IGZO TFT에 양·음의 Gate Bias Stress를 인가하고 시간별 Transfer 변화를 비교했습니다.

| 조건 | 원본 표시 |
| --- | --- |
| PBS | VGS=+5 V |
| NBS | VGS=-5 V |
| Transfer 측정 표시 | VDS=0.1 V |
| 비교 시점 | 0·500·1000·2000·3600 s |

대표 PBS의 W/L=50/10 µm 네 지점에서는 ΔVth가 -0.50·-1.00·-0.95·+0.15 V로 표시돼 있습니다. NBS의 두 지점은 각각 -0.35 V입니다.

PBS에서도 모든 지점이 같은 방향으로 변하지 않았습니다. 평균값만으로 요약하기보다 지점별 곡선과 이동 방향을 함께 확인했습니다.

2차 시료에서는 시간에 따른 Transfer와 Output 변화도 별도로 측정했습니다. 시료와 측정 바이어스가 다른 결과는 같은 실험으로 합치지 않았습니다.

**2차 시료 PBS 전후 Transfer·Output**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#d8feefa78ff54c72a4973aec9ae009dc)

별도 시료에서 스트레스 시간에 따른 Transfer와 Output 변화를 함께 확인한 자료입니다.

</details>

## 온도 의존성 평가

- **온도:** 35\~105°C Transfer·Output 측정
- **대표 결과:** W/L=20/10 µm 소자의 Vth -1.90 → -2.55 V

<details>
<summary>35\~105°C 온도 의존성 평가</summary>

35°C부터 105°C까지 10°C 간격으로 Transfer·Output을 측정하고 이동도·문턱전압·SS·히스테리시스 변화를 정리했습니다.

| 대표 소자 | 지표 | 35°C | 105°C |
| --- | --- | --- | --- |
| P4\_Left\_1\_7 · W/L=20/10 µm | μFE (cm²/V·s) | 11.88 | 13.91 |
| P4\_Left\_1\_7 · W/L=20/10 µm | Vth (V) | -1.90 | -2.55 |
| P4\_Right\_3\_8 · W/L=50/10 µm | μFE (cm²/V·s) | 9.46 | 26.48 |
| P4\_Right\_3\_8 · W/L=50/10 µm | Vth (V) | -0.70 | -1.46 |

대표 20/10 µm 소자의 Vth 변화는 두 끝값 기준 -0.65 V이며, 50/10 µm 소자는 -0.76 V입니다. Transfer의 이동과 Output 전류 변화, 누설 영역의 변화를 함께 확인했습니다.

**온도 의존성 · W/L=20/10 µm**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#31772ccd69b2400d969ba2c75f9b3a5c)

35\~105°C에서 측정한 Transfer·Output과 지표 표입니다. 대표 Vth는 -1.90→-2.55 V로 이동했습니다.

**온도 의존성 · W/L=50/10 µm**

[상세 그림 — Notion](https://app.notion.com/p/3ff23ec941b78149a545f3218597a1a7#545b537ae6914e9b9ffa19bc9c8c7302)

온도별 Transfer·Output과 지표를 비교한 별도 대표 소자입니다. Vth는 -0.70→-1.46 V입니다.

</details>

## 분석에서 중점적으로 본 점

- 평균값과 개별 위치의 곡선을 함께 확인
- 샘플·Sweep·온도·스트레스 조건을 구분해 결과 해석

**관련 경력:** [ADRC 인턴](../BACKGROUND.md#adrc-연구실-인턴)

[← 전체 프로젝트](../README.md#프로젝트)

