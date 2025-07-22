# 📌 netlogon
- Windows 도메인 컨트롤러(DC) 내에 존재하는 공유폴더
- 도메인 환경에서 클라이언트 컴퓨터 로그인 시 필요한 스크립트 또는 정책 파일 저장

<br>

## ◼️ 주요 내용
#### ✔️ 경로
- C:\Windows\SYSVOL\sysvol\<도메인 이름>\scripts
- \\\\<도메인 이름>\netlogon으로 접근

<br>

#### ✔️ 주요 역할
1. 로그온 스크립트 배포
   - 사용자나 컴퓨터가 도메인에 로그인할 때 실행되는 스크립트를 넣어두는 곳
   - .bat, .cmd, .vbs 등
2. 도메인 컨트롤러 자동 복제 대상
   - 여러 DC가 존재할 경우 Netlogon 폴더가 자동으로 복제됨 (SYSVOL 복제)
   - 모든 DC에서 동일 스크립트 사용 가능
3. 그룹 정책(GPO)과 연동
    - Netlogon 폴더에 스크립트를 넣고 GPO에서 로그온/로그오프 스크립트 지정 → 사용자 로그인 시 자동 실행

<br>

## ◼️ 사용 사례

<br>

## ◼️ 예시

```bash
# PowerShell 예시
Get-ADUser -Filter * | Select-Object Name, Enabled
```

<br>

## ◼️ 참고 링크

---
#### 느낀 점
- 핵심: Netlogon에 접속되지 않으면 스크립트를 받아오지 못한다!