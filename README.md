# Nice! Nano (클론) 보드를 Watchman 동글로 변환하는 방법

사실 별 어려운건 없어요
(작성중)

# 준비물
## 하드웨어 (공통)

- Nice! Nano 및 클론 보드
  
## 퀵 스타트

- UF2 형식 펌웨어 파일

## 펌웨어를 직접 변환하려면

- python: https://www.python.org/downloads/
- Microsoft UF2 utils: https://github.com/microsoft/uf2
- Valve VR Radio 펌웨어 (app, 필요한 경우 softdevice 펌웨어도)

# 방법

Nice! Nano 및 클론 보드들은 USB 메모리처럼 인식되고, 간편하게 펌웨어를 교체할 수 있는 구조로 되어 있습니다. 컴퓨터에 보드를 연결하면, USB 메모리로 인식되어 내부의 파일을 볼 수 있습니다.
USB 메모리 안의 텍스트 파일을 열어서, Softdevice 버전이 무슨 버전인지 확인하세요. 6.x.x 버전이면 application 펌웨어만 필요합니다. 그렇지 않으면, 먼저 softdevice부터 플래싱해야합니다.
**시작하기 전, 반드시 내부 파일들을 모두 백업하시는 것을 추천합니다.**

## 펌웨어 플래싱
Softdevice 버전이 6.x.x: UF2 펌웨어 파일을 USB 메모리에 복사하세요. 끝입니다. 이제 SteamVR 동글이 됐어요!
