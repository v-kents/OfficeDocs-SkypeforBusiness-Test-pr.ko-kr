﻿---
title: 대규모 모임 예약 프로세스
TOCTitle: 대규모 모임 예약 프로세스
ms:assetid: de267458-885f-4176-a8d7-1a218e67640e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205334(v=OCS.15)
ms:contentKeyID: 49305260
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 대규모 모임 예약 프로세스

 

_**마지막으로 수정된 항목:** 2012-10-22_

대규모 전용 모임 풀에서는 한 번에 하나의 대규모 모임만 지원되므로 대규모 모임 간 충돌을 방지하기 위해 대규모 모임 예약 프로세스를 구현하는 것이 좋습니다. 이러한 예약 프로세스의 목적은 대규모 모임을 쉽게 설정할 수 있게 지원하는 것입니다. 이러한 기능은 Lync Server 또는 Lync Server 클라이언트에서 직접 제공되지 않습니다. 이러한 프로세스를 구현하는 한 가지 방법은 조직 지원 팀의 발권 시스템(사용 가능한 경우)을 사용하는 것입니다.

대규모 모임 이끌이는 대규모 모임 예약 시 다음 단계를 수행해야 합니다.

1.  모임 이끌이나 대리자가 예정된 모임의 시간, 기간 및 규모와 발표자 목록을 결정합니다. 또한 예상된 모임 규모가 250명을 초과하거나 250명 미만의 모임을 위한 최상의 사용자 환경을 유지하려는 경우 대규모 모임 요청을 제출합니다.

2.  예약 직원은 요청된 날짜와 시간이 예약 가능한지 확인합니다. 전용 풀에서 한 번에 하나의 대규모 모임만 지원되므로 예약 직원은 요청한 날짜 및 시간에 예약된 다른 모임이 있는지 알아보기 위해 대규모 모음 일정을 확인해야 합니다. 요청한 시간이 예약 가능하면 직원은 모임 요청을 승인합니다.

3.  요청이 승인되면 예약 직원(전용 풀에 대한 자격 증명 사용)이 Lync 2013용 온라인 모임 추가 기능과 Outlook을 사용하여 대규모 전용 모임 풀에 모임을 설정합니다. 모임에 참가하는 데 사용될 URL은 승인 알림의 일부로 요청자에게 제공됩니다.

4.  모임 이끌이나 대리자는 Outlook을 사용하여 예정된 모임을 예약하고 모임 참가용 URL을 모임 초대에 추가합니다. 그런 다음 초대할 사용자를 지정하여 모임 초대를 보냅니다.
    
    다음 그림은 대규모 모임 예약을 위한 일반적인 요청 및 승인 워크플로를 보여 줍니다.
    
    ![회의 예약 워크플로](images/JJ205334.5d8b1f62-1dc3-47bf-bf8f-be2d8899ab9d(OCS.15).jpg "회의 예약 워크플로")

