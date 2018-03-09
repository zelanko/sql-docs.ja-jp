---
title: "SMO and DMO XPs サーバー構成オプション | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
caps.latest.revision: "15"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f1f892536e56f791c74ffbe6db1e9245caa2f08a
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a>SMO and DMO XPs サーバー構成オプション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  このサーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) の拡張ストアド プロシージャを使用するには、SMO and DMO XPs オプションを使用します。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]の DMO は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で削除されました。  
  
 次の表に、このオプションで使用可能な値を示します。  
  
|ReplTest1|意味|  
|-----------|-------------|  
|0|SMO 拡張ストアド プロシージャ (XP) を使用できません。|  
|@shouldalert|SMO 拡張ストアド プロシージャ (XP) を使用できます。 これは既定値です。|  
  
 この設定はすぐに有効になります。  
  
## <a name="examples"></a>使用例  
 次の例では、SMO の拡張ストアド プロシージャを有効にします。  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server 管理オブジェクト &#40;SMO&#41; プログラミング ガイド](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
