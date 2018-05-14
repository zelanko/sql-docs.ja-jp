---
title: Security Audit イベント カテゴリ |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8d4524c7c723c48f4acae72178dc58f5a858cc05
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
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
  
  
