---
title: "サーバーのパブリック権限 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ベスト プラクティス [データベース エンジン]"
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# サーバーのパブリック権限
  このルールでは、public サーバー ロールにサーバー権限があるかどうかを調べます。 サーバー上で作成されたログインは、すべて public サーバー ロールのメンバーです。 この条件が満たされる場合、サーバー上のログインにはすべてサーバー権限が付与されます。  
  
## ベスト プラクティスと推奨事項  
 public サーバー ロールにサーバー権限を付与しないでください。  
  
> [!IMPORTANT]  
>  セットアップの完了後、 **PUBLIC** ロールには、 **専用管理者接続** 以外のすべてのエンドポイントに対する **CONNECT**権限が付与されます。 これは正常な動作です。通常は変更しないでください  (アクセスの制御には、新しいログインの作成時に自動的に付与される **CONNECT SQL** 権限が使用されます)。  
  
### 詳細情報  
 [SQL Server の保護](../../relational-databases/security/securing-sql-server.md)  
  
  