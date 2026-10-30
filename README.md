# neo

카네비모빌리티 통합형 차량 디스플레이(클러스터 + IVI, 1920×1080) HTML 프로토타입입니다.
브라우저만 있으면 동작하며 ProtoPie 앱이나 API 키 없이 사용할 수 있습니다.

## 주요 화면
- **클러스터**: 3D 차량(P/D 뷰, 도어·창문·미러·트렁크 애니메이션, 전조등·비상등), ADAS(크루즈·차간거리·LDW·LKA), Telltale, 클러스터 TBT·미디어
- **내비게이션**: 지도, 장소 검색, 경유지(최대 5개), 경로 옵션, TBT, 주유소·전기차 충전소
- **미디어**: USB 음악, Bluetooth 음악, 라디오, YouTube(카테고리·검색·자막·전체화면, 주행 중 영상 가림), 이미지
- **Zoom**: 회의 홈·참가·호스트(실내 카메라 미리보기)·참가자·주행 중 영상 일시정지·클러스터 회의 카드 (웹 버전은 데모 데이터로 동작)
- **전화**: 연락처·통화 화면, Bluetooth 기기 연결 시나리오
- **카메라**: 서라운드 뷰(Top / Rear / Left / Right), 후방 주차 가이드라인, 근접 센서 표시
- **설정**: Connection / Vehicle(차량 색상) / Assist Driving / User Profile / System(Color theme) / Sound / Display / Exterior Light / Voice
- **공조·하단 내비게이션바**, 화면 끄기(Screen off)

## 사용 방법
- 하단 HW 키 바: Vehicle(전원·Screen off) / Gear / Steering / Door / Light / Drive Mode / Window·Mirror / ADAS
  - **Steering**: 핸들 아이콘을 좌우로 드래그하거나 마우스 휠로 회전(±450°), 더블클릭 시 중앙 복귀. 카메라 화면의 주차 궤적선이 핸들 각도를 따라 움직입니다.
- 키보드: `Enter` 시동 ON/OFF, `Esc` 전원 OFF, `1`–`4` 도어, `5` 트렁크, `0` 모든 도어 닫기
- HW 키 바 숨기기: 바 오른쪽 `Hide ▾` (다시 열기: 오른쪽 아래 `DEMO ▴`)
- Color theme: 설정 → System 에서 강조색 변경(배경·하단 바 그라데이션 포함)

## 카메라 · 웹캠 연동
- 카메라 화면의 각 영역(Top / Rear / Left / Right)을 터치하면 연결할 웹캠을 선택할 수 있습니다. (예: 핸드폰 가상 웹캠 DroidCam)
- 브라우저 보안 정책상 **https 주소(GitHub Pages) 또는 `localhost`** 에서만 카메라를 사용할 수 있습니다. `http://IP주소` 로 열면 동작하지 않습니다.
- 카메라 권한을 차단한 경우 주소창 왼쪽 자물쇠 → 카메라 → 허용 후 새로고침하세요.

## 외부 서비스
| 기능 | 키 없이 (기본) | 키 있을 때 |
|---|---|---|
| 지도 | Leaflet + Esri World Dark Gray 타일 (대체: OpenStreetMap 타일), 지명 현지어 | TomTom Orbis 벡터 지도(MapLibre GL), 지명 영어 표시, 실시간 교통 |
| 장소 검색 | Photon, Nominatim, Overpass (OpenStreetMap) | TomTom Search (한국은 `kr-api.tomtom.com` 우선) |
| 경로 안내 | OSRM 공개 서버 | TomTom Routing (교통 반영) |
| 라디오 | Radio Browser | — |
| YouTube | 영상 목록 표시 안 됨 (키 필요 안내 표시) | YouTube Data API v3 카테고리별 인기 영상·검색 (설정 국가 기준), 재생은 YouTube 임베드 플레이어 |
| Zoom | 데모 데이터 (회의·참가자 예시) | — (실제 Zoom 연동은 사내 로컬 실행 환경에서만 동작) |
| 3D 차량 | three.js | — |
| 폰트 | Pretendard | — |

공개 무료 서버(OSRM 데모, Nominatim, Overpass, Radio Browser)는 사용량 제한·이용 정책이 있어 데모 용도로만 사용합니다. 상용 서비스에는 사용할 수 없습니다.

## API 키 (로컬 사용 시)
웹(GitHub Pages) 버전은 **API 키 없이** 동작합니다. 지도는 무료 지도(Esri/OpenStreetMap), YouTube는 인기 영상 목록 없이 표시됩니다.
TomTom 지도·YouTube 인기 영상은 각자 PC의 로컬 사본에 키를 넣어 사용합니다. (설정 방법은 로컬 프로젝트 폴더의 README 참고)
**키가 들어간 `index.html` 은 이 저장소에 올리지 마세요.**

### 참고: YouTube Data API
- 발급: Google Cloud Console → YouTube Data API v3 사용 설정 → 사용자 인증 정보 → **공개 데이터(API 키)** 선택 → 키 제한에서 웹사이트 제한 + API 제한(YouTube Data API v3)
- 무료 할당량: 프로젝트당 하루 10,000 단위
- 키로 가능한 목록

| 목록 | 할당량 |
|---|---|
| 국가별 인기 동영상 (현재 한국) | 1회 1단위 |
| 카테고리별 인기 (음악·게임·스포츠·뉴스·영화 등) | 1회 1단위 |
| 다른 국가 인기 (국가 코드 변경) | 1회 1단위 |
| 특정 채널·재생목록 영상 | 1회 1~2단위 |
| 키워드 검색 | 1회 **100단위** (하루 약 100회) |

- 불가: 홈 추천·구독·시청 기록·내 재생목록 등 개인화 목록 (Google 로그인(OAuth) 필요)
- 재생은 공식 YouTube 임베드(IFrame) 플레이어를 사용합니다. 퍼가기가 막힌 영상은 재생되지 않습니다.
- YouTube 이용약관상 주행 중 재생, 플레이어 개조·광고 제거 등은 제한되므로 차량 양산 적용 시 별도 검토가 필요합니다.

### 참고: TomTom
- 발급: developer.tomtom.com → Dashboard → API key. 키에서 사용할 API(Maps(Orbis)·Search·Routing·Traffic)와 허용 도메인을 설정합니다.
- 벡터 지도는 키로 Orbis 지도 스타일을 받아올 때만 표시되며, 실패하면 이미지 지도 → 무료 지도 순으로 자동 전환됩니다.
- 키별 무료 사용 한도가 있고 초과 시 과금됩니다. (한도·요금은 TomTom 공식 페이지 기준으로 확인)
- 지원 국가
  - 지도 표시: 전 세계
  - 경로·교통 등 일부 API: 국가별 지원 범위가 다름 (예: Matrix Routing 지원 목록에 중국·일본 없음)
- **한국 데이터 규정** (TomTom Region-specific content)
  - 한국 상세 데이터는 한국 전용 서버 `kr-api.tomtom.com` 으로만 제공되며, 한국에서 처리·호스팅됩니다. 해외에서 요청하면 응답이 느릴 수 있습니다.
  - 한국 데이터를 한국 밖에 다운로드·저장·캐시·호스팅할 수 없습니다. (웹 브라우저 캐시는 예외)
  - 한국 내 장소의 좌표를 화면에 표시할 수 없습니다.
- 참고: [Market Coverage](https://developer.tomtom.com/matrix-routing-v2-api/documentation/product-information/market-coverage), [Region-specific content](https://docs.tomtom.com/routing-api/documentation/tomtom-orbis-maps/v3/product-information/region-specific-content)

## ProtoPie Connect 연동 (선택)
ProtoPie Connect 실행 중이면 `http://localhost:9981` 에 자동 연결됩니다. 다른 주소는 `?server=http://주소:포트`.
