# HexIsle · 헥스아일 - 개척의 시대

육각형 땅으로 이루어진 섬에서 자원을 모으고, 교환하고, 정착지와 도시를 넓혀 **10점**을 먼저 모으는 2~4인 개척 게임이에요. 나 한 명과 AI 1~3명이 플레이해요.

**플레이:** https://kimminji-design.github.io/hexisle/

- 서버 없이 브라우저에서 돌아가는 HTML 파일 하나예요. AI도 브라우저 안에서 계산해요.
- 휴대폰은 가로 화면 전용이에요. 홈 화면에 추가하면 주소창 없는 전체화면으로 열려요.
- 진행 상황은 브라우저에 자동 저장돼요.

## 사용한 외부 자료
- [three.js](https://threejs.org/) 0.147 (MIT), jsDelivr CDN으로 불러와요.
- 지형·말·카드 텍스처와 3D 스캔: [Poly Haven](https://polyhaven.com/) (CC0)
- 글꼴: 레벨업(LevelUp), Hada Type Foundry (SIL Open Font License 1.1)

## 코드 구조 (PC·모바일 분리 원칙)
- `index.html`: 게임 전체 스크립트(규칙·AI·튜토리얼·멀티·기록). PC와 모바일이 **같은 코드**를 써요.
- `common.css`: PC·모바일 공통 스타일. 여기를 고치면 **양쪽 모두** 바뀌어요.
- `pc.css`: PC 전용 (`html:not(.phone) …`). PC 화면은 여기서 고쳐요.
- `mobile.css`: 모바일 전용 (`html.phone …`). 모바일 화면은 여기서 고쳐요.
  - `common.css` 안에도 `html.phone`/`html:not(.phone)`로 시작하는 규칙이 남아 있어요. 다른 파일로 옮기면 적용 순서가 바뀌어 결과가 달라질 수 있는 규칙들이라 제자리에 뒀어요. 이 규칙들도 선택자로 막혀 있어서 반대쪽 기기에는 적용되지 않아요.
- 그래픽 품질: `index.html`의 `GFX.mobile` / `GFX.pc`. 모바일 값은 고정하고, PC 품질 조정은 `GFX.pc`에서만 해요.
- CSS 파일을 고치면 `index.html`의 `<link … ?v=숫자>`를 1 올려 주세요. 브라우저가 예전 CSS를 붙잡고 있지 않게 하려는 거예요.
