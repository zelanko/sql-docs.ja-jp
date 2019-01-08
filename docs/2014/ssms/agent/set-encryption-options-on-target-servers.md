---
title: 対象サーバーでの暗号化オプションの設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9443319c17c2148284d606aebcad89db38de12eb
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52781474"
---
# <a name="set-encryption-options-on-target-servers"></a>対象サーバーでの暗号化オプションの設定
  マスター サーバーと一部またはすべての対象サーバーの間で SSL (Secure Sockets Layer) 暗号通信の証明書を使用できない場合、これらの間のチャネルを暗号化するには、必要なセキュリティ レベルを使用するように対象サーバーを構成します。  
  
 マスター サーバーと対象サーバーの間の特定の通信チャネルに求められる適切なセキュリティ レベルを構成するには、対象サーバーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのレジストリ サブキー **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\**\<*instance_name*>**\SQLServerAgent\MsxEncryptChannelOptions(REG_DWORD)** を、次のいずれかの値に設定します。 \<*instance_name*> の値は **MSSQL.***n* です。 たとえば、 **MSSQL.1** や **MSSQL.3**となります。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|この対象サーバーとマスター サーバーの間の暗号化を無効にします。 対象サーバーとマスター サーバー間のチャネルのセキュリティを別の手段で保護する場合にこのオプションを選択します。|  
|**1**|この対象サーバーとマスター サーバーの間のみ暗号化を有効にしますが、証明書の検証は必要ありません。|  
|**2**|この対象サーバーとマスター サーバーの間で、完全な SSL 暗号化と証明書の検証を有効にします。 この設定が既定値です。 別の値を選択する具体的な理由がある場合を除いて、この値を変更しないことをお勧めします。|  
  
 **1** または **2** を指定する場合、マスター サーバーと対象サーバーの両方で SSL を有効にしている必要があります。 **2** を指定する場合、マスター サーバーには適切に署名された証明書も必要になります。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>参照  
 [データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
  
