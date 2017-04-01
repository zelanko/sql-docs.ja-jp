---
title: "[ディストリビューション データベースのプロパティ] | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.configdistwizard.distdbproperties.f1"
helpviewer_keywords: 
  - "[ディストリビューション データベースのプロパティ] ダイアログ ボックス"
ms.assetid: 0f404ab9-1237-4936-8df5-888baab6a245
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# [ディストリビューション データベースのプロパティ]
   **ディストリビューション データベースのプロパティ** ダイアログ ボックスでさまざまなプロパティを表示して、データベースの履歴の保有期間とトランザクションの保有期間を設定できます。  
  
## オプション  
 **名前**  
 ディストリビューション データベースの名前です。既定の名前は "distribution" です (読み取り専用)。  
  
 **[ファイルの場所]**  
 データベース ファイルとログ ファイルの場所です (読み取り専用)。  
  
 **[トランザクションの保有期間]**  
 ディストリビューション保有期間とも呼ばれます。 トランザクション レプリケーションで格納されるトランザクションの期間の長さです。 詳しくは、「 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)」をご覧ください。  
  
 **[履歴の保有期間]**  
 すべての種類のレプリケーションで格納される、履歴メタデータの期間の長さです。  
  
 **[キュー リーダー エージェントのセキュリティ]**  
 キュー リーダー エージェントは、トランザクション レプリケーションのキュー更新サブスクリプションで使用されます。 選択した場合、キュー リーダー エージェントが自動的に作成 **更新サブスクリプションを含むトランザクション パブリケーション** 上、 **パブリケーションの種類** パブリケーションの新規作成ウィザードのページです。 クリックして **セキュリティの設定.** アカウントを変更する、エージェントの実行し、は、ディストリビューターに接続します。  
  
 キュー リーダー エージェントを選択して作成することもできます。 **キュー リーダー エージェントを作成する** (このオプションは、エージェントが既に作成されている場合は無効)、このページにします。  
  
 キュー リーダー エージェントのその他の接続情報は、次の 2 つの場所で指定されます。  
  
-   エージェントで指定された資格情報を使用してパブリッシャーに接続する、 **パブリッシャーのプロパティ** から利用可能なダイアログ ボックス、 **パブリッシャー** のページ、 **ディストリビューターのプロパティ** ] ダイアログ ボックス。  
  
-   サブスクリプションの新規作成ウィザードの [ディストリビューション エージェント]。エージェントは、ここで指定された資格情報を使用してサブスクライバーに接続します。  
  
 詳細については、次を参照してください。  \\[レプリケーション エージェントのセキュリティ モデル](../Topic/Replication%20Agent%20Security%20Model.md)します。  
  
## 参照  
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  