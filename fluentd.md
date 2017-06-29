# Fluentd
- http://www.fluentd.org/
- 데이터/로그 수집기
    - 시스템간 로그 수집/전송 기능을 통합
    - 쉬운 설정 & 적은 리소스 & 신뢰성 & 높은 성능
    - JSON format

## config
- source : http, tcp 등으로 전송된 데이터 중
- match : tag와 match되면 해당 작업 수행, match는 else if로 처리되므로 작은 단위부터 정의해야 함
- filter : 데이터 변환도 가능, source > filter 1...n > match 수행됨
- system : 전역 설정
- parsor : json 외 format 변환 시 사용
- @include : 파일 참조
- 확장 플러그인 : 온갖 input, output, formatter plugin 사용 가능
    ```
    # http://this.host:9880/myapp.access?json={"event":"data"}
    # tag : myapp.access
    # time: (current time)
    # record : {"event":"data"}
    <source>
        @type http
        port 9880
    </source>

    <filter myapp.*>
        @type record_transformer
        <record>
            host_param "#{Socket.gethostname}"
        </record>
    </filter>

    <match myapp.*>
        @type file
        path /var/log/fluent/access
    </match>

    <system>
        log_level error
    <system>
    ```

## usage
- buffer
    - tag 별로 chunk 생성
    - file에 쓰면 서비스 재시작 시 buffer도 복구 가능
- Fluentd & Kafka
    https://www.slideshare.net/repeatedly/fluentd-and-kafka
    http://docs.fluentd.org/v0.12/articles/out_kafka
    https://github.com/fluent/fluent-plugin-kafka
