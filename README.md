# Jetson Setup Guide FAQ

---

## 설치환경

<details>
<summary>1) Jetson을 설치하는데 Host PC가 꼭 필요한가요?</summary>
<p>
네, Jetson 모듈을 설치하고 설정하기 위해서는 Host PC가 필요합니다. Host PC는 Jetson의 운영 체제를 설치하는 데 필요한 소프트웨어를 다운로드하고, 초기 설정을 수행하는 데 사용됩니다.<br>
주의할 점은 Jetson 설치를 위한 Host PC는 리눅스 운영 체제를 사용해야 하며, 가상 머신에서는 설치가 지원되지 않는다는 것입니다.
</p>
<img src="https://github.com/MDSTech-Jetson/FAQ/blob/myungsu/img/1-1.jpg?raw=true" width="830"/>
</details>

<details>
<summary>2) Host PC는 꼭 우분투 PC여야 하나요? 윈도우 PC 사용은 불가능한가요?</summary>
<p>
Jetson 설치 소프트웨어는 리눅스에서만 제공되며, Host PC에 우분투 운영체제를 사용하는 것을 권장드립니다.  
따라서 윈도우 PC에서는 설치가 불가능하며, 가상 머신을 사용할 경우 USB를 통해 Jetson을 인식할 수 없어 설치가 불가능합니다.
</p>
</details>

<details>
<summary>3) Host PC의 우분투는 어떤 버전으로 설치해야 하나요?</summary>
<p>
Jetson을 운영하기 위해서는 JetPack을 설치해야 하며, JetPack 버전에 따라 Host PC의 우분투 버전도 달라집니다.
</p>

| JetPack 버전 | SDK Manager | Ubuntu LTS | 스크립트 설치 |
|-------------|-------------|------------|---------------|
| JetPack 6   | 지원        | 22.04 LTS  | Host PC 우분투 버전 제안 없음 |
| JetPack 5   | 지원        | 20.04 LTS  | Host PC 우분투 버전 제안 없음 |
| JetPack 4   | 지원        | 18.04 LTS  | Host PC 우분투 버전 제안 없음 |
</details>

---

## 설치

<details>
<summary>1) Jetson은 어떻게 설치해야 하나요?</summary>
<p>
Jetson 모듈을 설치하기 전에 먼저 확인해야 할 점은 Developer Kit인지 아니면 3rd Party 보드인지입니다.<br>
개발 키트인 경우, 설치 방법은 세 가지가 있습니다:
- SDK Manager 통한 설치 방법  
- 플래시 스크립트 통한 설치 방법  
- balenaEtcher를 사용해서 SD카드를 부팅용 디스크로 굽는 방법  

3rd Party 보드인 경우에는 보드 제조사에서 제공하는 플래시 스크립트를 사용하면 됩니다.
</p>
<p>
관련 블로그 링크 및 설치 스크립트 참고 가능
</p>
</details>

<details>
<summary>2) 어떤 SD카드를 사용해야 하나요? 아무거나 사용해도 상관없나요?</summary>
<p>
Jetson 모듈에 사용할 SD 카드는 최소 64GB 용량을 추천합니다.
</p>
</details>

<details>
<summary>3) SSD에 설치해서 부팅하고 싶은데 설치방법이 다른가요?</summary>
<p>
SSD 설치 및 부팅 과정은 SDK Manager에서 스토리지 옵션을 "NVMe"로 선택하면 가능하며, 플래시 스크립트 사용 시에도 SSD 파티션을 지정하면 설치 가능합니다.
</p>
<img src="https://github.com/MDSTech-Jetson/FAQ/blob/myungsu/img/2-3.png?raw=true" width="830"/>
</details>

<details>
<summary>4) 리커버리 모드인지 어떻게 확인하죠?</summary>
<p>
USB로 연결 후 호스트 PC에서 터미널 열고 <code>lsusb</code> 입력  
결과 목록에서 "NVIDIA Corp. APX"가 보이면 리커버리 모드 진입
</p>
<img src="https://github.com/MDSTech-Jetson/FAQ/blob/myungsu/img/2-4.png?raw=true" width="830"/>
</details>

---

## Jetson SW - JetPack

<details>
<summary>1) JetPack이 뭔가요? 윈도우나 일반 리눅스를 설치하면 안 되나요?</summary>
<p>
JetPack은 Jetson에서 AI 추론 소프트웨어를 개발하기 위한 라이브러리 환경을 제공하며, 모든 소프트웨어 플랫폼은 Jetson Linux (L4T) 위에 구축됩니다.  
일반적인 x86 기반 윈도우/리눅스 설치는 불가능하며, JetPack 사용이 필수적입니다.
</p>
<img src="https://github.com/MDSTech-Jetson/FAQ/blob/myungsu/img/3-1.png?raw=true" width="830"/>
</details>

<details>
<summary>2) Jetson Nano에 JetPack 6 설치가 가능한가요?</summary>
<p>
불가능합니다. JetPack 6은 Jetson Orin 시리즈만 지원하며, Jetson Nano는 JetPack 4까지 지원됩니다.
</p>
</details>

---

## JetPack 지원 보드

| JetPack 버전 | AGX Orin | Orin Nano | Orin NX | Xavier NX | AGX Xavier | TX2 | Nano | TX1 |
|-------------|----------|-----------|---------|-----------|------------|-----|------|-----|
| 6           | O        | O         | O       |           |            |     |      |     |
| 5           | O        | O         | O       | O         | O          |     |      |     |
| 4           |          |           |         | O         | O          | O   | O    | O   |
