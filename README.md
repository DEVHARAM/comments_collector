## Comment Collector
### requirements
* Chrome driver - https://chromedriver.storage.googleapis.com/index.html?path=2.43/
* PhantomJS - http://phantomjs.org/download.html
* Selenium - https://www.seleniumhq.org/
* bs4(Beautiful soap) - https://www.crummy.com/software/BeautifulSoup/bs4/doc/

### Introduce
* 네이버 기사 댓글 수집기입니다.
* 연예, 정치, 경제, 사회 중 한가지 카테고리를 선택하여 랭크 순위권 기사의 댓글을 수집합니다.
* 30위까지의 수집이 끝나면 하루 전의 랭크로 이동하여 반복 작업합니다.

* `collector.py` : 실제 수집기
* `value.py` : URL string 모음

### How to run
1. requirements의 Chrome driver 혹은 PhantomJS를 운영체제에 맞는 버전으로 다운로드
2. requirements.txt 로 python package install

    ```pip install -r requirements.txt```
3. collector.py 에서 `MAX_LOOP_SHOW_MORE_BTN`, `MAX_RANK` 수치 조정
    * `MAX_LOOP_SHOW_MORE_BTN` : 댓글 더보기 버튼, 한 기사당 수집하는 댓글 갯수
    * `MAX_RANK` : 1위부터 30위 까지 존재하는 랭크에서 몇 순위의 기사까지 수집할 지 정하는 수
    * `SLEEP_TIME` : 각 버튼 클릭 후 리소스 로드까지 대기할 시간, 리소스 전부 로딩까지 대기하는 기능이 없기 때문에 추가
4. collector.py를 실행
    * ent, pol, eco, soc : 카테고리, 각각 연예, 정치, 경제, 사회
    * period : 수집 시작 날짜 ~ 수집 끝나는 날짜 (Format : Y-m-d)
5. collected 폴더에 `category_%Y%m%d.txt` 로 파일 생성

