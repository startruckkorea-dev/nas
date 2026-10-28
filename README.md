# STK-NAS 포털

SharePoint STK-NAS 홈에 iframe 으로 넣는 업무 바로가기 화면입니다.

- 화면: `index.html`
- 바로가기 목록 · 주소: `links.json` — 이름 · 주소(url) · 설명(desc) · 아이콘만 고치면 다음 접속부터 반영됩니다.
  `url` 이 비어 있으면 「링크 준비 중」 으로 흐리게 표시됩니다.

```html
<iframe src="https://startruckkorea-dev.github.io/nas/" width="100%" height="950" frameborder="0" style="border-radius:12px; border:none;"></iframe>
```
