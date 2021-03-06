﻿---
title: 전화 회의 정보 보고서
TOCTitle: 전화 회의 정보 보고서
ms:assetid: 1d61cd81-dcfe-40b4-9a41-a73b038bc216
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204728(v=OCS.15)
ms:contentKeyID: 49302992
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 전화 회의 정보 보고서

 

_**마지막으로 수정된 항목:** 2015-03-09_

전화 회의 정보 보고서에서는 전화 회의에 참가한 모든 사용자에 대한 자세한 정보를 제공합니다. 예를 들어 사용자가 전화 회의에 참가한 날짜/시간, 사용자가 전화 회의에서 나간 날짜/시간, 그리고 해당 사용자를 전화 회의에 연결하는 데 사용된 끝점의 사용자 에이전트와 같은 정보를 확인할 수 있습니다. 각 전화 회의에서 사용자의 역할(예: 발표자, 참석자) 관련 정보도 볼 수 있습니다. 그러나 가장 중요한 기능은 전화 회의에 정상적으로 참가하여 전화 회의를 완료한 사용자가 그렇지 않은 사용자를 빠르게 확인할 수 있는 것입니다.

## 전화 회의 정보 보고서 액세스

다음 보고서에서 전화 회의 정보 보고서에 액세스할 수 있습니다.

  - [Lync Server 2013의 통화 허용 제어 보고서](lync-server-2013-call-admission-control-report.md)(전화 회의의 정보 메트릭 클릭)

  - [Lync Server 2013의 오류 목록 보고서](lync-server-2013-failure-list-report.md)(전화 회의 메트릭 클릭)

  - [Lync Server 2013의 사용자 활동 보고서](lync-server-2013-user-activity-report.md)(전화 회의 URI 메트릭 클릭)

전화 회의 정보 보고서에서 진단 보고서(정보) 메트릭을 클릭하면 [Lync Server 2013의 진단 보고서](lync-server-2013-diagnostic-report.md)에 액세스할 수 있습니다.

## 필터

없음. 전화 회의 정보 보고서는 필터링할 수 없습니다.

## 메트릭

다음 표에서는 전화 회의 정보 보고서의 전화 회의 정보 섹션에서 제공되는 정보를 보여 줍니다.

### 전화 회의 정보 메트릭

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>이름</th>
<th>이 항목에 대한 정렬 가능 여부</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>전화 회의 URI</strong></p></td>
<td><p></p></td>
<td><p>전화 회의에 할당된 URI입니다. 예를 들면 다음과 같습니다.</p>
<p>sip:kmyer@litwareinc.com;gruu;opaque=app:conf:focus:id:drg2y8v4</p></td>
</tr>
<tr class="even">
<td><p><strong>풀 FQDN</strong></p></td>
<td><p></p></td>
<td><p>세션에 포함된 등록자 풀 또는 에지 서버의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>시작 시간</strong></p></td>
<td><p></p></td>
<td><p>전화 회의가 시작된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>이끌이</strong></p></td>
<td><p></p></td>
<td><p>전화 회의를 구성한 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>종료 시간</strong></p></td>
<td><p></p></td>
<td><p>전화 회의가 종료된 날짜 및 시간입니다.</p></td>
</tr>
</tbody>
</table>


다음 표에서는 전화 회의 정보 보고서의 전화 회의 참가 섹션에서 제공되는 정보를 보여 줍니다.

### 전화 회의 참가 메트릭

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>이름</th>
<th>이 항목에 대한 정렬 가능 여부</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>사용자</strong></p></td>
<td><p></p></td>
<td><p>전화 회의에 참가한 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>역할</strong></p></td>
<td><p></p></td>
<td><p>전화 회의 참가자가 수행하는 역할(예: 발표자)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>연결</strong></p></td>
<td><p></p></td>
<td><p>참가자의 네트워크 연결(일반적으로 내부 발신 또는 외부 발신)입니다.</p></td>
</tr>
<tr class="even">
<td><p>참가 시간</p></td>
<td><p></p></td>
<td><p>참가자가 전화 회의에 참가한 날짜 및 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>나간 시간</strong></p></td>
<td><p></p></td>
<td><p>참가자가 전화 회의에서 나간 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>사용자 에이전트</strong></p></td>
<td><p></p></td>
<td><p>참가자의 끝점에 사용된 소프트웨어의 식별자입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>진단 보고서</strong></p></td>
<td><p></p></td>
<td><p>진단 및 문제 해결 정보를 제공합니다. 여기에는 실패한 세션에 대한 SIP 응답 코드, 진단 헤더, 전화 회의 참가 시간 및 진단 ID가 포함됩니다.</p></td>
</tr>
</tbody>
</table>


다음 표에서는 전화 회의 정보 보고서의 전화 회의 형식 섹션에서 제공되는 정보를 보여 줍니다.

### 전화 회의 형식 메트릭

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>이름</th>
<th>이 항목에 대한 정렬 가능 여부</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>사용자</strong></p></td>
<td><p></p></td>
<td><p>전화 회의에 참가한 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>참가 시간</strong></p></td>
<td><p></p></td>
<td><p>참가자가 전화 회의에 참가한 날짜 및 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>나간 시간</strong></p></td>
<td><p></p></td>
<td><p>참가자가 전화 회의에서 나간 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>전화 회의 서버</strong></p></td>
<td><p></p></td>
<td><p>전화 회의에 사용된 전화 회의 서버의 URI입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>진단 보고서</strong></p></td>
<td><p></p></td>
<td><p>진단 및 문제 해결 정보를 제공합니다. 여기에는 실패한 세션에 대한 SIP 응답 코드, 진단 헤더, 전화 회의 참가 시간 및 진단 ID가 포함됩니다.</p></td>
</tr>
</tbody>
</table>

