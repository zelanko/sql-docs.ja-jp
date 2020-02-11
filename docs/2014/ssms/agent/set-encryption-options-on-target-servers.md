---
title: ターゲット サーバーでの暗号化オプションの設定 | Microsoft Docs
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
ms.openlocfilehash: b27dd81df572e289d182fdaa637a3af972b3d603
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63244974"
---
# <a name="set-encryption-options-on-target-servers"></a>ターゲット サーバーでの暗号化オプションの設定
  マスター サーバーと一部またはすべてのターゲット サーバーの間で SSL (Secure Sockets Layer) 暗号通信の証明書を使用できない場合、これらの間のチャネルを暗号化するには、必要なセキュリティ レベルを使用するようにターゲット サーバーを構成します。  
  
 特定のマスターサーバー/対象サーバーの通信チャネルに必要な適切なレベルのセキュリティを構成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]には、対象サーバーのエージェントのレジストリサブキー **\\\HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server****>**** \<instance_name \SQLServerAgent\MsxEncryptChannelOptions (REG_DWORD) を次のいずれかの値に設定します。 \< *Instance_name*> の値は**MSSQL です。**_n_。 たとえば、 **MSSQL.1** や **MSSQL.3**となります。  
  
|値|[説明]|  
|-----------|-----------------|  
|**0**|このターゲット サーバーとマスター サーバーの間の暗号化を無効にします。 ターゲット サーバーとマスター サーバー間のチャネルのセキュリティを別の手段で保護する場合にこのオプションを選択します。|  
|**1**|このターゲット サーバーとマスター サーバーの間のみ暗号化を有効にしますが、証明書の検証は必要ありません。|  
|**2**|このターゲット サーバーとマスター サーバーの間で、完全な SSL 暗号化と証明書の検証を有効にします。 これは、既定の設定です。 別の値を選択する具体的な理由がある場合を除いて、この値を変更しないことをお勧めします。|  
  
 
  **1** または **2** を指定する場合、マスター サーバーとターゲット サーバーの両方で SSL を有効にしている必要があります。 
  **2** を指定する場合、マスター サーバーには適切に署名された証明書も必要になります。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>参照  
 [データベースエンジン &#40;SQL Server 構成マネージャーへの暗号化接続を有効にする&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
  
