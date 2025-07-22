# 📌 VM 스크립트
- 가상머신(VM)을 자동으로 제어하기 위한 방식
- 기존 GUI 방식을 스크립트 명령어로 작성하여 자동화

<br>

## ◼️ 주요 내용
- VM 자동 생성, 설정, 운영 등에 사용
- PowerCLI(PowerShell), Bash, Python+pyvmomi 등을 통해 작성
  - PowerCLI: VMware 환경에서 제일 많이 쓰는 방식
  - Shell Script: Linux VM 제어 시 주로 사용

<br>

|자동화 대상|예시|
|------|---|
|VM 생성|4vCPU, Memory 8GB, Windows 설치된 VM 1대 생성|
|VM 설정 변경|VM에 vTPM 장치 추가, 네트워크 어댑터 변경|
|VM 전원 제어|Power ON/OFF/재부팅 등|
|이미지 배포|Golden Image로 VDI 50대 만들기 등|

<br>

## ◼️ 사용 사례

#### Horizon 환경
- 특정 Pool에 속한 VDI VM 상태 점검
- 문제 발생한 VM만 재시작 또는 초기화
- Golden Image 스냅샷 후 Pool 업데이트 트리거

<br>

## ◼️ 예시 (PowerCLI 기반)
- 신규 입사자용 VM 자동 생성: AD 정보 기반 VM 이름 생성 → 템플릿 배포
- 야간 시간 VDI 전체 전원 OFF: 오후 9시마다 전원 OFF 스케줄 스크립트 실행
- 월 1회 전체 스냅샷 백업: 매월 1일마다 전체 VM 스냅샷 자동 실행
- 특정 사용자 VM만 초기화: 사용자 목록 받은 후 해당 VM만 스냅샷 복원
```powershell
# vCenter 접속
Connect-VIServer -Server vcenter.company.com -User "admin" -Password "password"

# 템플릿으로부터 새로운 VM 생성
New-VM -Name "salzzing-Win11-VM01" -Template "Win11-Template" -Datastore "Datastore1" -VMHost "ESXi01"

# VM 전원 켜기
Start-VM -VM "salzzing-Win11-VM01"

# VM 재부팅
Restart-VM -VM "salzzing-Win11-VM01"

# 스냅샷 찍기/복원
New-Snapshot -VM "salzzing-Win11-VM01" -Name "BeforeUpdate"
Restore-Snapshot -VM "salzzing-Win11'VM01" -Name "BeforeUpdate"

# Horizon Pool 대상 VM 상태 점검
Get-VM -Name "*-VM01" | Select Name, PowerState, Host
```

<br>

---
#### 느낀 점

