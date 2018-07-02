.. |br| raw:: html


Data Analytics
=======================================

이 매뉴얼에서는 Smart[Fleet] 플랫폼의 다양한 데이터 분석 기능 및 API 사용법에 대해서 소개합니다.

Driving Scoring
-----------------------

우선 먼저 소개 드리는 내용은 운전자 습관 분석에 대한 내용입니다.
Smart[Fleet] 플랫폼에서는 고객사에서 제공하는 GPS 위치 정보 ``lat`` , ``lon`` 를 기반으로 운전자 습관 분석을 위한 다음 항목을 분석합니다.

- GPS 맵매칭을 통한 정확한 운행 거리 계산
- 주요 안전 운행 습관 분석 (급출발, 급정거, 급감속, 급과속)
- 맵 데이터를 통한 정교한 과속 분석 (맵매칭을 통한 도로 제한 속도 기반 과속 여부 판단)
- 안전 운전 점수 평가 알고리즘을 통한 점수 제공 (100점 만점)

본 기능을 통해서 Smart[Fleet] 플랫폼이 제공하고자 하는 모습은 제공되는 API를 통해 다음과 같은 UI를 손쉽게 구현하는데 있다.

1. 운전자 점수 및 주요 안전 운행 습관 현황 

.. image:: ../images/score/score.png
	:width: 30%


2. 주요 이벤트 위치 정보 및 주행별 점수 현황

.. image:: ../images/score/map_marks.png
	:width: 30%

Requirements
~~~~~~~~~~~~~

운전자 습관 분석을 위한 요구사항은 다음과 같습니다.

1. `Smart[Fleet] 플랫폼 센서 메시지 포맷 <http://smart-fleet-docs.readthedocs.io/ko/latest/message/#id6>`__ 을 준수하는 ``GPS`` , ``OBD`` , ``BLACKBOX`` 센서다.
2. 각 센서는 기본적으로 ``GPS`` , ``OBD`` , ``BLACKBOX`` 포맷 내 ``lat`` , ``lon`` 값을 포함한다.
3. 각 센서가 제공하는 ``Microtrip`` 의 플랫폼 전송 주기는 5초 미만이여야 한다. 


Scoring APIs
~~~~~~~~~~~~~

본 절에서는 Smart[Fleet]에서 제공하는 운전자 습관 분석 관련 API을 설명합니다.

운행한 Trip 별 통계 리스트 조회
^^^^^^^^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify
.. rst-class:: table-width-fix

본 API는 각 운행 ``Trip`` 별로 계산된 운전 점수와 운행 중 Scoring 기반이 되는 ``급가속``, ``급감속``, ``운행거리``, ``과속횟수`` 정보를 제공합니다. 

========  ========================================================
GET       /api/tre/v1_3/vehicle/{vehicleId}/analytics/drivingScore
========  ========================================================

.. role:: underline
        :class: underline

:underline:`Request (최신 2개의 운행별 운전자 점수)` :

.. code-block:: shell

    curl --request GET \
    --url 'https://smartfleet.sktelecom.com:9901/api/tre/v1_3/vehicle/{{vehicleID}}/analytics/drivingScore?limit=2' \     

:underline:`Results (최신 2개의 운행별 운전자 점수)` :


.. code-block:: json

    {
        "data": [
            {
                "id": {
                    "id": "978926b0-6f68-11e8-8dc3-833dc5b9c077"
                },
                "createdTime": 1528940243972,
                "vehicleId": {
                    "id": "244bee00-3c7b-11e8-8994-85c175e72d24"
                },
                "userId": {
                    "id": "13814000-1dd2-11b2-8080-808080808080"
                },
                "score": 70.96813194953879,
                "accel": 18,
                "deAccel": 6,
                "dist": 49162,
                "overSpeed": 152
            },
            {
                "id": {
                    "id": "9dda8280-6ed6-11e8-8dc3-833dc5b9c077"
                },
                "createdTime": 1528873283657,
                "vehicleId": {
                    "id": "244bee00-3c7b-11e8-8994-85c175e72d24"
                },
                "userId": {
                    "id": "13814000-1dd2-11b2-8080-808080808080"
                },
                "score": 59.972895863052784,
                "accel": 0,
                "deAccel": 1,
                "dist": 3505,
                "overSpeed": 33
            }
        ],
        "nextPageLink": {
            "limit": 2,
            "startTime": null,
            "endTime": null,
            "ascOrder": false,
            "idOffset": "9dda8280-6ed6-11e8-8dc3-833dc5b9c077"
        },
        "hasNext": true
    }

.. note::
    Scoring 관련 상세 API는 https://smartfleet.sktelecom.com/apidoc 를 참고하세요.


주요 운전 습관에 대한 GPS Event 상세 정보
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

본 API는 주요 운전 습관에 대한 Smart[Fleet]에서 분석한 근거를 제공합니다. 
예를 들어 운전자의 ``급감속`` 위치 또는 ``과속`` 위치 및 과속 제한 및 실제 속도 정보 등을 제공합니다.

========  ========================================================
GET       /api/tre/v1_3/vehicle/{vehicleId}/analytics/gpsEvent
========  ========================================================


:underline:`Attritube Description` :

========  ========================================================
Key       Description
========  ========================================================
eventTy   - 주요 운전 습관 항목
          1. 급출발
          2. 급가속
          3. 급감속
          4. 급정지
          5. 과속
========  ========================================================


:underline:`Request (최신 2개의 상세 이벤트)` :

.. code-block:: shell

    curl --request GET \
    --url 'https://smartfleet.sktelecom.com:9901/api/tre/v1_3/vehicle/{vehicleId}/analytics/gpsEvent?limit=2' \


:underline:`Results (최신 2개의 상세 이벤트)` :

.. code-block:: json

    {
        "data": [
            {
                "id": {
                    "id": "7ca5e8e7-6f73-11e8-89a5-9de9665a30fc"
                },
                "createdTime": 1528940243797,
                "vehicleId": {
                    "id": "244bee00-3c7b-11e8-8994-85c175e72d24"
                },
                "tripId": {
                    "id": "978926b0-6f68-11e8-8dc3-833dc5b9c077"
                },
                "eventTs": 1528939593000,
                "eventTy": 5,
                "info": "{\"id\":\"ID_0169595\",\"maxSpd\":40000,\"rank\":107}",
                "deviceType": "BLACKBOX",
                "serviceType": null,
                "speedMh": 67680,
                "userId": {
                    "id": "13814000-1dd2-11b2-8080-808080808080"
                },
                "posLat": 37.3928,
                "posLon": 127.108052
            },
            {
                "id": {
                    "id": "7ca5e8e6-6f73-11e8-89a5-9de9665a30fc"
                },
                "createdTime": 1528940243797,
                "vehicleId": {
                    "id": "244bee00-3c7b-11e8-8994-85c175e72d24"
                },
                "tripId": {
                    "id": "978926b0-6f68-11e8-8dc3-833dc5b9c077"
                },
                "eventTs": 1528939591000,
                "eventTy": 5,
                "info": "{\"id\":\"ID_0169595\",\"maxSpd\":40000,\"rank\":107}",
                "deviceType": "BLACKBOX",
                "serviceType": null,
                "speedMh": 74160,
                "userId": {
                    "id": "13814000-1dd2-11b2-8080-808080808080"
                },
                "posLat": 37.39295,
                "posLon": 127.107777
            }
        ],
        "nextPageLink": {
            "limit": 2,
            "startTime": null,
            "endTime": null,
            "ascOrder": false,
            "idOffset": "7ca5e8e6-6f73-11e8-89a5-9de9665a30fc"
        },
        "hasNext": true
    }


운전 습관 점수
^^^^^^^^^^^

운전자의 현재까지 집계된 운전 습관 점수를 제공한다.

========  =============================================================
GET       /api/tre/v1_3/vehicle/{vehicleId}/analytics/drivingScore/stat
========  =============================================================


:underline:`Request (최신 2개의 상세 이벤트)` :

.. code-block:: shell

    curl --request GET \
  --url https://smartfleet.sktelecom.com:9901/api/tre/v1_3/vehicle/{vehicleId}/analytics/drivingScore/stat \

:underline:`Results` :

.. code-block:: json

    {
        "id": {
            "id": "244bee00-3c7b-11e8-8994-85c175e72d24"
        },
        "createdTime": 1528940244041,
        "userId": {
            "id": "13814000-1dd2-11b2-8080-808080808080"
        },
        "count": 40,
        "score": 73.72696393191347,
        "distance": 450311
    }