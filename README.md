# STK 바로가기(리디렉션)

SharePoint 를 보안 프록시(`*.mcas.ms`)로 열면 페이지 안 링크에도 `.mcas.ms` 가 붙어 일부 사이트(Concur 등)의 SSO 로그인이 실패합니다.
SharePoint 바로가기에 아래 주소를 넣으면 github.io 를 한 번 거쳐 원래 주소로 열립니다.

| 대상 | SharePoint 에 넣을 주소 |
|---|---|
| Concur | `https://startruckkorea-dev.github.io/nas/?to=concur` |

- 대상 추가 · 변경: `go.json` 에 `"키": { "name": "이름", "url": "https://..." }` 추가(키는 영문 소문자 · 숫자 · `-`)
- 등록된 키 · https 주소로만 이동하고, 그 밖의 값은 이동하지 않습니다.
- 키 없이 열면(`/nas/`) 등록된 바로가기 목록이 나옵니다.
- 예전 주소 `/nas/go/?to=키` 도 그대로 동작합니다.
