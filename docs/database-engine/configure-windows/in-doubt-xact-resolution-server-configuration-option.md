---
title: "in-doubt xact resolution サーバー構成オプション | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- distributed transactions [SQL Server], unresolved transactions
- unresolved transactions
- in-doubt xact resolution option
ms.assetid: 3426fd32-cad2-4f2f-8ca9-e0296cc12703
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3c3676d0c6b240bce2c7523cb2dceba90813fa3c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="in-doubt-xact-resolution-server-configuration-option"></a>in-doubt xact resolution サーバー構成オプション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **in-doubt xact resolution** オプションは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) で解決できないトランザクションの既定の結果を制御する場合に使用します。 トランザクションを解決できない原因は、復旧時の MS DTC のダウン タイムまたは状態が不明なトランザクション結果に関連している場合があります。  
  
 次の表は、状態が不明なトランザクションの解決について考えられる結果の値を示しています。  
  
|結果の値|説明|  
|-------------------|-----------------|  
|0|推測しません。 状態が不明なトランザクションを MS DTC で解決できない場合、復旧は失敗します。|  
|1|コミットを推測します。 MS DTC の状態が不明なトランザクションは、コミットされたと見なされます。|  
|2|中断を推測します。 MS DTC の状態が不明なトランザクションは、中断されたと見なされます。|  
  
 次の例のように、長時間にわたるダウン タイムの可能性を最低限に抑えるために、管理者はコミットまたは中断を推測するようにこのオプションを設定できます。  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 2 -– presume abort  
GO  
RECONFIGURE  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 また、次の例のように、DTC エラーを認識するために、既定値 (推測なし) のままにして復旧を失敗させることができます。  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 1 -– presume commit  
GO  
reconfigure  
GO  
ALTER DATABASE pubs SET ONLINE –- run recovery again  
GO  
sp_configure 'in-doubt xact resolution', 0 –- back to no assumptions  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 **in-doubt xact resolution** は拡張オプションです。 **sp_configure** システム ストアド プロシージャを使用して **in-doubt xact resolution** の設定を変更するには、 **show advanced options** を 1 に設定する必要があります。 新しい設定は、サーバーを再起動しなくてもすぐに有効になります。  
  
> [!NOTE]  
>  分散トランザクションに関係するすべての [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで、このオプションを同じように構成すると、データの不整合を防ぐことができます。  
  
## <a name="see-also"></a>参照  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  

