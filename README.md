# neo

카네비모빌리티 통합형 차량 디스플레이(클러스터 + IVI, 1920×1080) HTML 프로토타입입니다.
브라우저만 있으면 동작하며 ProtoPie 앱이나 API 키 없이 사용할 수 있습니다.

## 사용 방법
- 하단 데모 버튼 바: Power / Gear / Door / Light / Drive Mode
- 키보드: `Enter` 시동, `1`–`4` 도어, `5` 트렁크, `0` 모든 도어 닫기
- 데모 바 숨기기: 바 오른쪽 `숨기기 ▾` (다시 열기: 오른쪽 아래 `DEMO ▴`)

## 외부 서비스 (API 키 불필요)
| 기능 | 서비스 |
|---|---|
| 지도 | CARTO Dark Matter (OpenStreetMap 데이터) |
| 장소 검색 | Photon, Nominatim, Overpass (OpenStreetMap) |
| 경로 안내 | OSRM 공개 서버 |
| 라디오 | Radio Browser |
| 비디오 | YouTube 임베드 (기본 데모 영상) |

공개 무료 서버를 사용하므로 데모 용도에 맞춰 사용합니다.

## 선택: 개인 API 키
설정 → System 에서 TomTom 키(지도·검색·경로)와 YouTube Data API 키(인기 영상 목록)를 입력할 수 있습니다.
키는 입력한 사람의 브라우저에만 저장되며 이 저장소에는 포함되지 않습니다. **API 키를 이 저장소에 올리지 마세요.**

## ProtoPie Connect 연동 (선택)
ProtoPie Connect 실행 중이면 `http://localhost:9981` 에 자동 연결됩니다. 다른 주소는 `?server=http://주소:포트`.
