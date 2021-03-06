﻿---
title: 채팅방 관리
TOCTitle: 채팅방 관리
ms:assetid: d4835cf4-cd09-4769-a08e-e92706861b64
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205292(v=OCS.15)
ms:contentKeyID: 49305141
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 채팅방 관리

 

_**마지막으로 수정된 항목:** 2013-02-21_

새 영구 채팅 서버 채팅방을 만들려면

    New-CsPersistentChatRoom -Name Foo1 -PersistentChatPoolFqdn client.contoso.com -Category client.contoso.com\Foo [other parameters]


> [!IMPORTANT]
> 다음 중 하나에 해당하는 경우 -PersistentChatPoolFqdn은 필요하지 않습니다. 
> <UL>
> <LI>
> <P>영구 채팅 서버 풀이 하나만 존재합니다.</P>
> <LI>
> <P>범주에 풀 FQDN을 제공합니다.</P>
> <LI>
> <P>추가하는 채팅방에 풀 FQDN을 제공합니다.</P></LI></UL>



기존 영구 채팅 서버 채팅방을 변경하려면

    Set-CsPersistentChatRoom -Identity testCat -Members @{Add="sip:user1@contoso.com", "CN=container,DC=contoso,DC=com"}
    Set-CsPersistentChatRoom -Identity testCat -Managers @{Add="sip:user2@contoso.com"}
    Set-CsPersistentChatRoom -Identity testCat -Presenters @{Add="sip:user1@contoso.com"}

Windows PowerShell: 구성원, 관리자, 발표자를 동시에 설정할 수 있습니다. 이들은 모두 AllowedMembers의 일부로 추가되거나, 호스트 범주의 DeniedMembers로 제외될 수 있습니다. type=normal인 채팅방에는 발표자를 포함할 수 없습니다.

## 채팅방 만들기, 가져오기, 설정, 지우기 또는 제거

새 채팅방을 만들려면

    New-CsPersistentChatRoom -Name <String> [-PersistentChatPoolFqdn <String>]-Category <String> [-Description <String>] [-Disabled <Switch Parameter>] [-Type <Normal | Auditorium>] [-AddIn <String>] [-Privacy <ChatRoomPrivacy> {Open | Closed | Secret}] [-Invitations <Switch Parameter>]

채팅방을 설정하려면

    Set-CsPersistentChatRoom -Identity <String> [-Name <String>] [-Category <String>] [-Description <String>] [-Disabled <boolean>] [-Type <Normal | Auditorium>] [-AddIn <String>] [-Privacy <ChatRoomPrivacy> {Open | Closed | Secret}] [-Invitations <Enum>] [-Members <PSListModifier<String>>] [-Managers <PSListModifier<String>>] [-Presenters <PSListModifier<String>>] [-Force < Switch Parameter >] [-Confirm <Switch Parameter>][-WhatIf <Switch Parameter>]

채팅방을 가져오려면

    Get-CsPersistentChatRoom -Identity <String>

또는

    Get-CsPersistentChatRoom -filter <String> [-PersistentChatPoolFqdn <String>] [-SearchDescription] [-Member <String>] [-Manager <string>] [-Category <string>] [-Addin <string>] [-Disabled <bool>] [-Privacy <ChatRoomPrivacy> {Open | Closed | Secret}] [-Type <ChatRoomType> {Normal | Auditorium}] [-Invitations <ChatRoomInvitations> {False | Inherit}] [-ChatContentExceedsMB <int>] [-ResultSize <int>]

여기서, –filter는 이름 및 설명만 지원하며 이름/설명이 키워드 문자열과 일치하는 채팅방을 찾는 데 유용합니다. PoolFqdn은 지정된 영구 채팅 서버 풀에서 검색합니다.

채팅방을 지우거나 채팅방의 메시지를 지우려면

    Clear-CsPersistentChatRoom [-Identity] <string> -EndDate <DateTime> [-WhatIf] [-Confirm]  [<CommonParameters>]

또는

    Clear-CsPersistentChatRoom [-Instance] <ChatRoomObject> -EndDate <DateTime> [-WhatIf] [-Confirm] [<CommonParameters>]

채팅방을 제거하려면

    Remove-CsPersistentChatRoom [-Identity] <string> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>]

또는

    Remove-CsPersistentChatRoom [-Instance] <ChatRoomObject> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>]

