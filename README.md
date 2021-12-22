# CRP(Chrome Releases Parser)

## 개요

- https://chromereleases.googleblog.com/ 를 파싱하여 특정 기간 동안 발생한 취약점 종류, 벡터, 찾은 사람, 등에 대한 빈도 수를 체크하기위해 만들었습니다.
- xlsx 파일로 파일이 저장됩니다.
- CRP에 대한 문서는 추후 깃헙에 추가될 예정입니다.

## 시작

- 필수 설치

  ```
  $ pip3 install beautifulsoup4
  $ pip3 install openpyxl
  ```

- 사용법

  ```
  oz1ng@LAPTOP-6F0C4A2N:/mnt/c/Users/ghdxo/Desktop/BoB/팀_프로젝트/bobjour-domino/CRP-Chrome_Releases_Parser-$ python3 CRP.py --help
  usage: CRP.py [-h] [--updated_max UPDATED_MAX] [--updated_min UPDATED_MIN] [--max_results MAX_RESULTS]
                [--load_path LOAD_PATH] [--save_path SAVE_PATH]
  
  CRP(Chrome_Releases_Parser)
  
  optional arguments:
    -h, --help            show this help message and exit
    --updated_max UPDATED_MAX, -M UPDATED_MAX
                          updated-max : 검색 마지막 날짜 : 없으면 가장 최신 업데이트까지 # format : 2021-10-01
    --updated_min UPDATED_MIN, -m UPDATED_MIN
                          updated-min : 검색 시작 날짜 : 없으면 가장 최초 업데이트부터, 웬만하면 주는게 좋다. # format : 2021-09-01
    --max_results MAX_RESULTS, -r MAX_RESULTS
                          max-results : 한번에 검색할 결과 개수
    --load_path LOAD_PATH, -l LOAD_PATH
                          load cumulative file path : 누적(로드)시킬 파일 경로. 옵션 안주면 ./CRP_Data.xlsx에 자동으로 누적. False 입력시 누적 X
    --save_path SAVE_PATH, -s SAVE_PATH
                          save file path : 저장할 파일 경로. 옵션 안주면 ./CRP_Data.xlsx 이름으로 저장
  ```

- 파싱 내용

  - Reward
  - Severity
  - Vuln
  - Vuln_Vector
  - Who
  - 날짜별 데이터..

- 파싱 대상

  - 기본적으로 `Stable Channel Update for Desktop`에 대한 내용만 파싱합니다. <br>만약 변경하고 싶다면  `self.parse_target`의 값을 바꿔주면 됩니다.

    ```python
    class CRP():
        def __init__(self, ...): 
            ...
    		self.parse_target = "Stable Channel Update for Desktop"
            ...
    ```

## 업데이트

### 2021-12-22

- 깃에 업로드
