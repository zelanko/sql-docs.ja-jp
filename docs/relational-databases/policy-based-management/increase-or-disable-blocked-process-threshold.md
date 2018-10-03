---
title: blocked process threshold の増加または無効化 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 523ac3bfe8f1b9f96840cbfe5ca523bf0640cf79
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47717850"
---
# <a name="increase-or-disable-blocked-process-threshold"></a>blocked process threshold の増加または無効化
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このルールでは、blocked process threshold オプションが 0 (無効) に設定されているか、5 (秒) 以上の値に設定されていることを確認します。 blocked process threshold オプションを 1 ～ 4 の値に設定すると、デッドロック モニターが絶えず実行される可能性があります。 1 ～ 4 の値はトラブルシューティングでのみ使用し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービスの協力がない場合は長期間または実稼働環境で使用しないでください。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 この問題を解決するには、blocked process threshold オプションを 5 (秒) 以上の値に設定するか、値を 0 に設定して blocked process threshold を無効にします。 blocked process threshold を `5` 秒に設定するには、次のステートメントを実行します。  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 5 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="for-more-information"></a>詳細情報  
 [blocked process threshold サーバー構成オプション](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
