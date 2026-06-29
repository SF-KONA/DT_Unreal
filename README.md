# HMGICS Final Process Digital Twin

## 프로젝트 개요

본 프로젝트는 **HMGICS(Hyundai Motor Group Innovation Center in Singapore)의 셀 생산 방식**을 참고하여, 자동차 생산 공정 중 **파이널 공정 영역**을 Unreal Engine 기반 디지털 트윈 환경으로 구현한 프로젝트입니다.

기존 컨베이어 중심 생산 방식이 아닌, **AGV 기반 차량 이동 구조**와 **셀 단위 공정 흐름**을 반영하여 실제 스마트팩토리 환경과 유사한 시뮬레이션 공간을 구성하는 것을 목표로 합니다.

본 프로젝트에서는 자동차 최종 조립 단계 중 일부인 **글래스 공정, 시트 공정, 휠 공정**을 중심으로 공정 흐름을 구성하고, 체크포인트와 블루프린트를 활용하여 차량 이동, 공정 상태 변경, UI 표시 기능을 구현했습니다.

<img width="1193" height="356" alt="image" src="https://github.com/user-attachments/assets/9a4eb150-2428-4500-afea-404e6bd414e3" />

<img width="1407" height="798" alt="image" src="https://github.com/user-attachments/assets/ecae3c6e-92cf-4f8c-ab3f-38c5f854fd58" />

<img width="955" height="548" alt="Image" src="https://github.com/user-attachments/assets/6ef1ce84-a12a-4db7-8f4f-6f2db6d961ba" />

<img width="1185" height="794" alt="Image" src="https://github.com/user-attachments/assets/d9331f46-4f55-4242-a684-38ca25890f6b" />

---

## 프로젝트 목표

* HMGICS의 셀 생산 방식과 AGV 기반 물류 흐름을 Unreal Engine 환경에서 시각화
* 자동차 파이널 공정의 주요 단계인 시트, 휠, 타이어 공정을 디지털 트윈 형태로 구현
* AGV 이동 경로와 체크포인트를 활용한 공정 진행 흐름 구성
* 블루프린트를 활용한 차량 상태 변경, 공정 상태 관리, UI 팝업 기능 구현
* 파이프, 그리퍼, 설비 프레임, 작업 구역 등 공장 환경 오브젝트를 배치하여 실제 생산 현장과 유사한 공간 구성

---

## 참고 배경

HMGICS는 기존의 일자형 컨베이어 생산 방식에서 벗어나, **셀 기반 생산 방식**과 **AGV 기반 이동 구조**를 활용하는 스마트 제조 환경을 지향합니다.

본 프로젝트는 이러한 생산 방식에서 착안하여, 차량이 AGV를 통해 각 공정 셀로 이동하고, 공정별 상태가 변경되는 흐름을 Unreal Engine으로 구현했습니다.

참고 자료:
https://www.hyundaimotorgroup.com/ko/story/CONT0000000000122356

---

## 주요 구현 범위

### 1. 파이널 공정 구성

본 프로젝트의 공정 흐름은 다음과 같이 구성됩니다.

```text
AGV 출발
↓
Seat Process
↓
Wheel Process
↓
Tire Process
↓
Complete
```

각 공정은 체크포인트를 기준으로 구분되며, 차량이 특정 지점에 도달하면 해당 공정 단계로 상태가 변경됩니다.

---

### 2. AGV 기반 차량 이동

* AGV를 활용하여 차량이 공정 구역을 따라 이동하도록 구성
* 공정별 체크포인트를 배치하여 현재 차량 위치와 공정 단계를 구분
* 차량 이동 흐름을 통해 HMGICS의 셀 생산 방식과 유사한 구조 표현

---

### 3. 체크포인트 기반 공정 상태 관리

공정별 체크포인트를 활용하여 차량의 현재 공정 상태를 관리합니다.

예시 공정 상태:

```text
대기
진행 중
완료
```

체크포인트 도달 여부에 따라 차량의 현재 공정이 변경되며, 이후 UI 또는 오브젝트 상태 표시와 연동할 수 있도록 구성했습니다.

---

### 4. 블루프린트 기반 기능 구현

Unreal Engine의 블루프린트를 활용하여 공정 흐름과 상태 변경 로직을 구현했습니다.

주요 기능 예시:

* 차량 또는 AGV 이동 제어
* 체크포인트 도달 감지
* 현재 공정 단계 변경
* 공정 상태 값 변경
* 차량 정보 UI 팝업 표시
* 공정 상태에 따른 텍스트 및 색상 변경

---

### 5. 차량 정보 UI

차량 또는 AGV를 클릭했을 때 현재 공정 정보를 확인할 수 있는 UI를 구성했습니다.

UI에서 표시하는 정보 예시:

* 차량 ID
* 현재 공정
* 공정 상태
* 다음 공정
* 완료 여부

이를 통해 단순한 3D 공장 환경이 아니라, 차량의 상태와 공정 흐름을 확인할 수 있는 디지털 트윈 형태로 확장했습니다.

---

## 공장 환경 구성

실제 스마트팩토리 환경과 유사하게 보이도록 다음과 같은 오브젝트를 배치했습니다.

* 공정별 셀 영역
* AGV 이동 경로
* 체크포인트
* 차량 모델
* 파이프 구조물
* 그리퍼
* 설비 프레임
* 로봇 및 작업 장비
* 상태 표시용 오브젝트
* 공정 구역 라인 및 색상 표시

---

## 기술 스택

| 구분               | 사용 기술                      |
| ---------------- | -------------------------- |
| Game Engine      | Unreal Engine              |
| Visual Scripting | Blueprint                  |
| 3D Environment   | Unreal Level Design        |
| UI               | Unreal UMG Widget          |
| Simulation Logic | Blueprint Event / Function |
| Version Control  | Git / GitHub               |

---

## 프로젝트 구조

```text
DT_Unreal
└─ DT_Project
   ├─ Config
   ├─ Content
   │  ├─ Blueprints
   │  ├─ Levels
   │  ├─ Materials
   │  ├─ Meshes
   │  ├─ UI
   │  └─ Vehicles
   └─ DT_Project.uproject
```

---

## 주요 폴더 설명

| 폴더           | 설명                          |
| ------------ | --------------------------- |
| `Blueprints` | 공장 설비, 상태 관리, 상호작용 관련 블루프린트 |
| `Levels`     | 공장 환경 및 시뮬레이션 레벨            |
| `Materials`  | 바닥, 라인, 셀 영역 등 머티리얼         |
| `Meshes`     | 공장 구성에 사용되는 3D 메시           |
| `UI`         | 차량 정보 팝업 등 UMG 위젯           |
| `Vehicles`   | AGV, 차량, 체크포인트 관련 에셋        |

---

## 핵심 시뮬레이션 흐름

```text
1. 차량이 AGV에 의해 이동
2. AGV가 공정별 체크포인트에 도달
3. 체크포인트에 따라 현재 공정 상태 변경
4. 차량 정보 UI에 현재 상태 반영
5. 공정 완료 후 다음 공정으로 이동
6. 모든 공정 완료 시 Complete 상태로 변경
```

---

## 실행 방법

1. Unreal Engine을 실행합니다.
2. `DT_Project/DT_Project.uproject` 파일을 엽니다.
3. `Content/Levels` 폴더에서 메인 레벨을 실행합니다.
4. Play 버튼을 눌러 시뮬레이션을 확인합니다.
5. 차량 또는 AGV를 클릭하여 현재 공정 정보를 확인합니다.

---

## 기대 효과

* HMGICS의 셀 생산 방식과 AGV 기반 생산 흐름을 직관적으로 이해할 수 있음
* 자동차 파이널 공정의 이동 및 상태 변화를 3D 환경에서 시각적으로 확인 가능
* 블루프린트 기반으로 공정 로직을 구성하여 추후 공정 추가 및 상태 확장이 용이함
* 실제 스마트팩토리 디지털 트윈 프로젝트로 확장 가능한 기반 구조 확보

---

## 팀 프로젝트 의의

본 프로젝트는 Unreal Engine과 Blueprint를 활용하여 단순한 3D 시각화가 아닌, **공정 흐름, 차량 이동, 상태 변화, UI 표시가 연결된 디지털 트윈 시뮬레이션**을 구현하는 데 중점을 두었습니다.

팀 단위로 공장 환경 구성, 차량 이동, 공정 로직, UI, 에셋 배치 등을 분담하여 HMGICS의 스마트 제조 환경을 디지털 공간에서 재현하고자 했습니다.
