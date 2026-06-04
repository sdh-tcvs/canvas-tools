# 사내 툴킷 — 배포 가이드

## 파일 구성
```
index.html              ← 로그인 페이지 (비밀번호 입력)
tools.html              ← 툴 목록 메인 페이지
ppt-image-extractor.html ← PPT 미디어 추출기
README.md               ← 이 파일
```

---

## GitHub Pages로 배포하는 방법 (무료, 외부 접속 가능)

### 1단계 — 비밀번호 변경
`index.html`을 열어 아래 줄을 찾아 원하는 비밀번호로 변경하세요:
```js
const PASSWORD = 'changeme';  // ← 여기를 바꾸세요
```

### 2단계 — GitHub 저장소 만들기
1. https://github.com 에서 로그인
2. 우측 상단 **+** → **New repository** 클릭
3. Repository name: `company-tools` (원하는 이름)
4. **Public** 선택 → **Create repository** 클릭

### 3단계 — 파일 업로드
1. 저장소 페이지에서 **uploading an existing file** 클릭
2. 이 폴더의 모든 파일을 드래그 업로드
3. **Commit changes** 클릭

### 4단계 — GitHub Pages 활성화
1. 저장소 → **Settings** → **Pages**
2. Source: **Deploy from a branch**
3. Branch: **main** / **/ (root)** → **Save**
4. 몇 분 후 `https://[계정명].github.io/company-tools` 로 접속 가능!

---

## 새 도구 추가하는 방법

### 1. 새 HTML 파일 추가
새 도구 파일(예: `excel-cleaner.html`)을 같은 폴더에 넣기

### 2. `tools.html`의 TOOLS 배열에 항목 추가
```js
{
  id: 'excel-cleaner',
  name: 'Excel 데이터 정리기',
  shortDesc: 'CSV/XLSX 파일의 중복·빈칸을 자동으로 정리',
  tags: ['Excel', 'CSV', '데이터'],
  badge: 'new',          // 'new' | 'updated' | 'beta' | null
  badgeLabel: '신규',
  updated: '2025-06-10',
  file: 'excel-cleaner.html',
  iconBg: 'rgba(52,211,153,.12)',
  iconBorder: 'rgba(52,211,153,.25)',
  iconColor: '#34d399',
  iconSvg: `<rect x="3" y="3" width="18" height="18" rx="2"/>...`,  // SVG path
  features: [
    '기능 설명 1',
    '기능 설명 2',
  ],
  steps: [
    { strong: '파일 업로드', text: ' — 드래그 앤 드롭' },
    { strong: '설정 선택', text: ' — 정리 옵션 선택' },
    { strong: '다운로드', text: ' — 완성 파일 저장' },
  ]
}
```

### 3. GitHub에 파일 업로드 후 푸시하면 자동 배포!

---

## 비밀번호 변경 방법
`index.html`의 `const PASSWORD = '...'` 값만 바꿔서 GitHub에 다시 업로드

> ⚠️ 이 비밀번호는 클라이언트 측 JS로만 검증됩니다.
> 민감한 내부 정보가 포함된 경우엔 서버 사이드 인증을 별도로 구성하세요.
