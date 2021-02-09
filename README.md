# MonitoringLambda
AWS Cloudwatch 알람발생시, Telegram으로 모니터링사항을 노티받을 수 있는 Lambda 구현

## 진행방식 
<img src = "https://user-images.githubusercontent.com/78723318/107340298-f0db2d80-6b00-11eb-92ec-cf0eaff86841.PNG">

## Labmda 제한사항 
- 런타임 Python 3.8
- Layer추가 : request,urllib 등 필요한 모듈
- 타임아웃 : 최소 30초이상

### 텔레그램API
1) getUpdates <br>
  목적 : 메세지들의 결과 저장 (chat-id 확인가능) <Br>
  test request URL : https://api.telegram.org/bot<bot 토큰명>/getUpdates
2) sendMessage <br>
  목적 : text 이하의 메세지를 텔레그램으로 전송<Br>
  test request URL : https://api.telegram.org/bot<bot 토큰명>/sendMessage?
chat_id=<전송할 채널 id>&text=<보낼 msg>
3) sendPhoto <br>
  목적 : file id 에 해당하는 photo 를 텔레그램으로 전송<br>
test request URL : https://api.telegram.org/bot<bot 토큰명>/sendPhoto?
chat_id=<전송할 채널 id>&&photo=<보낼 phot 파일>
  
 텔레그램API 참고) https://core.telegram.org/bots/api


