# STK 바로가기(리디렉션)

SharePoint 를 보안 프록시(`*.mcas.ms`)로 열면 페이지 안 링크에도 `.mcas.ms` 가 붙어 일부 사이트의 SSO 로그인이 실패합니다.
SharePoint 바로가기에 `https://redirect.startruckkorea.com/?to=키` 를 넣으면 이 사이트를 한 번 거쳐 원래 주소로 열립니다(로그인 없음).

- 목록은 `links.dat` 하나 — UTF-8 JSON 을 base64 로 바꾼 것입니다. 저장소에서 주소가 평문으로 보이지 않게 하는 정도이며 **보안 장치는 아닙니다**(누구나 되돌릴 수 있음).
- JSON 형식: `[{ "key": "키", "name": "이름", "desc": "설명", "url": "https://...", "color": "#RRGGBB" }]`
  - key 는 영문 소문자 · 숫자 · `-` 만. url 은 https 만(`.mcas.ms` 가 붙어 있으면 떼고 이동). `"use": false` 면 숨김.
- 키 없이 열면 등록된 바로가기 목록이 나옵니다. 예전 주소 `/go/?to=키` 도 그대로 동작합니다.

## links.dat 고치기(PowerShell)

```powershell
# 1) 풀기 → links.json 으로 저장해 메모장 등으로 고침
$b = (Get-Content .\links.dat -Raw) -replace '\s',''
[IO.File]::WriteAllText("$PWD\links.json", [Text.Encoding]::UTF8.GetString([Convert]::FromBase64String($b)))

# 2) 다시 묶기 → links.dat 덮어쓰기(links.json 은 올리지 말고 지움)
$j = [IO.File]::ReadAllText("$PWD\links.json"); $null = $j | ConvertFrom-Json   # 형식 확인
[IO.File]::WriteAllText("$PWD\links.dat", [Convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes($j)))
Remove-Item .\links.json
```
