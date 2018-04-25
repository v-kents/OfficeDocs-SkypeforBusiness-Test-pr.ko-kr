﻿---
title: Lync Server 2013에서 영구 채팅 서버의 작동 방법
TOCTitle: Lync Server 2013에서 영구 채팅 서버의 작동 방법
ms:assetid: 3d04e9a1-3f0c-458e-bcbe-d27c8c464276
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ683096(v=OCS.15)
ms:contentKeyID: 49885731
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 영구 채팅 서버의 작동 방법

 

_**마지막으로 수정된 항목:** 2012-11-21_

Lync Server 2013, 영구 채팅 서버를 사용하면 특정 주제에 관한 지속적인 단체 대화에 참가할 수 있습니다. 영구 채팅 서버는 조직이 다음을 수행하는 데 도움이 될 수 있습니다.

  - 지리적으로 분산되고 업무가 연관된 팀 간의 통신을 향상시킵니다.

  - 보다 많은 구성원과 정보를 보다 많이 공유할 수 있습니다.

  - 조직 내외부에서 광범위하게 정보를 공유할 수 있습니다.

  - 효율적인 정보 공유로 정보 오버로드를 줄여 줍니다.

  - 정보 인식을 향상시킵니다.

  - 중요한 지식과 정보의 배포를 향상시킵니다.

영구 채팅 서버는 Lync Server 2013에서 선택적인 역할로 배포할 수 있습니다. 영구 채팅는 전용 풀에서 실행되며 영구 채팅 서버 풀은 Lync Server 풀을 사용하여 메시지를 서버로 라우팅합니다. 클라이언트는 XCCOS(eXtensible Chat Communication Over SIP)를 사용합니다. Lync Server프런트 엔드 서버는 트래픽을 영구 채팅 서버 풀로 라우팅하도록 구성됩니다.

## 고급 아키텍처

다음 다이어그램에서는 영구 채팅 서버 아키텍처 및 서비스에 대한 개요를 제공합니다.

**영구 채팅 서버 고급 아키텍처**

![영구 채팅 서버 아키텍처.](images/JJ683096.5db6f36f-4461-4d87-ba77-463b7ffe609b(OCS.15).jpg "영구 채팅 서버 아키텍처.")

**영구 채팅 서버 고급 서비스**

![영구 채팅 서버 구성 요소.](images/JJ683096.b6d743aa-3a86-4081-aaef-4fe3257db4e7(OCS.15).jpg "영구 채팅 서버 구성 요소.")

영구 채팅 서버프런트 엔드 서버에서 실행되는 두 서비스는 다음과 같습니다.

  - 영구 채팅(채널)

  - 준수

## 영구 채팅(채널) 서비스

영구 채팅(채널) 서비스는 영구 채팅 서버의 핵심 서비스입니다. 이 서비스는 다음과 같은 기능을 제공합니다.

  - 수신 메시지를 허용합니다.

  - 영구 채팅방 내의 온라인 참가자를 등록하고 나열합니다.

  - 다른 채널 구독자에게 메시지를 재전송합니다.

  - 채널 관리, 채팅방 초대, 검색 및 새 콘텐츠 알림을 위한 논리를 구현합니다.

영구 채팅(채널) 서비스는 영구 채팅 저장소를 사용하여 채팅방 콘텐츠 및 기타 시스템 메타데이터(권한 부여 규칙 등)에 액세스합니다. 이 서비스는 채팅방에 업로드되는 파일을 영구 채팅 파일 저장소에 저장합니다.

## 준수 서비스

준수 서비스는 영구 채팅 서버의 선택적인 구성 요소이며 채팅 콘텐츠 및 이벤트를 영구 채팅 준수 저장소에 보관합니다. 조직에 영구 채팅 활동을 보관해야 하는 규정이 있는 경우 선택적인 영구 채팅 준수 서비스를 배포할 수 있습니다. 준수 서비스는 영구 채팅 풀의 각 영구 채팅 서버에 설치됩니다. 영구 채팅 서버 준수 서비스를 구성하면 채팅방 참가 및 나가기, 메시지 게시 및 읽기와 같은 사용자 활동이 기록됩니다. 준수 서비스는 보관해야 하는 파일을 영구 채팅 준수 파일 저장소에 저장합니다.

## 영구 채팅 웹 서비스

Lync Server프런트 엔드 서버에서는 IIS(인터넷 정보 서비스)를 사용하는 다음과 같은 두 가지 서비스가 실행되고 웹 구성 요소로 구현됩니다.

  - **파일 업로드/다운로드를 위한 영구 채팅 웹 서비스** 채팅방에서 파일을 게시 및 검색합니다.

  - **채팅방 관리를 위한 영구 채팅 웹 서비스** 채팅방을 관리하고 새 채팅방을 만들 수 있는 기능을 사용자에게 제공합니다.

## 영구 채팅 서버는 어떻게 사용합니까?

영구 채팅 서버는 Lync Server 2013 인프라 내의 선택적인 서버 역할입니다. 영구 채팅 서버 역할을 설치할 경우 정책을 통해 관리자가 설정한 모든 사용자가 Lync 2013 클라이언트에서 영구 채팅을 사용할 수 있습니다. 영구 채팅 서버를 배포하고 사용자가 정책에 따라 기능을 사용하도록 설정하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 영구 채팅 서버 배포](lync-server-2013-deploying-persistent-chat-server.md)를 참조하십시오.

영구 채팅 서버 배포에서 설정을 구성하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 영구 채팅 서버 배포](lync-server-2013-deploying-persistent-chat-server.md) 및 [Lync Server 2013, 영구 채팅 서버 관리](managing-lync-server-2013-persistent-chat-server.md)를 참조하십시오.

Lync 2013 클라이언트에서 영구 채팅 기능을 사용할 수 있도록 정책으로 사용자를 설정하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 영구 채팅 서버 배포](lync-server-2013-deploying-persistent-chat-server.md) 및 [Lync Server 2013, 영구 채팅 서버 관리](managing-lync-server-2013-persistent-chat-server.md)를 참조하십시오.

영구 채팅 준수를 배포한 경우 [Lync Server 2013, 영구 채팅 서버 관리](managing-lync-server-2013-persistent-chat-server.md)에서 준수용 설정을 구성하는 방법에 대한 자세한 내용을 확인하십시오.

## 영구 채팅 통화 흐름

Lync 클라이언트는 XCCOS를 사용하여 영구 채팅 서비스와 통신합니다. 다음 시퀀스에서는 로그인 프로세스와 일반적인 방 구독 및 메시지 게시 시나리오에 대해 설명합니다.

## 로그인

다음 시퀀스에서는 로그인 프로세스에 대해 설명합니다.

1.  Lync 클라이언트가 먼저 SIP SUBSCRIBE를 전송하여 서버에서 인밴드 프로비전 문서를 검색합니다. 이 문서에는 사용자에 대해 영구 채팅이 설정 또는 해제되었는지 여부와 영구 채팅 서버 풀에 대한 SIP URI 목록이 표시됩니다.

2.  Lync 클라이언트는 SIP INVITE 메시지를 이전 단계에서 얻은 영구 채팅 서버의 SIP URI에 전송합니다. INVITE 시퀀스 뒤에 200 OK 및 ACK가 표시되고 Lync 클라이언트가 이제 영구 채팅 서버 끝점으로 SIP 세션을 열었습니다. 따라서 클라이언트가 채팅 메시지 또는 서버가 특정 작업을 수행하도록 요청하는 명령이 포함된 SIP INFO 메시지를 전송하여 영구 채팅 서버와 통신할 수 있습니다. 이러한 모든 메시지는 200 OK 또는 503 Service Unavailable(즉, 서버 부하가 심한 경우) 메시지로 응답됩니다. 클라이언트에 503 응답이 수신되면 메시지를 재시도합니다. 이 예에는 503 응답이 포함되지 않았습니다. 서버가 메시지 또는 명령을 수신하고 200 OK를 전송하는 경우 개별 SIP INFO 메시지의 형태로 클라이언트에 응답을 제공합니다. 이 응답에는 원래 명령에 대한 참조가 포함됩니다.

3.  Lync 클라이언트가 XCCOS **getserverinfo** 명령이 포함된 SIP INFO 메시지를 전송합니다. 영구 채팅 서버는 영구 채팅 서비스 구성에 대한 정보가 포함된 새 SIP INFO 메시지로 회신합니다.

4.  Lync 클라이언트가 XCCOS **getassociations** 명령이 포함된 SIP INFO 메시지를 전송합니다. 영구 채팅 서버는 해당 사용자가 구성원인 방 목록이 포함된 새 SIP INFO 메시지로 회신합니다. Lync 클라이언트는 이 명령을 반복해서 해당 사용자가 관리자인 방 목록을 검색합니다.

5.  Lync 클라이언트는 "현재 상태" 문서에서 후속 방 목록을 가져옵니다. 각 후속 방이 "roomSetting" 범주로 표시됩니다. 모든 후속 방은 방 URI의 목록이 포함된 XCCOS **bjoin** 명령을 포함하는 단일 SIP INFO 메시지로 참가할 수 있습니다. 후속 방 목록이 서버에 저장되기 때문에 어떤 컴퓨터의 어떤 클라이언트에서도 지정된 사용자 URI에 대한 후속 방 목록이 동일하게 표시됩니다. Lync 클라이언트는 또한 열린 방 목록을 로컬 컴퓨터 레지스트리에 보관하고(사용자가 이 옵션을 설정한 경우) 각각의 열린 방에 대해 XCCOS **join** 명령을 포함하는 SIP INFO 메시지를 전송하여 로그인 시 이러한 방에 참가합니다. 이 목록은 레지스트리에 보관되기 때문에 서로 다른 컴퓨터에서 실행되는 두 개의 Lync 클라이언트에서 서로 다를 수 있습니다.

6.  참가한 각 방에서 Lync 클라이언트는 XCCOS **bccontext** 명령이 포함된 SIP INFO 메시지를 전송합니다. 영구 채팅 서버는 해당 방의 최신 채팅 메시지가 포함된 새로운 SIP INFO 메시지로 회신합니다.

7.  Lync 클라이언트가 XCCOS **getinv** (that is, get invitation) 명령이 포함된 SIP INFO 메시지를 전송하여 클라이언트에 아직 표시되지 않은 새로운 방 초대를 요청합니다. 영구 채팅 서버는 이러한 방 목록을 개별 SIP INFO 메시지로 반환합니다.

## 방 구독 및 메시지 게시

다음 시퀀스에서는 일반적인 방 구독 및 메시지 게시 시나리오에 대해 설명합니다.

1.  Lync 클라이언트에서 User1이 **채팅방 참가**를 클릭하고, **검색**을 클릭한 후 몇 가지 검색 조건을 입력합니다. 클라이언트는 이 검색 조건과 함께 XCCOS **chansrch**(방 검색) 명령이 포함된 SIP INFO 메시지를 전송합니다. 영구 채팅 서버는 백 엔드 데이터베이스를 쿼리하고 검색 조건에 맞는 사용 가능한 방 목록이 포함된 새로운 SIP INFO 메시지로 회신합니다.

2.  User1이 참가하려는 채팅방을 선택한 후 **이 방 팔로우**를 클릭합니다. 클라이언트는 XCCOS **join** 명령과 사용자가 선택한 방 ID가 포함된 SIP INFO 메시지를 영구 채팅 서버에 전송합니다. 영구 채팅 서버는 프로비전 데이터가 포함된 SIP INFO 메시지로 회신합니다.

3.  Lync 클라이언트가 XCCOS **bccontext**(백채트 컨텍스트) 명령이 포함된 SIP INFO 메시지를 영구 채팅 서버에 전송합니다. 영구 채팅 서버는 채팅 기록을 검색하고 이를 별도의 SIP INFO 메시지로 클라이언트에 반환합니다. 이때 사용자가 방에 들어가고 참가할 준비가 됩니다.

4.  User1이 새 메시지를 입력한 후 **보내기**를 클릭합니다. Lync 클라이언트는 SIP INFO XCCOS **grpchat** 명령으로 메시지를 채팅방에 게시합니다. 영구 채팅 서버는 이 새 메시지의 복사본을 영구 채팅 백 엔드 데이터베이스에 저장합니다.

5.  영구 채팅 서버가 SIP INFO XCCOS **grpchat** 메시지의 또 다른 복사본을 이미 채팅방에 들어와 있던 User2에게 보냅니다.

## 영구 채팅 준수 통화 흐름

영구 채팅 서버는 메시지 큐(또는 MSMQ) 및 추가 준수 데이터베이스(mgccomp)를 사용하여 준수 데이터를 처리합니다. 준수 이벤트를 처리하는 방법에 대한 예로 다음 이벤트 시퀀스에서는 메시지 게시 이벤트가 처리되는 방법에 대해 설명합니다.

1.  사용자가 메시지를 방에 게시합니다.

2.  영구 채팅 서버가 이 이벤트와 관련된 정보를 개인 메시지 큐에 넣습니다.

3.  영구 채팅 준수 서버가 큐에서 이 이벤트를 읽고 이를 나중에 처리할 수 있도록 mgccomp 데이터베이스에 넣습니다.

4.  주기적으로 영구 채팅 준수 서버가 데이터베이스에 있는 일련의 이벤트를 처리하고 이를 처리할 수 있도록 영구 채팅 준수 어댑터로 전송합니다.

5.  어댑터가 데이터를 처리했으면 영구 채팅 준수 서버가 mgccomp 데이터베이스에서 해당 이벤트를 삭제합니다.
