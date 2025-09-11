[설치환경]
 1) Jetson을 설치하는데 Host PC가 꼭 필요한가요?
네, Jetson 모듈을 설치하고 설정하기 위해서는 Host PC가 필요합니다. Host PC는 Jetson의 운영 체제를 설치하는 데 필요한 소프트웨어를 다운로드하고, 초기 설정을 수행하는 데 사용됩니다. 
주의할 점은 Jetson 설치를 위한 Host PC는 리눅스 운영 체제를 사용해야 하며, 가상 머신 에서는 설치가 지원되지 않는다는 것입니다.

<img src="https://github.com/MDSTech-Jetson/FAQ/blob/myungsu/img/1-1.jpg?raw=true" width="830"/>

2) Host PC는 꼭 우분투 PC여야 하나요?? 윈도우 PC사용은 불가능한가요?
Jetson 설치 소프트웨어는 리눅스에서만 제공되고, Host PC에 우분투 운영체제를 사용하는 것을 권장 드립니다. . 따라서 윈도우 PC에서는 설치가 불가능하며, 가상 머신을 사용할 경우 USB를 통해 Jetson을 인식할 수 없어 설치가 불가능합니다.

 3) Host PC의 우분투는 어떤 버전으로 설치해야 하나요?
Jetson을 운영하기 위해서는 JetPack을 설치해야 하며, JetPack 버전에 따라 Host PC의 우분투 버전도 달라집니다.

| JetPack 버전 | SDK Manager | Ubuntu LTS | 스크립트 설치 |
|-------------|-------------|------------|---------------|
| JetPack 6   | 지원        | 22.04 LTS  | Host PC 우분투 버전 제안 없음 |
| JetPack 5   | 지원        | 20.04 LTS  | Host PC 우분투 버전 제안 없음 |
| JetPack 4   | 지원        | 18.04 LTS  | Host PC 우분투 버전 제안 없음 |

[설치]
 1) Jetson은 어떻게 설치해야 하나요? 
Jetson 모듈을 설치하기 전에 먼저 확인해야 할 점은 Developer Kit인지 아니면 3rd Party 보드인지입니다.
개발 키트인 경우, 설치 방법은 세 가지가 있습니다. 	
	1. SDKmanager 통한 설치 방법 
	2. 플래시 스크립트 통한 설치 방법 
	3. balenaEtcher 를 사용해서 sd카드를 부팅용 디스크로 굽는 방법. 
 
반면, 3rd Party 보드인 경우에는 보드 제조사에서 플래시 스크립트를 제공하고 있습니다. 각 보드에 맞는 설치 지침을 따라 진행하면 됩니다. 

avermedia 및 jetpack 설치 는 아래 링크를 통해 확인할 수 있습니다. (블로그 링크 기제 예정)

2) 어떤 SD카드를 사용해야 하나요? 아무거나 사용해도 상관없나요?
Jetson 모듈에 사용할 SD 카드는 기본적으로 최소 64GB의 용량을 가진 SD 카드를 사용하는 것을 추천합니다. 

3) SSD에 설치해서 부팅하고 싶은데 설치방법이 다른가요?
SSD에 설치하고 부팅하는 과정은 크게 다르지 않습니다.
SDK Manager를 통한 설치 과정 중 스토리지 선택 옵션에서 "NVMe"를 선택하면 SSD에 설치 및 부팅이 가능합니다.

플래시 스크립트를 통한 설치 과정 중 명령어 입력 시 스토리지 선택 옵션을 nvme0np1과 같이 SSD 파티션으로 입력하면 설치할 수 있습니다.
자세한 설치 방법은 “” 1) Jetson은 어떻게 설치해야 하나요? “”에서 확인할 수 있습니다.

<img src="https://github.com/MDSTech-Jetson/FAQ/blob/myungsu/img/2-3.png?raw=true" width="830"/>

4) 리커버리 모드인지 어떻게 확인하죠?
리커버리 모드에서 USB로 연결한 후, 호스트 PC에서 터미널을 열고 “lsusb”를 입력합니다.
결과 목록에서 “NVIDIA Corp. APX”라는 항목을 확인하면 Jetson이 리커버리 모드에 진입한 것입니다. 만약 리커버리 모드가 아니라면 NVIDIA Corp. APX로 표시되는 장치가 없습니다.

<img src="https://github.com/MDSTech-Jetson/FAQ/blob/myungsu/img/2-4.png?raw=true" width="830"/>

[Jetson SW - JetPack]
 1) JetPack이 뭔가요? 윈도우나 일반적인 리눅스를 Jetson에 설치하면 안되나요?
JetPack은 Jetson에서 AI추론 소프트웨어를 개발하기 위한 라이브러리 환경을 제공하며 모든 SW 플랫폼은 LTS Linux 커널이 있는 Jetson Linux (L4T) 위에 구축되어집니다.
<img src="https://github.com/MDSTech-Jetson/FAQ/blob/myungsu/img/3-1.png?raw=true" width="830"/>
JetPack 이외에 일반적인 리눅스나 윈도우를 Jetson 모듈에 설치하는 것은 불가능합니다. Jetson 모듈은 ARM 아키텍처를 기반으로 하고 있어, 일반적인 x86 기반의 윈도우나 리눅스는 호환되지 않습니다. 특히, SoC 형태로 제공되는 GPU 커널 드라이버는 NVIDIA에서 제공하므로 JetPack의 사용이 필수적입니다.

2) Jetson Nano에 JetPack6 설치 안되나요? 
불가능합니다. Jetson Nano는 JetPack 6을 지원하지 않습니다. JetPack 6은 Jetson Orin 시리즈만 지원합니다. Jetson Nano는 JetPack 4 버전까지 지원됩니다.

## JetPack 지원 보드

| JetPack 버전 | AGX Orin | Orin Nano | Orin NX | Xavier NX | AGX Xavier | TX2 | Nano | TX1 |
|-------------|----------|-----------|---------|-----------|------------|-----|------|-----|
| 6           | O        | O         | O       |           |            |     |      |     |
| 5           | O        | O         | O       | O         | O          |     |      |     |
| 4           |          |           |         | O         | O          | O   | O    | O   |



