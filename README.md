# HR 대시보드

브라우저에서 인사관리대장파일을 직접 읽어 보여주는 단일 페이지 대시보드입니다.
데이터는 브라우저 메모리에서만 처리되며 외부로 전송되지 않습니다. 저장소에는 **코드만** 올립니다.

## 사용법
1. GitHub Pages 주소로 접속 (크롬/엣지 권장)
2. «폴더 선택» → 인사관리대장이 있는 폴더 지정 (이름이 `★인사관리대장`으로 시작하는 xlsx 중 최신 파일 자동 선택)
3. 이후 새로고침하면 같은 폴더에서 최신 파일을 다시 읽습니다. 사파리 등 미지원 브라우저는 매번 재선택합니다.

## 배포 (GitHub Pages)
Settings → Pages → Source: `main` / `(root)`

## 주의
- 프라이빗 저장소여도 Pages 사이트 자체는 공개 URL입니다(접근 제어는 Enterprise Cloud 플랜에서만 가능). 사이트에는 코드만 있고 데이터는 없습니다.
- `.gitignore`로 xlsx/csv 커밋을 막아 두었습니다.
- `계정명.github.io` 아래의 Pages 사이트들은 브라우저에서 같은 출처(origin)로 취급됩니다. 이 대시보드에 허용한 폴더 접근 권한을 같은 계정의 다른 Pages 사이트도 쓸 수 있으므로, 같은 계정에 신뢰할 수 없는 코드를 Pages로 올리지 마세요.
- 파이어폭스·사파리에서는 폴더를 고를 때 브라우저가 "파일 N개를 업로드"한다는 확인 창을 띄웁니다. 브라우저 고정 문구이며 실제로는 어디에도 전송되지 않습니다.
- 사내망에서 `cdn.sheetjs.com`이 차단되면 파일을 읽을 때 안내 메시지가 뜹니다. 아래 "구성"의 방법으로 SheetJS를 `vendor/`에 넣으면 해결됩니다.

## 구성
- `index.html` : 앱 본체
- `vendor/chart.umd.min.js` : Chart.js 4.5.1 (MIT, 라이선스 동봉)
- SheetJS 0.20.3 : 공식 CDN(`cdn.sheetjs.com`)에서 로드. 외부 CDN 의존을 없애려면 아래로 내려받아 `vendor/`에 두고 `index.html`의 `<script src>`를 `vendor/xlsx.full.min.js`로 바꾸세요.
  `curl -O https://cdn.sheetjs.com/xlsx-0.20.3/package/dist/xlsx.full.min.js`
