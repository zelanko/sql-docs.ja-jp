---
title: "Security Audit イベント カテゴリ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Security Audit event category [SQL Server]
- event classes [Analysis Services], security audit
- security events [Analysis Services]
ms.assetid: 9686a495-68d7-4137-8e30-2655aa519f6c
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bb384601c49088675c25547b3ae7dc21b4510380
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="security-audit-event-category"></a>セキュリティ監査イベント カテゴリ
  セキュリティ監査イベント カテゴリには、次の表に示したイベント クラスがあります。  
  
|Event Class|イベント ID|Description|  
|-----------------|--------------|-----------------|  
|Audit Login|1|トレースの開始後に発生したすべての新しい接続イベントを記録します。たとえば、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスを実行しているサーバーとの接続をクライアントが要求するイベントなどが記録されます。|  
|Audit Logout|2|トレースの開始後に発生したすべての新しい接続解除イベントを記録します。たとえば、クライアントが接続解除コマンドを実行するイベントなどが記録されます。|  
|Audit Server Starts and Stops|4|サービスのシャットダウン、起動、一時停止の各利用状況を記録します。|  
|Audit Object Permission Event|18|オブジェクト権限の変更をすべて記録します。|  
|Audit Admin Operations Even|19|バックアップ、復元、同期、アタッチ、デタッチ、イメージ読み込み、およびイメージ保存のためのサーバー操作を記録します。|  
  
 セキュリティ監査の各イベント クラスに関連する列については、「 [Security Audit のデータ列](../../analysis-services/trace-events/security-audit-data-columns.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services トレース イベント](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  

