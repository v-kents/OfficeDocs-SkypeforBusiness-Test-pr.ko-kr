﻿---
title: Lync 사용 휴대폰 및 Lync Server 2013에서 전화 번호 기능 사용
TOCTitle: Lync 사용 휴대폰 및 Lync Server 2013에서 전화 번호 기능 사용
ms:assetid: 975a1df8-a159-4aa4-a991-5972a535998e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn383570(v=OCS.15)
ms:contentKeyID: 56558970
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync 사용 휴대폰 및 Lync Server 2013에서 전화 번호 기능 사용

 

_**마지막으로 수정된 항목:** 2013-08-09_

Lync의 전화 번호 기능은 사용자가 휴대폰, "일반 전화" 또는 PSTN(공중 전화망)에 연결된 기타 장치를 사용하여 회의의 오디오 부분에 참가할 수 있는 방법을 제공합니다. Lync를 사용하여 모임에 참가하면 일반적으로 **모임 오디오 참가** 대화 상자가 나타납니다.

![Lync를 사용하여 모임 오디오 참가 창 스크린샷](images/Dn383570.e28f17f0-9f17-44ef-b893-f4ef132f47ac(OCS.15).png "Lync를 사용하여 모임 오디오 참가 창 스크린샷")

**전화 번호**를 선택한 후에는 드롭다운 목록에서 전화 번호를 선택할 수 있습니다. Lync Server 2013에서 선택한 번호로 전화를 걸면 사용자는 전화기를 사용해 회의의 오디오 부분에 참석할 수 있습니다.

드롭다운 목록은 **Lync – 옵션** 대화 상자의 **전화** 탭에 입력한 전화 번호(휴대폰, 집 전화 또는 기타 전화)로 채워집니다.

![Lync 휴대폰 설정 옵션 스크린샷](images/Dn383570.03d2f25d-49e2-47b4-b1e9-b1614fc0c11c(OCS.15).png "Lync 휴대폰 설정 옵션 스크린샷")

**전화** 탭에 전화 번호를 입력하지 않은 경우에는 드롭다운 상자에 사용할 수 있는 번호가 나타나지 않습니다. 그러나 언제든지 **새 번호**를 클릭하여 Lync Server에서 원하는 번호로 전화를 걸도록 할 수 있습니다.

![Lync 모임 오디오 참가 전화 번호 창 스크린샷](images/Dn383570.27f2ac7a-cc1c-465c-b145-202ad03af4f2(OCS.15).png "Lync 모임 오디오 참가 전화 번호 창 스크린샷")

전화 번호 기능은 의도한 대로 Lync Server에서 PSTN 전화 번호로 전화를 걸 수 있도록 한다면 매우 큰 효과를 발휘할 수 있습니다. 그러나 Lync 사용 끝점에서 Lync Server에 전화를 걸어 달라고 요청하는 경우(예: 회의실 전화)에는 성능이 다소 떨어질 수 있습니다. 다음은 발생할 수 있는 문제와 문제를 해결할 수 있는 두 가지 방법을 소개합니다.

먼저 전화 번호 기능에 Lync 사용 전화기의 전화 번호를 제공하는 경우 어떤 일이 일어나는지 알아보겠습니다. 김진철이 Lync Server에서 Lync Server 사용 전화 번호인 1-206-555-1219로 전화를 걸도록 하여 모임에 참가한다고 가정해 보겠습니다. 처음에는 김진철이 모임에 연결되지만 몇 초 지난 후 Lync에 **통화가 완료되지 않았거나 종료되었습니다** 메시지가 표시되고 김진철은 모임에서 나간 것으로 표시됩니다.

![Lync 전화 회의 창의 스크린샷](images/Dn383570.c2a81727-8751-41b5-946a-03a1b75b9d95(OCS.15).png "Lync 전화 회의 창의 스크린샷")

그러나 Lync 대화 창 안에는 분명히 차이가 있습니다. **참가자** 제목에 나열된 이름은 김진철이 유일하지만 창의 제목 표시줄을 잘 살펴보면 회의 총 참가자가 4명인 것을 알 수 있습니다.

마찬가지로 다른 회의 참가자의 대화 창을 살펴보면 그 어디에서도 김진철을 볼 수 없습니다.

![Lync 참가자 목록 창 스크린샷](images/Dn383570.fa5990cf-2694-402c-ac06-946aa66b6837(OCS.15).png "Lync 참가자 목록 창 스크린샷")

그럼에도 김진철은 Lync 사용 전화기를 사용해 통화의 오디오 부분에 참가할 수 있습니다. 전화 번호 기능이 실제로 효과가 있었지만 사용자 경험은 최적에 미치지 못했습니다.

이 문제를 해결하는 방법에는 최소 두 가지가 있습니다. 김진철이 취했던 방식대로 이미 회의에 참가했다면 일반적으로 다른 형식을 사용해 문제를 해결할 수 있습니다. 예를 들어, 메신저 대화를 보내면 대화 창에 자신을 비롯한 모든 회의 참가자가 표시됩니다.

![Lync 대화 및 참가자 목록 스크린샷](images/Dn383570.9b5ff6d6-9f73-467c-99a7-ef3aa8bd7e7a(OCS.15).png "Lync 대화 및 참가자 목록 스크린샷")

이제 계획했던 방식대로 모임에 참가할 수 있습니다.

또는 모임에 참가하는 방식을 변경해 애초에 이 문제가 발생하지 않도록 할 수 있습니다. Lync Server에서 Lync Server 사용 전화기에 전화를 걸도록 해야 한다면 먼저 오디오 연결 없이 모임에 참가해야 합니다. 이렇게 하려면 '모임 오디오 참가' 대화 상자가 나타날 때 '오디오에 참가 안 함'을 선택합니다.

![Lync 모임 오디오 참가 안 함 창 스크린샷](images/Dn383570.280a148d-cce5-4b02-87f9-9f78f17a81c1(OCS.15).png "Lync 모임 오디오 참가 안 함 창 스크린샷")

모임에 제대로 연결된 경우 Lync Server 사용 전화기도 모임에 참가하도록 "초대"할 수 있습니다. 이렇게 하려면 사용자 아이콘 위에 마우스를 놓은 다음 **다른 사용자 초대**를 클릭합니다.

![Lync 더 많은 참가자 초대 창 스크린샷](images/Dn383570.69b81b29-d1d2-4ed3-acb6-e37dd18e3d86(OCS.15).png "Lync 더 많은 참가자 초대 창 스크린샷")

그러면 **메신저 대화 보내기** 대화 상자가 나타납니다. 실제로 메신저 대화를 보내는 것이 아니므로 대화 상자 제목을 무시하고 Lync 사용 전화기의 전화 번호를 입력합니다.

![메신저 대화 보내기 대화 상자 스크린샷](images/Dn383570.cd67a3f0-06d8-41ba-a808-c067f64bec9f(OCS.15).png "메신저 대화 보내기 대화 상자 스크린샷")

**확인**을 클릭하면 Lync Server가 대화 상자에 입력된 번호로 전화를 겁니다. 연결에 성공하면 Lync 사용 전화기를 통해 전체 오디오 기능을 이용할 수 있으며 전체 회의 참석자 명단을 보고 상호 작용할 수 있습니다.

