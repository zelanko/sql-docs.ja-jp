---
title: "blocked process threshold の増加または無効化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ベスト プラクティス [データベース エンジン]"
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# blocked process threshold の増加または無効化
  このルールでは、blocked process threshold オプションが 0 (無効) に設定されているか、5 (秒) 以上の値に設定されていることを確認します。 blocked process threshold オプションを 1 ～ 4 の値に設定すると、デッドロック モニターが絶えず実行される可能性があります。 1 ～ 4 の値はトラブルシューティングでのみ使用し、[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービスの協力がない場合は長期間または実稼働環境で使用しないでください。  
  
## ベスト プラクティスと推奨事項  
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
  
## 詳細情報  
 [blocked process threshold サーバー構成オプション](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md)  
  
## 参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  