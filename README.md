# STK-NAS 포털

SharePoint STK-NAS 홈에 iframe 으로 넣는 업무 바로가기 화면입니다.

- 화면: `index.html`
- 바로가기 목록 · 주소: `links.json` — 이름 · 주소(url) · 설명(desc) · 아이콘만 고치면 다음 접속부터 반영됩니다.
  `url` 이 비어 있으면 「링크 준비 중」 으로 흐리게 표시됩니다.

```html
<iframe src="https://startruckkorea-dev.github.io/nas/" width="100%" height="950" frameborder="0" style="border-radius:12px; border:none;"></iframe>
```

## 바로 열면 SSO 가 깨지는 사이트(go)

SharePoint 를 보안 프록시(`*.mcas.ms`)로 열면 페이지 안 링크에도 `.mcas.ms` 가 붙어 일부 사이트(Concur 등)의 SSO 로그인이 실패합니다.
SharePoint 바로가기에는 아래처럼 중간 페이지 주소를 넣으면 원래 주소로 열립니다.

- Concur: `https://startruckkorea-dev.github.io/nas/go/?to=concur`
- 대상 추가: `go.json` 에 `"키": { "name": "이름", "url": "https://..." }` 한 줄 추가(등록된 키 · https 주소만 이동)
