﻿---
title: Lync Server 2013에서 사용자별 현재 상태 정책 할당
TOCTitle: Lync Server 2013에서 사용자별 현재 상태 정책 할당
ms:assetid: fd1097b7-248d-4b78-8c43-456b03257c18
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182614(v=OCS.15)
ms:contentKeyID: 49305624
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 사용자별 현재 상태 정책 할당

 

_**마지막으로 수정된 항목:** 2015-03-09_

현재 상태 정책은 현재 상태에 영향을 미치는 제한 집합입니다. 다음 표에서는 Lync Server 2013에서 사용할 수 있는 현재 상태 정책 설정에 대해 설명합니다.

### 현재 상태 정책 설정

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>XML 이름</th>
<th>표시 이름</th>
<th>설명</th>
<th>유형</th>
<th>값</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CategorySubscriptions</p></td>
<td><p>구독자 범주의 최대 구독 수</p></td>
<td><p>구독자의 범주 구독 수를 제한합니다. 예를 들어 Communicator가 사용자의 현재 상태를 구독하면 대화 상대 카드, 일정 데이터, 메모, 서비스 및 상태 범주 각각에 대한 범주 구독을 가져오게 됩니다.</p>
<p>설정이 0인 경우 다른 사용자가 사용자나 대화 상대 개체의 상태를 구독할 수 없습니다.</p>


> [!NOTE]
> 이 설정에 지정된 숫자가 높을 경우 성능이 심각하게 저하될 수 있으며 해당 사용자의 현재 상태를 구독하는 사용자가 많아집니다.


</td>
<td><p>정수</p></td>
<td><p>0-3000</p></td>
</tr>
<tr class="even">
<td><p>PromptedSubscribers</p></td>
<td><p>현재 상태 구독에 대해 대기할 수 있는 최대 알림 수</p></td>
<td><p>프롬프트 구독자 테이블의 항목 수를 제한합니다. 이 설정으로, 해당 사용자에 대해 대기할 수 있는 최대 프롬프트 수가 결정됩니다. 예를 들어 사용자 A가 사용자 B의 현재 상태를 구독할 때 사용자 B는 사용자 A가 이제 사용자 B의 현재 상태를 구독한다는 프롬프트를 받게 되며 사용자 B의 프롬프트 구독자 테이블에서 승인 프롬프트가 만들어집니다. 사용자 B가 구독을 수락하거나 승인하고 나면 사용자 B의 프롬프트 구독자 테이블에서 승인 프롬프트가 제거됩니다.</p>
<p>설정이 0인 경우 다른 사람이 사용자의 현재 상태를 구독할 때 해당 사용자에게 메시지가 표시되지 않습니다.</p></td>
<td><p>정수 또는 토큰</p></td>
<td><p>0-500</p></td>
</tr>
</tbody>
</table>


기본적으로 **기본 정책** 및 **서비스: 보통** 현재 상태 정책은 Lync Server를 배포할 때 설치됩니다. 다음 표에는 두 개의 현재 상태 정책에 대한 특정 설정이 나와 있습니다.

### 현재 상태 정책

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>정책 이름</th>
<th>설명</th>
<th>CategorySubscriptions</th>
<th>PromptedSubscribers</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>기본 정책</p></td>
<td><p>일반 사용자를 위한 정책이며, 기본 현재 상태 정책입니다.</p></td>
<td><p>1000</p></td>
<td><p>200</p></td>
</tr>
<tr class="even">
<td><p>서비스: 보통</p></td>
<td><p>기타 사용자가 개체의 현재 상태를 구독해야 하는 응용 프로그램을 위한 정책입니다.</p></td>
<td><p>1000</p></td>
<td><p>0</p></td>
</tr>
</tbody>
</table>

