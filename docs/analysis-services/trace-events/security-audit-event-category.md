---
title: "Security Audit イベント カテゴリ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Security Audit event category [SQL Server]
- event classes [Analysis Services], security audit
- security events [Analysis Services]
ms.assetid: 9686a495-68d7-4137-8e30-2655aa519f6c
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d78568fe6eda8384494fb1e1e064eed707065b38
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="security-audit-event-category"></a>セキュリティ監査イベント カテゴリ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
  
  
