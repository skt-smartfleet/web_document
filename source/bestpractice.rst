.. |br| raw:: html

   <br />

Best Practices
=======================================

Smart[Fleet] 플랫폼을 기반으로 Connected Car 솔루션 개발 시 필요한 주요한 Tip을 제공합니다.

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
 
상기 과정을 정상적으로 수행하면 Smart[Fleet] 플랫폼의 선택된 메시지들을 정의된 HTTP 서버에 전송합니다.


Push 메시지 수신을 위한 서버 기동
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Smart[Fleet]에서 제공하는 Push 메시지는 HTTP 프로토콜을 준수하며, 
메시지를 수신하기 위해서는 HTTP 서버 운용하여야 합니다.

간단한 테스트를 위해 node.js 기반의 HTTP 서버를 AWS 인스턴스에 기동하여 정상적으로 메시지를 수신하는 테스트를 진행합니다.

아래는 node.js의 express 모듈을 통해 구현된 HTTP POST 요청을 수신하고 응답하는 코드입니다. node.js 및 express 모듈에 대한 설명은 생략 합니다.

.. code-block:: javascript
    
    var http = require('http');

    http.createServer(function (req, res) {
    var jsonData = "";
    req.on('data', function (chunk) {
        jsonData += chunk;
    });
    req.on('end', function () {
        console.log(jsonData);
        res.writeHead(200);
    });
    }).listen(8888);


상기 코드를 AWS 인스턴스에 구동시키고 Smart[Fleet] 프로토콜을 준수하는 단말이 메시지를 플랫폼에 전달하면, 다음과 같이 Push 메시지가 전달 되는 것을 볼 수 있습니다.

.. image:: ../images/push_log.png
