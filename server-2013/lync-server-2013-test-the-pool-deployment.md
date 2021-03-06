﻿---
title: 'Lync Server 2013: 풀 배포 테스트'
TOCTitle: 풀 배포 테스트
ms:assetid: ffd80617-155a-4041-bbeb-74503e7938dd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413092(v=OCS.15)
ms:contentKeyID: 49305650
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 풀 배포 테스트

 

_**마지막으로 수정된 항목:** 2013-09-25_

다음 절차에서는 프런트 엔드 풀의 배포를 테스트하는 방법을 설명합니다.

## 풀 배포를 테스트하려면

1.  Active Directory 컴퓨터 및 사용자를 사용하여 Lync Server 2013이 설치된 Lync Server 2013 제어판 배포에 대한 관리자 역할의 Active Directory 사용자 개체를 **CSAdministrator** 그룹에 추가합니다.
    

    > [!IMPORTANT]
    > CsAdministors 그룹에 적합한 사용자와 그룹을 추가하지 않으면 Lync Server 제어판을 열 때 권한 없음: RBAC(역할 기반 액세스 제어) 인증이 실패했기 때문에 액세스가 거부되었습니다."와 같은 오류 메시지가 표시됩니다.



2.  사용자 개체가 현재 로그온되어 있는 경우 로그오프하고 다시 로그온하여 새 그룹 지정을 등록합니다.
    

    > [!NOTE]
    > Lync Server 2013을 실행하는 서버의 로컬 관리자는 사용자 계정으로 설정할 수 없습니다.



3.  관리 계정을 사용하여 Lync Server 제어판이 설치된 컴퓨터에 로그온합니다.

4.  Lync Server 제어판을 시작한 후 자격 증명을 제공하라는 메시지가 나타나면 자격 증명을 제공합니다. Lync Server 제어판에 배포 정보가 표시됩니다.

5.  왼쪽 탐색 표시줄에서 **토폴로지** 를 클릭한 후 서비스 상태에 녹색 화살표가 표시된 컴퓨터가 나타나며, 배포되어 온라인 상태로 설정된 각 Lync Server 서버 역할 옆에 복제 상태를 나타내는 녹색 확인 표시가 있는지 확인합니다.

6.  왼쪽 탐색 표시줄에서 **사용자** 및 **사용자 사용** 을 차례로 클릭합니다.

7.  **새 Lync Server 사용자** 페이지에서 **추가** 를 클릭합니다.

8.  찾을 개체에 대한 검색 매개 변수를 정의하려면 **Active Directory에서 선택** 페이지에서 **검색** 을 선택하고 경우에 따라 **필터 추가** 를 클릭하면 됩니다. **LDAP 검색** 을 선택하고 LDAP 식을 입력하여 반환되는 개체를 필터링하거나 제한할 수도 있습니다. 검색 옵션을 결정했으면 **찾기** 를 클릭합니다.

9.  검색 결과 창에서 이 검색 세션에 대한 개체를 모두 선택하고 **확인** 을 클릭합니다.

10. **새 Lync Server 사용자** 페이지의 **사용자** 화면 표시에 선택한 개체(들)가 나타납니다. **사용자를 풀에 할당** 목록에서 개체가 속해야 하는 서버를 선택합니다.
    
    아래에 개체를 구성할 수 있는 여러 옵션이 나와 있습니다.
    
      - **사용자의 SIP URI 생성**
    
      - **전화 통신**
    
      - **줄 URI**
    
      - **회의 정책**
    
      - **클라이언트 버전 정책**
    
      - **PIN 정책**
    
      - **외부 액세스 정책**
    
      - **보관 정책**
    
      - **위치 정책**
    
      - **클라이언트 정책**
    
    기본적인 기능을 테스트하기 위해 **사용자의 SIP URI 생성** 설정에 대해 원하는 옵션을 선택하고 **사용** 을 클릭합니다(구성의 다른 옵션에는 기본 설정이 사용됨).

11. 요약 페이지가 표시되며, 이 페이지의 **사용** 열에는 개체를 바로 사용할 수 있다는 확인 표시가 나타납니다. **SIP 주소** 열에 사용자 로그인 구성에 필요한 주소가 표시됩니다.

12. 도메인에 가입된 컴퓨터에 사용자 로그온하고 도메인의 다른 컴퓨터에 다른 사용자로 로그온합니다.

13. 두 개의 클라이언트 컴퓨터 각각에 Lync 2013을 설치한 다음 두 사용자가 모두 Lync Server 2013에 로그인하고 서로에게 인스턴트 메시지를 보낼 수 있는지 확인합니다.

## 참고 항목

#### 개념

[Lync Server 2013에서 클라이언트 및 장치 배포](lync-server-2013-deploying-clients-and-devices.md)

