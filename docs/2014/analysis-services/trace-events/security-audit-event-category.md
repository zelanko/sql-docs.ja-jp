---
title: Security Audit イベント カテゴリ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Security Audit event category [SQL Server]
- event classes [Analysis Services], security audit
- security events [Analysis Services]
ms.assetid: 9686a495-68d7-4137-8e30-2655aa519f6c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9d52589fc39376d5dfdfa3f540d3d1d47e89f448
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224242"
---
# <a name="security-audit-event-category"></a>セキュリティ監査イベント カテゴリ
  セキュリティ監査イベント カテゴリには、次の表に示したイベント クラスがあります。  
  
|Event Class|イベント ID|説明|  
|-----------------|--------------|-----------------|  
|Audit Login|1|トレースの開始後に発生したすべての新しい接続イベントを記録します。たとえば、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスを実行しているサーバーとの接続をクライアントが要求するイベントなどが記録されます。|  
|Audit Logout|2|トレースの開始後に発生したすべての新しい接続解除イベントを記録します。たとえば、クライアントが接続解除コマンドを実行するイベントなどが記録されます。|  
|Audit Server Starts and Stops|4|サービスのシャットダウン、起動、一時停止の各利用状況を記録します。|  
|Audit Object Permission Event|18|オブジェクト権限の変更をすべて記録します。|  
|Audit Admin Operations Even|19|バックアップ、復元、同期、アタッチ、デタッチ、イメージ読み込み、およびイメージ保存のためのサーバー操作を記録します。|  
  
 セキュリティ監査の各イベント クラスに関連する列については、「 [Security Audit のデータ列](security-audit-data-columns.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services トレース イベント](analysis-services-trace-events.md)  
  
  
