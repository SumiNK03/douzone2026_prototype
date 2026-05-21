# 🧶 Knitching - 뜨개질 도안 학습 플랫폼

뜨개질 도안을 학습하고 탐색할 수 있는 웹 기반 학습 플랫폼입니다.

## 📋 프로젝트 개요

**Knitching**은 대바늘, 코바늘 등 다양한 뜨개질 도안을 검색하고 학습할 수 있는 인터랙티브한 웹 애플리케이션입니다.

> 💡 이 프로젝트는 **React 구현 전 프로토타입**입니다.  
> 현재 **Vanilla HTML/CSS/JavaScript**로 구현되었으며, 추후 React로 마이그레이션될 예정입니다.

### ⭐ 현재 구현된 기능
- ✅ **메인 화면**: 대시보드, 커리큘럼, 진도율
- ✅ **검색 기능**: 도안 이름, 작가명, 카테고리 기반 실시간 검색
- ✅ **UI/UX**: 반응형 디자인, 애니메이션, 호버 효과

## 📁 프로젝트 구조

```
5주차/
├── index.html              # 메인 HTML 파일
├── style.css               # 전체 스타일시트
├── data.json               # 도안 데이터 (JSON)
├── images/                 # 이미지 및 픽토그램 폴더
│   ├── logo.svg           # 로고
│   ├── 프로필사진.png      # 프로필 이미지
│   ├── 알림.svg            # 알림 아이콘
│   ├── 학습 중인 과정.svg  # 네비게이션 아이콘
│   ├── 둘러보기.svg
│   ├── 도안 - 대바늘.svg
│   ├── 도안 - 코바늘.svg
│   ├── 설정.svg
│   ├── 도안1.jpg ~ 도안4.jpg  # 도안 썸네일 이미지
│   └── (기타 리소스)
├── readme.md               # 프로젝트 문서
└── 메인 화면.png           # 디자인 가이드

```

## ✨ 주요 기능

### 1. **사이드바 네비게이션**
- 둘러보기 (기본 활성화)
- 학습 중인 과정
- 도안-대바늘
- 도안-코바늘
- 설정
- 호버/클릭 시 색상 애니메이션 (회색 → 파란색 → 배경색 채우기)

### 2. **상단 헤더바**
- 검색창 (돋보기 아이콘 포함)
- 알림 아이콘
- 프로필 사진 (원형, 여백 제거, 얼굴 중앙 상단 정렬)
- 사용자명 표시

### 3. **메인 콘텐츠 영역**

#### 대시보드 섹션 (파란색 배경)
- **프로필 카드**: 수강 중인 도안 이미지
- **커리큘럼 테이블**: 
  - 5개 강좌 목록
  - 수강 여부 상태 표시 (완료/수강중/미완료)
  - 상태별 색상 구분 (파란색/주황색/빨간색)
- **진도율 파이 차트**: 원형 차트로 진도 시각화

#### 새로 등록된 도안 섹션
- 3개 도안 카드 그리드 레이아웃
- 각 카드: 썸네일 이미지 표시
- 호버 시 상향 애니메이션

### 4. **검색 기능** ⭐
- **실시간 검색**: 입력 시 즉시 필터링
- **검색 대상**: 도안 이름, 작가명, 카테고리
- **검색 결과**: 새로 등록된 도안처럼 그리드 형태로 표시
- **정보 표시**: 이미지, 이름, 작가명, 카테고리 배지
- **초기화**: "닫기" 버튼으로 검색 초기화

## 📊 데이터 구조 (data.json)

```json
{
  "patterns": [
    {
      "id": 1,
      "name": "도안 이름",
      "author": "작가명",
      "image": "images/도안1.jpg",
      "category": "대바늘" | "코바늘"
    },
    ...
  ]
}
```

## 🛠️ 기술 스택

- **HTML5**: 의미론적 마크업
- **CSS3**: 반응형 디자인, 그라디언트, 애니메이션
- **JavaScript (Vanilla)**: 
  - JSON 데이터 로드 (Fetch API)
  - 실시간 검색 필터링
  - 동적 UI 상태 관리
  - 이벤트 리스너 (클릭, 입력)

## 🎨 디자인 특징

### 색상 팔레트
- **주요색**: #1e52f0 (파란색)
- **배경색**: #f8f9fd (연한 파란색)
- **텍스트**: #222 (다크 그레이)
- **상태색**: 
  - 완료: #1e52f0 (파란색)
  - 수강중: #f0811e (주황색)
  - 미완료: #e52525 (빨간색)

### 반응형 레이아웃
- **사이드바**: 240px 고정 너비
- **메인 콘텐츠**: Flex 레이아웃
- **그리드**: 3열 (768px 이하에서 1열)

## 📱 주요 UI 컴포넌트

### 네비게이션 메뉴
- SVG 아이콘 + 텍스트
- `color: inherit` 활용으로 상태 변화 시 색상 자동 변경
- 활성화 상태: 파란 배경 + 흰색 텍스트/아이콘

### 프로필 사진
- 정방형 이미지를 원형으로 표시
- `background-size: 150%` + `background-position: center 35%`로 여백 제거
- 얼굴이 원 중앙에 위치하도록 정렬

### 검색 결과 카드
- 썸네일 이미지
- 도안 정보 (이름, 작가명)
- 카테고리 배지
- 호버 효과 (translateY + 그림자)

## 🔧 JavaScript 핵심 로직

### JSON 데이터 로드
```javascript
async function loadPatternData() {
  const response = await fetch('data.json');
  const data = await response.json();
  allPatterns = data.patterns;
}
```

### 실시간 검색 필터링
```javascript
function performSearch(query) {
  const searchLower = query.toLowerCase();
  const results = allPatterns.filter(pattern => 
    pattern.name.toLowerCase().includes(searchLower) ||
    pattern.author.toLowerCase().includes(searchLower) ||
    pattern.category.toLowerCase().includes(searchLower)
  );
}
```

## 🚀 사용 방법

1. **파일 확인**: 모든 이미지와 `data.json` 파일이 올바른 경로에 있는지 확인
2. **로컬 서버 실행**: 
   ```bash
   # Python 3
   python -m http.server 8000
   
   # Python 2
   python -m SimpleHTTPServer 8000
   ```
3. **브라우저 접속**: `http://localhost:8000`

## 📝 주요 CSS 클래스

| 클래스 | 용도 |
|--------|------|
| `.sidebar` | 좌측 사이드바 |
| `.sidebar-nav` | 네비게이션 메뉴 |
| `.top-bar` | 상단 헤더바 |
| `.content-body` | 메인 콘텐츠 영역 |
| `.dashboard-section` | 대시보드 (파란 배경) |
| `.explore-section` | 새로운 도안 섹션 |
| `.explore-card` | 도안 카드 |
| `.search-results-section` | 검색 결과 영역 |
| `.avatar` | 프로필 사진 |

## 🎯 향후 개선 사항

### Phase 1: React 마이그레이션 🚀
- [ ] React 프로젝트 구조 생성
- [ ] 컴포넌트 분해 (Sidebar, Header, DashBoard, SearchResults 등)
- [ ] React State 관리 (useState, useContext, Redux 검토)
- [ ] 기존 로직 React Hook으로 재구현
- [ ] 스타일 마이그레이션 (CSS-in-JS 또는 Tailwind 검토)

### Phase 2: 기능 확장
- [ ] 백엔드 API 연동 (현재: JSON 파일 기반)
- [ ] 사용자 인증 기능
- [ ] 도안 상세 페이지
-

### Phase 3: UX/성능 개선
- [ ] 모바일 반응형 최적화


## 📄 라이센스

더존비앤씨티 인턴십 프로젝트

---

**Last Updated**: 2026년 5월 21일
