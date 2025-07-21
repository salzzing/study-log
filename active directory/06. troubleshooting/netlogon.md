## 📌 netlogon

---

### ◼️ 개요
- Windows 도메인 컨트롤러(DC) 내에 존재하는 공유폴더
- 도메인 환경에서 클라이언트 컴퓨터 로그인 시 필요한 스크립트 또는 정책 파일 저장

<br>

### ◼️ 내용
##### ✔️ 경로
- C:\Windows\SYSVOL\sysvol\<도메인 이름>\scripts
- \\\\<도메인 이름>\netlogon으로 접근

<br>

##### ✔️ 주요 역할


- **내용**

<br>

### ◼️ 사용 사례

<br>

### ◼️ 예시

```bash
# PowerShell 예시
Get-ADUser -Filter * | Select-Object Name, Enabled
```

<br>

### ◼️ 참고 링크

---
##### 느낀 점
