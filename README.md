# Logisim Tetris

이 저장소는 Logisim으로 구현한 테트리스 회로 프로젝트입니다.

## 요구사항
- Java (Logisim 실행을 위한 환경)
- Logisim 또는 Logisim-evolution 설치

## 사용 방법
1. Logisim을 실행합니다.
2. 메뉴에서 `File -> Open`을 선택하고 저장소의 [Tetris.circ](Tetris.circ)를 엽니다.
3. 시뮬레이션을 활성화하려면 `Simulate -> Ticks Enabled` 또는 Logisim-evolution의 해당 설정을 사용하세요.
4. 회로에 연결된 스위치/버튼을 조작하여 블록을 이동하거나 회전시킵니다.

※ 구체적인 입력(왼쪽/오른쪽/회전/하강)은 회로 내 입력핀이나 패널에 구현된 스위치에 따라 달라집니다.

## 파일 목록
- [Tetris.circ](Tetris.circ) — Logisim 회로 파일
- [README.md](README.md) — 이 문서

## 주의 및 참고
- Logisim 버전 차이로 일부 동작이 다를 수 있습니다. Logisim-evolution을 권장합니다.
- 회로를 수정할 때는 원본 파일을 백업하세요.


## 회로 정보
- 메인 회로 파일: `Tetris.circ` — 게임 로직, 디스플레이 드라이버, 입력 처리 등이 포함됩니다.
- 클록(타이밍): 회로는 외부 클록(Clock 컴포넌트 또는 Logisim의 Ticks)을 사용하여 게임 속도와 타이밍을 제어합니다.
- 권장 주파수: **128 Hz** — 안정적인 게임 속도와 타이밍을 위해 이 값을 권장합니다. Logisim-evolution에서는 Clock의 `ticks per second` 또는 시뮬레이션 설정에서 주파수를 조정하세요.

## 메인 서브회로
아래는 `Tetris.circ`의 메인 회로에서 사용되는 주요 서브회로 목록과 간단한 설명입니다.

- `Xdecoder`: X(열) 좌표 디코더 — 열 선택용 신호 생성.
- `Ydecoder`: Y(행) 좌표 디코더 — 행 선택용 신호 생성.
- `Block_Control`: 블록의 위치, 이동, 회전 및 입력 처리 제어 로직.
- `GameMemory`: 게임 보드 상태(행 레지스터) 저장 및 읽기.
- `Tetromino_Rom`: 테트로미노 모양과 회전 데이터 ROM.
- `Block_Overlay`: 단일 블록을 보드에 오버레이하여 출력 행 데이터를 생성.
- `Block_Overlay_All`: 모든 블록 오버레이를 병렬로 처리해 전체 디스플레이 출력을 생성.
- `Collision_Detector`: 블록 충돌 및 경계 검사 로직.
- `Clockdevide`: 클록 분주기 — 내부 타이밍(예: SlowClock/FastClock) 생성.
- `Down_Lock`: 블록 하강 시 잠금/고정 관련 로직.
- `Block_Random_Generator`: 다음 블록을 결정하는 난수 생성기.
- `LineClear`: 행이 가득 찼는지 검사하고 라인 클리어 처리를 수행.
- `isThisFull`: 특정 행이 가득 찼는지 판단하는 헬퍼 회로.
- `MakingOffset`: 좌표 오프셋 계산 보조 회로.
- `NewRowSelector`: 라인 클리어 또는 갱신 시 새로운 행 선택기.
- `Score_Level`: 점수 집계 및 레벨 관리 로직.




