﻿---
title: 'Lync Server 2013: E9-1-1 개요'
TOCTitle: E9-1-1 개요
ms:assetid: c01e6774-bc9f-4c5b-a60b-478b7317b2b7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412936(v=OCS.15)
ms:contentKeyID: 49304907
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 E9-1-1 개요

 

_**마지막으로 수정된 항목:** 2012-10-29_

Microsoft Lync Server 2013에서는 Lync 클라이언트 및 Lync Phone Edition 장치로부터 걸려온 E9-1-1(고급 9-1-1) 통화를 지원합니다. Lync Server에서 E9-1-1을 사용하도록 구성하면 Lync 2013 또는 Lync Phone Edition에서 걸려온 긴급 통화에 위치 정보 서비스 데이터베이스의 ERL(Emergency Response Location) 정보가 포함됩니다. ERL은 주소와 사무실 건물 또는 복합 시설 내의 위치를 더 정확히 식별하는 데 도움이 되는 기타 정보로 구성됩니다. 사용자가 긴급 통화를 하면 Lync Server는 중재 서버를 통해 E9-1-1 위치 및 콜백 정보와 함께 통화 오디오를 E9-1-1 서비스 공급자로 라우팅합니다. E9-1-1 서비스 공급자는 발신자의 주소를 사용하여 발신자의 위치에 서비스를 제공하는 PASP(Public Safety Answering Point)로 통화를 라우팅하고 PSAP가 발신자 ERL을 조회하는 데 사용하는 ESQK(Emergency Service Query Key)를 함께 전송합니다.

Lync Server에서는 긴급 통화를 E9-1-1 서비스 공급자로 라우팅하기 위한 두 가지 방법을 지원합니다.

  - 적격 E9-1-1 서비스 공급자에 대한 SIP(Session Initiation Protocol) 트렁크 연결

  - PSTN(공중 전화망) 기반 E9-1-1 서비스 공급자에 대한 ELIN(Emergency Location Identification Number) 게이트웨이

SIP 트렁크 E9-1-1 서비스 공급자를 사용할 경우 위치 정보 서비스 데이터베이스에 ERL을 추가한 다음 E9-1-1 서비스 공급자가 유지 관리하는 MSAG(마스터 주소 가이드)에 대해 위치가 올바른지 확인합니다. 위치 정보가 없거나 MSAG에 대해 확인되지 않은 위치를 포함하는 통화를 E9-1-1 서비스 공급자가 받을 경우 E9-1-1 서비스 공급자는 국가 ECRC(Emergency Call Response Center)로 통화를 라우팅합니다. 이 ECRC에는 가능한 경우 구두로 발신자의 위치를 확인하여 적절한 PSAP로 통화를 수동으로 라우팅하도록 특별히 교육 받은 직원이 있습니다. 또한 일부 SIP 트렁크 E9-1-1 서비스 공급자도 ECRC로 연결할 수 있는 PSTN DID(Direct Inward Dialing) 번호를 고객에게 제공하고 있습니다. 이 DID 번호는 SIP 트렁크가 실패할 경우 9-1-1 통화를 라우팅하기 위한 대체 수단을 제공합니다.

고정된 위치가 있는 TDM(Time Division Multiplexing) 및 IP 기반 PBX(Private Branch Exchange) 전화와는 달리 Lync 끝점은 유동적일 가능성이 매우 높습니다. E9-1-1 기능을 배포할 경우 Lync Server에서는 발신자의 위치에 관계없이 발신자의 위치에 서비스를 제공하는 PSAP로 긴급 통화가 라우팅될 수 있도록 보장합니다. 예를 들어 사용자의 주 사무실이 워싱턴의 레드몬드에 있지만 사용자가 캔자스 위치타의 지점에서 긴급 통화를 거는 경우 SIP 트렁크 또는 PSTN 기반 E9-1-1 서비스 공급자는 레드몬드가 아닌 위치타의 PSAP로 통화를 라우팅합니다.

게이트웨이를 사용하는 경우에도 역시 위치 정보 서비스 데이터베이스에 ERL을 추가하지만 각 위치에 대한 ELIN 번호를 포함합니다. 긴급 통화 중에는 ELIN 번호가 긴급 발신 번호가 됩니다. 그러면 PSTN 통신 회사에서 ELIN을 ALI(Automatic Location Identification) 데이터베이스에 업로드했는지 확인해야 합니다.


> [!NOTE]
> Lync로 연결된 아날로그 장치는 위치 정보 서비스에서 위치 정보를 받거나 위치를 E9-1-1 서비스 공급자로 전송할 수 없습니다. SIP 트렁크 E9-1-1 서비스 공급자 옵션을 사용하며 아날로그 전화에서 E9-1-1을 지원해야 하는 경우에는 두 가지 옵션이 있습니다. 
> <UL>
> <LI>
> <P><STRONG>기존 PS-ALI 옵션</STRONG>&nbsp;&nbsp;&nbsp;아날로그 전화가 배포된 각 사이트에 로컬 PSTN 게이트웨이가 있고 각 아날로그 전화에 DID가 있는 경우, PS-ALI(Private Switch/Automatic Location Identification) 서비스 공급자를 통해 직접 아날로그 장치의 위치를 프로비전할 수 있습니다. 이 경우 이러한 전화로부터 걸려온 E9-1-1 통화를 E9-1-1 서비스 공급자 SIP 트렁크로 라우팅하는 대신 통화가 로컬 게이트웨이를 통해 사이트에 서비스를 제공하는 PSTN 공급자로 직접 라우팅되도록 특수하게 만들어진 Lync 음성 정책을 구성하여 아날로그 장치 연락처 개체에 할당할 수 있습니다. 긴급 통화가 걸려오면 PSTN 트렁크와 연결된 PS-ALI 공급자의 데이터베이스가 각 아날로그 전화의 DID를 실제 위치에 매핑하고 이 위치를 PSAP에 제공합니다. 전화가 다른 ERL로 이동될 때마다 PS-ALI 서비스 공급자에서 이러한 레코드가 업데이트되어야 합니다.</P>
> <LI>
> <P><STRONG>E9-1-1 서비스 공급자 옵션</STRONG>&nbsp;&nbsp;&nbsp;E9-1-1 서비스 공급자가 지원하는 경우 E9-1-1 서비스 공급자에 아날로그 전화 DID 및 해당 ERL을 등록할 수 있습니다. 공급자가 PIDF-LO 데이터가 포함되지 않은 통화를 Lync Server로부터 받을 경우 공급자는 발신자의 DID 번호와 일치하는 번호가 데이터베이스에 있는지 확인할 수 있습니다. 공급자는 해당 데이터베이스에서 검색된 ERL을 사용하여 긴급 통화를 올바른 PASP로 자동으로 라우팅할 수 있습니다. PSAP는 아날로그 장치의 DID 및 발송자가 발신자 위치를 조회할 수 있도록 하는 ESQK 레코드를 받습니다.</P></LI></UL>ELIN 게이트웨이 옵션을 사용하며 아날로그 장치에서 E9-1-1을 지원해야 하는 경우에는 위의 첫 번째 옵션에 설명되어 있는 것처럼 PS-ALI 서비스 공급자를 통해 직접 아날로그 장치의 위치를 프로비전할 수 있습니다.



Lync Server 관점에서 보면 E9-1-1 프로세스를 두 단계로 나눌 수 있습니다.

  - 1단계: 위치 얻기

  - 2단계: 긴급 통화를 E9-1-1 서비스 공급자로 라우팅

이 섹션에서는 이 두 단계의 작동 방식에 대해 설명합니다.

클라이언트 위치를 자동으로 감지하도록 인프라를 구성하려는 경우 먼저 발신자를 위치에 매핑하는 데 사용할 네트워크 요소를 결정해야 합니다. 가능한 옵션에 대한 자세한 내용은 [Lync Server 2013에서 위치를 확인하는 데 사용되는 네트워크 요소 정의](lync-server-2013-defining-the-network-elements-used-to-determine-location.md)를 참조하십시오.

## 이 섹션의 내용

  - [Lync Server 2013에서 위치 얻기](lync-server-2013-acquiring-a-location.md)

  - [Lync Server 2013에서 SIP 트렁크를 사용하여 E9-1-1 통화 라우팅](lync-server-2013-routing-e9-1-1-calls-by-using-a-sip-trunk.md)

  - [Lync Server 2013에서 ELIN 게이트웨이를 사용하여 E9-1-1 전화 라우팅](lync-server-2013-routing-e9-1-1-calls-by-using-an-elin-gateway.md)

