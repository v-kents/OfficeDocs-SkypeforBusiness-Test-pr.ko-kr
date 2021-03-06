﻿---
title: Lync Server 2013의 모니터링 배포
TOCTitle: Lync Server 2013의 모니터링 배포
ms:assetid: 117f4a3e-0670-4388-a553-b9854921145f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398199(v=OCS.15)
ms:contentKeyID: 49302846
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 모니터링 배포

 

_**마지막으로 수정된 항목:** 2013-12-17_

Microsoft Lync Server 2013 모니터링 인프라는 크게 변경되었으며, 가장 큰 변화는 모니터링 서버 역할이 더 이상 사용되지 않는다는 것입니다. 별도의 모니터링 서버 역할을 제공하는 대신(일반적으로 조직이 모니터링 서버로 작동할 전용 컴퓨터를 설정해야 했음), 이제는 모니터링 서비스가 각 프런트 엔드 서버에 배치됩니다. 이 변경으로 인해 제공되는 주요 이점은 다음과 같습니다.

  - Lync Server 2013 구현 시 필요한 서버 역할의 수가 감소합니다. 이 경우 모니터링 서버 서버 역할이 감소하므로 모니터링 전용 서버를 유지 관리할 필요가 없어져 비용도 줄일 수 있습니다.

  - Lync Server 절치 및 관리가 간편해집니다. 각 프런트 엔드 서버에 모니터링 서비스를 자동으로 배치함으로써 더 이상 모니터링 서버 역할을 설치, 구성 및 관리하지 않아도 됩니다.


> [!NOTE]
> Lync Server 2013에서는 보관 서버 역할도 더 이상 사용되지 않습니다. 모니터링 서비스와 마찬가지로 Lync Server 2013 보관 서비스도 이제는 각 프런트 엔드 서버에 배치됩니다. 모니터링 및 보관은 같은 SQL Server 데이터베이스 인스턴스를 공유하는 경우가 많으므로, 이러한 변화는 중요합니다.



사용자들이 예상한 것처럼, 이러한 변경은 모니터링 서비스 설치 및 관리 방법에 큰 영향을 줍니다. 예를 들어 모니터링 서버 역할이 더 이상 없기 때문에 모니터링 서버 노드도 Lync Server 토폴로지 작성기에서 제거되었으며, 따라서 더 이상 토폴로지 작성기의 새 모니터링 서버 마법사를 사용하여 토폴로지에 새 모니터링 서버를 추가하지 않습니다. 이 마법사 역시 더 이상 존재하지 않습니다. 대신, 다음과 같은 두 단계를 완료하여 일반적으로 토폴로지 내에서 모니터링 서비스를 구현합니다.

1.  새 Lync Server 풀을 설치함과 동시에 모니터링을 사용하도록 설정합니다. Lync Server 2013에서 모니터링은 풀 단위로 사용하거나 사용하지 않도록 설정됩니다. 실제로 모니터링 데이터를 수집하지 않고도 풀에 대해 모니터링을 사용하도록 설정할 수 있는데, 이 프로세스에 대해서는 이 설명서의 통화 정보 기록 및 체감 품질 설정 구성 섹션에서 설명합니다.

2.  모니터링 저장소(모니터링 데이터베이스)를 새 풀과 연결합니다. 단일 모니터링 저장소를 여러 풀과 연결할 수 있습니다. 즉, 등록자 풀에 있는 사용자의 수에 따라서는 각 풀에 대해 별도의 모니터링 데이터베이스를 설정하지 않아도 됩니다. 대신 단일 모니터링 저장소를 여러 풀에서 사용할 수 있습니다.

새 풀을 만들 때 모니터링도 동시에 사용하도록 설정하는 것이 더 쉬운 경우가 많지만, 모니터링을 사용하지 않도록 설정한 상태에서 새 풀을 만들 수도 있습니다. 이렇게 하는 경우 나중에 토폴로지 작성기를 사용하여 서비스를 사용하도록 설정할 수 있습니다. 토폴로지 작성기를 사용하면 풀에 대해 모니터링을 사용 또는 사용하지 않도록 설정하거나, 풀을 다른 모니터링 저장소와 연결할 수 있습니다. 모니터링 서버 역할은 더 이상 없지만 모니터링 저장소(모니터링 서비스를 통해 수집되는 데이터를 저장하는 데 사용되는 백 엔드 데이터베이스)는 하나 이상 만들어야 합니다. 이러한 백 엔드 데이터베이스는 Microsoft SQL Server 2008 R2 또는 Microsoft SQL Server 2012를 사용하여 만들 수 있습니다.


> [!NOTE]
> 풀에 대해 모니터링이 사용하도록 설정된 경우 토폴로지를 변경하지 않고도 모니터링 데이터 수집 프로세스를 사용하지 않도록 설정할 수 있습니다. Lync Server 관리 셸에서는 CDR(통화 정보 기록) 또는 QoE(체감 품질) 데이터 수집을 사용하지 않도록 설정했다가 나중에 다시 사용하도록 설정하는 방법을 제공합니다. 자세한 내용은 이 문서의 통화 정보 기록 및 체감 품질 설정 구성 섹션을 참조하십시오.



Lync Server 2013에서 모니터링과 관련하여 향상된 또 다른 중요한 기능은, 이제 Lync Server 모니터링 보고서가 IPv6을 지원한다는 점입니다. IP 주소 필드를 사용하는 보고서는 1) 사용 중인 SQL 쿼리 및 2) IPv6 주소가 모니터링 데이터베이스에 저장되는지 여부에 따라 IPv4 또는 IPv6 주소를 표시합니다.


> [!NOTE]
> SQL Server 에이전트 서비스 시작 유형이 자동이고 SQL Server 에이전트 서비스가 모니터링 데이터베이스를 보유하는 SQL 인스턴스에 대해 실행되고 있는지 확인하여 기본 모니터링 SQL 서버 유지 관리 작업이 예약을 통해 SQL Server 에이전트 서비스 권한 하에 실행되도록 합니다.



이 설명서에서는 Lync Server 2013용으로 모니터링 및 모니터링 보고서를 설치하고 구성하는 프로세스를 안내합니다. 또한 다음 작업을 수행할 수 있도록 단계별 지침을 제공합니다.

  - 토폴로지에서 모니터링을 사용하도록 설정하고 프런트 엔드 풀과 모니터링 저장소를 연결합니다.

  - SQL Server Reporting Services 및 Lync Server 모니터링 보고서를 설치합니다. 모니터링 보고서는 모니터링 데이터베이스에 저장된 정보에 대한 여러 가지 보기를 제공하는 미리 구성된 보고서입니다.

  - CDR(통화 정보 기록) 및 QoE(체감 품질) 데이터 수집을 구성합니다. 통화 정보 기록을 사용하면 VoIP(Voice over IP) 전화 통화, IM(인스턴트 메시징), 파일 전송, A/V(오디오/비디오) 회의, 응용 프로그램 공유 세션 등의 Lync Server 기능 사용을 추적할 수 있습니다. QoE 메트릭은 손실된 네트워크 패킷 수, 백그라운드 노이즈, "지터"(패킷 지연의 차이) 크기 등 조직의 오디오 및 비디오 통화 품질을 추적합니다.

  - 모니터링 데이터베이스에서 CDR 및/또는 QoE 레코드를 수동으로 삭제합니다.

