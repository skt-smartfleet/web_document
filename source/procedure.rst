.. |br| raw:: html

   <br />

서비스 세부 절차
=======================================

전체 세부 절차
------------------

.. rst-class:: text-align-justify

Smart[Fleet] 플랫폼에서 제공하는 Open API를 이용하여 커넥티드카 서비스 및 장치를 개발하고자 하는 파트너업체들은 다음과 같은 기본 절차를 통해서 이용할 수 있습니다.

※ `Smart[Fleet] 웹 포털 사이트 <http://223.39.127.140:9000>`__

|br|

.. image:: ../images/procedure/1.png

|br|
|br|

파트너별 이용 안내
---------------------

.. rst-class:: text-align-justify

Smart[Fleet] 플랫폼을 이용하는 파트너 유형별로 아래 절차를 참고하셔서 본 파트너 매뉴얼을 활용하시면 보다 편리하게 이용하실 수 있습니다.

|br|

커넥티드카 서비스 사업자
~~~~~~~~~~~~~~~~~~~~~~~~~~

1. 사업 문의

..

  .. rst-class:: text-align-justify

  Smart[Fleet] 포털 ‘Support/사업문의’ 메뉴를 통해서 커넥티드카 서비스 및 Smart[Fleet] 플랫폼 활용방안 등에 대해서 문의를 하실 수 있습니다. 등록된 문의는 SKT Smart[Fleet] 사업 컨설팅 전문가에게 전달되어 전문가의 컨설팅 서비스를 받으실 수 있습니다. 고객사와 함께 할 협력사를 모집하고, SKT 담당자를 통해 센서 등 단말제조업체 등을 소개받을 수 있습니다.

2. 서비스 및 회사 등록

..

  .. rst-class:: text-align-justify

  구체적인 사업 계획이 잡히고 SKT 담당자와의 협의가 완성되면 포털에서 서비스 등록을 신청합니다. 세부 절차는 :ref:`3.3.1. 서비스 등록 절차 <service-registration-portal>` 를 참고하시기 바랍니다.

3. 협력사 등록

..

  서비스 및 함께 사업을 할 협력회사를 등록합니다. 귀사로부터 귀사의 차량을 위임받을 수도 있고, 반대로 협력사의 차량을 위임받아서 귀사가 관리할 수 있습니다.
  세부 절차는 :ref:`3.3.2. 회사(협력사) 등록 절차 <company-registration-portal>` 를 참고하시기 바랍니다.

4. 차량 등록

..

  .. rst-class:: text-align-justify

  커넥티드카 서비스 대상 차량을 등록합니다. 차량 내 각종 정보를 수집하기 위해서 부착되는 센서들이 차량 정보를 인식할 수 있도록 차량에 대한 자세한 정보를 입력합니다.
  세부 절차는 :ref:`3.3.3. 차량 등록 절차 <vehicle-registration-portal>` 를 참고하시기 바랍니다.

5. 센서 등록

..

  .. rst-class:: text-align-justify

  등록한 차량에 부착된, 또는 부착할 센서 장치 등을 등록합니다. 세부 절차는 :ref:`3.3.4. 센서 등록 절차 <sensor-registration-portal>` 를 참고하시기 바랍니다.

6. 차량과 센서 연결

..

  .. rst-class:: text-align-justify

  차량과 센서를 포털에 등록하면 Smart[Fleet] 플랫폼이 자동으로 차량과 센서간 연결을 제어하고, 차량으로부터 커넥티드카 서비스를 위한 각종 정보들을 수집하기 시작합니다.

7. 디렉터 등록

..

  .. rst-class:: text-align-justify

  등록된 차량이 다수이어서 소수의 관리자가 관리하기 어려울 경우에는 복수의 디렉터를 할당할 수 있습니다. 세부 절차는 :ref:`3.3.5. 디렉터 등록 절차 <director-registration-portal>` 를 참고하시기 바랍니다.

8. 드라이버 등록

..

  .. rst-class:: text-align-justify

  차량을 관리하지 않지만 실제 운전을 담당할 운전자를 드라이버로 등록할 수 있습니다. 세부 절차는 :ref:`3.3.6. 운전자 등록 절차 <driver-registration-portal>` 를 참고하시기 바랍니다.

9. 차량 위임

..

  .. rst-class:: text-align-justify

  커넥티드카 서비스 모델에 따라서 고객사의 차량을 협력사(예: 보험회사 등)에 관리권한을 위임할 수 있습니다. 위임받은 협력사는 귀사의 차량을 관리할 수 있으며, 차량관리 정보는 귀사에게 보고됩니다. 세부 절차는 :ref:`3.3.7. 위임회사 등록 절차 <delegated-company-registration-portal>` 를 참고하시기 바랍니다.

|br|
|br|

Device 개발자
~~~~~~~~~~~~~~

  .. rst-class:: text-align-justify

차량 내 부착되는 Device는 Smart[Fleet] platform과 MQTT프로토콜을 이용하여 통신합니다. MQTT에 대한 자세한 사항은 `MQTT.org <http://mqtt.org/>`__ 를 참고하시기 바랍니다.
|br|
Device개발 협력사는 Smart[Fleet] 플랫폼과 Device를 연결하기 위해서는 다음 절차를 참고하시기 바랍니다.

  .. rst-class:: text-align-justify

1. `3.3.1. 서비스 등록 <#service-registration>`__ , `3.3.2. 회사등록 <#company-partner-registration>`__ 절차 중 'API를 활용한 등록' 절차에서 설명한 예시를 참고하여 Platform와 연결하는 방법을 익힐 수 있습니다.
2. Activation이 필요한 센서에 대해서는 `3.3.3. 차량 등록 <#vehicle-registration>`__ 절차 내용을 참고하시기 바랍니다.
3. Smart[Fleet] 플랫폼과 연결이 완료되면 차량 내 부착된 센서들로부터 수집된 정보를 플랫폼으로 전송하기 시작합니다. 세부 절차는 `3.3.4. 센서 등록 <#sensor-registration>`__ 절차를 참고하시기 바랍니다. |br| 차량 내 센서가 Smart[Fleet] 플랫폼으로 센싱한 정보를 정상적으로 전송하기 위해서는 Smart[Fleet] 플랫폼에서 정의한 단말기 메시지 포맷을 맞추어야 합니다. 단말기 매시지 포맷 규격은 :ref:`6. 단말기 메시지 포맷 <message-format>` 내용을 참고하시기 바랍니다.
4. 어플리케이션에서 센서로부터 특정 데이터를 요구하거나, 특정 행동을 요청할 경우에는 RPC를 사용합니다. RPC 이용 절차는 `3.4.2. Sensor RPC <#device-rpc>`__ 내용을 참고하시기 바랍니다.
5. 마지막으로 SDK를 참고하여 개발을 하실 수 있습니다. |br| ODB2나 ADAS와 같이 센서가 부착된 디바이스를 개발하는 개발자는 :ref:`5.1. Embedded-C SDK <embedded-c-sdk>` 를 참고하시고, 스마트폰의 GPS를 사용하여 개발하는 개발자는 :ref:`5.2 Android SDK <android-sdk>` , :ref:`5.3. Object-C(iOS) SDK <object-c-sdk>` 내용을 참고하시기 바랍니다.

|br|
|br|

App 개발자
~~~~~~~~~~~~~

.. rst-class:: text-align-justify

Smart[Fleet] 에서 제공하는 포털을 사용하지 않을 경우 고객사에서 자체적으로 App을 제작할 수 있습니다.  자체 App 개발을 진행하는 경우에는 Smart[Fleet] 플랫폼에서 제공하는 REST-API를 활용하여 커넥티드카 서비스 App을 보다 쉽게 개발할 수 있습니다.

.. rst-class:: text-align-justify

1. 우선 Smart[Fleet] 구성 요소의 등록 방법은 `3.3. 구성요소(Entity) 등록 <#entity>`__ 절차를 통해서 자세하게 확인할 수 있습니다.
2. REST-API 규격을 이용하여 사용하여 Smart[Fleet] platform 에 데이터를 만들고 조회할 수 있습니다. REST API 규격에 대해서는 :ref:`4. API 규격 <api-specification>` 내용을 참고하시기 바랍니다.
3. 차량에 부착된 센서들로부터 전송되는 자동차 운행과 관련된 정보의 메시지 포맷은 :ref:`6. 단말기 메시지 포맷 <message-format>` 내용을 참고하시기 바랍니다.

.. rst-class:: text-align-justify

Web App을 개발하는 개발자는 :ref:`7.2. Web Application Simulator <web-application-simulator>` 내용을 참고하시기 바랍니다.

|br|
|br|

.. _entity-procedure:

구성요소(Entity) 등록
------------------------

서비스 등록 (Service Registration)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _service-registration-portal:

Smart[Fleet] 포털을 통한 등록
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

1. Smart[Fleet] 메인의 ‘서비스 등록’ 버튼을 통해 등록 신청 페이지로 이동합니다.

|br|

.. image:: ../images/procedure/3-1-1.png

|br|

.. rst-class:: text-align-justify

2. 필수 항목을 작성하여 서비스 등록 신청을 하면 신청한 내용이 SKT담당자에게 전달되고 검토 결과는 입력한 이메일로 발송됩니다.

|br|

.. image:: ../images/procedure/3-1-2.png

|br|

.. rst-class:: text-align-justify

3. 서비스 등록이 완료될 경우 운영사 계정이 자동으로 생성되며 ID는 입력한 이메일 주소와 동일합니다. 비밀번호는 등록완료 안내메일의 링크를 통해 설정이 가능합니다.

|br|

API를 활용한 등록
^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

포털을 통해서 회사 계정을 받은 파트너사에게 Smart[Fleet] 플랫폼에 접근할 수 있는 JWT 토큰을 제공합니다. REST API를 통해서 정상적으로 등록한 서비스의 토큰을 확인하는 방법은 다음과 같습니다.


로그인 요청 정보 API
''''''''''''''''''''

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+------------+------------------------------------+
| **POST**   | `/api/auth/login <https://app.swag |
|            | gerbub.com/apis/tremoteye/tremote  |
|            | yeapi/1.0.0#/Auth/post_api_auth_l  |
|            | ogin>`__                           |
+------------+------------------------------------+

-  Header

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+--------------+--------+------------------+--------------+
| option       | Type   | Default          | Description  |
+==============+========+==================+==============+
| Content-Type | string | application/json | content type |
+--------------+--------+------------------+--------------+

-  Body

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+----------+--------+-------------------------+
| Key      | Type   | Description             |
+==========+========+=========================+
| username | string | 로그인할 아이디(이메일) |
+----------+--------+-------------------------+
| password | string | 패스워드                |
+----------+--------+-------------------------+

.. role:: underline
        :class: underline

-  Example Code

:underline:`Request`

.. code-block:: none

	content-type:"application/json"

        {
		"username":"example@example.com",
		"password":"1234"
        }


:underline:`Response (code: 200)`

.. code-block:: json

	{
		"token":"eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJzeXNhZG1pbkB0aG…",
		"refreshToken": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJzeXNhZG1…"
	}

.. rst-class:: text-align-justify

요청이 성공하면(code:200) Response에서 인증 토큰으로 사용할 token 필드를 얻을 수 있습니다. Token 필드는 HTTP Header에 “X-Authorization"의 값으로 사용되며 로그인할 때마다 변경됩니다. 토큰이 있으면 해당 계정에 접근할 수 있으므로 외부 유출이 안되도록 주의해야 합니다.
|br|
토큰을 얻었으면 회사 정보 등록 API를 통해 서비스를 등록합니다.
|br|
요청 파라미터를 입력할 때 ServiceType이 중복되지 않도록 해야 합니다. ServiceType은 Unique 값으로 하나의 ServiceType에 한 운영사만 등록할 수 있습니다.

회사 정보 등록 API
''''''''''''''''''

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+------------+--------------------------------------+
| **POST**   | `/api/tre/v1/company <https://app.sw |
|            | aggerhub.com/apis/tremoteye/tremotey |
|            | eapi/1.0.0#/Company/post_api_tre_v1_ |
|            | company>`__                          |
+------------+--------------------------------------+

-  Header

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-----------------+--------+------------------+--------------+
| option          | Type   | Default          | Description  |
+=================+========+==================+==============+
| Content-Type    | string | application/json | content type |
+-----------------+--------+------------------+--------------+
| X-authorization | string |                  | auth token   |
+-----------------+--------+------------------+--------------+

-  Body

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-------------------+---------+-----------------------------------------+
| Key               | Type    | Description                             |
+===================+=========+=========================================+
| name              | string  | 등록할 회사 명칭                        |
+-------------------+---------+-----------------------------------------+
| region            | string  | 등록할 회사 지역                        |
+-------------------+---------+-----------------------------------------+
| serviceType       | string  | 운용하는 사업 명칭                      |
+-------------------+---------+-----------------------------------------+
| picName           | string  | 등록할 COMPANY_ADMIN 이름               |
+-------------------+---------+-----------------------------------------+
| picPhone          | string  | 등록할 COMPANY_ADMIN 연락처             |
+-------------------+---------+-----------------------------------------+
| picEmail          | string  | 등록할 COMPANY_ADMIN 이메일             |
+-------------------+---------+-----------------------------------------+
| picPasswd         | string  | 등록할 COMPANY_ADMIN 패스워드           |
+-------------------+---------+-----------------------------------------+
| picDivision       | string  | 등록할 COMPANY_ADMIN 소속 부서          |
+-------------------+---------+-----------------------------------------+
| sktManagerName    | string  | SKT 담당 매니저 이름                    |
+-------------------+---------+-----------------------------------------+
| sktManagerEmail   | string  | SKT 담당 매니저 이메일                  |
+-------------------+---------+-----------------------------------------+
| cooperationTask   | string  | 협력사 정보, 협력사 업무에 대해 기술    |
+-------------------+---------+-----------------------------------------+
| description       | string  | 추가 정보                               |
+-------------------+---------+-----------------------------------------+
| rpcNotifyHost     | string  | RPC 결과를 전송받기 위한 서버 호스트    |
+-------------------+---------+-----------------------------------------+
| rpcNotifyPort     | integer | RPC 결과를 전송받기 위한 서버 포트      |
+-------------------+---------+-----------------------------------------+
| rpcNotifyBasePath | string  | RPC 결과를 전송받기 위한 서버 기본 경로 |
+-------------------+---------+-----------------------------------------+

-  Example Code

:underline:`Request`

.. code-block:: none

        content-type:"application/json"
	X-Authorization: "Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJzeXNhZG1pbkB0aG…"

	{
		"name":"운영사A",
		"region":"대한민국",
		"serviceType":"example",
		"picName":"김담당자",
		"picEmail":"companya@example.com",
		"picPhone":"010-0000-0000",
		"picPasswd":"1234",
		"picDivision":"사업1팀",
		"sktManagerName":"박매니저",
		"sktManagerEmail":"manager@skt.com",
		"cooperationTask":"수리",
		"description":"additional description",
		"rpcNotifyHost":"localhost",
		"rpcNotifyPort":9000,
		"rpcNotifyBasePath":"/rpc_noti"
	}


:underline:`Response (code: 200)`

.. code-block:: json

	{
		"id": {
			"id": "c7fc12a0-beea-11e7-8bdf-af923035d741"
		},
		"createdTime": 1509530124485,
		"name": "운영사A",
		"serviceType": "example",
		"master": true,
		"masterId": {
			"id": "c7fc12a0-beea-11e7-8bdf-af923035d741"
		},
		"picPasswd": "1234",
		"picName": "김담당자",
		"picPhone": "010-0000-0000",
		"picEmail": "companya@example.com",
		"picDivision": "사업1팀",
		"sktManagerName": "박매니저",
		"sktManagerEmail": "manager@skt.com",
		"cooperationTask": "수리",
		"description": "additional description",
		"rpcNotifyHost": "localhost",
		"rpcNotifyPort": 9000,
		"rpcNotifyBasePath": "/rpc_noti"
	}

.. rst-class:: text-align-justify

정상적으로 등록하면(code:200) 위와 같이 생성된 회사 정보를 Response 값으로 확인할 수 있습니다.
|br|
운영사는 master 필드가 true로 출력되므로 master 필드를 통해 이 회사가 운영사로 등록됐는지 구분할 수 있습니다. 생성한 회사 계정으로 처음 로그인할 때 입력한 picEmail를 아이디, picPasswd를 패스워드로 사용합니다. 예시로 보면 companya@example.com이 아이디, 123가 패스워드입니다. 패스워드는 로그인 후에 변경할 수 있습니다.
|br|
REST API를 사용할 때 입력하는 Company ID는 Response 데이터에 있는 id 필드입니다. 예시에 있는 c7fc12a0-beea-11e7-8bdf-af923035d741이 Company
ID입니다.

|br|
|br|

회사(협력사) 등록 (Company (Partner) Registration)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _company-registration-portal:

Smart[Fleet] 포털을 통한 등록
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

1. 운영사 Admin 계정으로 로그인 후 ‘협력사’ 메뉴에서 등록 가능합니다.

|br|

.. image:: ../images/procedure/3-2-1.png

|br|

.. rst-class:: text-align-justify

2. 협력사 리스트 페이지에서 등록버튼을 통해 등록 페이지 이동

|br|

.. rst-class:: text-align-justify

.. image:: ../images/procedure/3-2-2.png

|br|

.. rst-class:: text-align-justify

3. 필수 항목 입력

|br|

.. image:: ../images/procedure/3-2-3.png

|br|

API를 활용한 등록
^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

운영사 계정을 통해서 협력사를 생성할 수 있습니다. 협력사를 등록하기 전에 운영사 계정으로 로그인하여 토큰 데이터를 얻습니다. ‘\ `3.3.1. 서비스 등록절차 <#회사-정보-등록-api>`__\ ’와 비교하면 계정이 가진 권한에 차이가 있을 뿐 등록 절차는 동일합니다.

로그인 요청 정보 API
''''''''''''''''''''

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+------------+----------------------------------------+
| **POST**   | `/api/auth/login  <https://app.swagger |
|            | hub.com/apis/tremoteye/tremoteyeap     |
|            | i/1.0.0#/Auth/post_api_auth_logi       |
|            | n>`__                                  |
+------------+----------------------------------------+

-  Header

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+--------------+--------+------------------+--------------+
| option       | Type   | Default          | Description  |
+==============+========+==================+==============+
| Content-Type | string | application/json | content type |
+--------------+--------+------------------+--------------+

-  Body

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+----------+--------+-------------------------+
| Key      | Type   | Description             |
+==========+========+=========================+
| username | string | 로그인할 아이디(이메일) |
+----------+--------+-------------------------+
| password | string | 패스워드                |
+----------+--------+-------------------------+

-  Example Code

:underline:`Request`

.. code-block:: none

        content-type:"application/json"

	{
		"username":"companya@example.com",
		"password":"1234"
	}


:underline:`Response (code: 200)`

.. code-block:: json

	{
		"token":"eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJzeXNhZG1pbkB0aG…",
		"refreshToken": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJzeXNhZG1…"
	}

.. rst-class:: text-align-justify

요청 파라미터를 입력할 때 협력사 ServiceType에는 운영사와 동일한 ServiceType을 기입합니다. 요청이 성공하면(code:200) Response에서 인증 토큰으로 사용할 token 필드를 얻을 수 있습니다. 토큰을 얻었으면 회사 정보 등록 API를 통해 서비스를 등록합니다.

회사 정보 등록 API
''''''''''''''''''

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+-------------+-----------------------------------------------+
|  **POST**   | `api/tre/v1/company <https://app.swaggerhub.c |
|             | om/apis/tremoteye/tremoteyeapi/1.0.0#/Company |
|             | /post_api_tre_v1_comapany>`__                 |
+-------------+-----------------------------------------------+


-  Header

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-----------------+--------+------------------+--------------+
| option          | Type   | Default          | Description  |
+=================+========+==================+==============+
| Content-Type    | string | application/json | content type |
+-----------------+--------+------------------+--------------+
| X-authorization | string | application/json | auth token   |
+-----------------+--------+------------------+--------------+

-  Body

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-------------------+---------+-----------------------------------------+
| Key               | Type    | Description                             |
+===================+=========+=========================================+
| name              | string  | 등록할 회사 명칭                        |
+-------------------+---------+-----------------------------------------+
| region            | string  | 등록할 회사 지역                        |
+-------------------+---------+-----------------------------------------+
| serviceType       | string  | 운용하는 사업 명칭                      |
+-------------------+---------+-----------------------------------------+
| picName           | string  | 등록할 COMPANY_ADMIN 이름               |
+-------------------+---------+-----------------------------------------+
| picPhone          | string  | 등록할 COMPANY_ADMIN 연락처             |
+-------------------+---------+-----------------------------------------+
| picEmail          | string  | 등록할 COMPANY_ADMIN 이메일             |
+-------------------+---------+-----------------------------------------+
| picPasswd         | string  | 등록할 COMPANY_ADMIN 패스워드           |
+-------------------+---------+-----------------------------------------+
| picDivision       | string  | 등록할 COMPANY_ADMIN 소속 부서          |
+-------------------+---------+-----------------------------------------+
| sktManagerName    | string  | SKT 담당 매니저 이름                    |
+-------------------+---------+-----------------------------------------+
| sktManagerEmail   | string  | SKT 담당 매니저 이메일                  |
+-------------------+---------+-----------------------------------------+
| cooperationTask   | string  | 협력사 정보, 협력사 업무에 대해 기술    |
+-------------------+---------+-----------------------------------------+
| description       | string  | 추가 정보                               |
+-------------------+---------+-----------------------------------------+
| rpcNotifyHost     | string  | RPC 결과를 전송받기 위한 서버 호스트    |
+-------------------+---------+-----------------------------------------+
| rpcNotifyPort     | integer | RPC 결과를 전송받기 위한 서버 포트      |
+-------------------+---------+-----------------------------------------+
| rpcNotifyBasePath | string  | RPC 결과를 전송받기 위한 서버 기본 경로 |
+-------------------+---------+-----------------------------------------+

-  Example Code


:underline:`Request`

.. code-block:: none

        content-type:"application/json"
	X-Authorization: "Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJzeXNhZG1pbkB0aG…"

	{
		"name":"협력사B",
		"region":"대한민국",
		"serviceType":"example",
		"picName":"김담당자",
		"picEmail":"companyb@example.com",
		"picPhone":"010-0000-0000",
		"picPasswd":"1234",
		"picDivision":"사업1팀",
		"sktManagerName":"박매니저",
		"sktManagerEmail":"manager@skt.com",
		"cooperationTask":"수리",
		"description":"additional description",
		"rpcNotifyHost":"localhost",
		"rpcNotifyPort":9000,
		"rpcNotifyBasePath":"/rpc_noti"
	}


:underline:`Response (code: 200)`

.. code-block:: json

	{
		"id": {
			"id": "3820ea50-beec-11e7-8bdf-af923035d741"
		},
		"createdTime": 1509530742131,
		"name": "협력사A",
		"serviceType": "example",
		"master": false,
		"masterId": {
			"id": "c7fc12a0-beea-11e7-8bdf-af923035d741"
		},
		"picPasswd": "1234",
		"picName": "김담당자",
		"picPhone": "010-0000-1111",
		"picEmail": "companya@example.com",
		"picDivision": "사업1팀",
		"sktManagerName": "박매니저",
		"sktManagerEmail": "manager@skt.com",
		"cooperationTask": "수리",
		"description": "additional description",
		"rpcNotifyHost": "localhost",
		"rpcNotifyPort": 9000,
		"rpcNotifyBasePath": "/rpc_noti"
	}

.. rst-class:: text-align-justify

정상적으로 등록하면(code:200) 위와 같이 생성된 회사 정보를 Response 값으로 확인할 수 있습니다.
|br|
협력사는 Master 필드가 False로 출력되므로 Master 필드를 통해 이 회사가 협력사로 등록됐는지 구분할 수 있습니다. 생성한 회사 계정으로 처음 로그인할 때 입력한 picEmail를 아이디로, picPasswd를 패스워드로 사용합니다. 예시로 보면 companyb@example.com이 아이디이고, 1234는 패스워드입니다. 패스워드는 변경할 수 있습니다.
|br|
REST API를 사용할 때 입력하는 Company ID는 Response 데이터에 있는 id입니다. 예시에 있는 3820ea50-beec-11e7-8bdf-af923035d741이 Company ID입니다.

|br|
|br|

차량 등록 (Vehicle Registration)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _vehicle-registration-portal:

Smart[Fleet] 포털을 통한 등록
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

1. 서비스에 사용할 차량을 등록하는 단계이며, 차량메뉴에서 등록이 가능합니다.

|br|

.. image:: ../images/procedure/3-3-1.png

|br|

.. rst-class:: text-align-justify

2. 차량 리스트 페이지에서 등록 버튼을 통해 등록 페이지로 이동합니다.

|br|

.. image:: ../images/procedure/3-3-2.png

|br|

.. rst-class:: text-align-justify

3. 차량 등록 시 1대씩 등록하거나 파일을 이용하여 대량으로 등록 가능합니다.

|br|

.. image:: ../images/procedure/3-3-3.png

|br|

4. 고객사가 관리중인 파일을 이용하여 대량으로 등록할 경우 CSV파일 형식만 처리 가능합니다. 파일의 양식은 샘플파일을 다운로드하여 참고할 수 있습니다.

|br|

.. image:: ../images/procedure/3-3-4.png

|br|

API를 활용한 등록
^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

COMPANY_ADMIN, DIRECTOR 계정은 관리하고자 하는 차량을 등록할 수 있습니다. DIRECTOR 계정으로 차량을 생성할 경우 담당 관리자로 해당 DIRECTOR가 설정됩니다. 협력사 계정으로 차량을 등록할 경우 운영사가 차량을 사용할 수 있도록 운영사를 CTOV에 추가합니다.
|br|
요청 파라미터를 입력할 때 mileage는 0을 초과해야 합니다. 파라미터를 누락하거나 0을 입력하면 에러 코드31(파라미터 누락 - Paramsameter 'mileage' can't be empty!) 오류가 발생합니다.

차량 등록 API
'''''''''''''

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+------------+--------------------------------------------+
| **POST**   | `/api/tre/v1/vehicle <https://app.swaggerh |
|            | ub.com/apis/tremoteye/tremoteyeapi/        |
|            | 1.0.0#/Vehicle/post_api_tre_v1_ve          |
|            | hicle>`__                                  |
+------------+--------------------------------------------+

-  Header

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-----------------+--------+------------------+--------------+
| option          | Type   | Default          | Description  |
+=================+========+==================+==============+
| Content-Type    | string | application/json | content type |
+-----------------+--------+------------------+--------------+
| X-authorization | string |                  | auth token   |
+-----------------+--------+------------------+--------------+

-  Body

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+----------------+--------+--------------+------------------+
| Key            | Type   | Enum         | Description      |
+================+========+==============+==================+
| vehicleNo      | string |              | 차량 번호        |
+----------------+--------+--------------+------------------+
| vendor         | string |              | 제조사           |
+----------------+--------+--------------+------------------+
| modelCode      | string |              | 모델 코드        |
+----------------+--------+--------------+------------------+
| modelName      | string |              | 모델 이름        |
+----------------+--------+--------------+------------------+
| modelYear      | number |              | 제조년도         |
+----------------+--------+--------------+------------------+
| missionType    | string | AUTO |br|    | 변속기 타입      |
|                |        | MANUAL       |                  |
+----------------+--------+--------------+------------------+
| fuelType       | string | DIESEL |br|  | 연료 타입        |
|                |        | GASOLINE |br||                  |
|                |        | LPG          |                  |
+----------------+--------+--------------+------------------+
| mileage        | number |              | 차량 총 주행거리 |
+----------------+--------+--------------+------------------+
| category       | string | TRUCK |br|   | 카테고리         |
|                |        | BUS |br|     |                  |
|                |        | TAXI |br|    |                  |
|                |        | PERSONAL ETC |                  |
+----------------+--------+--------------+------------------+
| usage          | string |              | 사용 용도        |
+----------------+--------+--------------+------------------+
| displacement   | number |              | 배기량           |
+----------------+--------+--------------+------------------+
| additionalInfo | string |              |                  |
+----------------+--------+--------------+------------------+

-  Example Code

:underline:`Request`

.. code-block:: none

        content-type:"application/json"
	X-Authorization: "Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJzeXNhZG1pbkB0aG…"

	{
		"vehicleNo": "00가0001",
		"vendor": "현대자동차",
		"modelCode": "G80",
		"modelName": "제네시스",
		"modelYear": 2017,
		"missionType": "AUTO",
		"fuelType": "DIESEL",
		"mileage":1,
		"category": "PERSONAL",
		"usage": "배송용",
		"displacement": 1999,
		"additionalInfo": "string"
	}

:underline:`Response (code: 200)`

.. code-block:: json

	{
		"id": {
			"id": "45f8a100-bef0-11e7-8bdf-af923035d741"
		},
		"createdTime": 1509532483338,
		"companyId": {
			"id": "c7fc12a0-beea-11e7-8bdf-af923035d741"
		},
		"directorId": {
			"id": "13814000-1dd2-11b2-8080-808080808080"
		},
		"currentDriverId": {
			"id": "13814000-1dd2-11b2-8080-808080808080"
		},
		"latestTripId": {
			"id": "13814000-1dd2-11b2-8080-808080808080"
		},
		"serviceType": "example",
		"vehicleNo": "00가0001",
		"modelName": "제네시스",
		"modelCode": "G80",
		"vendor": "현대자동차",
		"sensorCount": 0,
		"status": "DEACTIVATED",
		"additionalInfo": "string",
		"modelYear": 2017,
		"usage": "배송용",
		"category": "PERSONAL",
		"missionType": "AUTO",
		"fuelType": "DIESEL",
		"displacement": 1999,
		"mileage": 1,
		"delegateUserCount": 0,
		"lastTripMsgType": null
	}

.. rst-class:: text-align-justify

요청이 성공하면(code:200) Response에서 차량-센서 매핑할 때 사용하는 Vehicle ID를 얻을 수 있습니다. Vehicle ID는 Response 데이터에 있는 id 필드 안 id값입니다. 예시에 있는 45f8a100-bef0-11e7-8bdf-af923035d741이 Vehicle ID입니다.
|br|
처음 등록할 때 차량은 DEACTIVATED 상태로 설정됩니다.

|br|
|br|

센서 등록 (Sensor Registration)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _sensor-registration-portal:

Smart[Fleet] 포털을 통한 등록
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

1. 운영사 및 협력사Admin 계정으로 로그인 후 센서메뉴에서 등록 가능합니다.

|br|

.. image:: ../images/procedure/3-4-1.png

|br|

.. rst-class:: text-align-justify

2. 센서 리스트에서 등록버튼을 눌러 등록화면으로 이동합니다.

|br|

.. image:: ../images/procedure/3-4-2.png

|br|

.. rst-class:: text-align-justify

3. 차량 등록 시 1대씩 등록하거나 파일을 이용하여 대량으로 등록 가능합니다.

|br|

.. image:: ../images/procedure/3-4-3.png

|br|

.. rst-class:: text-align-justify

4. 고객사가 관리중인 파일을 이용하여 대량으로 등록할 경우 CSV파일 형식만 처리 가능합니다.
파일의 양식은 샘플파일을 다운로드하여 참고할 수 있습니다.

|br|

.. image:: ../images/procedure/3-4-4.png

|br|

API를 활용한 등록
^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

센서는 COMPANY_ADMIN 권한을 가진 회사 계정으로만 등록할 수 있습니다.

센서 등록 API
'''''''''''''

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+------------+--------------------------------------------+
| **POST**   | `/api/tre/v1/sensor <https://app.swaggerh  |
|            | ub.com/apis/tremoteye/tremoteyeapi/1.0.0#/ |
|            | Sensor/post_api_tre_v1_sensor>`__          |
+------------+--------------------------------------------+


-  Header

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-----------------+--------+------------------+--------------+
| option          | Type   | Default          | Description  |
+=================+========+==================+==============+
| Content-Type    | string | application/json | content type |
+-----------------+--------+------------------+--------------+
| X-authorization | string |                  | auth token   |
+-----------------+--------+------------------+--------------+

-  Body

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+--------------------+---------+-----------+---------------------------------+
| Key                | Type    | Enum      | Description                     |
+====================+=========+===========+=================================+
| serialNo           | string  |           | 센서 Serial No.                 |
+--------------------+---------+-----------+---------------------------------+
| credentialsId      | string  |           | Access Token                    |
+--------------------+---------+-----------+---------------------------------+
| vendor             | string  |           | 제조사                          |
+--------------------+---------+-----------+---------------------------------+
| type               | string  | OBD2 |br| | 센서 타입                       |
|                    |         | ADAS      |                                 |
+--------------------+---------+-----------+---------------------------------+
| activationRequired | boolean |           | RPC로 센서 활성화 필요한지 여부 |
+--------------------+---------+-----------+---------------------------------+
| missionType        | string  |           | 변속기 타입                     |
+--------------------+---------+-----------+---------------------------------+
| additionalInfo     | string  |           | 추가 정보                       |
+--------------------+---------+-----------+---------------------------------+

-  Example Code


:underline:`Request`

.. code-block:: none

        content-type:"application/json"
	X-Authorization: "Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJzeXNhZG1pbkB0aG…"

	{
		"serialNo": "A1",
		"credentialsId": "00000000000000000002",
		"vendor": "sk",
		"type": "OBD2",
		"activationRequired": true,
		"additionalInfo": "string"
	}


:underline:`Response (code: 200)`

.. code-block:: json

	{
		"id": {
			"id": "05a55bc0-bf63-11e7-8bdf-af923035d741"
		},
		"createdTime": 1509581767542,
		"vehicleId": {
			"id": "13814000-1dd2-11b2-8080-808080808080"
		},
		"companyId": {
			"id": "c7fc12a0-beea-11e7-8bdf-af923035d741"
		},
		"directorId": {
			"id": "13814000-1dd2-11b2-8080-808080808080"
		},
		"status": "DEACTIVATED",
		"vendor": "sk",
		"type": "OBD2",
		"additionalInfo": "string",
		"lastTripMsgType": null,
		"activationRequired": true,
		"vehicleNo": null,
		"serialNo": "A1",
		"credentialsId": "00000000000000000002"
	}

.. rst-class:: text-align-justify

요청이 성공하면(code:200) Response에서 차량과 센서를 매핑할 때 사용하는 Sensor ID를 얻을 수 있습니다. Sensor ID는 Response 데이터에 있는 id 필드 내의 id 값입니다. 예시에 있는 45f8a100-bef0-11e7-8bdf-af923035d741이 Sensor ID입니다.
|br|
처음 등록할 때 센서는 DEACTIVATED 상태로 설정됩니다. 해당 센서의 activationRequired 필드가 false이면 DEACTIVATED상태일 때도 차량과 매핑이 가능합니다. 매핑하면 ACTIVATED 상태가 됩니다.

|br|
|br|

디렉터 등록 (Director Registration)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _director-registration-portal:

Smart[Fleet] 포털을 통한 등록
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

1. 운영사 및 협력사 Admin로그인 후 각 회사의 디렉터를 등록할 수 있습니다.

|br|

.. image:: ../images/procedure/3-5-1.png

|br|

.. rst-class:: text-align-justify

2. 디렉터 리스트에서 등록 버튼을 눌러 등록 페이지로 이동합니다.

|br|

.. image:: ../images/procedure/3-5-2.png

|br|

.. rst-class:: text-align-justify

3. 필수 정보를 입력한 후 등록버튼을 누르면 입력한 이메일로 디렉터 등록 안내메일이 발송됩니다.

|br|

.. image:: ../images/procedure/3-5-3.png

|br|

.. rst-class:: text-align-justify

4. 수신한 협력사 등록신청 메일에서 비밀번호를 등록하면 협력사 계정 생성이 완료됩니다. ID는 입력한 이메일주소이며 비밀번호는 메일을 통해 등록한 비밀번호 입니다.

|br|

.. image:: ../images/procedure/3-5-4.png

|br|

API를 활용한 등록
^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

디렉터는 COMPANY_ADMIN 권한을 가진 회사 계정으로만 등록할 수 있습니다. 특정 차량들에 대해 관리자로 지정되어 관리하거나, 타 회사의 차량을 위임받아서 모니터링 할 수 있습니다.

디렉터 정보 등록 API
''''''''''''''''''''

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+------------+----------------------------------------------+
| **POST**   | `/api/tre/v1/director <https://app.swaggerhub|
|            | .com/apis/tremoteye/tremoteyeapi/            |
|            | 1.0.0#/Director/post_api_tre_v1_d            |
|            | irector>`__                                  |
+------------+----------------------------------------------+


-  Header

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-----------------+--------+------------------+--------------+
| option          | Type   | Default          | Description  |
+=================+========+==================+==============+
| Content-Type    | string | application/json | content type |
+-----------------+--------+------------------+--------------+
| X-authorization | string |                  | auth token   |
+-----------------+--------+------------------+--------------+

-  Body

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+----------+--------+-------------+
| Key      | Type   | Description |
+==========+========+=============+
| name     | string | 디렉터 이름 |
+----------+--------+-------------+
| email    | string | 이메일      |
+----------+--------+-------------+
| phone    | string | 연락처      |
+----------+--------+-------------+
| password | string | 패스워드    |
+----------+--------+-------------+

-  Example Code

:underline:`Request`

.. code-block:: none

        content-type:"application/json"
	X-Authorization: "Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJzeXNhZG1pbkB0aG…"

	{
		"name": "디렉터C",
		"email": "directorc@example.com",
		"phone": "010-0000-0000",
		"password": "1234",
	}


:underline:`Response (code: 200)`

.. code-block:: json

	{
		"id": {
			"id": "8e904530-c06c-11e7-8bdf-af923035d741"
		},
		"createdTime": 1509695813887,
		"companyId": {
			"id": "c7fc12a0-beea-11e7-8bdf-af923035d741"
		},
		"name": "디렉터C",
		"phone": "010-0000-0000",
		"vehicleId": null,
		"latestTripId": {
			"id": "13814000-1dd2-11b2-8080-808080808080"
		},
		"email": "directorc@example.com",
		"authority": "DIRECTOR",
		"password": null,
		"additionalInfo": null,
		"passwordUpdatedTime": 1509695813887
	}

.. rst-class:: text-align-justify

등록할 때 입력한 email이 아이디입니다. Example Code에서 아이디는 directorc@example.com 이고, 패스워드는 1234 입니다. Authority 필드를 통해 해당 계정이 DIRECTOR 계정인지 DRIVER 계정인지 구분할 수 있습니다.

|br|
|br|

운전자 등록 (Driver Registration)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _driver-registration-portal:

Smart[Fleet] 포털을 통한 등록
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

1. 운영사 및 협력사 Admin로그인 후 각 회사의 드라이버를 등록할 수 있습니다.

|br|

.. image:: ../images/procedure/3-6-1.png

|br|

.. rst-class:: text-align-justify

2. 드라이버 리스트에서 등록 버튼을 눌러 등록 페이지로 이동합니다.

|br|

.. image:: ../images/procedure/3-6-2.png

|br|

.. rst-class:: text-align-justify

3. 필수 정보를 입력한 후 등록버튼을 누르면 드라이버의 등록이 완료됩니다.

|br|

.. image:: ../images/procedure/3-6-3.png

|br|

API를 활용한 등록
^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

운전자는 COMPANY_ADMIN 권한을 가진 회사 계정으로만 등록할 수 있습니다. 차량 운행 서비스를 이용할 수 있습니다.

운전자 등록 API
'''''''''''''''

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+------------+---------------------------------------------+
| **POST**   | `/api/tre/v1/driver <https://app.swaggerhub |
|            | .com/apis/tremoteye/tremoteyeapi/           |
|            | 1.0.0#/Driver/post_api_tre_v1_driver>`__    |
+------------+---------------------------------------------+

-  Header

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-----------------+--------+------------------+--------------+
| option          | Type   | Default          | Description  |
+=================+========+==================+==============+
| Content-Type    | string | application/json | content type |
+-----------------+--------+------------------+--------------+
| X-authorization | string |                  | auth token   |
+-----------------+--------+------------------+--------------+

-  Body

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+----------+--------+-------------+
| Key      | Type   | Description |
+==========+========+=============+
| name     | string | 운전자 이름 |
+----------+--------+-------------+
| email    | string | 이메일      |
+----------+--------+-------------+
| phone    | string | 연락처      |
+----------+--------+-------------+
| password | string | 패스워드    |
+----------+--------+-------------+

-  Example Code

:underline:`Request`

.. code-block:: none

        content-type:"application/json"
	X-Authorization: "Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJzeXNhZG1pbkB0aG…"

	{
		"name": "드라이버B",
		"email": "driverb@example.com",
		"phone": "010-0000-0000",
		"password": "1234"
	}


:underline:`Response (code: 200)`

.. code-block:: json

	{
		"id": {
			"id": "69b5f470-c06d-11e7-8bdf-af923035d741"
		},
		"createdTime": 1509696181554,
		"companyId": {
			"id": "c7fc12a0-beea-11e7-8bdf-af923035d741"
		},
		"name": "드라이버B",
		"phone": "010-0000-0000",
		"vehicleId": null,
		"latestTripId": {
			"id": "13814000-1dd2-11b2-8080-808080808080"
		},
		"email": "driverb@example.com",
		"authority": "DRIVER",
		"password": null,
		"additionalInfo": null,
		"passwordUpdatedTime": 1509696181554
	}

.. rst-class:: text-align-justify

등록할 때 입력한 email이 아이디가 됩니다. Example Code에서 아이디는 driverb@example.com 이고, 패스워드는 1234 입니다. Authority 필드를 통해 해당 계정이 DIRECTOR 계정인지 DRIVER 계정인지 구분할 수 있습니다.

|br|
|br|

위임 회사 등록 (Delegated Company Registration)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _delegated-company-registration-portal:

Smart[Fleet] 포털을 통한 등록
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

1. 운영사 Admin로그인 후 협력사 메뉴에서 각 회사를 위임 회사로 설정할 수 있습니다.

|br|

.. image:: ../images/procedure/3-7-1.png

|br|

.. rst-class:: text-align-justify

2. 협력사 리스트에서 주요협력사 스위치를 눌러 활성화 합니다.

|br|

.. image:: ../images/procedure/3-7-2.png

|br|

.. rst-class:: text-align-justify

3. 주요 협력사로 선택한 회사에 차량을 위임할 수 있습니다. 해당 기능은 차량 메뉴에서 이용 가능합니다.

|br|

.. image:: ../images/procedure/3-7-3.png

|br|

.. rst-class:: text-align-justify

4. 차량 리스트 화면에서 차량 위임버튼을 눌러 위임 화면으로 이동합니다.

|br|

.. image:: ../images/procedure/3-7-4.png

|br|

.. rst-class:: text-align-justify

5. 차량 선택 후 추가버튼을 눌러 차량을 선택된 차량 영역으로 이동시킨 후 다음으로 이동합니다.

|br|

.. image:: ../images/procedure/3-7-5.png

|br|

.. rst-class:: text-align-justify

6. 위임할 회사를 검색 및 선택한 후 위임 버튼을 눌러 위임을 완료합니다.

|br|

.. image:: ../images/procedure/3-7-6.png

|br|

API를 활용한 등록
^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

협력 관계에 있는 회사에 차량을 위임하면 그 회사는 위임 회사가 됩니다. 그 전에 위임하는 회사가 먼저 협력사를 위임 후보 회사로 등록해야 합니다. 회사 간 ServiceType이 동일해야 합니다.

위임 후보 회사 등록 API
'''''''''''''''''''''''

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+------------+-------------------------------------------+
| **POST**   |`/api/tre/v1/company/{companyId}/relation/\|
|            |company <https://app.swaggerhub.com/apis/t\|
|            |remoteye/tremoteyeapi/1.0.0#/Relation/post\|
|            |_api_tre_v1_company__companyId__relation_c\|
|            |ompany>`__                                 |
+------------+-------------------------------------------+

-  Header

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-----------------+--------+------------------+--------------+
| option          | Type   | Default          | Description  |
+=================+========+==================+==============+
| Content-Type    | string | application/json | content type |
+-----------------+--------+------------------+--------------+
| X-authorization | string |                  | auth token   |
+-----------------+--------+------------------+--------------+

-  Path

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-----------+--------+-----------------------------------+
| Key       | Type   | Description                       |
+===========+========+===================================+
| companyId | string | 자신의 회사 ID (위임하는 회사 ID) |
+-----------+--------+-----------------------------------+

-  Body

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+--------------------+-------------+-----------------------------------------------+
| Key                | Type        | Description                                   |
+=============+======+=============+===============================================+
| toCompanyId | id   | string      | 위임 후보로 등록할 회사 ID (위임받는 회사 ID) |
+-------------+------+-------------+-----------------------------------------------+

-  Example Code

:underline:`Request`

.. code-block:: none

        content-type:"application/json"
	X-Authorization: "Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJzeXNhZG1pbkB0aG…"

	{
		"toCompanyId": {
			"id": "def51a30-c06e-11e7-8bdf-af923035d741"
		}
	}


:underline:`Response (code: 200)`

.. code-block:: json

	{
		"id": {
			"id": "50117bd0-c071-11e7-8bdf-af923035d741"
		},
		"createdTime": 1509697451337,
		"fromCompanyId": {
			"id": "c7fc12a0-beea-11e7-8bdf-af923035d741"
		},
		"toCompanyId": {
			"id": "def51a30-c06e-11e7-8bdf-af923035d741"
		},
		"serviceType": "example",
		"fromCompanyName": "운영사A",
		"toCompanyName": "협력사C"
	}

.. rst-class:: text-align-justify

위임 후보 회사로 등록되어 있는 회사에 특정 차량을 위임할 수 있습니다. 차량을 위임받은 회사는 위임 후보가 아닌 위임 회사가 됩니다.

위임 후보 회사에 차량 위임 API
''''''''''''''''''''''''''''''

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+------------+------------------------------------+
| **POST**   | `/api/tre/v1/director/{directorId}\|
|            | /relation/vehicle <https://app.swa\|
|            | ggerhub.com/apis/tremoteye/tremote\|
|            | yeapi/1.0.0#/Relation/post_api_tre\|
|            | _v1_cicle>`__                      |
+------------+------------------------------------+

-  Header

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-------------+--------+-------------------------+
| Key         | Type   | Description             |
+=============+========+=========================+
| toCompanyId | string | 차량을 위임받을 회사 ID |
+-------------+--------+-------------------------+

-  Path

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-----------------+--------+------------------+--------------+
| option          | Type   | Default          | Description  |
+=================+========+==================+==============+
| Content-Type    | string | application/json | content type |
+-----------------+--------+------------------+--------------+
| X-authorization | string |                  | auth token   |
+-----------------+--------+------------------+--------------+

-  Body

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+------------------+-------------+----------------+
| Key              | Type        | Description    |
+===========+======+=============+================+
| vehicleId | id   | string      | 위임할 차량 ID |
+-----------+------+-------------+----------------+

-  Example Code

:underline:`Request`

.. code-block:: none

        content-type:"application/json"
	X-Authorization: "Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJzeXNhZG1pbkB0aG…"

	{
		"vehicleId": {
			"id": "45f8a100-bef0-11e7-8bdf-af923035d741"
		}
	}


:underline:`Response (code: 200)`

.. code-block:: json

	{
		"id": {
			"id": "1a598a90-c072-11e7-8bdf-af923035d741"
		},
		"createdTime": 1509698195891,
		"fromCompanyId": {
			"id": "c7fc12a0-beea-11e7-8bdf-af923035d741"
		},
		"fromCompanyName": "운영사A",
		"toCompanyId": {
			"id": "def51a30-c06e-11e7-8bdf-af923035d741"
		},
		"toCompanyName": "협력사C",
		"vehicleId": {
			"id": "45f8a100-bef0-11e7-8bdf-af923035d741"
		},
		"vehicleNo": "00가0001"
	}

|br|
|br|

위임 디렉터 등록 (Delegated Director Registration)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Smart[Fleet] 포털을 통한 등록
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

1. 차량을 디렉터에게 할당하는 기능으로 운영사 및 협력사 Admin계정으로 로그인 후 차량메뉴에서 위임 가능합니다.

|br|

.. image:: ../images/procedure/8-1.png

|br|

.. rst-class:: text-align-justify

2. 차량 리스트 화면에서 차량 할당버튼을 눌러 할당 화면으로 이동합니다.

|br|

.. image:: ../images/procedure/8-2.png

|br|

.. rst-class:: text-align-justify

3. 차량 선택 후 추가버튼을 눌러 차량을 선택된 차량 영역으로 이동시킨 후 다음으로 이동합니다.

|br|

.. image:: ../images/procedure/8-3.png

|br|

.. rst-class:: text-align-justify

4. 할당할 디렉터를 검색 및 선택한 후 위임 버튼을 눌러 위임을 완료합니다.

|br|

.. image:: ../images/procedure/8-4.png

|br|

API를 활용한 등록
^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

Company_Admin, Director 권한 계정은 Director 에게 특정 차량의 권한을 위임할 수 있습니다. API를 통해 권한이 설정된 디렉터는 할당된 차량에 대해 Delegated_director 권한을 가집니다. Company_admin은 자신의 회사에 속한 차량 또는 위임 회사에 할당한 차량에 대해서만 본인이 속한 회사의 Director에게 권한을 설정 할 수 있습니다. Director는 본인이 관리하는 차량에 한해서 다른 Director 를 Delegated Director로 설정 할 수 있습니다. 단, Director 가 다른 회사 소속일 경우에는 위임 회사에 차량 위임 권한을 가진 Director일 경우에만 권한 위임이 가능합니다.

|br|

디렉터 정보 등록 API
''''''''''''''''''''

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+------------+-------------------------------------------+
| **POST**   | `/api/tre/v1/director/{directorId}\       |
|            | /relation/vehicle <https://app.swaggerhub\|
|            | .com/apis/tremoteye/tremoteyeapi/\        |
|            | 1.0.0#/Relation/post_api_tre_v1_d\        |
|            | irector__directorId__relation_vehicle>`__ |
+------------+-------------------------------------------+

-  Header

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-----------------+--------+------------------+--------------+
| option          | Type   | Default          | Description  |
+=================+========+==================+==============+
| Content-Type    | string | application/json | content type |
+-----------------+--------+------------------+--------------+
| X-authorization | string |                  | auth token   |
+-----------------+--------+------------------+--------------+

-  Path

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+------------+--------+---------------------------+
| Key        | Type   | Description               |
+============+========+===========================+
| directorId | string | 차량을 위임받을 디렉터 ID |
+------------+--------+---------------------------+

-  Body

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+------------------+-------------+----------------+
| Key              | Type        | Description    |
+===========+======+=============+================+
| vehicleId | id   | string      | 위임할 차량 ID |
+-----------+------+-------------+----------------+

-  Example Code

:underline:`Request`

.. code-block:: none

        content-type:"application/json"
	X-Authorization: "Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJzeXNhZG1pbkB0aG…"

	{
		"vehicleId": {
			"id": "45f8a100-bef0-11e7-8bdf-af923035d741"
		}
	}


:underline:`Response (code: 200)`

.. code-block:: json

	{
		"id": {
			"id": "74d18670-c073-11e7-8bdf-af923035d741"
		},
		"createdTime": 1509698777167,
		"companyId": {
			"id": "c7fc12a0-beea-11e7-8bdf-af923035d741"
		},
		"companyName": "운영사A",
		"userId": {
			"id": "8e904530-c06c-11e7-8bdf-af923035d741"
		},
		"userName": "디렉터C",
		"vehicleId": {
			"id": "45f8a100-bef0-11e7-8bdf-af923035d741"
		},
		"vehicleNo": "00가0001",
		"userRole": "DELEGATED_DIRECTOR"
	}

|br|
|br|

위임 운전자 등록 (Delegated Driver Registration)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Smart[Fleet] 포털을 통한 등록
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

1. 운영사 및 협력사 어드민, 디렉터 계정으로 로그인하여 차량 메뉴에서 등록 가능합니다.

|br|

.. image:: ../images/procedure/3-9-1.png

|br|

.. rst-class:: text-align-justify

2. 차량 정보를 눌러 상세페이지로 이동합니다.

|br|

.. image:: ../images/procedure/3-9-2.png

|br|

.. rst-class:: text-align-justify

3. 차량 상세 정보의 드라이버 영역에 드라이버 이름을 입력하면 자동으로 검색된 리스트가 표시되며 리스트에세 드라이버를 선택 후 수정버튼을 눌러 저장합니다.

|br|

.. image:: ../images/procedure/3-9-3.png

|br|

API를 활용한 등록
^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

Company_admin, director 권한 계정은 Driver 에게 특정 차량을 운행 할 수 있는 권한을 위임할 수 있습니다. API를 통해 권한이 설정된 Driver 는 해당 차량에 대해 delegated_driver 권한을 가집니다. Company_admin은 자신의 회사에 속한 차량 또는 위임회사에 할당된 차량에 대해서만 본인이 속한 회사의 driver에게 권한을 설정 할 수 있습니다.

Director는 본인이 관리하는 차량이거나 본인이 Delegated_director로 등록된 차량에 한해서 본인이 속한 회사의 driver에게 권한을 설정 할 수 있습니다.

Driver에게 이용 가능한 차량 등록 API
''''''''''''''''''''''''''''''''''''

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+------------+---------------------------------------+
| **POST**   | `/api/tre/v1/driver/{driverId}/rel\   |
|            | ation/vehicle <https://app.swaggerhub\|
|            | .com/apis/tremoteye/tremoteyeapi/\    |
|            | 1.0.0#/Relation/post_api_tre_v1_d\    |
|            | river__driverId__relation_vehicle>`__ |
+------------+---------------------------------------+

-  Header

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+-----------------+--------+------------------+--------------+
| option          | Type   | Default          | Description  |
+=================+========+==================+==============+
| Content-Type    | string | application/json | content type |
+-----------------+--------+------------------+--------------+
| X-authorization | string |                  | auth token   |
+-----------------+--------+------------------+--------------+

-  Path

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+----------+--------+-----------------------------+
| Key      | Type   | Description                 |
+==========+========+=============================+
| driverId | string | 차량을 위임받을 드라이버 ID |
+----------+--------+-----------------------------+

-  Body

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+------------------+-------------+----------------+
| Key              | Type        | Description    |
+===========+======+=============+================+
| vehicleId | id   | string      | 위임할 차량 ID |
+-----------+------+-------------+----------------+

-  Example Code

:underline:`Request`

.. code-block:: none

        content-type:"application/json"
	X-Authorization: "Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJzeXNhZG1pbkB0aG…"

	{
		"vehicleId": {
			"id": "45f8a100-bef0-11e7-8bdf-af923035d741"
		}
	}


:underline:`Response (code: 200)`

.. code-block:: json

	{
		"id": {
			"id": "9b631230-c074-11e7-8bdf-af923035d741"
		},
		"createdTime": 1509699271373,
		"companyId": {
			"id": "c7fc12a0-beea-11e7-8bdf-af923035d741"
		},
		"companyName": "운영사A",
		"userId": {
			"id": "69b5f470-c06d-11e7-8bdf-af923035d741"
		},
		"userName": "드라이버B",
		"vehicleId": {
			"id": "45f8a100-bef0-11e7-8bdf-af923035d741"
		},
		"vehicleNo": "00가0001",
		"userRole": "DRIVER"
	}

|br|
|br|

Device 연동 절차
-----------------

Device Connection
~~~~~~~~~~~~~~~~~

.. rst-class:: text-align-justify

Smart[Fleet] 플랫폼은 단말과 연동을 위해 MQTTS 프로토콜을 사용합니다. 단말이 MQTTS 프로토콜을 통해 Smart[Fleet] 플랫폼과 연동할 때 다음의 설정 값이 필요합니다.

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+-----------------------------------+-----------------------------------+
| 구분                              | Value                             |
+===================================+===================================+
| URL                               | `smartfleet.sktelecom.com <http:/ |
|                                   | /smartfleet.sktelecom.com>`__     |
+-----------------------------------+-----------------------------------+
| Port                              | 8883                              |
+-----------------------------------+-----------------------------------+
| username                          | 할당 받은 Access Token (20자리)   |
|                                   | 값                                |
+-----------------------------------+-----------------------------------+
| password                          | N/A                               |
+-----------------------------------+-----------------------------------+
| cleanSession                      | True                              |
+-----------------------------------+-----------------------------------+
| version                           | 3.1.1                             |
+-----------------------------------+-----------------------------------+

.. rst-class:: text-align-justify

Username 필드에는 해당 단말의 Credentials ID 값을 입력합니다. 단말의 Credentials ID 값은 `Smart[Fleet] REST API <https://app.swaggerhub.com/apis/tremoteye/tremoteyeapi/1.0.0#/Sensor/get_api_tre_v1_sensor>`__ 를 통해서 얻을 수 있습니다. cleanSession 필드가 true면 이전 세션 정보가 아직 존재할 경우 클라이언트와 서버에서 이전 세션 정보를 삭제합니다. MQTT 버전은 3.1.1을 사용합니다.

:underline:`Example Code`

.. code-block:: javascript

	const mqtt = require('mqtt');

	const client = mqtt.connect('mqtts://smartfleet.sktelecom.com:8883',{
		username : "",
		clean : true,
		rejectUnauthorized : false
	});

|br|
|br|

Device RPC
~~~~~~~~~~

.. rst-class:: text-align-justify

RPC는 Remote Procedure Call의 약자로 원격에 있는 함수를 호출해주는 기능을 말합니다. Device RPC는 어플리케이션에서 원격으로 센서의 기능을 호출함으로써 제어합니다. 어플리케이션에서 요청된 단말 제어 절차는 아래와 같습니다.

|br|

.. image:: ../images/procedure/4-2.png

|br|

Pre-Step
^^^^^^^^

.. rst-class:: text-align-justify

`3.4.1. Device Connection <#device-connection>`__ 절차를 거칩니다. 단말이 정상적으로 연결되면 세션이 생성됩니다. 세션이 생성된 후 RPC 요청을 수신하기 위해 토픽을 구독합니다. MQTTS에서 토픽을 구독하면 필터에 일치하는 토픽에 대한 발행물이 클라이언트로 송신됩니다. 여기서 필터에 일치하는 발행물은 해당 단말에 대한 RPC 요청이 됩니다.
|br|
RPC 요청을 수신하는 토픽은 아래와 같습니다.

.. rst-class:: table-width-fix

+-----------+-----------------------------+
| **Topic** | v1/sensors/me/rpc/request/+ |
+-----------+-----------------------------+

:underline:`Example Code`

.. code-block:: javascript

	client.subscribe("v1/sensors/me/rpc/request/+");

.. rst-class:: text-align-justify

Device RPC 절차 이전에 `3.4.3. Device Activation <#_Device_Activation>`__ 절차를 거칩니다. 서비스 등록 단계에서 RPC 결과 및 단말 Attribute 변경 정보를 수신하기 위한 HTTP Server 주소를 기입 받습니다.

Procedure
^^^^^^^^^

.. rst-class:: text-align-justify

1. 고객사의 Application에서 단말 제어 요청이 발생합니다.

.. rst-class:: text-align-justify

2. 고객사의 Application이 HTTPS POST 메시지를 통해서 RPC 요청을 수행합니다. 요청 메시지 포맷은 `6.2. RPC 메시지 포맷 <rpc-message-format>`__ 을 참고합니다. |br| RPC 요청 API는 아래와 같습니다.

.. rst-class:: table-width-fix

+------------+----------------------------------------------+
| **POST**   | `/api/plugins/rpc/twoway/{sensorId\          |
|            | } <https://app.swaggerhub.com/apis/\         |
|            | tremoteye/tremoteyeapi/1.0.0#/Sensor/\       |
|            | post_api_plugins_rpc_twoway__sensorId_>`__   |
+------------+----------------------------------------------+

.. rst-class:: text-align-justify

3. 플랫폼은 2번과정에서 수신한 RPC 요청 메세지를 단말에 포워딩 합니다. 이 때, 플랫폼은 RPC에 대한 요청 식별자 Request-ID를 Topic의 하나로 제공합니다.

.. rst-class:: text-align-justify

+-----------+----------------------------------------+
| **Topic** | v1/sensors/me/rpc/request/{Request-ID} |
+-----------+----------------------------------------+

.. rst-class:: text-align-justify

4. 단말은 RPC 요청을 수신했다는 Ack를 플랫폼에 Return합니다. 단 해당 수신에 대한 Ack 메시지가 20초 내로 전송되지 않으면 Timeout 된 후 에러로 처리됩니다. |br| RPC Ack를 발송하는 토픽은 아래와 같습니다.

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+-----------------+-----------------------------------------------------+
| **Topic**       | v1/sensors/me/rpc/response/{Request-ID}             |
+-----------------+-----------------+-----------------------------------+
| **메시지 포맷** | :ref:`Response <vendor-specific-msg-response>` 참조 |
+-----------------+-----------------+-----------------------------------+

.. rst-class:: text-align-justify

5. 플랫폼은 RPC 요청 수신 결과 메세지를 포워딩하여 Application에 상기 4번의 Response 형태로 응답합니다.

.. rst-class:: text-align-justify

6. 단말은 RPC 결과를 플랫폼에 전달합니다. RPC 결과를 발송하는 토픽은 아래와 같습니다.

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+-----------------+-----------------------------------------------------+
| **Topic**       | v1/sensors/me/rpc/result/{Request-ID}               |
+-----------------+-----------------+-----------------------------------+
| **메시지 포맷** | :ref:`Result <vendor-specific-msg-result>` 참조     |
+-----------------+-----------------+-----------------------------------+

.. rst-class:: text-align-justify

7. 플랫폼은 상기 6번 과정의 Attribute가 Update 된 경우에 해당 결과를 그대로 고객사의 application에 푸시 형태로 제공합니다. 이 때 주소는 Prestep에서 정의한 HTTP Server 주소를 활용합니다.

|br|
|br|

Device Activation
~~~~~~~~~~~~~~~~~

.. rst-class:: text-align-justify

일부 OBD 단말은 정보를 올리기 위해서는 차량과 매핑을 통해 가져올 수 있는 센서 데이터들을 설정해야 합니다. 차량의 모델, 배기량, 연료 타입 등에 따라 측정 가능한 센서 데이터의 개수와 종류가 달라질 수 있기 때문입니다.
OBD가 측정 할 수 있는 센서 데이터의 종류가 100가지 있다고 가정하면 차량 A는 50가지, 차량 B는 40가지 이렇게 차량마다 측정 데이터가 다를 수 있습니다.
이를 위해 차량에 맞는 데이터만 가져오도록 설정하는 작업이 단말 활성화 절차(Device Activation)입니다.
|br|
Device Activation은 활성화가 필요한 절차, 필요하지 않은 절차로 나뉘어집니다.

|br|

Activation이 필요한 단말의 등록 절차
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

센서 동작 전 센서의 활성화(Activation)가 요구되는 단말에 적용되는 등록 절차를 기술합니다.

|br|

.. image:: ../images/procedure/4-3-1.png

|br|

Prestep
'''''''

.. rst-class:: text-align-justify

사전에 각 단말은 SKT에서 제공한 Access Token (Sensor API의 credentialsId 필드)을 보유하고 있어야 하며, Application (고객사)에서도 동일한 Access Token을 보유하고 있어야 합니다.

Procedure
'''''''''

.. rst-class:: text-align-justify

1. Application Owner가 포털이나 HTTPS API를 통하여 플랫폼에 단말의 정보를 등록합니다. 센서 등록 설명은 `3.2.4. 센서 등록 <#센서-등록-sensor-registration>`__ 절차를 참고합니다.

.. rst-class:: text-align-justify

2. 플랫폼은 1번 과정에서 요청받은 정보를 기반으로 단말을 등록합니다. 상기 등록 과정에서 오류가 발생한 경우에는 수신 받은 인터페이스에 따라 회신합니다.

.. rst-class:: text-align-justifys

3. 단말을 플랫폼에 연결을 시도합니다. 세부 절차는 `3.4.1. Device Connection <#device-connection>`__ 절차를 참고합니다.

.. rst-class:: text-align-justify

4. 단말이 연결되면 세션이 생성됩니다. 세션이 생성된 후 RPC 요청을 수신하기 위해 토픽을 구독합니다. MQTTS에서 토픽을 구독하면 필터에 일치하는 토픽에 대한 발행물이 클라이언트로 송신됩니다. 여기서 필터에 일치하는 발행물은 해당 단말에 대한 RPC 요청이 됩니다. |br| RPC 요청을 수신하는 토픽은 아래와 같습니다.

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+-----------+-----------------------------+
| **Topic** | v1/sensors/me/rpc/request/+ |
+-----------+-----------------------------+

:underline:`Example Code`

.. code-block:: javascript

	client.subscribe("v1/sensors/me/rpc/request/+");

.. rst-class:: text-align-justify

5. 차량과 등록된 센서 간 매핑을 요청합니다. 매핑 API는 아래와 같습니다.

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+------------+------------------------------------------+
| **POST**   | `/api/tre/v1/sensor/{sensorId}/veh\      |
|            | icle/{vehicleId} <https://app.swaggerhub\|
|            | .com/apis/tremoteye/tremoteyeapi/\       |
|            | 1.0.0#/Sensor/post_api_tre_v1_sen\       |
|            | sor__sensorId__vehicle__vehicleId_>`__   |
+------------+------------------------------------------+

.. rst-class:: text-align-justify

6. 플랫폼에서 요청 받은 단말이 Activation이 필요한지 여부를 판단합니다. 단말의 Activation 필요 여부는 플랫폼에 단말을 등록할 때 입력한 activationRequired 필드 값에 따라 구분합니다. activationRequired 값이 true이면 Activation이 필요하다고 간주합니다.

.. rst-class:: text-align-justify

7. 상기 6번 과정에서 단말이 Activation이 필요하다고 명시된 경우 플랫폼은 해당 단말에 Activation 정보를 내려주기 위한 RPC를 제공합니다. |br| 메시지 포맷은 :ref:`6.2.2. Device Activation의 Request <device-activation-request>` 항목을 참고합니다.

.. rst-class:: text-align-justify

8. 단말이 7번 단계의 Activation 요청을 수신합니다.

.. rst-class:: text-align-justify

9. 단말은 이에 따라 Activation 수행 예정이라는 메세지를 플랫폼에 전달합니다. |br| 메시지 포맷은 :ref:`6.2.2. Device Activation의 Response <device-activation-response>` 항목을 참고합니다. |br| 해당 메세지를 발송하는 토픽은 아래와 같습니다.

.. rst-class:: text-align-justify

+-------------------+-----------------------------------+
| **Topic**         | v1/sensors/me/rpc/response/{Reque\|
|                   | st-ID}                            |
+-------------------+-----------------------------------+
| **메시지 포맷**   | `Response  <device-activation-res |
|                   | ponse>`__                         |
+-------------------+-----------------------------------+

.. rst-class:: text-align-justify

10. 플랫폼이 고객사(포털 또는 HTTP Response)에게 9번 과정의 단말 RPC 메시지 수신 상태를 전달합니다. 이는 매핑과 Activation은 추후에 진행되는 것을 명시합니다.

.. rst-class:: text-align-justify

11. 단말이 Activation을 수행한 후에 Activation 결과를 단말이 플랫폼에 전달합니다. Activation 작업은 일반적으로 일정 시간이 걸릴 수 있습니다. |br| Activation 결과를 발송하는 토픽은 아래와 같습니다.

.. rst-class:: text-align-justify

+-------------------+-----------------------------------+
| **Topic**         | v1/sensors/me/rpc/result/{Request\|
|                   | -ID}                              |
+-------------------+-----------------------------------+
| **메시지 포맷**   | `Result <device-activation-resul  |
|                   | t>`__                             |
+-------------------+-----------------------------------+

.. rst-class:: text-align-justify

12. 플랫폼은 수신한 Activation 결과를 저장하고 정상적으로 Activation이 된 경우 단말과 차량을 매핑합니다.

.. rst-class:: text-align-justify

13. 플랫폼은 12번의 결과를 고객사에 전달합니다.

|br|

Activation이 필요하지 않는 단말의 등록 절차
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

단말 동작 전 단말의 활성화(Activation)가 요구되지 않는 단말에 적용되는 등록 절차를 기술합니다.

|br|

.. image:: ../images/procedure/4-3-2.png

|br|

Prestep
'''''''

.. rst-class:: text-align-justify

사전에 각 단말은 SKT에서 제공한 Access Token (Sensor API의 credentialsId 필드)을 보유하고 있어야 하며, Application (고객사)에서도 동일한 Access Token을 보유하고 있어야 합니다.

Procedure
'''''''''

.. rst-class:: text-align-justify

1. Application Owner가 포털이나 HTTPS API를 통하여 플랫폼에 단말의 정보를 등록합니다. 센서 등록 설명은 `3.3.4. 센서 등록 <#sensor-registration>`__ 절차을 참고합니다.

.. rst-class:: text-align-justify

2. 플랫폼은 1번 과정에서 요청받은 정보를 기반으로 단말을 등록합니다. 상기 등록 과정에서 오류가 발생한 경우에는 수신 받은 인터페이스에 따라 회신합니다.

.. rst-class:: text-align-justify

3. 단말과 플랫폼간 연결을 시도합니다. 세부 절차는 `3.4.1. Device Connection <#device-connection>`__ 내용을 참고합니다.

.. rst-class:: text-align-justify

4. 단말이 연결되면 세션이 생성됩니다. 세션이 생성된 후 RPC 요청을 수신하기 위해 토픽을 구독합니다. MQTTS에서 토픽을 구독하면 필터에 일치하는 토픽에 대한 발행물이 클라이언트로 송신됩니다. 여기서 필터에 일치하는 발행물은 해당 단말에 대한 RPC 요청이 됩니다. |br| RPC 요청을 수신하는 토픽은 아래와 같습니다.

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+-----------+-----------------------------+
| **Topic** | v1/sensors/me/rpc/request/+ |
+-----------+-----------------------------+

:underline:`Example Code`

.. code-block:: javascript

	client.subscribe("v1/sensors/me/rpc/request/+");

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

5. 차량과 등록된 센서 간 매핑을 요청합니다. 매핑 API는 아래와 같습니다.

+------------+------------------------------------------+
| **POST**   | `/api/tre/v1/sensor/{sensorId}/vehicle/{\|
|            | vehicleId} <https://app.swaggerhub.com/a\|
|            | pis/tremoteye/tremoteyeapi/1.0.0#/Sensor\|
|            | /post_api_tre_v1_sensor__sensorId__vehic\|
|            | le__vehicleId_>`__                       |
+------------+------------------------------------------+

.. rst-class:: text-align-justify

6. 플랫폼에서 요청 받은 단말이 Activation이 필요한지 여부를 판단합니다. 단말의 Activation 필요 여부는 플랫폼에 단말을 등록할 때 입력한 activationRequired 필드 값에 따라 구분합니다. activationRequired 값이 false이면 Activation이 필요없다고 간주합니다.

.. rst-class:: text-align-justify

7. Activation이 필요없다고 판단되면 5번 과정의 매핑 요청에 따라 센서 엔티티에 센서가 연결된 차량의 식별자를 기입하여 논리적인 링크를 구성합니다.

.. rst-class:: text-align-justify

8. 플랫폼이 고객사(포털 또는 HTTPS Response)에게 센서와 차량 매핑 결과를 전달합니다.

|br|
|br|

OBD Device Procedure
~~~~~~~~~~~~~~~~~~~~

.. rst-class:: text-align-justify

단말 활성화 작업까지 마쳤다면 실제로 운행 데이터를 송수신할 차례입니다.
|br|
OBD 단말이 데이터를 전송하는 프로시저를 명세합니다.

|br|

OBD Trip Data
^^^^^^^^^^^^^

.. rst-class:: text-align-justify

OBD 센서에서 발생한 운행 기록을 위한 정보를 업로드 하는 절차를 기술합니다.

|br|

.. image:: ../images/procedure/4-4-1.png

|br|

Prestep
'''''''

.. rst-class:: text-align-justify

본 가이드 문서 중 `3.3.4. Device Activation <#device-activation>`__ 절차를 정상적으로 수행합니다.

Procedure
'''''''''

.. rst-class:: text-align-justify

1. 단말은 차량의 운행이 시작되는 순간부터 등록 시점에 명세한 주기에 따라 Microtrip 데이터를 플랫폼에 전달합니다. |br| 플랫폼에 Microtrip 전달하는 토픽은 아래와 같습니다. QoS 값은 ‘1’로 설정합니다.

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+-------------------+------------------------------------------+
| **Topic**         | v1/sensors/me/tre                        |
+-------------------+------------------------------------------+
| **메시지 포맷**   | `Microtrip <microtrip-message-format>`__ |
+-------------------+------------------------------------------+

.. rst-class:: text-align-justify

2. 단말은 차량 운행이 종료된 후 운행 종료를 알리는 Trip 데이터를 플랫폼에 전달합니다. |br| 플랫폼에 Trip 전달하는 토픽은 아래와 같습니다. QoS 값은 1로 설정합니다.

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+-----------------+--------------------------------------+
| **Topic**       | v1/sensors/me/tre                    |
+-----------------+--------------------------------------+
| **메시지 포맷** | `Trip <trip-messgae-format>`__       |
+-----------------+--------------------------------------+

|br|
|br|

OBD Event Data
^^^^^^^^^^^^^^

.. rst-class:: text-align-justify

OBD 센서에서 발생한 운행 이벤트 정보를 업로드 하는 절차를 기술합니다.

|br|

.. image:: ../images/procedure/4-4-2.png

|br|

Prestep
'''''''

.. rst-class:: text-align-justify

본 가이드 문서 중 `3.4.3. Device Activation <#device-activation>`__ 절차를 정상적으로 수행합니다.

Procedure
'''''''''

.. rst-class:: text-align-justify

1. 차량에서 플랫폼에 전달할 이벤트가 발생합니다.

.. rst-class:: text-align-justify

2. 1번 과정에서 발생한 이벤트를 아래 규격에 맞추어 플랫폼에 전달합니다. 이벤트는 Time Series와 Attributes 두 종류로 나눠지며 서로 다른 토픽을 사용합니다. |br| 플랫폼에 이벤트 전달하는 토픽은 아래와 같습니다. QoS 값은 1로 설정합니다.

.. rst-class:: table-width-fix
.. rst-class:: text-align-justify

+-----------+-----------------------------+--------------------------+
| **Topic** | *Time Series 이벤트인 경우* | v1/sensors/me/telemetry  |
|           +-----------------------------+--------------------------+
|           | *Attributes 이벤트인 경우*  | v1/sensors/me/attributes |
+-----------+-----------------------------+--------------------------+

.. rst-class:: text-align-justify

전달 가능한 이벤트는 아래와 같습니다. 메세지 포맷은 `6.1.1 Payload Types <payload-types>`__ 를 참조합니다.

-  Diagnostic Information (Time Series)
-  Collision warning (Driving) (Time Series)
-  Collision warning (Paramsking) (Time Series)
-  Battery Warning (Attributes)
-  Unplugged Warning (Attributes)
-  Turn-off Warning (Attributes)

|br|
|br|
