# TCAD 교육과정 및 반도체 설계 툴 체인 정리

## 1. 교육 개요

| 항목 | 내용 |
|---|---|
| 주제 | TCAD (반도체 소자·공정 시뮬레이션) |
| 대상 | 취준생, 대학원생 |
| 기간 | 4주 (주 5일, 총 20일) |
| 일과 | 하루 8시간 (점심 포함) → 실질 7시간 |
| 총 시간 | 약 140시간 |
| 일과 구성 | 이론·시연 3시간 + 실습 4시간 |
| 툴 방침 | Synopsys Sentaurus는 실습에서 제외하고 개념 비교로만 소개 |

---

## 2. 교육용 툴 구성

| 툴 | 역할 | 비고 |
|---|---|---|
| **Silvaco (Athena/Atlas)** | 공정+소자 통합 시뮬레이션 메인 툴 | 교육용/학술 라이선스 이용 |
| **DEVSIM** (오픈소스, 파이썬) | 지배방정식 직접 다루기, 수강생 개인 PC 실습 | 비용 부담 없음 |
| **Sentaurus** (개념 비교) | SDE → Sprocess → Sdevice → SVisual 흐름 소개 | 스크립트 리딩만, 실습 없음 |

---

## 3. 4주 커리큘럼

### 1주차: 기초와 환경 (소자 시뮬레이션 입문)

| 요일 | 내용 |
|---|---|
| 월 | 반도체 물리 복습, TCAD 개념, 툴 설치 (Silvaco, DEVSIM) |
| 화 | 메쉬 생성, 도핑 정의, 지배방정식 (Poisson, 연속방정식) |
| 수 | PN 다이오드 I-V, C-V |
| 목 | 바이어스 조건, 수렴 문제 해결법 |
| 금 | 쇼트키 다이오드와 BJT 실습 + 주간 퀴즈 |

### 2주차: 공정 시뮬레이션

| 요일 | 내용 |
|---|---|
| 월 | 산화 (Deal-Grove), 증착, 식각 |
| 화 | 이온주입 (프로파일, 채널링) |
| 수 | 확산, 어닐링, 접합 깊이 |
| 목 | 공정 흐름 통합 (NMOS 전체 공정 스크립트) |
| 금 | 공정 → 소자 연계 실습 + 주간 과제 |

### 3주차: MOSFET 특성과 심화

| 요일 | 내용 |
|---|---|
| 월 | MOSFET Id-Vg, Id-Vd, 문턱전압 추출 |
| 화 | 채널 길이 스케일링, 단채널 효과, DIBL |
| 수 | 산화막 두께, 도핑, 접합 깊이 민감도 분석 |
| 목 | 이동도 모델, 캘리브레이션 개념 |
| 금 | Sentaurus 비교 데이 (스크립트 구조 리딩) + 파이썬 자동화 (파라미터 스윕) |

### 4주차: 프로젝트

| 요일 | 내용 |
|---|---|
| 월 | 주제 선정과 설계 (목표 사양 설정) |
| 화~목 | 시뮬레이션, 최적화, 결과 정리 |
| 금 | 발표와 리뷰, 포트폴리오 정리 |

### 운영 포인트

- 3주차 금요일의 **파이썬 자동화**는 취준생과 대학원생 모두에게 가장 실용적인 파트입니다.
- 4주차 프로젝트는 "목표 사양을 정하고 공정 변수로 달성하기"로 하면 면접용 스토리가 됩니다.
- 취준생에게는 "공정 변수가 소자 특성을 어떻게 바꾸는가"를 설명하는 능력이 면접 포인트입니다.
- 대학원생은 4주차에 FinFET, GAA, 스트레인 같은 심화 주제를 선택 과제로 두면 수준차를 흡수할 수 있습니다.

---

## 4. 반도체 설계·제조 툴 맵

> **참고:** Virtuoso는 TCAD가 아니라 Cadence의 아날로그/커스텀 IC 설계 툴(회로도, 레이아웃)입니다. TCAD는 소자·공정 물리를 다루고, Virtuoso는 그 결과로 나온 모델을 이용해 회로를 설계합니다.

### 4.1 공정/소자 (TCAD)

- Synopsys Sentaurus
- Silvaco Victory (Athena/Atlas의 후속)
- 오픈소스: DEVSIM 등
- 용도: 공정 레시피 보정, 신소자(FinFET, GAA) 개발

### 4.2 컴팩트 모델 / SPICE

- 모델 추출: Keysight IC-CAP, Synopsys MBP
- 시뮬레이터: Synopsys HSPICE, Cadence Spectre, Siemens Eldo, 오픈소스 ngspice
- 역할: TCAD 결과를 회로용 모델(BSIM 등)로 연결

### 4.3 아날로그/커스텀 설계

- Cadence Virtuoso (사실상 표준)
- Synopsys Custom Compiler, Siemens Tanner
- 오픈소스: Magic, Xschem, KLayout

### 4.4 디지털 설계 (RTL → 레이아웃)

- 시뮬레이션: Synopsys VCS, Cadence Xcelium, Siemens Questa (오픈소스: Verilator)
- 논리합성: Synopsys Design Compiler, Cadence Genus (오픈소스: Yosys)
- 배치배선(P&R): Cadence Innovus, Synopsys IC Compiler II / Fusion Compiler (오픈소스: OpenROAD)

### 4.5 검증 / 사인오프

- 물리검증(DRC/LVS): Siemens Calibre (업계 표준), Synopsys IC Validator
- 타이밍: Synopsys PrimeTime, Cadence Tempus
- 전력/IR: Ansys RedHawk, Cadence Voltus
- 형식검증, 등가성 검사: Synopsys Formality, Cadence Conformal

### 4.6 제조 연계 / 수율

- 마스크/OPC: Siemens Calibre, Synopsys Proteus
- 공정 제어, 수율 분석: 팹 자체 시스템과 전용 솔루션

### 4.7 패키지 / 보드

- Cadence Allegro, Siemens Xpedition, Altium
- 열/구조 해석: Ansys

### 시장 구조

상용 3사(Synopsys, Cadence, Siemens EDA)가 대부분을 차지하며, Silvaco와 Ansys가 틈새를 채웁니다.

---

## 5. 케이스별 진행 프로세스와 툴

### 케이스 1: 디지털 SoC/ASIC (예: MCU, NPU)

| 단계 | 내용 | 툴 |
|---|---|---|
| 1 | 스펙·아키텍처 | 문서, SystemC/파이썬 모델 |
| 2 | RTL 설계 | Verilog/SystemVerilog |
| 3 | 기능 검증 | VCS / Xcelium / Questa (오픈: Verilator) |
| 4 | 논리합성 | Design Compiler / Genus (오픈: Yosys) |
| 5 | DFT·스캔 삽입 | Synopsys DFT Compiler, Cadence Modus |
| 6 | 배치배선 (P&R) | Innovus / Fusion Compiler (오픈: OpenROAD) |
| 7 | 사인오프 | PrimeTime/Tempus (타이밍), Voltus/RedHawk (전력·IR), Calibre (DRC/LVS) |
| 8 | Tape-out | GDSII → 팹 |

### 케이스 2: 아날로그/혼성 IC (예: LDO, ADC, PLL)

| 단계 | 내용 | 툴 |
|---|---|---|
| 1 | 스펙 정의, 토폴로지 선정 | - |
| 2 | 회로도 입력 | Virtuoso Schematic (오픈: Xschem) |
| 3 | 회로 시뮬레이션 (PVT 코너, 몬테카를로 포함) | Spectre / HSPICE (오픈: ngspice) |
| 4 | 레이아웃 | Virtuoso Layout (오픈: Magic, KLayout) |
| 5 | 물리검증 | Calibre DRC/LVS |
| 6 | 기생 추출 (PEX) | Calibre xRC, StarRC |
| 7 | 포스트레이아웃 시뮬레이션 | 기생 포함 Spectre 재검증 |
| 8 | Tape-out | - |

### 케이스 3: 신공정/신소자 개발 (예: GAA 트랜지스터)

| 단계 | 내용 | 툴 |
|---|---|---|
| 1 | 구조 설계, 공정 흐름 정의 | - |
| 2 | 공정 시뮬레이션 | Sentaurus Process / Silvaco Athena |
| 3 | 소자 시뮬레이션 | Sentaurus Device / Silvaco Atlas (오픈: DEVSIM) |
| 4 | 실측 데이터와 캘리브레이션 | 팹 측정 장비 데이터 |
| 5 | 컴팩트 모델 추출 | IC-CAP, MBP (BSIM-CMG 등) |
| 6 | PDK 구성 | 모델, 디자인룰, 셀 라이브러리 |
| 7 | 회로 설계팀에 PDK 제공 | 이후 케이스 1·2로 연결 |

이 케이스가 **TCAD 과정이 전체 흐름에서 차지하는 위치**를 보여줍니다.

### 케이스 4: 오픈소스 교육용 칩 (예: 소형 RISC-V)

| 단계 | 내용 | 툴 |
|---|---|---|
| 1 | RTL 작성 | Verilog |
| 2 | 시뮬레이션 | Verilator / Icarus + GTKWave |
| 3 | 합성 → P&R → 사인오프 | OpenLane (Yosys + OpenROAD + Magic + KLayout 통합) |
| 4 | 공정 | SkyWater 130nm 또는 IHP 130nm 오픈 PDK |
| 5 | 아날로그 부분 | Xschem + ngspice |
| 6 | 실제 제작 | 셔틀 프로그램 (Tiny Tapeout 등) |

라이선스 없이 RTL부터 GDS까지 전 과정을 경험하기에 가장 좋습니다.

---

## 6. 전체 흐름 요약

```
TCAD (케이스 3)
   ↓
컴팩트 모델 / PDK
   ↓
아날로그 설계 (케이스 2)  /  디지털 설계 (케이스 1)
   ↓
검증 · 사인오프 (Calibre, PrimeTime 등)
   ↓
Tape-out → 팹 제작
```

---

## 7. 다음 단계 제안

- 4주차 마지막 날에 **"산업 툴 체인 오리엔테이션"** 강의로 5장 내용을 활용
- 케이스 4를 기반으로 **TCAD 과정 뒤 2주 확장 과정(오픈소스 RTL-to-GDS)** 구성
- 1주차 상세 실습 스크립트 및 평가표 작성
