.. |br| raw:: html

   <br />

Best Practices
=======================================

Smart[Fleet] 플랫폼을 기반으로 Connected Car 솔루션 개발 시 필요한 주요한 Tip을 제공합니다.

|br|

Web Push
-----------------------

Smart[Fleet] 플랫폼은 차량 디바이스로 부터 전달 받은 데이터 및 제어 정보를 실시간으로 Push 받을 수 있습니다.
Push 메시지를 수신하기 위해서는 아래 2가지 준비가 필요합니다.

1. Push 메시지를 수신하기 위한 서버 정보 멏 수신하고자 하는 메시지 타입 정의
2. Push 메시지 수신을 위한 서버 기동


Push 메시지 타입 및 수신 서버 주소 정의
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

수신받고자 하는 Push 메시지 타입이나 수신 서버는 Smart[Fleet] 내 서비스 정보를 
저장하는 ``Company`` 엔티티에 명시합니다. 
`Company Entity <http://smart-fleet-docs.readthedocs.io/ko/latest/entity/#company-registration-api>`__ 
API를 통해 아래 2가지 Key 정보를 상황에 맞추어 수정하면 됩니다.

+----------------+---------------------------------------+
| key            | Description                           |
+----------------+---------------------------------------+
| notifyHost     | Push 메시지 수신 서버 경로 정보       |
+----------------+---------------------------------------+
| notifyMsgType  | 수신하고자 하는 Push 메시지 타입 정보 |
|                | |br| ty 번호를 Comma로 구분하여 명세  |
|                | |br| - ** 특수 ty **                  |
|                | |br| 300 : All RPC Messages           |
|                | |br| 400 : All Rule Alarm Messages    |
+----------------+---------------------------------------+

예를 들어, HTTP 서버 주소가 http://192.168.0.100:9090/noti 이고 
수신하고자 하는 메시지의 ty 값이 7, 8, 101, 102 이고, 
추가로 RPC 제어 결과를 Push 받고자 하면 PUT Method를 통해 기존에 저장된 Company Entity를 수정한다.

.. code-block:: json

    {
        "notifyHost":"http://192.168.0.100:9090/noti",
        "notifyMsgType": "7, 8, 101, 102, 300"
    }
 
