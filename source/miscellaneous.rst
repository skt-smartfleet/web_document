.. |br| raw:: html

   <br />

Miscellaneous
=======================================


Swing Interworking
-----------------------

General Information
~~~~~~~~~~~~~~~~~~~~~

Smart[Fleet]을 사용해서 SKT 단말의 개통 정보를 확인할 수 있습니다. 확인이 가능한 개통 정보는 다음과 같습니다.

* 단말 개통에 따른 추가 정보 (IMEI, MDN, ICCID, IMSI 등)
* 단말의 현재 망 연동 현황 (망 연동 정상, 이용정지, 휴지정지, 해지정지, 직권해지, 일반해지 등)
* 단말이 현재 가입된 요금제 정보

아래 예제는 차량 ``vehicle`` 및 소유자 ``director`` 가 단말에 정상적으로 매핑 된 후 SKT의 가입망으로 통해서
정상적으로 등록된 단말의 조회 정보입니다. 단말의 요금제 ``subscription``, IMSI ``imsi``, 
IMEI ``serialNo``, MDN ``mdn`` 이 정상적으로 등록된 것을 확인하실 수 있습니다.

추가로 단말의 현재 망 연동 상태를 알려주는 ``nwStatus`` 의 의미는 다음 표와 같습니다.

========  ========================================================
Value     Description
========  ========================================================
00        미개통 및 SKT망 Cat.M1 연동이 아닌 단말
01        정상 개통
02        이용 정지
03        휴지 정지
04        해지 정지
05        직권 해지
06        일반 해지
99        원인 불상의 오류 (admin@smartfleet.sktelecom.com 연락)
========  ========================================================

.. code-block:: json

    {
        "id": {
            "id": "6802f7b0-0b34-11e8-9f2b-d3c31ebad2b2"
        },
        "createdTime": 1517918034596,
        "vehicleId": {
            "id": "6678d540-0b34-11e8-9f2b-d3c31ebad2b2"
        },
        "companyId": {
            "id": "37bb69a0-fb64-11e7-b6fe-d3c31ebad2b2"
        },
        "directorId": {
            "id": "6d91d980-0b34-11e8-9f2b-d3c31ebad2b2"
        },
        "status": "ACTIVATED",
        "vendor": "bbb",
        "type": "OBD",
        "additionalInfo": {
            "extra": "infoTest",
            "subscription": "aaaa",
            "imsi": "450109900011234",
            "iccid": "8982050809121205771F"
        },
        "lastTripMsgType": null,
        "activationRequired": false,
        "vehicleNo": "26나8999",
        "serialNo": "777888999000888",
        "credentialsId": null,
        "mdn": "01203331234",
        "nwStatus": "01"
    }

Major Actions
~~~~~~~~~~~~~~~~~~~~~

아래 표는 고객이 개통, 명의 변경 등의 업무를 통해서 접수된 내용을 Smart[Fleet] 처리하는 내용을 명시합니다.

============  ========================================================
Actions       Description
============  ========================================================
개통           정상 적인 개통 후에는 개통 시 명시된 주요 파라미터들이 상기 예제 JSON과 같이 플랫폼에 적시됩니다. |br| MDN을 발급 받은 경우에는 MDN 번호로 단말을 조회할 수 있습니다. 
기기 변경       정상 또는 정지 상태에서 고객의 요청에 따른 기기 변경 시에는, |br|
              1. 기존 기기에 매핑된 차량 및 소유자의 정보를 변경되는 기기에 해제 합니다.
              2. 변경되는 기기에 상기 차량 및 소유자의 정보를 자동으로 매칭합니다. 
명의 변경       정상 또는 정지 상태에서 고객의 요청에 따른 명의 변경 시에는, 
              * 기존 단말의 등록 상태를 모두 삭제합니다. 명의 변경에 따른 소유자 변경 처리는 별도의 Application단에서 진행합니다.  
번호 변경       정상 또는 정지 상태에서 고객의 요청에 따른 번호 변경 시에는,
              * MDN 번호를 신규 번호로 업데이트 합니다.
SIM 변경       정상 또는 정지 상태에서 고객의 요청에 따른 SIM 변경 시에는, 
              * ICCID, IMSI를 교체한 정보로 업데이트 합니다.
해지           정상 또는 정지 상태에서 고객의 요청에 따른 단말 해지 시에는,
              * 등록된 단말의 상태 정보를 모두 삭제합니다. 해지에 따른 고객 정보 Backup은 Application단에서 진행합니다.
정지           정상 상태에서 일시, 이용, 휴지, 해지 정지로 전환되는 상태에는,
              * 정지 상태의 상태를 단말의 ``nwStatus`` key에 업데이트 합니다.
요금제 변경      정상 또는 정지 상태에서의 고객의 요청에 따른 요금제 변경 시에는, 
              * 변경된 요금제 코드 정보를 단말 상태에 업데이트 합니다. 
============  ========================================================


일시 정지 해지 방법
~~~~~~~~~~~~~~~

단말 중에는 개통 방식에 따라 초기에 일시정지 상태로 보급되는 경우가 있을 수 있습니다. 이번 절에서는 해당 단말의 일시정지 해지하여 정상 개통 상태로 변경하는 방식을 기술합니다.

일시정지 상태의 단말은 `Device Entity <http://smart-fleet-docs.readthedocs.io/ko/latest/entity/#sensor-registration>`__  조회 시 상기 언급된 ``nwStatus`` 가 ``02`` 로 설정되어 있어야 하며, 
일시정지를 위해서는 다음 API를 호출합니다. (해당 API 호출 권한은 해당 단말을 소유한 COMPANY_ADMIN 입니다)

+------------+----------------------------------------------------------+
| **POST**   | /api/tre/v1_4/swing/unpause                              |
+------------+----------------------------------------------------------+

- Request Body

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify


========  =======  ========  ========================================================
Name      Type     M/O       Description
========  =======  ========  ========================================================
mdn       String   M         일시정지 해지를 위한 단말 MDN 번호   
========  =======  ========  ========================================================

해당 API 호출이 정상적으로 동작한 경우에는 대상 단말의 Device 상태를 조회하여 ``nwStatus`` 가 ``01`` 로 정상 변경되었는지 확인 부탁 드립니다. 만약 비정상적 동작으로 인하여 에러 코드를 리턴 받으신 경우에는 
해당 단말 UUID와 리턴 코드와 함께 admin@smartfleet.sktelecom.com 으로 연락 부탁 드립니다.

Data Interworking using kafka
-----------------------------

본 절에서는 Kafka를 통해서 Smart[Fleet]에 주행 데이터를 제공하는 방법에 대해서 기술합니다. 
본 Kafka를 통한 연결은 고객사에서 단말을 직접 Smart[Fleet]에 연결하지 않고, Smart[Fleet]의 API를 사용하고자 할때 사용합니다.

Architecture
~~~~~~~~~~~~~

.. image:: ../images/kafka/kafka_arc_01.png
	:width: 70%
	:align: center


Kafka 연동을 위해서 필요한 구조는 상단 그림에 명칭된 바와 같이 
``고객사 시스템 - Customer's System`` 와 ``Smart[Fleet]`` 으로 구성되고, 
2개의 시스템은 아래와 같이 데이터를 연동합니다. (아래 번호는 그림의 적색원에 번호와 동일합니다)

1. 고객사 시스템 자체 프로토콜을 통해서 단말과 고객사 백엔드 시스템을 연동하여 단말의 운행 데이터를 수집합니다.
2. 고객사 시스템에서 1 단계에서 수집한 단말 데이터 중 데이터 분석을 위해서 필요한 데이터를 ``Smart[Fleet] Kafka Cluster`` 로 전달합니다.
3. 2번 단계에서 수집된 단말 데이터를 기반으로 분석한 결과를 REST API를 통하여 고객사 시스템에서 호출합니다.


Preliminary Process
~~~~~~~~~~~~~~~~~~~~

`Smart[Fleet] Entity Architecture <http://smart-fleet-docs.readthedocs.io/ko/latest/architecture/>`__ 에 따라 
수신한 데이터로부터 연결된 차량 및 센서(디바이스)를 구분하기 위해서는 아래의 명시된 Smart[Fleet] Entity는 사전에 Smart[Fleet]에 등록되어 있어야 합니다.
이 외에 ``Driver`` , ``Director`` 및 ``Deligated Entities`` 를 고객사 시나리오에 따라 추가 하고자 할때는 `Device Entity <http://smart-fleet-docs.readthedocs.io/ko/latest/entity/#sensor-registration>`__ 를 참고하시어 
언급된 추가 Entity들을 저장하시면 됩니다.

1. `Device Entity <http://smart-fleet-docs.readthedocs.io/ko/latest/entity/#sensor-registration>`__ ``Mandatory``
2. `Vehicle Entity <http://smart-fleet-docs.readthedocs.io/ko/latest/entity/#vehicle-registration>`__ ``Mandatory``

.. note::
 .. rst-class:: text-align-justify

	Kafka 연동이 필요하신 경우에는 접속을 위해서 admin@smartfleet.sktelecom.com 으로 요청 부탁 드립니다.  Kafka 연동에 필요한 사항을 공지드리겠습니다.


Data Structure
~~~~~~~~~~~~~~

우선 Kafka를 통해서 Smart[Fleet]에 연동을 위해서는 아래의 토픽을 사용합니다.

============  ================================================================================================================
Topic Name    Description
============  ================================================================================================================
sf-microtrip  단말에서 운행 시작 후 주기적으로 보내는 ``microtrip`` 메세지를 포함하는 토픽으로 
              `Device Procedure <http://smart-fleet-docs.readthedocs.io/ko/latest/device/#device-procedure>`__ 중 
              ``microtrip`` 단계에 해당하는 메시지를 포함합니다.
sf-trip       단말에서 운행 종료 후 보내는 ``trip`` 메세지를 포함하는 토픽으로 
              `Device Procedure <http://smart-fleet-docs.readthedocs.io/ko/latest/device/#device-procedure>`__ 중
              ``trip`` 단계에 해당하는 메시지를 포함합니다.
sf-event      단말에서 운행 중 전송하는 ``event`` 메세지를 포함하는 토픽으로
              `Event Data <https://smart-fleet-docs.readthedocs.io/ko/latest/device/#event-data>`__ 중
              ``Publish Vehicle Event`` 단계에 해당하는 메시지를 포함합니다.
============  ================================================================================================================


각 토픽에 전달해야하는 메시지 구조는 다음과 같으며, JSON Format을 따릅니다.


Message Format for ``sf-microtrip`` Topic
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

============  ========  ==========  ====================================================================================================
Key           M/O       Type        Value
============  ========  ==========  ====================================================================================================
data          M         String      아래 ``Microtrip Message Format`` 참조
msgType       M         String      메시지 타입 ``microtrip``
============  ========  ==========  ====================================================================================================

``Microtrip Message Format`` Table

============  ========  ==========  ====================================================================================================
Key           M/O       Type        Value
============  ========  ==========  ====================================================================================================
date          M         String      전송 시간 (YYYY-MM-DDTHH:MM)
deviceType    M         String      디바이스 타입 (Smart[Fleet] 지원 단말 국한)
companyID     M         String      할당받은 ``company`` 식별자 
payload       M         String      `Device Procedure <http://smart-fleet-docs.readthedocs.io/ko/latest/device/#device-procedure>`__ 
                                    정의된 각 단말에 맞는 Microtrip 규격을 따라 운행 정보 기입합니다. 추가로 해당 Payload는
                                    `Aggregated Microtrip <http://smart-fleet-docs.readthedocs.io/ko/latest/message/#aggregated-microtrip>`__ 
                                    형태로 다수의 Microtrip이 JSON Array로 묶일 수 있습니다.
ts            M         String      Microtrip 수집 시간 (Timestamp msec)
createdTime   M         String      해당 메시지가 고객사 시스템에 등록된 시간 (Timestamp in milliseconds)
tripId        M         String      다수의 Microtrip이 하나의 Trip으로 묶이면 하나의 Trip으로 식별하여 명시
                                    고객사에서 UUID 형태로 별도 관리하시어 보내시면 됩니다.
microTripId   M         String      Smart[Fleet]에 등록된 Microtrip ID의 식별자
                                    고객사에서 UUID 형태로 별도 관리하시어 보내시면 됩니다.
vehicleId     M         String      Smart[Fleet]에 등록된 센서에 연결된 차량의 식별자 
sensorId      M         String      Smart[Fleet]에 등록된 센서에 식별자
============  ========  ==========  ====================================================================================================

.. code-block:: json

    {  
        "data":{  
            "date":"2018-07-02T15:10",
            "deviceType":"BLACKBOX",
            "companyId":"9340ba10-37ae-11e8-ad7d-833dc5b9c077",
            "payload":"[
                {\"tid\":664,\"try\":1,\"lat\":34.812622,\"lon\":126.417328,\"sp\":0,\"clt\":1530511744000},
                {\"tid\":664,\"try\":1,\"lat\":34.812622,\"lon\":126.417328,\"sp\":0,\"clt\":1530511746000},
                {\"tid\":664,\"try\":1,\"lat\":34.812622,\"lon\":126.417328,\"sp\":0,\"clt\":1530511748000},
                {\"tid\":664,\"try\":1,\"lat\":34.812622,\"lon\":126.417328,\"sp\":0,\"clt\":1530511750000}
            ]",
            "createdTime":1530511807210,
            "tripId":"715e6920-7db7-11e8-8dc3-833dc5b9c077",
            "microTripId":"917014a0-7dbe-11e8-8dc3-833dc5b9c077",
            "vehicleId":"ea9e81a0-3c65-11e8-a83e-69177a4f662b",
            "ts":1530511802000,
            "sensorId":"ece013c0-37b0-11e8-bc18-956d65b68a0a"
        },
        "msgType":"microtrip"
    }



Message Format for ``sf-trip`` Topic
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

============  ========  ==========  ====================================================================================================
Key           M/O       Type        Value
============  ========  ==========  ====================================================================================================
data          M         String      아래 ``Trip Message Format`` 참조
msgType       M         String      메시지 타입 ``trip``
latestTrip    M         String      아래 ``latestTrip Message Format`` 참조
============  ========  ==========  ====================================================================================================

``Trip Message Format`` Table

============  ========  ==========  ====================================================================================================
Key           M/O       Type        Value
============  ========  ==========  ====================================================================================================
deviceType    M         String      디바이스 타입 (Smart[Fleet] 지원 단말 국한)
companyID     M         String      할당받은 ``company`` 식별자 
payload       M         String      `Device Procedure <http://smart-fleet-docs.readthedocs.io/ko/latest/device/#device-procedure>`__ 
                                    정의된 각 단말에 맞는 Trip 규격을 따라 운행 정보 기입합니다. 
startTs       M         String      운행 시작 시간 (Timestamp msec)
endTs         M         String      운행 종료 시간 (Timestamp msec)
startDt       O         String      운행 시작 시간 (YYYY-MM-DD HH:MM:SS)
endDt         O         String      운행 종료 시간 (YYYY-MM-DD HH:MM:SS) 
createdTime   M         String      해당 메시지가 고객사 시스템에 등록된 시간 (Timestamp in milliseconds)
tripId        M         String      다수의 Microtrip이 하나의 Trip으로 묶이면 하나의 Trip으로 식별하여 명시
                                    고객사에서 UUID 형태로 별도 관리하시어 보내시면 됩니다.
vehicleId     M         String      Smart[Fleet]에 등록된 센서에 연결된 차량의 식별자 
sensorId      M         String      Smart[Fleet]에 등록된 센서에 식별자
userId        M         String      Smart[Fleet]에 등록된 운전자 식별자 (``driver`` 가 적용되었을 경우)
============  ========  ==========  ====================================================================================================

``latestTrip Message Format`` Table

============  ========  ==========  ====================================================================================================
Key           M/O       Type      s  Value
============  ========  ==========  ====================================================================================================
deviceType    M         String      디바이스 타입 (Smart[Fleet] 지원 단말 국한)
Id            O         String      Smart[Fleet]에 등록된 최신 Trip 데이터의 식별자 (if possible)
============  ========  ==========  ====================================================================================================


.. code-block:: json

    {  
        "data":{  
            "deviceType":"BLACKBOX",
            "companyId":"9340ba10-37ae-11e8-ad7d-833dc5b9c077",
            "payload":"{\"tid\":537,\"dis\":2142,\"stlat\":37.45194,\"stlon\":127.000317,\"edlat\":37.448247,\"edlon\":127.006768}",
            "endTs":1530514616000,
            "createdTime":1530513694199,
            "startDt":"2018-07-02 15:41:29",
            "endDt":"2018-07-02 15:56:56",
            "tripId":"f62bc070-7dc2-11e8-96b3-bf7af28e956c",
            "startTs":1530513689000,
            "vehicleId":"33baba10-3c6c-11e8-a83e-69177a4f662b",
            "userId":"13814000-1dd2-11b2-8080-808080808080",
            "sensorId":"ece60730-37b0-11e8-ad7d-833dc5b9c077"
        },
        "latestTrip":{
            "deviceType":"BLACKBOX"
        },
        "msgType":"trip"
    }



Message Format for ``sf-event`` Topic
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

============  ========  ==========  ====================================================================================================
Key           M/O       Type        Value
============  ========  ==========  ====================================================================================================
data          M         String      아래 ``Event Message Format`` 참조
msgType       M         String      메시지 타입 ``event``
============  ========  ==========  ====================================================================================================

``Event Message Format`` Table

============  ========  ==========  ====================================================================================================
Key           M/O       Type        Value
============  ========  ==========  ====================================================================================================
deviceType    M         String      디바이스 타입 (Smart[Fleet] 지원 단말 국한)
companyID     M         String      할당받은 ``company`` 식별자 
payload       M         String      `Device Procedure <http://smart-fleet-docs.readthedocs.io/ko/latest/device/#device-procedure>`__ 
                                    정의된 각 단말에 맞는 Microtrip 규격을 따라 운행 정보 기입합니다. 추가로 해당 Payload는
                                    `Aggregated Microtrip <http://smart-fleet-docs.readthedocs.io/ko/latest/message/#aggregated-microtrip>`__ 
                                    형태로 다수의 Microtrip이 JSON Array로 묶일 수 있습니다.
eventTs       M         String      이벤트 발생 시간 (Timestamp msec)
eventDt       O         String      이벤트 발생 시간 (YYYY-MM-DD HH:MM:SS) 
createdTime   M         String      해당 메시지가 고객사 시스템에 등록된 시간 (Timestamp in milliseconds)
tripId        M         String      다수의 Microtrip이 하나의 Trip으로 묶이면 하나의 Trip으로 식별하여 명시
                                    고객사에서 UUID 형태로 별도 관리하시어 보내시면 됩니다.
eventId       M         String      Smart[Fleet]에 등록된 센서에서 발생한 이벤트의 식별자
vehicleId     M         String      Smart[Fleet]에 등록된 센서에 연결된 차량의 식별자 
sensorId      M         String      Smart[Fleet]에 등록된 센서에 식별자
userId        M         String      Smart[Fleet]에 등록된 운전자 식별자 (``driver`` 가 적용되었을 경우)
ty            M         String      Smart[Fleet]에서 이벤트를 구분하는 
                                    `ty <https://smart-fleet-docs.readthedocs.io/ko/latest/message/#message-format-for-sensor>`__ 값
============  ========  ==========  ====================================================================================================

