# PIPELINE
> Kafka를 MessageBroker로 사용하는 JSON RPC의 Python 구현체

## 개발

### 개발 환경
- Git
- Python 3.10.13
- Docker (version 26.1.1, build 4cf5afa)
- Docker Compose

### 개발 환경 구축
- 소스코드 다운로드
    ```bash
    git clone https://github.com/MemoriaScent/pipeline.git
    ```
- 소스코드 폴더로 이동
    ```bash
    cd pipeline
    ```
- VirtualEnv 구성
    ```bash
    python3 -m venv .venv
    ```
- VirtualEnv 활성화
    ```bash
    # Linux, macOS
    source .venv/bin/activate
    
    # Windows
    .venv/bin/activate.bat
    ```
- PIP 최신버전 업그레이드
    ```bash
    pip install -U pip
    ```
- 의존성 패키지 및 프로젝트 설치
    ```bash
    pip install -e .
    ```
- Kafka 구성 (Docker Compose 사용)
    ```bash
    docker compose up -d
    ```

### 개발 환경 종료
- Kafka 종료
    ```bash
    # 터미널의 Working Directory(pwd)가 프로젝트 최상단 폴더이어야 함 
    docker compose down
    ```
- VirtualEnv 해제
    ```bash
    # Linux, macOS, Windows
    deactivate
    ```
- Docker 임시 파일 삭제(선택사항)
    ```bash
    docker system prune -a
    ```

### 라이브러리 사용법
> examples 폴더 참고 
> (개별 예제 폴더의 `receiver.py`와 `sender.py`을 차례대로 실행 시킬것)

- `examples`
  - `simple` 가장 단순한 형태의 사용법
  - `class` 객체 메서드를 RPC로 호출하는 방법

### CLI 사용법
> 작성중...

## 개념
> Claude 3 Haiku를 사용하여 작성되었음

### API
API(Application Programming Interface)는 다른 소프트웨어 구성 요소와 상호 작용할 수 있는 방법을 정의하는 일종의 인터페이스입니다. 이를 통해 개발자들은 다른 애플리케이션이나 서비스의 기능을 자신의 애플리케이션에 통합할 수 있습니다.

API의 주요 특징은 다음과 같습니다:

1. 표준화된 인터페이스: API는 애플리케이션 간 통신을 위한 표준화된 방법을 제공합니다. 이를 통해 개발자들은 다른 시스템과 쉽게 상호 작용할 수 있습니다.

2. 데이터 및 기능 액세스: API를 통해 개발자들은 다른 애플리케이션이나 서비스가 제공하는 데이터와 기능에 접근할 수 있습니다. 이를 통해 새로운 애플리케이션을 빠르게 개발할 수 있습니다.

3. 확장성: API를 사용하면 애플리케이션을 확장하고 새로운 기능을 추가할 수 있습니다. 이를 통해 애플리케이션의 기능을 지속적으로 향상시킬 수 있습니다.

4. 상호 운용성: API를 통해 다른 시스템과 원활하게 상호 작용할 수 있습니다. 이를 통해 애플리케이션 간 데이터 공유와 통합이 가능해집니다.

API는 웹 서비스, 모바일 앱, 데스크톱 프로그램 등 다양한 분야에서 사용됩니다. 개발자들은 API를 활용하여 새로운 애플리케이션을 빠르게 개발하고 기존 애플리케이션을 확장할 수 있습니다.

### RPC
RPC(Remote Procedure Call)는 클라이언트 프로세스가 서버 프로세스에 있는 함수나 메서드를 호출할 수 있게 해주는 프로토콜입니다. 이를 통해 클라이언트는 서버의 기능을 사용할 수 있습니다.

RPC의 주요 특징은 다음과 같습니다:

1. 투명성: 클라이언트는 서버의 위치나 통신 방식에 대해 알 필요가 없습니다. 클라이언트는 마치 로컬 함수를 호출하듯이 서버의 함수를 호출할 수 있습니다.

2. 네트워크 추상화: RPC는 네트워크 통신 과정을 추상화하여 개발자가 네트워크 프로그래밍에 대한 지식 없이도 분산 시스템을 구축할 수 있게 해줍니다.

3. 동기/비동기 호출: RPC는 동기 호출과 비동기 호출을 모두 지원합니다. 동기 호출은 클라이언트가 서버의 응답을 기다리는 방식이고, 비동기 호출은 클라이언트가 응답을 기다리지 않고 다른 작업을 수행할 수 있는 방식입니다.

4. 다양한 프로토콜 지원: RPC는 HTTP, TCP, UDP 등 다양한 네트워크 프로토콜을 지원합니다.

RPC는 분산 시스템 개발에 널리 사용되며, 대표적인 RPC 프레임워크로는 gRPC, Apache Thrift, JSON-RPC 등이 있습니다. 이러한 RPC 프레임워크를 사용하면 개발자는 네트워크 통신 복잡성을 추상화하고 분산 시스템을 보다 쉽게 구축할 수 있습니다.

### HTTP
HTTP(Hypertext Transfer Protocol)는 웹 브라우저와 웹 서버 간의 통신을 위한 표준 프로토콜입니다. HTTP는 클라이언트-서버 모델을 기반으로 하며, 클라이언트(웹 브라우저)가 서버에 요청을 보내면 서버가 응답을 보내는 방식으로 동작합니다.

HTTP의 주요 특징은 다음과 같습니다:

1. 요청-응답 모델: 클라이언트가 서버에 요청을 보내면 서버가 응답을 보내는 방식으로 동작합니다.

2. 무상태(Stateless) 프로토콜: HTTP는 각 요청이 독립적이며, 이전 요청에 대한 정보를 저장하지 않습니다. 이를 보완하기 위해 쿠키, 세션 등의 기술이 사용됩니다.

3. 다양한 메서드 지원: HTTP는 GET, POST, PUT, DELETE 등 다양한 메서드를 지원하여 다양한 작업을 수행할 수 있습니다.

4. 헤더 정보 전송: HTTP 요청과 응답에는 메타데이터인 헤더 정보가 포함되어 있어 추가적인 정보를 전달할 수 있습니다.

5. 상태 코드 전송: HTTP 응답에는 상태 코드가 포함되어 있어 요청의 처리 결과를 알 수 있습니다.

HTTP는 웹 브라우저와 웹 서버 간의 통신뿐만 아니라 다양한 애플리케이션 간의 통신에도 사용됩니다. 최근에는 RESTful API, GraphQL 등 HTTP를 기반으로 하는 다양한 웹 서비스 아키텍처가 등장했습니다.

### JSON RPC
JSON-RPC(JSON Remote Procedure Call)는 JSON(JavaScript Object Notation) 형식을 사용하는 RPC(Remote Procedure Call) 프로토콜입니다. RPC와 마찬가지로 클라이언트가 서버의 함수를 호출할 수 있게 해주는 프로토콜입니다.

JSON-RPC의 주요 특징은 다음과 같습니다:

1. JSON 데이터 형식 사용: JSON-RPC는 JSON 형식을 사용하여 데이터를 전송합니다. JSON은 사람이 읽기 쉽고 기계가 처리하기 쉬운 데이터 형식입니다.

2. 경량성: JSON-RPC는 XML-RPC에 비해 경량적이며, 데이터 전송량이 적어 네트워크 대역폭 사용이 낮습니다.

3. 언어 독립성: JSON-RPC는 언어 독립적이므로 다양한 프로그래밍 언어에서 사용할 수 있습니다.

4. 동기/비동기 호출 지원: JSON-RPC는 동기 호출과 비동기 호출을 모두 지원합니다.

5. 오류 처리: JSON-RPC는 오류 처리를 위한 표준 메커니즘을 제공합니다.

JSON-RPC는 주로 웹 서비스, 마이크로서비스 등의 분산 시스템 개발에 사용됩니다. 클라이언트는 JSON-RPC 요청을 보내고 서버는 이에 대한 응답을 JSON 형식으로 보냅니다. 이를 통해 클라이언트와 서버 간의 통신이 가능해집니다.

JSON-RPC는 간단하고 효율적이며 언어 독립적이라는 장점으로 인해 널리 사용되고 있습니다. 특히 RESTful API와 함께 사용되어 강력한 웹 서비스 아키텍처를 구축할 수 있습니다.

### MessageBroker
RPC는 클라이언트가 서버의 함수를 호출할 수 있게 해주는 프로토콜입니다. RPC를 사용하면 클라이언트는 서버의 위치나 통신 방식에 대해 알 필요 없이 마치 로컬 함수를 호출하듯이 서버의 함수를 호출할 수 있습니다.

반면, 메시지 브로커는 메시지 생산자와 메시지 소비자 사이에서 메시지를 중개하는 역할을 합니다. 메시지 브로커는 메시지 큐, 발행/구독(Pub/Sub) 모델 등을 제공하여 분산 시스템 간의 비동기 통신을 가능하게 합니다.

RPC와 메시지 브로커는 다음과 같은 방식으로 함께 사용될 수 있습니다:

RPC 호출과 메시지 브로커 연계: RPC 호출의 결과를 메시지 브로커를 통해 다른 서비스에 전달할 수 있습니다. 이를 통해 서비스 간 비동기 통신이 가능해집니다.
메시지 브로커를 통한 RPC 호출: 메시지 브로커를 통해 RPC 호출을 전달할 수 있습니다. 이를 통해 서비스 간 비동기 호출이 가능해집니다.
메시지 브로커를 통한 데이터 전달: RPC 호출의 입력 데이터나 출력 데이터를 메시지 브로커를 통해 전달할 수 있습니다. 이를 통해 서비스 간 데이터 공유가 가능해집니다.
이와 같이 RPC와 메시지 브로커를 함께 사용하면 분산 시스템의 확장성, 유연성, 신뢰성 등을 높일 수 있습니다. RPC는 서비스 간 동기 호출을 가능하게 하고, 메시지 브로커는 서비스 간 비동기 통신을 가능하게 합니다.

Kafka와 Redis는 모두 메시지 브로커(Message Broker)의 역할을 하지만, 각각의 특성과 사용 사례가 다릅니다.

Kafka:
- Kafka는 분산 메시지 큐 시스템으로, 대량의 데이터를 안정적이고 효율적으로 처리할 수 있습니다.
- Kafka는 데이터 스트리밍 플랫폼으로 사용되며, 실시간 데이터 처리, 로그 수집, 이벤트 소싱 등에 적합합니다.
- Kafka는 높은 처리량과 내구성을 제공하며, 데이터 파티셔닝, 복제, 스케일링 등의 기능을 통해 대규모 분산 시스템에 적합합니다.
- Kafka는 메시지 보존 기능을 제공하여 과거 데이터에 대한 접근이 가능합니다.

Redis:
- Redis는 메모리 기반의 NoSQL 데이터베이스로, 빠른 응답 속도와 다양한 데이터 구조를 제공합니다.
- Redis는 메시지 브로커로 사용될 수 있으며, 주로 실시간 데이터 처리, 캐싱, 세션 관리 등에 활용됩니다.
- Redis는 메시지 큐, 발행/구독(Pub/Sub) 모델, 스트림 등의 기능을 제공하여 메시지 브로커로 사용될 수 있습니다.
- Redis는 메시지 보존 기능이 제한적이며, 주로 최신 데이터에 대한 빠른 접근이 필요한 경우에 사용됩니다.

요약하면, Kafka는 대규모 데이터 처리와 실시간 데이터 스트리밍에 적합한 메시지 브로커이며, Redis는 빠른 응답 속도와 다양한 데이터 구조를 제공하는 메시지 브로커입니다. 사용 사례와 요구 사항에 따라 Kafka 또는 Redis를 선택하여 메시지 브로커로 활용할 수 있습니다.

### Kafka
Kafka는 Apache Software Foundation에서 개발한 분산 스트리밍 플랫폼입니다. Kafka는 다음과 같은 주요 특징을 가지고 있습니다:

1. 분산 아키텍처:
   - Kafka는 클러스터 기반의 분산 아키텍처를 가지고 있습니다.
   - 클러스터 내에서 데이터는 파티션으로 나뉘어 저장되며, 이를 통해 확장성과 내결함성을 제공합니다.

2. 높은 처리량:
   - Kafka는 초당 수백만 개의 메시지를 처리할 수 있는 높은 처리량을 제공합니다.
   - 이를 통해 대량의 데이터를 실시간으로 처리할 수 있습니다.

3. 내구성:
   - Kafka는 데이터 복제와 파티셔닝을 통해 높은 내구성을 제공합니다.
   - 데이터는 여러 노드에 복제되어 저장되므로 장애 발생 시에도 데이터 손실을 방지할 수 있습니다.

4. 메시지 보존:
   - Kafka는 메시지를 로그 파일에 저장하여 일정 기간 동안 보존할 수 있습니다.
   - 이를 통해 과거 데이터에 대한 접근이 가능합니다.

5. 다양한 사용 사례:
   - Kafka는 실시간 데이터 처리, 로그 수집, 이벤트 소싱, 데이터 파이프라인 구축 등 다양한 분야에서 사용됩니다.

Kafka는 주로 대규모 데이터 처리, 실시간 데이터 스트리밍, 마이크로서비스 아키텍처 등의 분야에서 활용됩니다. Kafka는 높은 처리량, 내구성, 확장성 등의 특징으로 인해 대규모 분산 시스템 개발에 적합한 플랫폼으로 평가받고 있습니다.

## 오픈소스 기여 및 이슈 트래커

### 버그 발견시
- Github의 Issues 페이지에 등록해 주시기 바랍니다.

### 오픈소스 기여
- 아직 데모 버전으로 다양한 이슈가 존재할 수 있습니다.
- 분산 MessageBroker를 사용한 RPC 통신에 관심이 있으시다면 해당 프로젝트에 기여해 주시기 바랍니다.
- Git 프로젝트를 fork하여 기여한 후 Pull Requests를 통해 merge 요청해 주시기 바랍니다.

### Open Source License
- GNU Lesser General Public License v2.1
