﻿---
title: 'Lync Server 2013: MPLS 네트워크에 대한 통화 허용 제어 서비스'
TOCTitle: MPLS 네트워크에 대한 통화 허용 제어 서비스
ms:assetid: 0beec6be-2431-4255-a3d2-512dd030e66a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398168(v=OCS.15)
ms:contentKeyID: 49302775
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 MPLS 네트워크에 대한 통화 허용 제어 서비스

 

_**마지막으로 수정된 항목:** 2012-09-22_

MPLS(Multiprotocol Label Switching) 네트워크에서는 모든 사이트가 풀 메쉬로 연결됩니다. 즉, 모든 사이트가 인터넷 서비스 공급자의 MPLS 백본에 직접 연결되며 각 사이트에는 MPLS 클라우드에 대한 WAN 링크에 사용할 대역폭이 프로비전됩니다. IP 라우팅을 제어하는 네트워크 허브 또는 중앙 사이트는 없습니다. 다음 그림에서는 MPLS 기술을 기반으로 하는 간단한 네트워크를 보여 줍니다.

**예제 MPLS 네트워크**

![MPLS를 사용하는 CAC](images/Gg398168.54602e6e-ec11-4dae-936d-b01acda8a179(OCS.15).jpg "MPLS를 사용하는 CAC")

MPLS 네트워크에서 CAC(통화 허용 제어)를 배포하려면 MPLS 클라우드를 나타내는 네트워크 지역을 만든 다음 각 MPLS 위성 사이트를 나타내는 네트워크 사이트를 만듭니다. 다음 그림에서는 위 그림의 예제 MPLS 네트워크를 나타내도록 네트워크 지역 및 네트워크 사이트를 구성하는 방법을 보여 줍니다. 전체 대역폭 제한 및 대역폭 세션 제한은 각 네트워크 사이트에서 MPLS 클라우드를 나타내는 네트워크 지역으로의 WAN 링크 용량을 기반으로 합니다.

**MPLS 네트워크의 네트워크 지역 및 네트워크 사이트**

![MPLS를 사용하는 CAC(통화 허용 제어) 다이어그램](images/Gg398168.f8f76283-5c0c-4133-8a78-3fbbfd016dc4(OCS.15).jpg "MPLS를 사용하는 CAC(통화 허용 제어) 다이어그램")

