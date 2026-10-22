# 포트폴리오 대시보드 (매일 자동 갱신)

## 폴더 구성 (한 폴더에 모아두세요)
- portfolio_dashboard.py : 프로그램 본체
- tickers.csv : 종목명 ↔ 종목코드 (엑셀의 종목명과 똑같이 써야 함)
- 내 엑셀(.xlsx) : 폴더 안 가장 최근 파일을 자동 사용 (Total Sheet 필요)
- run_daily.bat : 더블클릭 실행용 (Windows)
- dashboard.html : 실행하면 생성되는 대시보드
- data/ : 일별 기록(history.csv) 자동 저장

## 1회 준비
1. Python 설치 후 `pip install openpyxl`
2. tickers.csv 확인 – KODEX 미국우주항공은 코드가 비어 있으니 직접 입력
   (나머지 코드도 한번 훑어보세요. 틀리면 해당 종목만 "이전 가격 사용"으로 표시됩니다)
3. `python portfolio_dashboard.py` 실행 → dashboard.html 열기

## 매일 자동 실행
- Windows: 작업 스케줄러 → 기본 작업 만들기 → 매일 → 프로그램: run_daily.bat
  (장 마감 후 15:40 이후 권장)
- Mac/Linux: crontab -e → `40 15 * * 1-5 cd /경로 && python3 portfolio_dashboard.py`

## 엑셀 수정 시
종목을 추가·수정하면 다음 실행 때 자동 반영됩니다.
새 종목은 tickers.csv에도 한 줄 추가하세요.
읽는 위치: Total Sheet 5행부터 'Total' 행 전까지 / B종목 C평균단가 D수량 E투자비용 H등급 J섹터

## 참고
- 추이 그래프는 프로그램을 실행한 날부터 쌓입니다 (하루 1점).
- 시세는 네이버 금융 데이터를 사용하며 지연되거나 형식이 바뀌면 조회가 실패할 수 있습니다.
- 상승=빨강, 하락=파랑(한국식) 색상입니다.
  
