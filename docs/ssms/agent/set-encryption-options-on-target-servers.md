---
title: "対象サーバーでの暗号化オプションの設定 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d2f91c1117333f037d77d146000cf44ba885e292
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="set-encryption-options-on-target-servers"></a>対象サーバーでの暗号化オプションの設定
マスター サーバーと一部またはすべての対象サーバーの間で SSL (Secure Sockets Layer) 暗号通信の証明書を使用できない場合、これらの間のチャネルを暗号化するには、必要なセキュリティ レベルを使用するように対象サーバーを構成します。  
  
マスター サーバーと対象サーバーの間の特定の通信チャネルに求められる適切なセキュリティ レベルを構成するには、対象サーバーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのレジストリ サブキー **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\**\<*instance_name*>**\SQLServerAgent\MsxEncryptChannelOptions(REG_DWORD)** を、次のいずれかの値に設定します。 \<*instance_name*> の値は **MSSQL.***n* です。 たとえば、 **MSSQL.1** や **MSSQL.3**となります。  
  
|値|説明|  
|---------|---------------|  
|**0**|この対象サーバーとマスター サーバーの間の暗号化を無効にします。 対象サーバーとマスター サーバー間のチャネルのセキュリティを別の手段で保護する場合にこのオプションを選択します。|  
|**1**|この対象サーバーとマスター サーバーの間のみ暗号化を有効にしますが、証明書の検証は必要ありません。|  
|**2**|この対象サーバーとマスター サーバーの間で、完全な SSL 暗号化と証明書の検証を有効にします。 この設定が既定値です。 別の値を選択する具体的な理由がある場合を除いて、この値を変更しないことをお勧めします。|  
  
**1** または **2** を指定する場合、マスター サーバーと対象サーバーの両方で SSL を有効にしている必要があります。 **2** を指定する場合、マスター サーバーには適切に署名された証明書も必要になります。  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry_md.md)]  
  
## <a name="see-also"></a>参照  
[データベース エンジンへの暗号化接続を有効にする方法 (SQL Server 構成マネージャー)](http://msdn.microsoft.com/en-us/e1e55519-97ec-4404-81ef-881da3b42006)  
  
