﻿---
title: Lync Server 2013 메신저 및 현재 상태
TOCTitle: 메신저 및 현재 상태
ms:assetid: 6a93ae95-3b64-410b-ab72-74dea232f065
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg417162(v=OCS.15)
ms:contentKeyID: 49303934
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 메신저 및 현재 상태

 

_**마지막으로 수정된 항목:** 2013-10-07_

IM(인스턴트 메시징) 및 현재 상태는 모든 Lync Server 배포에서 자동으로 설치됩니다.

*현재 상태* 정보를 사용하면 적절한 통신 형식을 통해 제때 동료에게 연락을 할 수 있으므로 작업 환경의 생산성을 높일 수 있습니다. 사용자의 현재 상태는 사용 가능성, 통신 가능 여부, 추가 참고 사항(위치, 상태 등), 그리고 사용자에게 연락할 수 있는 방법 등이 포함되는 정보 컬렉션입니다. Lync Server에서는 사진, 위치 정보, 그리고 다양한 현재 상태 집합 등이 추가되어 현재 상태가 개선됩니다. 현재 상태에는 기본 상태인 "대화 가능", "다른 용무 중", "회의 중" 이외에 "퇴근", "방해 금지", "곧 돌아오겠음" 등의 여러 항목이 있습니다. 관리자가 조직별로 사용자 지정된 현재 상태를 정의할 수도 있습니다.

연락처 관리 및 사용자 액세스 옵션을 사용하면 다른 사람이 볼 수 있는 정보를 제어할 수 있습니다. 사용자는 서로 다른 연락처 수준을 설정할 수 있으며, 각 수준은 서로 다른 수준의 현재 상태 정보를 볼 수 있습니다.

연락처 목록을 확인하는 것만으로 필요한 정보를 한 눈에 파악할 수 있습니다. 다른 사용자의 현재 상태는 색이 지정된 간단한 아이콘으로 표시되며, 사진과 위치도 표시됩니다.

Lync Server와 기타 제품(예: Outlook, SharePoint)을 통합하면 연락처 이름이 전자 메일 메시지, 팀 웹 사이트 등에 표시될 때마다 해당 사용자의 상태와 연락처 정보도 표시됩니다. 또한 Exchange 2013을 배포한 경우 Lync Server 및 Exchange 2013이 각 제품의 클라이언트가 액세스할 수 있는 통합 연락처 저장소를 공유할 수 있습니다.

사용자는 Lync Server의 인스턴트 메시징을 통해 서로에게 필요한 정보를 제때 전달할 수 있습니다. 원하는 경우에는 MSN/Windows Live, Yahoo\!, AOL 등의 공용 IM 네트워크 사용자와도 통신할 수 있습니다. Windows Live, AOL, Yahoo\! 등의 공용 IM 연결에는 별도의 라이선스가 필요할 수도 있습니다. Lync Server에는 또한 XMPP(Extensible Messaging and Presence Protocol) 호환성이 포함되므로, 사용자가 Google Talk와 같은 XMPP 서비스 사용자와 IM 메시지 및 현재 상태 정보를 교환할 수 있습니다.


> [!IMPORTANT]
> <UL>
> <LI>
> <P>2012년 9월 1일 현재 신규 또는 갱신 계약에 대해 Microsoft Lync "PIC USL"(공용 메신저 연결 사용자 구독 라이선스)을 더 이상 구입할 수 없습니다. 유효 라이선스를 보유한 고객은 서비스 종료 날짜까지 Yahoo! Messenger와 계속 페더레이션할 수 있습니다. AOL 및 Yahoo!는 서비스 종료 날짜를 2014년 6월로 발표했습니다. 자세한 내용은 <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Lync Server 2013의 공용 메신저 연결 지원</A>을 참고하세요.</P>
> <LI>
> <P>PIC USL은 Lync Server 또는 Office Communications Server가 Yahoo! Messenger와 페더레이션하는 데 필요한 월별 사용자 단위 구독 라이선스입니다. Microsoft는 Yahoo!의 지원 여부에 따라 이 서비스를 제공할 수 있었으며 해당 서비스의 기본 계약은 곧 종료될 예정입니다.</P>
> <LI>
> <P>Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 메신저 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.</P></LI></UL>



사용자는 대화 내용을 통해 이전 IM 대화를 추적하고, 몇 개월 전에 IM을 통해 교환한 정보를 검색할 수 있습니다.

영구 채팅 기능은 사용자가 사용자가 오랜 시간 동안 지속되는 여러 당사자 간의 항목 기반 대화에 참가할 수 있게 해줍니다. 채팅방(토론 포럼)에 게시되는 메시지는 지속될 수 있으므로(오랜 시간 동안 사용 가능함) 다른 위치 및 부서의 사람들이 동시에 온라인 상태가 아니더라도 참가할 수 있습니다.

조직에서 준수 규정을 따라야 하는 경우 조직의 모든 사용자에 대해 또는 지정한 특정 사용자에 대해서만 인스턴트 메시지 내용을 보관하도록 메시지 보관 기능을 배포할 수 있습니다. 또한 Exchange 2013을 배포할 경우에는 IM 보관을 Exchange의 원본 위치 유지 기능과 통합하여 준수에 대한 단일 관리 환경을 제공할 수 있습니다.

