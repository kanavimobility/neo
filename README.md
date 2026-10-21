# neo

카네비모빌리티 통합형 차량 디스플레이(클러스터 + IVI, 1920×1080) HTML 프로토타입입니다.
브라우저만 있으면 동작하며 ProtoPie 앱이나 API 키 없이 사용할 수 있습니다.

## 주요 화면
- **클러스터**: 3D 차량(P/D 뷰, 도어·창문·미러·트렁크 애니메이션, 전조등·비상등), ADAS(크루즈·차간거리·LDW·LKA), Telltale, 클러스터 TBT·미디어
- **내비게이션**: 지도, 장소 검색, 경유지(최대 5개), 경로 옵션, TBT, 주유소·전기차 충전소
- **미디어**: USB 음악, Bluetooth 음악, 라디오, 비디오, 이미지
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

## 외부 서비스 (API 키 불필요)
| 기능 | 서비스 |
|---|---|
| 지도 | Leaflet + Esri World Dark Gray 타일 (대체: OpenStreetMap 타일) |
| 장소 검색 | Photon, Nominatim, Overpass (OpenStreetMap) |
| 경로 안내 | OSRM 공개 서버 |
| 라디오 | Radio Browser |
| 비디오 | YouTube 임베드 (기본 데모 영상) |
| 3D 차량 | three.js |
| 폰트 | Pretendard |

공개 무료 서버를 사용하므로 데모 용도로만 사용합니다. (각 서버의 사용량 제한·이용 정책 적용)

## 선택: 개인 API 키
설정 → System 에서 아래 키를 입력할 수 있습니다.
- **TomTom 키**: Orbis 벡터 지도(MapLibre GL), 실시간 교통, 장소 검색
  - TomTom 지원 국가는 약 238개국이며 중국·일본은 미지원입니다. 한국 상세 데이터는 한국 전용 서버(`kr-api.tomtom.com`)로만 제공됩니다.
- **YouTube Data API 키**: 인기 영상 목록

키는 입력한 사람의 브라우저에만 저장되며 이 저장소에는 포함되지 않습니다. **API 키를 이 저장소에 올리지 마세요.**

## ProtoPie Connect 연동 (선택)
ProtoPie Connect 실행 중이면 `http://localhost:9981` 에 자동 연결됩니다. 다른 주소는 `?server=http://주소:포트`.
