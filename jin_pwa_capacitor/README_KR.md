# 진 스탯 대시보드 v3 — "앱"으로 쓰는 방법 (PWA + 안드로이드 앱)

이 프로젝트는 **웹(HTML)** 로 만든 대시보드를
1) **스마트폰에 바로 설치 가능한 PWA** 로 쓰고,
2) 원하면 **안드로이드 APK/AAB(진짜 앱)** 로 포장(Wrapper)할 수 있게 해둔 버전입니다.

---

## 1) 제일 쉬운 방법: PWA로 설치하기 ✅ (추천)

### PC에서 한번만: 웹에 올리기
PWA는 **HTTPS 주소**가 있어야 설치가 안정적으로 됩니다.

- 방법 A: GitHub Pages
- 방법 B: Cloudflare Pages
- 방법 C: Netlify/Vercel

업로드 후 휴대폰에서 그 주소를 열고 설치하면 끝!

### 안드로이드(Chrome)
1. 휴대폰 크롬에서 주소 열기
2. 메뉴(⋮) → **"홈 화면에 추가"** 또는 **"앱 설치"**
3. 홈 화면에 앱 아이콘 생김

### iPhone(Safari)
1. 사파리로 주소 열기
2. 공유 버튼 → **"홈 화면에 추가"**

---

## 2) 진짜 "앱"(APK)로 만들기: Capacitor 📦

> 필요: PC에 **Node.js LTS**, **Android Studio** 설치

### (1) 설치
프로젝트 폴더에서:

```bash
npm install
```

### (2) 안드로이드 프로젝트 생성
```bash
npm run cap:android
```

### (3) 동기화
```bash
npm run cap:sync
```

### (4) Android Studio 열기
```bash
npm run cap:open:android
```

Android Studio에서:
- **Build > Build Bundle(s) / APK(s)**
- APK 생성 후 휴대폰에 설치하면 됩니다.

---

## 3) 오프라인(비행기모드)에서도 열리게 해둠 ✈️
`www/sw.js`(서비스워커)가 **index.html, manifest, 아이콘**을 캐시합니다.

---

## 폴더 구조
- `www/` : 실제 앱 화면(웹)
  - `index.html`
  - `manifest.webmanifest`
  - `sw.js`
  - `icon-192.png`, `icon-512.png`

---

## Troubleshooting
- 설치 메뉴가 안 뜨면: HTTPS인지 확인 + 크롬 캐시 삭제 후 재시도
- 아이콘이 안 보이면: 브라우저 캐시 삭제 후 재접속
- APK 빌드 에러: Android Studio에서 SDK 설치/업데이트 확인
