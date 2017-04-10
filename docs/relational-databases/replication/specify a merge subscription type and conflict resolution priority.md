---
title: "マージ サブスクリプションの種類と競合解決の優先度の指定 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "02/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "マージ レプリケーションの競合解決 [SQL Server レプリケーション], マージ サブスクリプションの競合回避モジュール"
  - "競合回避 [SQL Server レプリケーション]、マージ レプリケーション"
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# マージ サブスクリプションの種類と競合解決の優先度の指定 (SQL Server Management Studio)
  マージ サブスクリプションの種類と競合解決の優先度を指定する、 **サブスクリプションの種類** サブスクリプションの新規作成ウィザードのページです。 このウィザードの使用に関する詳細については、次を参照してください。 [プル サブスクリプションを作成する](../../relational-databases/replication/create-a-pull-subscription.md) と [プッシュ サブスクリプションを作成する](../../relational-databases/replication/create-a-push-subscription.md)です。  
  
 サブスクリプションが作成された後でのサーバー サブスクリプションの種類の優先順位を変更できる、サブスクリプションの種類を変更できません、 **サブスクリプションのプロパティ - \< Publisher>: \< PublicationDatabase>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) 」および「 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)」を参照してください。  
  
### マージ サブスクリプションの種類と競合解決の優先度を指定するには  
  
1.   **サブスクリプションの種類** の新しいサブスクリプション ウィザード、[選択] ページ **クライアント** または **Server** の **サブスクリプションの種類** オプション。  
  
2.  サブスクリプションの種類を選択した場合 **Server**, の値 (0.00 ~ 99.99) を入力しても、 **競合解決の優先度** オプション。  
  
### 競合解決の優先度を変更するには  
  
1.   **サブスクリプションのプロパティ - \< Publisher>: \< PublicationDatabase>** 、パブリッシャー側での値 (0.00 ~ 99.99) を入力、 **優先順位** オプション。  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## 参照  
 [マージ レプリケーションの競合検出および解決の詳細](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  