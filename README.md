# 🚀 Jetson Setup Guide FAQ

---

<h2>설치환경</h2>

<details>
<summary> <b> Q1. Jetson을 설치하는데 Host PC가 꼭 필요한가요? </b> </summary>
<p>
<br>
✅ <b>답변:</b><br>
네, Jetson 모듈을 설치하고 설정하기 위해서는 Host PC가 필요합니다.<br><br>
Host PC는 Jetson 운영 체제를 설치하고 초기 설정을 수행하는 데 사용됩니다.<br><br>
⚠️ <b>주의:</b> Jetson 설치를 위한 Host PC는 <b>리눅스 운영체제</b>여야 하며, 가상 머신에서는 설치가 지원되지 않습니다.
</p>
<img src="https://github.com/MDSTech-Jetson/FAQ/blob/myungsu/img/1-1.jpg?raw=true" width="830"/>
</details>

---

<details>
<summary>
<b> Q2. Host PC는 꼭 우분투 PC여야 하나요? 윈도우 PC 사용은 불가능한가요? </b>
</summary>
<p>
<br>
✅ <b>답변:</b><br>
Jetson 설치 소프트웨어는 리눅스에서만 제공됩니다.<br><br>
Host PC는 <b>우분투</b> 운영체제 사용을 권장하며, 윈도우 PC에서는 설치가 불가능합니다.<br><br>
가상 머신을 사용할 경우 USB로 Jetson을 인식할 수 없어 설치가 불가능합니다.
</p>
</details>

---

<details>
<summary>
<b> Q3. Host PC의 우분투는 어떤 버전으로 설치해야 하나요?</b>
</summary>
<br>
<p>
✅ <b>답변:</b><br>
JetPack 버전에 따라 Host PC 우분투 버전이 달라집니다.
</p>

| JetPack 버전 | SDK Manager | Ubuntu LTS | 스크립트 설치 |
|-------------|-------------|------------|---------------|
| JetPack 6   | 지원        | 22.04 LTS  | Host PC 우분투 버전 제안 없음 |
| JetPack 5   | 지원        | 20.04 LTS  | Host PC 우분투 버전 제안 없음 |
| JetPack 4   | 지원        | 18.04 LTS  | Host PC 우분투 버전 제안 없음 |
</details>

---

<h2>설치 방법</h2>

<details>
<summary>
<b> Q1. Jetson은 어떻게 설치해야 하나요? </b>
</summary>
<br>
<p>
✅ <b>답변:</b><br>
개발 키트인지 3rd Party 보드인지 먼저 확인합니다.<br><br>

<b>개발 키트 설치 방법:</b><br>
1. SDK Manager를 통한 설치<br>
2. 플래시 스크립트를 통한 설치<br>
3. balenaEtcher를 사용하여 SD카드를 부팅 디스크로 생성<br><br>

<b>3rd Party 보드 설치:</b><br>
- 보드 제조사에서 제공하는 플래시 스크립트 사용<br><br>

관련 블로그 링크 및 설치 스크립트 참고 가능
</p>
</details>

---

<details>
<summary>
<b> Q2. 어떤 SD카드를 사용해야 하나요? </b>
</summary>
<br>
<p>
✅ <b>답변:</b><br>
최소 64GB 이상 SD 카드 사용 추천
</p>
</details>

---

<details>
<summary>
<b> Q3. SSD에 설치해서 부팅하고 싶은데 설치방법이 다른가요? </b>
</summary>
<p>
<br>
✅ <b>답변:</b><br>
SDK Manager에서 스토리지 옵션을 "NVMe"로 선택하거나,<br>
플래시 스크립트에서 SSD 파티션 지정 시 SSD에 설치 가능
</p>
<img src="https://github.com/MDSTech-Jetson/FAQ/blob/myungsu/img/2-3.png?raw=true" width="830"/>
</details>

---

<details>
<summary>
<b> Q4. 리커버리 모드인지 어떻게 확인하죠? </b>
</summary>
<br>
<p>
✅ <b>답변:</b><br>
USB로 연결 후 터미널에서 <code>lsusb</code> 입력<br>
"NVIDIA Corp. APX"가 보이면 리커버리 모드 진입
</p>
<img src="https://github.com/MDSTech-Jetson/FAQ/blob/myungsu/img/2-4.png?raw=true" width="830"/>
</details>

---

<h2>Jetson SW - JetPack</h2>

<details>
<summary>
<b> Q1. JetPack이 뭔가요? <br>윈도우나 일반 리눅스를 설치하면 안 되나요? </b>
</summary>
<br>
<p>
✅ <b>답변:</b><br>
JetPack은 Jetson에서 AI 추론 소프트웨어 개발을 위한 라이브러리 환경 제공<br>
- Jetson Linux (L4T) 위에서만 작동<br>
- x86 기반 윈도우/리눅스는 설치 불가
</p>
<img src="https://github.com/MDSTech-Jetson/FAQ/blob/myungsu/img/3-1.png?raw=true" width="830"/>
</details>

---

<details>
<summary>
<b> Q2. Jetson Nano에 JetPack 6 설치가 가능한가요? </b>
</summary>
<br>
<p>
❌ <b>답변:</b><br>
불가능합니다.<br>
- JetPack 6 → Jetson Orin 시리즈만 지원<br>
- Jetson Nano → JetPack 4까지 지원<br><br>

JetPack 지원 리스트<br>
| JetPack 버전 | AGX Orin | Orin Nano | Orin NX | Xavier NX | AGX Xavier | TX2 | Nano | TX1 |
|-------------|----------|-----------|---------|-----------|------------|-----|------|-----|
| 6           | O        | O         | O       |           |            |     |      |     |
| 5           | O        | O         | O       | O         | O          |     |      |     |
| 4           |          |           |         | O         | O          | O   | O    | O   |
</p>
</details>