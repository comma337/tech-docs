# Apache Kafka
- 대용량 실시간 로그 처리에 특화된 분산 메시징 시스템
- porducer가 topic의 메세지를 생성해서 broker한테 주면 잘 쌓아놨다가 comsumer가 가져다가(pull) 처리함

특징
- 대용랑 로그 & 분산 처리 가능
- TCP 기반 > 
- 메세지를 batch로 전달 가능
- (메모리가 아닌) 파일 시스템에 저장 > 데이터 영속성 보장, 성능 개선
- 처리 즉시 삭제하지 않고 설정 시간 경과 후 삭제 > 재 처리 가능
- pull 방식 > comsumer가 원하는 시점에 원하는 만큼 데이터를 가져와서 처리할 수 있음, broker 부담 감소

