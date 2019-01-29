.. |br| raw:: html


Data Analytics
=======================================

이 매뉴얼에서는 Smart[Fleet] 플랫폼의 데이터 분석 기능과 API 사용법을 소개합니다.

Driving Scoring
-----------------------

운전자 습관 분석 기능을 소개합니다. 고객사에서 제공하는 GPS 위치 정보 ``lat`` , ``lon`` 를 기반으로 운전자 습관 분석을 합니다. 세부적으로 다음 항목을 분석합니다.

- 운행거리 : GPS 맵매칭을 통한 정확한 운행 거리
- 주요 위험 운행 습관 지수 : 급가속, 급감속, 과속
- 맵 데이터를 통한 정교한 과속 : 맵매칭을 통한 도로 제한 속도 기반 과속 여부 판단
- 안전 운전 점수(100점 만점) : 안전 운전 점수 평가 알고리즘 활용

분석결과를 고객사에서 활용할 수 있도록 다음과 같은 API를 제공합니다.

- 주행 별 안전 운전 점수 리스트
- 위험 운행 습관 발생 위치 리스트
- 누적 안전 운전 점수

고객사에서는 위 API를 통해 다음과 같은 UI를 손쉽게 구현할 수 있습니다.

1. 운전자 점수 및 주요 안전 운행 습관 현황

.. image:: ../images/score/score.png
	:width: 30%


2. 주요 이벤트 위치 정보 및 주행별 점수 현황

.. image:: ../images/score/map_marks.png
	:width: 30%

Requirements
~~~~~~~~~~~~~

본 기능을 사용하기 위해서는 다음 조건을 만족해야 합니다.

1. 고객사가 등록한 센서는 `Smart[Fleet] 플랫폼 센서 메시지 포맷 <http://smart-fleet-docs.readthedocs.io/ko/latest/message/#id6>`__ 을 준수하는 ``GPS`` , ``OBD`` , ``BLACKBOX`` 센서다.
2. 각 센서는 ``lat`` , ``lon`` 값을 포함한다.
3. 각 센서의 ``Microtrip`` 전송 주기는 5초 미만이다. 
4. 단말기에서 정확한 trip 별 주행 거리 전송이 가능하면 trip 메세지 전송 시 dis 항목에 trip 별 주행 거리를 전송한다. 단말기에서 정확한 trip 별 주행 거리 전송이 불가하면 trip 메세지 전송 시 dis 항목을 제외한다. 
5. 3Km 이상 주행한다.


Driving Scoring APIs
~~~~~~~~~~~~~~~~~~~~

본 절에서는 Smart[Fleet]에서 제공하는 운전자 습관 분석 관련 API을 설명합니다.

- APIs 요약

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------+----------------------------------------------------------------+----------------------------------------------------------+
| Method  | URL                                                            | Description                                              |
+=========+================================================================+==========================================================+
| GET     | /api/tre/v1_3/vehicle/{vehicleId}/analytics/drivingScore       | 차량의 Trip 별 운전자 습관 정보 조회                     |
+---------+----------------------------------------------------------------+----------------------------------------------------------+
| GET     | /api/tre/v1_2/driver/{driverId}/analytics/drivingScore         | 운전자의 Trip 별 운전자 습관 정보 조회                   |
+---------+----------------------------------------------------------------+----------------------------------------------------------+
| GET     | /api/tre/v1_3/vehicle/{vehicleId}/analytics/gpsEvent           | 차량의 주요 위험 운행 습관 발생 위치와 세부 정보         |
+---------+----------------------------------------------------------------+----------------------------------------------------------+
| GET     | /api/tre/v1_2/driver/{driverId}/analytics/gpsEvent             | 운전자의 주요 위험 운행 습관 발생 위치와 세부 정보       |
+---------+----------------------------------------------------------------+----------------------------------------------------------+
| GET     | /api/tre/v1_3/vehicle/{vehicleId}/analytics/drivingScore/stat  | 차량의 현재까지 집계된 안전 운전 점수                    |
+---------+----------------------------------------------------------------+----------------------------------------------------------+
| GET     | /api/tre/v1_3/trip/{tripId}/analytics/drivingScore             | Trip ID로 안전 운전 점수 조회                            |
+---------+----------------------------------------------------------------+----------------------------------------------------------+

차량의 Trip 별 운전자 습관 정보 조회
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify
.. rst-class:: table-width-fix

본 API는 각 운행 ``Trip`` 별 안전 운전 점수와 점수 계산의 기반이 되는 ``운행거리``, ``급가속횟수``, ``급감속횟수``, ``과속횟수`` 정보를 제공합니다. 

+------------+----------------------------------------------------------+
| **GET**    | /api/tre/v1_3/vehicle/{vehicleId}/analytics/drivingScore |
+------------+----------------------------------------------------------+

- Parameters

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-------------------+----------+-----------+----------------------------------------------------------+
| Name              | Type     | Required  | Description                                              |
+===================+==========+===========+==========================================================+
| X-Authorization   | string   | O         | Auth token                                               |
+-------------------+----------+-----------+----------------------------------------------------------+
| vehicleId         | string   | O         | Vehicle ID                                               |
+-------------------+----------+-----------+----------------------------------------------------------+
| limit             | integer  | O         | 한번에 가져올 리스트 개수                                |
+-------------------+----------+-----------+----------------------------------------------------------+
| idOffset          | string   |           | 페이징을 시작할 아이템의 id                              |
+-------------------+----------+-----------+----------------------------------------------------------+
| startTime         | number   |           | from time (unix timestamp)                               |
+-------------------+----------+-----------+----------------------------------------------------------+
| endTime           | number   |           | to time (unix timestamp)                                 |
+-------------------+----------+-----------+----------------------------------------------------------+
| ascOrder          | boolean  |           | false(defalut) : time descending, true : time ascending  |
+-------------------+----------+-----------+----------------------------------------------------------+

- Example Code

.. role:: underline
        :class: underline

:underline:`Request (최신 2개의 운행별 운전자 점수)` :

.. code-block:: none

    curl --request GET \
    --url 'https://smartfleet.sktelecom.com:9901/api/tre/v1_3/vehicle/{{vehicleID}}/analytics/drivingScore?limit=2' \

:underline:`Response (code: 200)`

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

운전자의 Trip 별 운전자 습관 정보 조회
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify
.. rst-class:: table-width-fix

본 API는 각 운행 ``Trip`` 별 안전 운전 점수와 점수 계산의 기반이 되는 ``운행거리``, ``급가속횟수``, ``급감속횟수``, ``과속횟수`` 정보를 제공합니다. 

+------------+----------------------------------------------------------+
| **GET**    | /api/tre/v1_2/driver/{driverId}/analytics/drivingScore   |
+------------+----------------------------------------------------------+

- Parameters

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-------------------+----------+-----------+----------------------------------------------------------+
| Name              | Type     | Required  | Description                                              |
+===================+==========+===========+==========================================================+
| X-Authorization   | string   | O         | Auth token                                               |
+-------------------+----------+-----------+----------------------------------------------------------+
| driverId          | string   | O         | Driver ID                                                |
+-------------------+----------+-----------+----------------------------------------------------------+
| limit             | integer  | O         | 한번에 가져올 리스트 개수                                |
+-------------------+----------+-----------+----------------------------------------------------------+
| idOffset          | string   |           | 페이징을 시작할 아이템의 id                              |
+-------------------+----------+-----------+----------------------------------------------------------+
| startTime         | number   |           | from time (unix timestamp)                               |
+-------------------+----------+-----------+----------------------------------------------------------+
| endTime           | number   |           | to time (unix timestamp)                                 |
+-------------------+----------+-----------+----------------------------------------------------------+
| ascOrder          | boolean  |           | false(defalut) : time descending, true : time ascending  |
+-------------------+----------+-----------+----------------------------------------------------------+

- Example Code

.. role:: underline
        :class: underline

:underline:`Request (최신 2개의 운행별 운전자 점수)` :

.. code-block:: none

    curl --request GET \
    --url 'https://smartfleet.sktelecom.com:9901/api/tre/v1_2/driver/{{driverID}}/analytics/drivingScore?limit=2' \

:underline:`Response (code: 200)`

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

차량의 주요 위험 운행 습관 발생 위치와 세부 정보
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

본 API는 주요 위험 운행 습관 발생 위치와 세부 정보를 제공합니다. 예를 들어 ``급감속`` 위치, ``과속`` 위치, 제한속도, 실제속도 등을 제공합니다.

+------------+----------------------------------------------------------+
| **GET**    | /api/tre/v1_3/vehicle/{vehicleId}/analytics/gpsEvent     |
+------------+----------------------------------------------------------+

- Parameters

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-------------------+----------+-----------+----------------------------------------------------------+
| Name              | Type     | Required  | Description                                              |
+===================+==========+===========+==========================================================+
| X-Authorization   | string   | O         | Auth token                                               |
+-------------------+----------+-----------+----------------------------------------------------------+
| vehicleId         | string   | O         | Vehicle ID                                               |
+-------------------+----------+-----------+----------------------------------------------------------+
| limit             | integer  | O         | 한번에 가져올 리스트 개수                                |
+-------------------+----------+-----------+----------------------------------------------------------+
| idOffset          | string   |           | 페이징을 시작할 아이템의 id                              |
+-------------------+----------+-----------+----------------------------------------------------------+
| startTime         | number   |           | from time (unix timestamp)                               |
+-------------------+----------+-----------+----------------------------------------------------------+
| endTime           | number   |           | to time (unix timestamp)                                 |
+-------------------+----------+-----------+----------------------------------------------------------+
| ascOrder          | boolean  |           | false(defalut) : time descending, true : time ascending  |
+-------------------+----------+-----------+----------------------------------------------------------+

- Attritube Description

========  ========================================================
Key       Description
========  ========================================================
eventTy   - 주요 위험 운행 습관 항목
          1. 급출발
          2. 급가속
          3. 급감속
          4. 급정지
          5. 과속
========  ========================================================

- Example Code

.. role:: underline
        :class: underline

:underline:`Request (최신 2개의 상세 이벤트)` :

.. code-block:: shell

    curl --request GET \
    --url 'https://smartfleet.sktelecom.com:9901/api/tre/v1_3/vehicle/{vehicleId}/analytics/gpsEvent?limit=2' \


:underline:`Response (code: 200)` :

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

운전자의 주요 위험 운행 습관 발생 위치와 세부 정보
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

본 API는 주요 위험 운행 습관 발생 위치와 세부 정보를 제공합니다. 예를 들어 ``급감속`` 위치, ``과속`` 위치, 제한속도, 실제속도 등을 제공합니다.

+------------+----------------------------------------------------------+
| **GET**    | /api/tre/v1_2/driver/{driverId}/analytics/gpsEvent       |
+------------+----------------------------------------------------------+

- Parameters

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-------------------+----------+-----------+----------------------------------------------------------+
| Name              | Type     | Required  | Description                                              |
+===================+==========+===========+==========================================================+
| X-Authorization   | string   | O         | Auth token                                               |
+-------------------+----------+-----------+----------------------------------------------------------+
| driverId          | string   | O         | Driver ID                                                |
+-------------------+----------+-----------+----------------------------------------------------------+
| limit             | integer  | O         | 한번에 가져올 리스트 개수                                |
+-------------------+----------+-----------+----------------------------------------------------------+
| idOffset          | string   |           | 페이징을 시작할 아이템의 id                              |
+-------------------+----------+-----------+----------------------------------------------------------+
| startTime         | number   |           | from time (unix timestamp)                               |
+-------------------+----------+-----------+----------------------------------------------------------+
| endTime           | number   |           | to time (unix timestamp)                                 |
+-------------------+----------+-----------+----------------------------------------------------------+
| ascOrder          | boolean  |           | false(defalut) : time descending, true : time ascending  |
+-------------------+----------+-----------+----------------------------------------------------------+

- Attritube Description

========  ========================================================
Key       Description
========  ========================================================
eventTy   - 주요 위험 운행 습관 항목
          1. 급출발
          2. 급가속
          3. 급감속
          4. 급정지
          5. 과속
========  ========================================================

- Example Code

.. role:: underline
        :class: underline

:underline:`Request (최신 2개의 상세 이벤트)` :

.. code-block:: shell

    curl --request GET \
    --url 'https://smartfleet.sktelecom.com:9901/api/tre/v1_2/driver/{driverId}/analytics/gpsEvent?limit=2' \


:underline:`Response (code: 200)` :

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

차량의 현재까지 집계된 안전 운전 점수
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

본 API는 현재까지 집계된 운전자의 운전 습관 점수를 제공합니다.

+------------+-------------------------------------------------------------------+
| **GET**    | /api/tre/v1_3/vehicle/{vehicleId}/analytics/drivingScore/stat     |
+------------+-------------------------------------------------------------------+

- Parameters

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-------------------+----------+-----------+----------------------------------------------------------+
| Name              | Type     | Required  | Description                                              |
+===================+==========+===========+==========================================================+
| X-Authorization   | string   | O         | Auth token                                               |
+-------------------+----------+-----------+----------------------------------------------------------+
| vehicleId         | string   | O         | Vehicle ID                                               |
+-------------------+----------+-----------+----------------------------------------------------------+

- Example Code

.. role:: underline
        :class: underline

:underline:`Request` :

.. code-block:: shell

    curl --request GET \
  --url https://smartfleet.sktelecom.com:9901/api/tre/v1_3/vehicle/{vehicleId}/analytics/drivingScore/stat \

:underline:`Response (code: 200)` :

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

Trip ID로 안전 운전 점수 조회
^^^^^^^^^^^^^^^^^^^^^^^^

본 API는 Trip ID 로 안전 운전 점수를 조회합니다.

+------------+-------------------------------------------------------------------+
| **GET**    | /api/tre/v1_3/trip/{tripId}/analytics/drivingScore                |
+------------+-------------------------------------------------------------------+

- Parameters

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-------------------+----------+-----------+----------------------------------------------------------+
| Name              | Type     | Required  | Description                                              |
+===================+==========+===========+==========================================================+
| X-Authorization   | string   | O         | Auth token                                               |
+-------------------+----------+-----------+----------------------------------------------------------+
| tripId            | string   | O         | Trip ID                                                  |
+-------------------+----------+-----------+----------------------------------------------------------+

- Example Code

.. role:: underline
        :class: underline

:underline:`Request` :

.. code-block:: shell

    curl --request GET \
  --url https://smartfleet.sktelecom.com:9901/api/tre/v1_3/trip/{tripId}/analytics/drivingScore \

:underline:`Response (code: 200)` :

.. code-block:: json

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
    }