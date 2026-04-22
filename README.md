# Nice! Nano (클론) 보드를 Watchman 동글로 변환하는 방법

사실 어려운건 없어요
(작성중입니다.)
VR 동글만 만들면 된다면, 퀵 스타트에서 펌웨어 파일 받고 -> 펌웨어 플래싱으로 넘어가세요.

# 준비물
## 하드웨어 (공통)

- Nice! Nano 및 클론 보드 (Adafruit UF2 bootloader 탑재 보드)
- (https://github.com/joric/nrfmicro/wiki/Alternatives)
  
## 퀵 스타트

- UF2 형식 펌웨어 파일

## 펌웨어를 직접 변환하려면

- python: https://www.python.org/downloads/
- Microsoft UF2 utils: https://github.com/microsoft/uf2
- Valve VR Radio 펌웨어 (app, 필요한 경우 softdevice 펌웨어도)

# 방법

Nice! Nano 및 클론 보드들은 일반적으로 USB 메모리처럼 인식되고, 간편하게 펌웨어를 교체할 수 있는 구조로 되어 있습니다. 컴퓨터에 보드를 연결하면, USB 메모리로 인식되어 내부의 파일을 볼 수 있습니다.
(이는 UF2 부트로더를 사용하기 때문입니다. https://github.com/adafruit/adafruit_nrf52_bootloader)
USB 메모리 안의 텍스트 파일을 열어서, Softdevice 버전을 확인하세요. S140 - 6.x.x 버전이면 application 펌웨어만 필요합니다. 그렇지 않으면, 먼저 softdevice부터 플래싱해야합니다. (이 경우에 대해 추가 작성중)
**시작하기 전, 반드시 내부 파일들을 모두 백업하시는 것을 추천합니다.**

## 펌웨어 플래싱

- Softdevice 버전이 S140 - 6.x.x: UF2 펌웨어 파일을 USB 메모리에 복사하세요. USB 메모리가 인식되지 않고, 자동으로 VR 동글로 인식되면 끝입니다. 이제 SteamVR 동글이 됐어요!
- Softdevice 버전이 6.x.x가 아님: (작성중)

## USB 인식이 안되나요?

- DFU 모드 (펌웨어를 수정 가능한 모드)로 수동 진입해야 하는 경우가 있습니다. RST (Reset) 핀, 그리고 GND (Ground) 핀을 빠르게 (0.5초 이내 간격으로) 2번 연결시키세요. DFU 모드에 진입하면, LED가 깜빡이는 등 변화가 보입니다.
- 올바른 데이터 전송이 가능한 USB 케이블을 사용하세요.
- UF2 부트로더가 탑재되지 않은 보드일 수 있습니다. 일반적으로, 그렇지 않은 경우는 Nordic의 기본 bootloader가 탑재되어 있을 수 있습니다. NRFUtil이나 NRFConnect (https://www.nordicsemi.com/Products/Wireless/Bluetooth-Low-Energy/Development-tools)를 사용해야 할 수 있습니다. 그렇지 않은 경우, 별도로 JTAG 프로그래머가 필요할 수 있습니다.
  - 흔하지 않을 것이라고 생각합니다. 찾아보면, 대부분의 Nice! Nano 및 클론 보드들은 Adafruit UF2 부트로더를 사용합니다.
  - 보드의 불량일 수도 있습니다.
