## 📌 AD 서버 내 폴더

---

### ◼️ 개요
- 도메인 컨트롤러(DC) 역할을 맡은 AD 서버 내에는 시스템 작동을 위한 핵심 폴더 존재

<br>

### ◼️ 내용
##### 1️⃣ SYSVOL
- 위치 : C:\Windows\SYSVOL\sysvol
- 역할
  - GPO 설정 저장
  - 로그인 스크립트 저장
  - 모든 DC 간 DFS-R 복제

⇒ 도메인에 **공통 적용**할 파일 및 정책 저장 공간

<br>

##### 2️⃣ NTDS (NT Directory Services)
- 위치 : C:\Windows\NTDS
- 역할
  - AD의 실제 데이터베이스 파일(Ntds.dit) 저장
  - 도메인 사용자, 컴퓨터, OU, 그룹 등 모든 디렉터리 정보 포함

<br>

##### 3️⃣ Logs (NTDS 로그)
- 위치 : 주로 C:\Windows\NTDS\\*.log
- 역할
  - AD 데이터베이스의 변경사항 기록
  - DC 간 복제, 장애 복구, rollback 시 활용

<br>

##### 4️⃣ AD DS Database Temp Folder
- 위치 : C:\Windows\NTDS\Temp.edb
- 역할
  - 일시적인 트랜잭션 작업 수행 시 사용하는 임시 공간
  - DB 작업 도중 생성되며 자동 관리됨

<br>

##### 5️⃣ Policies
- 위치 : C:\Windows\SYSVOL\domain\Policies
- 역할
  - GPO 객체의 **실제 정책 파일** 저장
  - 그룹 정책 편집기에서 설정한 정책을 파일 형태로 저장

<br>

##### 6️⃣ Netlogon (공유 폴더)
- 위치 : C:\Windows\SYSVOL\domain\scripts
- 공유 경로 : \\\domain.com\NETLOGON
- 역할
  - 로그온 스크립트 배포
  - VBS, BAT 파일 시 주로 사용

<br>

### ◼️ 사용 사례
- GPO 적용 불가 → SYSVOL 복제 상태 확인
- 사용자 정보 문제 발생 → NTDS 파일 상태 체크
- 로그인 스크립트 실행 불가 → NETLOGON 공유 경로 확인
- AD 서버 백업 및 복구 → NTDS/SYSVOL 확인

<br>

---
##### 느낀 점
- 더 확인해봐야 할 것
  - "모든 DC 간 DFS-R 복제"
  - AD와 데이터베이스의 상호작용
  - Policies 폴더 내 GPO 정책들이 실제로 어떻게 저장되며, 어떻게 동작하는지



