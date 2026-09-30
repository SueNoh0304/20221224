# 석영 ♥ 유리 모바일 청첩장

홍석영 · 엄유리의 결혼식(2022년 12월 24일 토요일 오후 6시, 광명무역센터컨벤션 3층 Grand Ballroom) 모바일 청첩장입니다.
서버나 빌드 과정이 필요 없는 정적 웹페이지라서 GitHub Pages에 올리면 바로 링크로 공유할 수 있습니다.

## 폴더 구성

```
index.html                 청첩장 페이지 (HTML·CSS·JS 한 파일)
images/
  cover.jpg                첫 화면 대표 사진
  gallery/01.jpg ~ 25.jpg  갤러리 원본 사진 (크게 보기용)
  thumbs/01.jpg ~ 25.jpg   갤러리 작은 사진 (목록용)
  illustration.jpg         직접 만든 일러스트 원본
  og-image.jpg             링크 공유 시 미리보기 이미지 (일러스트)
  favicon.png              브라우저 탭 아이콘 (일러스트)
  apple-touch-icon.png     아이폰 홈 화면 아이콘
  icon-512.png             큰 아이콘
.nojekyll                  GitHub Pages가 파일을 그대로 올리도록 하는 빈 파일
```

## GitHub Pages에 올리는 방법

1. GitHub에서 **New repository**를 만듭니다. 예: `wedding`, 공개(Public)로 설정합니다.
2. 저장소 화면에서 **Add file → Upload files**를 누르고, 이 폴더 안의 파일과 `images` 폴더를 통째로 끌어다 놓은 뒤 **Commit changes**를 누릅니다.
   - `.nojekyll`처럼 점으로 시작하는 파일은 컴퓨터에서 숨김 파일이라 안 보일 수 있습니다. 빠져도 페이지는 동작합니다.
3. **Settings → Pages**로 가서 *Source*를 **Deploy from a branch**, *Branch*를 **main / (root)** 로 고르고 **Save**를 누릅니다.
4. 1~2분 뒤 같은 화면 위쪽에 주소가 나타납니다. 예: `https://아이디.github.io/wedding/`

## 배포 후 꼭 할 일: 링크 미리보기 주소 바꾸기

카카오톡·문자로 링크를 보냈을 때 일러스트 미리보기가 뜨려면 이미지 주소가 전체 주소여야 합니다.
`index.html` 위쪽에서 `SITE_URL` 두 군데를 실제 주소로 바꿔 주세요.

```html
<meta property="og:url" content="https://아이디.github.io/wedding/">
<meta property="og:image" content="https://아이디.github.io/wedding/images/og-image.jpg">
```

GitHub 화면에서 `index.html` → 연필 아이콘(Edit)으로 바로 고치고 **Commit changes** 하면 됩니다.

> 카카오톡은 미리보기를 한동안 저장해 둡니다. 이미지를 바꿨는데 예전 미리보기가 계속 보이면
> [카카오 공유 디버거](https://developers.kakao.com/tool/debugger/sharing)에서 주소를 넣고 **캐시 초기화**를 누르세요.

## 내용 고치기

| 바꿀 것 | 위치 |
|---|---|
| 인사말 | `index.html`에서 `<div class="poem">` 아래 문장 |
| 예식 날짜·시간 | `const WEDDING = new Date('2022-12-24T18:00:00+09:00')` 과 표에 적힌 날짜 글자 |
| 교통 안내 | `id="t-sub"`(지하철), `t-bus`(버스), `t-ktx`(KTX·공항), `t-car`(자가용) 부분 |
| 사진 교체 | `images/gallery/`와 `images/thumbs/`에 같은 번호 이름으로 덮어쓰기 |
| 사진 개수 | `Array.from({length:25}` 의 숫자 |
| 색상 | `index.html` 맨 위 `:root { --pink … --deep … }` 값 |

## 화면 구성

- **휴대폰(세로):** 한 줄로 이어지는 청첩장 화면
- **폴드·태블릿·PC(가로로 넓은 화면):** 왼쪽에 대표 사진, 오른쪽에 청첩장. 폴드처럼 가운데가 접히는 기기에서 접히는 선을 피하도록 청첩장을 오른쪽 절반에 둡니다.
- **갤러리:** 사진을 누르면 크게 보이고, 두 손가락으로 확대, 두 번 탭해 확대, 옆으로 밀어 넘기기가 됩니다. PC에서는 마우스 휠과 방향키도 됩니다.
- **일정 저장:** 휴대폰 캘린더 파일(.ics, 하루 전 알림 포함)과 구글 캘린더
- **오시는 길:** 주소 복사, 네이버지도·카카오맵·티맵 바로가기, 지하철·버스·KTX·자가용 안내
- **공유:** 휴대폰 공유창(카카오톡 포함)과 링크 복사
