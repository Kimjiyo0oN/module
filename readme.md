## 사용 방법

### 기본 스케줄러 사용 방법
- **bin/config.json**
  - **설명**: 기본 스케줄러 환경 파일인 bin/config.json 소스에서 bin/configSample.json sample 파일 참고해서 사용 가능
  참고 파일과 같이 schedulers은 리스트 형식으로 여러개의 스케줄러 사용 가능하며 filePath은 파일 경로를 spec 확장자 포함 파일명 작성

- **bin/jsonformat.json**
  - **설명**: 해당 파일을 참고해서 사용 hostId, mac 유형 두개 중에 아무거나 사용 가능
  hostId, mac 의 데이터 소스가 같은 파일에 있을 시 한 줄 에 hostId :  hd11, mac : vdd1VV 형식 필수
  다른 소스로 사용 시 hostId 한줄에 hostId :  hd11 한 데이터이며 hostId, mac 개수는 동일해야함
  개수가 틀릴 시 hostId 개수만큼 나옴

- **bin/datasource.txt**
  - **설명**: 해당 파일을 참고해서 사용

 사용자 인터페이스 사용 안 할 시 위에 파일들을 사용하면 동작 가능
 
### 사용자 인터페이스 사용 시
[localHost](http://localhost:8082/) 로 사용 

- **Upload Data**
  - **설명**: Upload Data 는 단발성 데이터 전송(스케줄러X) / Data as String(datasource.txt) 형식, JSON Format(jsonformat.json) 형식 작성 후 제출 버튼
   hostId, mac 의 데이터 소스가 같은 파일로 설정하고 한 줄 에 hostId :  hd11, mac : vdd1VV 형식 필수
 
- **UUpload scheduler Data**
  - **설명**: Upload scheduler Data 는 스케줄러 기능 / Data as String(datasource.txt) 형식, JSON Format(jsonformat.json) 형식 작성 , JSON Format(configData) 후 제출 버튼
  configData 형식 작성 시 스케줄러 (schedulers) 안에 데이터는 리스트 형식이나 한개만 작성 가능
    {	"udtServer": {
              "ip": "172.30.211.149",
              "port": 8888
        },
        "schedulers": [
       {
            "name": "one",
            "cronStr": "50 27 * * * ?",
            "spec": "jsonformat.json",
            "filePath" : ""  
          }
        ]
      }
  hostId, mac 의 데이터 소스가 같은 파일로 설정하고 한 줄 에 hostId :  hd11, mac : vdd1VV 형식 필수
  이 입력된 스케줄러는 리스트 형식에 한개의 스케줄러만 작성 가능하지만 Manage Jobs 버튼 클릭 시 스케줄러 삭제 및 관리 가능
  다수의 config파일이 작동되는 원리

- **Data Upload and Scheduler Configuration**
  - **설명**: Data as String(datasource.txt) , JSON Format(jsonformat.json) 각각 스케줄러에 필요한 거 작성 후 제출하면 각각 저장됨(파일 이름 작성란에 config 파일 혹시 jsonformat.json 
    파일에 적는 소스의 파일 경로에 일치되게 포함 시켜줘야함)
    Configuration Data 에 config 파일 작성 후 파일 이름만 작성하면 스케줄러 작동
    이 스케줄러의 경우는 스케줄러 리스트 형식으로 다수의 스케줄러 작성이 가능하지만 이번에 작성된 스케줄러 제거되고 이 제출된 config 파일만 작동


