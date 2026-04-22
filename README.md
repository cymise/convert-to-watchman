# Nice! Nano (및 클론) 보드를 Watchman 동글로 변환하는 방법

어려운건 전혀 없어요.

VR 동글을 빠르게 만들고 싶으시다면: **퀵 스타트**에서 펌웨어 파일을 받으시고 -> **플래시 방법**으로 넘어가세요.

# 준비물
## 하드웨어 (공통)

- Nice! Nano 및 클론 보드 (Adafruit UF2 bootloader 탑재 보드)
  - NRF52840 탑재 보드가 필요합니다.
- ( https://github.com/joric/nrfmicro/wiki/Alternatives )

## 퀵 스타트

- https://github.com/cymise/convert-to-watchman/blob/main/flash.uf2
  - UF2 App 펌웨어 파일입니다.
  
## 펌웨어 제작

- https://github.com/ugokutennp/watchman-uf2
  - 이곳을 참고하여 동글 펌웨어를 제작합니다.
    - 요구 사항: SteamVR이 설치된 Windows PC
    - FW_gen.bat을 실행하면 App 펌웨어가 제작됩니다. (중요한 Valve VR Radio 펌웨어입니다.)
    - SW_gen.bat을 실행하면 SoftDevice 펌웨어가 제작됩니다. (필요시에만 사용합니다.)
    - 자세한 사용법은, 위 링크를 참조하세요. (일본어)

### 다른 방법

- Microsoft UF2 utils: https://github.com/microsoft/uf2
  - 위 repo의 툴을 사용할 수도 있습니다. (./utils/ 참고.)

# 플래시 방법

Nice! Nano 및 클론 보드들은 일반적으로 USB 메모리처럼 인식되고, 간편하게 펌웨어를 교체할 수 있는 구조로 되어 있습니다. 컴퓨터에 보드를 연결하면, USB 메모리로 인식되어 내부의 파일을 볼 수 있습니다.

(이는 UF2 부트로더를 사용하기 때문입니다. https://github.com/adafruit/adafruit_nrf52_bootloader)

USB 메모리 안의 텍스트 파일을 열어서, SoftDevice 버전을 확인하세요. S140 - 6.1.1 버전이면 App 펌웨어만 필요합니다. 그렇지 않으면, 먼저 SoftDevice 펌웨어부터 플래싱해야합니다. 

**시작하기 전, 반드시 내부 파일들을 모두 백업하시는 것을 추천합니다.** (파일을 복사해서, 컴퓨터에 붙여넣기 하면 됩니다. 간단해요.)

## 펌웨어 플래싱

- SoftDevice 버전이 S140 - 6.1.1임:
  - UF2 펌웨어 파일(App 펌웨어. SoftDevice 펌웨어가 아님!)을 USB 메모리에 복사하세요. USB 메모리가 인식 해제되고, 자동으로 다시 VR 동글로 인식되면 끝입니다.
- SoftDevice 버전이 위와 다름:
  1. 먼저, SoftDevice 펌웨어를 플래시 (USB 메모리에 복사)합니다.
    - USB 메모리로 인식이 되지 않는 경우: RST (Reset) 핀, 그리고 GND (Ground) 핀을 빠르게 (0.5초 이내 간격으로) 2번 연결시키세요.
    - 퀵 스타트의 링크는 SoftDevice 펌웨어가 없습니다. 직접 제작하세요.
  2. 그리고, App 펌웨어를 플래시 (USB 메모리에 복사)합니다. SB 메모리가 인식 해제되고, 자동으로 다시 VR 동글로 인식되면 끝입니다.

## USB 인식이 안되나요?

- DFU 모드 (펌웨어를 수정 가능한 모드)로 수동 진입해야 하는 경우가 있습니다. RST (Reset) 핀, 그리고 GND (Ground) 핀을 빠르게 (0.5초 이내 간격으로) 2번 연결시키세요. DFU 모드에 진입하면, LED가 깜빡이는 등 변화가 보입니다.
- 데이터 전송이 가능한 올바른 USB 케이블을 사용하세요. 가끔 데이터 전송이 안되는 케이블들도 있습니다.
- UF2 부트로더가 탑재되지 않은 보드일 수 있습니다. 일반적으로, 그렇지 않은 경우는 Nordic의 기본 bootloader가 탑재되어 있을 수 있습니다. NRFUtil이나 NRFConnect ( https://www.nordicsemi.com/Products/Wireless/Bluetooth-Low-Energy/Development-tools )를 사용해야 할 수 있습니다. 그렇지 않은 경우, 별도로 JTAG 프로그래머가 필요할 수 있습니다.
  - 흔하지 않을 것이라고 생각됩니다. Nice! Nano 및 클론 보드들은 일반적으로 Adafruit UF2 부트로더를 사용합니다.
  - 보드 자체의 불량일 수도 있습니다. (흔할 수 있음. 저렴한 보드들은 불량이 꽤 있습니다.)

# Thanks

- https://blog.naver.com/apple1004q/223291284897
  - 본 repo의 Quick Start UF2 펌웨어 파일은 본 블로그의 자료를 바탕으로 변환된 것을 밝힙니다. 진심으로 감사합니다.
  - 관련 추가 repository를 알려주셨습니다.
- https://github.com/ugokutennp/watchman-uf2
  - UF2 펌웨어 제작을 간편하게 수행하는 스크립트를 제작해주신 점, 진심으로 감사합니다.
 
# 본 문서의 방법을 수행함에 따라 발생하는 기기 고장 등 손해는 본인 책임입니다.
