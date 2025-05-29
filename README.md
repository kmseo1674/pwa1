##  인터랙티브 랜딩 페이지 프로젝트 ( PWA, Swiper, Google Maps API 활용)

이 프로젝트는 **Vanilla JavaScript**, **Swiper**, **Google Maps API** **PWA**를 활용하여 제작된 반응형 랜딩 페이지입니다.
PC 및 모바일 환경에서 부드럽고 자연스러운 사용자 경험을 제공합니다.

<br/>

### 주요 기능

- 반응형 메뉴 (모바일/데스크탑 구분)
- 메인 슬라이더 (Swiper 적용)
- 상품 슬라이드 (브레이크포인트 설정)
- 구글맵 표시
- PWA 기능

<br/>

### 사용 기술

| 태그 |![HTML](https://img.shields.io/badge/HTML5-F05032?logo=html5&logoColor=white&style=flat-square) |![CSS](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white&style=flat-square) |![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=000&style=flat-square) |![Swiper](https://img.shields.io/badge/Swiper-6332F6?logo=swiper&logoColor=white&style=flat-square) |![Google Maps](https://img.shields.io/badge/GoogleMaps-4285f4?logo=GoogleMaps&logoColor=white&style=flat-square) | ![PWA](https://img.shields.io/badge/PWA-5a0fc8?logo=PWA&logoColor=white&style=flat-square) |
|---|---|---|---|---|---|---|
| 설명 | 마크업 구조 | 반응형 스타일 처리 | DOM 제어, Swiper & GSAP 연동 | 슬라이더 구현 | 지도 표시 및 위치 마커 기능| 오프라인 접근 및 홈 화면 추가 |


<br/>

### 기능 상세 설명

### 1. 모바일 메뉴
- 기능:사용자가 탭을 클릭하면 사이드 메뉴가 열리고, 배경이 어두워집니다.
- 작동방식:메뉴가 열리면 body의 클래스에 fixed가 추가되어 스크롤이 비활성화됩니다.

 ``` JavaScript
  tab.addEventListener("click", function(e) {
    e.preventDefault();
    document.body.classList.add("fixed");
    mobile.classList.add("active");
    dim.classList.add("active");
});
```

---

### 2. 배경 클릭 시 메뉴 닫기

- 기능:사용자가 배경을 클릭하면 사이드 메뉴가 닫힙니다.
- 작동방식:배경 클릭 시 body의 fixed 클래스가 제거되어 스크롤이 다시 활성화됩니다.

```javascript
   dim.addEventListener("click", function() {
    document.body.classList.remove("fixed");
    mobile.classList.remove("active");
    dim.classList.remove("active");
});

```

---
### 3. 슬라이더 기능

- 기능: 메인 슬라이더와 서브 슬라이더를 사용하여 콘텐츠를 표시합니다.
- 작동 방식: 각 슬라이더에 대해 이전 및 다음 버튼과 페이지네이션이 설정됩니다.

```javascript
 const mainSwiper = new Swiper("#main_slider .swiper-container", {
    navigation: {
        prevEl: "#main_slider .swiper-button-prev",
        nextEl: "#main_slider .swiper-button-next"
    },
    pagination: {
        el: "#main_slider .swiper-pagination",
        type: "fraction"
    }
});

```

---
### 4. 구글 맵 표시

- 기능: 지정된 위치에 구글 맵을 표시하고 마커를 추가합니다.
- 작동 방식: 초기화 함수에서 위치와 줌 레벨을 설정하여 맵을 생성합니다.

```javascript
 function initMap() {
    let myLatLng = { lat: 37.390141551118695, lng: 126.97151846772532 };

    map = new google.maps.Map(document.getElementById("map"), {
        center: myLatLng,
        zoom: 16,
        mapTypeControl: false,
        zoomControl: false,
        fullscreenControl: false,
        rotateControl: false
    });

    let marker = new google.maps.Marker({
        position: myLatLng,
        map: map,
        title: "(주)오뚜기"
    });
}

```

---
