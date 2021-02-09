# MonitoringLambda
AWS Cloudwatch 알람발생시, Slack 및 Telegram으로 모니터링사항을 노티받을 수 있는 Lambda 구현

## 진행방식 
<img src = "https://user-images.githubusercontent.com/78723318/107340298-f0db2d80-6b00-11eb-92ec-cf0eaff86841.PNG">

## Labmda 제한사항 
- 런타임 Python 3.8
- Layer추가 : request,urllib 등 필요한 모듈
- 타임아웃 : 최소 30초이상

## 텔레그램API
1) getUpdates <br>
 - 목적 : 메세지들의 결과 저장 (chat-id 확인가능) <Br>
 - test request URL : https://api.telegram.org/bot<bot 토큰명>/getUpdates
2) sendMessage <br>
 - 목적 : text 이하의 메세지를 텔레그램으로 전송<Br>
 - test request URL : https://api.telegram.org/bot<bot 토큰명>/sendMessage?chat_id=<전송할 채널 id>&text=<보낼 msg>
3) sendPhoto <br>
- 목적 : file id 에 해당하는 photo 를 텔레그램으로 전송<br>
- test request URL : https://api.telegram.org/bot<bot 토큰명>/sendPhoto?chat_id=<전송할 채널 id>&&photo=<보낼 photo 파일>
  
 텔레그램API 참고) https://core.telegram.org/bots/api

## 슬랙API
1) chat.postMessage
- Method URL : https://slack.com/api/chat.postMessage
- HTTP Method : POST
- Content-types : application/x-www-form-urlencoded, application/json
- bot 에게 필요한 scope : chat:write
- test request URL : https://slack.com/api/chat.postMessage?token=<bot 토큰명>&channel=<채널명>&text=<보낼메세지>
2) files.upload
- Method URL : https://slack.com/api/files.upload
- HTTP Method : POST
- Content-tyes : application/x-www-form-urlencoded, multipart/form-data
- bot 에게 필요한 scope : files:write
- test request URL : https://slack.com/api/files.upload?<bot 토큰명>&channel=<채널명>&text=<보낼메세지>

  슬랙API 참고) https://api.slack.com/ <br>
 1. incoming webhook API 방식 : Slack 자체에서 생성한 App 이 메세지를 보냄<br>
 2. WEB API 방식(텔레그램과 같은 방식) : Slack 안에 설치한 새로운 App 이 메세지를 보냄<br>
