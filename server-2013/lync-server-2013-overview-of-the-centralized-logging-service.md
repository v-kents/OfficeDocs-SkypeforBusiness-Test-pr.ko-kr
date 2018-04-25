﻿---
title: 중앙화된 로깅 서비스 개요
TOCTitle: 중앙화된 로깅 서비스 개요
ms:assetid: 975718a0-f3e3-404d-9453-6224e73bfdd0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688145(v=OCS.15)
ms:contentKeyID: 49885884
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 중앙화된 로깅 서비스 개요

 

_**마지막으로 수정된 항목:** 2013-02-22_

중앙 로깅 서비스는 넓은 범위 또는 좁은 범위에서 제어된 방식으로 데이터를 수집할 수 있도록 합니다. 배포의 모든 서버에서 동시에 데이터를 수집할 수 있으며, 추적할 특정 요소를 정의하고 추적 플래그를 설정하여 단일 컴퓨터에서 검색 결과를 반환하거나 전체 서버의 모든 데이터 집합체에서 검색 결과를 반환할 수 있습니다. 중앙 로깅 서비스는 배포의 모든 서버에 대해 실행됩니다. 중앙 로깅 서비스의 아키텍처는 다음 에이전트와 서비스로 구성됩니다.

  - *중앙 로깅 서비스 에이전트*   ClsAgent.exe는 서비스 실행 파일로서, 컨트롤러와 통신하여 관리자가 컨트롤러에서 실행한 명령을 받습니다. 이 에이전트는 각 Lync Server 컴퓨터에서 서비스로 실행됩니다. 이 에이전트는 명령을 받으면 명령을 실행하며 추적하도록 정의된 구성 요소에 메시지를 전송하고 추적 로그를 디스크에 기록합니다. 또한 해당 컴퓨터에 대한 추적 로그를 읽고 요청 시 추적 데이터를 컨트롤러로 다시 전송합니다. ClsAgent는 **TCP 50001**, **TCP 50002** 및 **TCP 50003** 포트에서 명령을 수신합니다.

  - *중앙 로깅 서비스 컨트롤러*   ClsControllerLib.dll은 Lync Server 관리 셸 및 ClsController.exe의 명령 실행 엔진입니다. CLSControllerLib.dll은 Start, Stop, Flush 및 Search 명령을 ClsAgent로 전송합니다. 검색 명령이 전송되면 결과 로그가 ClsControllerLib.dll로 반환되어 집계됩니다. 이 컨트롤러는 에이전트에 명령을 전송하고, 이러한 명령의 상태를 수신하고, 검색 범위에 속한 모든 컴퓨터에 설치된 모든 에이전트로부터 반환되는 검색 로그 파일 데이터를 관리하고, 로그 데이터를 의미 있고 정렬된 출력 집합으로 집계합니다. 다음 항목에서는 Lync Server 관리 셸 사용에 대해 중점적으로 설명합니다. ClsController.exe는 Lync Server 관리 셸에서 제공되는 일부 기능으로 제한됩니다. 기본 디렉터리 C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\ClsAgent에서 명령줄에 `ClsController`를 입력하여 ClsController.exe에 대한 도움말을 볼 수 있습니다.

**ClsController에서 ClsAgent로의 통신**

![CLSController와 CLSAgent 간의 관계.](images/JJ688145.68c90811-5cf9-4a84-95b7-ea9ffc61eac4(OCS.15).jpg "CLSController와 CLSAgent 간의 관계.")

Windows Server 명령줄 인터페이스 또는 Lync Server 관리 셸을 사용하여 명령을 실행할 수 있습니다. 명령은 로그인된 컴퓨터에서 실행되어 ClsAgent에 로컬로 전송되거나 배포의 다른 컴퓨터 및 풀로 전송됩니다.

ClsAgent는 로컬 컴퓨터에 있는 모든 .CACHE 파일의 인덱스 파일을 유지합니다. ClsAgent는 CacheFileLocalFolders 옵션으로 정의된 모든 볼륨에 걸쳐 균등하게 분산되도록 .CACHE 파일을 할당하며 각 볼륨의 80% 이하만 사용합니다(**Set-CsClsConfiguration** cmdlet을 사용하여 로컬 캐시 위치와 비율을 구성 가능). 또한 ClsAgent는 오래된 캐시된 이벤트 추적 로그(.etl) 파일을 로컬 컴퓨터에서 에이징합니다. 2주 후에(**Set-CsClsConfiguration** cmdlet을 사용하여 기간을 구성 가능) 이러한 파일은 파일 공유로 복사되어 로컬 컴퓨터에서 삭제됩니다. 자세한 내용은 [Set-CsClsConfiguration](set-csclsconfiguration.md)을 참조하십시오. 검색 요청이 수신되면 검색 조건을 사용하여 캐시된 .etl 파일 집합을 선택하고 에이전트에서 유지되는 인덱스의 값을 사용하여 검색을 수행합니다.


> [!NOTE]
> 로컬 컴퓨터에서 파일 공유로 이동된 파일은 ClsAgent에서 검색할 수 있습니다. ClsAgent에서 파일을 파일 공유로 이동한 후에는 해당 파일의 에이징 및 제거를 유지하지 않습니다. 사용자는 파일 공유에서 파일 크기를 모니터링하여 파일을 삭제하거나 보관하는 관리 작업을 정의해야 합니다.



결과 로그 파일은 **Snooper.exe**를 비롯한 다양한 도구와 텍스트 파일을 읽을 수 있는 모든 도구(예: **Notepad.exe**)를 사용하여 읽고 분석할 수 있습니다. Snooper.exe는 Lync Server 2013 디버그 도구에 포함되어 있으며 웹을 통해 다운로드할 수 있습니다.

OCSLogger와 마찬가지로 중앙 로깅 서비스는 추적의 기준으로 사용되는 여러 구성 요소를 가지며 플래그(예: TF\_COMPONENT 및 TF\_DIAG)를 선택할 수 있는 옵션을 제공합니다. 또한 중앙 로깅 서비스에서는 OCSLogger의 로깅 수준 옵션을 유지합니다.

명령줄 ClsController에 비해 Windows PowerShell을 사용하는 것의 가장 중요한 장점은 사용자 지정 플래그 및 로깅 수준과 해당 문제 영역을 대상으로 하는 선택한 공급자를 사용하여 새로운 시나리오를 구성하고 정의할 수 있다는 점입니다. 반면 ClsController에서 사용할 수 있는 시나리오는 실행 파일에 정의된 시나리오로 한정됩니다.

이전 버전에서는 관리자와 지원 담당자가 배포의 컴퓨터에서 추적 파일을 수집할 수 있도록 OCSLogger.exe가 제공되었습니다. OCSLogger는 다양한 장점이 있지만 한 가지 단점이 있습니다. 즉, 한 번에 한 컴퓨터에서만 로그를 수집할 수 있습니다. 별도의 OCSLogger를 사용하여 여러 컴퓨터에 로그온할 수도 있지만 이렇게 하면 여러 로그가 생성되며 결과를 집계하기 어렵습니다.

사용자가 로그 검색을 요청하면 ClsController는 선택된 시나리오에 따라 요청을 전송할 컴퓨터를 결정합니다. 또한 저장된 .etl 파일이 있는 파일 공유로 검색을 전송해야 할지 여부를 결정합니다. 검색 결과가 ClsController에 반환되면 이 컨트롤러는 결과를 시간순으로 정렬된 단일 결과 집합으로 병합하여 사용자에게 제공합니다. 사용자는 검색 결과를 로컬 컴퓨터에 저장하여 추가로 분석할 수 있습니다.

로깅 세션을 시작할 때 해결할 문제와 관련된 시나리오를 지정해야 합니다. 한 번에 두 시나리오를 실행할 수 있으며, 그 중 하나는 AlwaysOn 시나리오여야 합니다. 이름에서 알 수 있듯이 AlwaysOn 시나리오는 모든 컴퓨터, 풀 및 구성 요소에 대한 정보를 수집하며 배포에서 항상 실행되어야 합니다.


> [!IMPORTANT]
> AlwaysOn 시나리오는 기본적으로 배포에서 실행되지 않으며, 사용자가 명시적으로 시작해야 합니다. 이 시나리오는 시작된 후에 명시적으로 중지될 때까지 계속 실행되며, 컴퓨터를 재부팅해도 실행 상태가 유지됩니다. 시나리오 시작 및 중지에 대한 자세한 내용은 <A href="lync-server-2013-using-start-for-the-centralized-logging-service-to-capture-logs.md">중앙화된 로깅 서비스에 시작을 사용하여 로그 캡처</A> 및 <A href="lync-server-2013-using-stop-for-the-centralized-logging-service.md">중앙화된 로깅 서비스에 중지 사용</A>을 참조하십시오.



문제가 발생할 경우 보고된 문제와 관련된 두 번째 시나리오를 시작합니다. 문제를 재현하고 두 번째 시나리오의 로깅을 중지합니다. 그런 다음 보고된 문제와 관련된 로그 검색을 시작합니다. 집계된 로그 컬렉션을 사용하여 사이트 내 모든 컴퓨터 또는 전체 배포 범위의 추적 메시지가 포함된 로그 파일이 생성됩니다. 검색 결과 제대로 분석할 수 없을 정도로 많은 데이터가 반환될 경우("신호 대 노이즈 비율"에서 노이즈가 너무 높음) 보다 좁은 범위의 매개 변수를 사용하여 검색을 다시 실행할 수 있습니다. 이렇게 하면 나타나는 패턴을 인식하여 문제에 더욱 명확하게 중점을 둘 수 있습니다. 몇 번의 구체화된 검색을 통해 문제와 관련된 데이터를 찾아 근본 원인을 파악할 수 있습니다.


> [!TIP]
> Lync Server에서 문제 시나리오에 직면하는 경우 “이 문제에 대해 이미 알고 있는 사항은 무엇인가?"를 자문하며 해결을 시작하십시오. 문제의 범위를 구체적으로 파악하면 Lync Server에서 작업 엔터티의 대부분이 필요 없어질 수 있습니다.<BR>사용자가 연락처를 검색할 때 최신 결과를 얻지 못하며 여러분이 이 사실을 알고 있는 시나리오를 예로 들어 보겠습니다. 이 경우 미디어 구성 요소, Enterprise Voice, 전화 회의 및 기타 여러 가지 구성 요소에서는 문제를 확인할 필요가 없습니다. 이 상황에서 모르는 사항은 문제가 실제로 발생한 위치(클라이언트 쪽 또는 서버 쪽)일 것입니다. 연락처는 Active Directory에서 User Replicator를 통해 수집되어 ABServer(주소록 서버)를 경유하여 클라이언트에 전달됩니다. ABServer는 기본적으로 오전 1:30에 RTC 데이터베이스(여기에 User Replicator가 업데이트 기록)에서 업데이트를 가져와 주소록 파일에 수집합니다. 한편 Lync Server 클라이언트는 임의 스케줄로 새 주소록을 검색합니다. 여러분은 이러한 프로세스 작동 방식을 알기 때문에 근본 원인을 찾을 때 User Replicator가 Active Directory에서 데이터를 수집하는 것과 관련된 문제, ABServer가 주소록 파일을 검색하고 만들지 않는 문제, 클라이언트가 주소록 파일을 다운로드하지 않는 문제가 있는지만 확인하면 됩니다.

