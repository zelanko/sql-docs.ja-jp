---
title: "MSSQL_ENG014157 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014157 エラー"
ms.assetid: 1a0890cf-d977-43e0-a2ba-9c5ff1a8f856
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# MSSQL_ENG014157
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|14157|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|サブスクライバー '%s' によって作成された、パブリケーション '%s' に対するサブスクリプションは、有効期限が切れたので削除されました。|  
  
## 説明  
 サブスクライバーは、パブリケーションの保有期間で指定された時間内にパブリッシャーと同期する必要があります。 サブスクライバーがこの期間内に同期しないと、サブスクリプションの有効期限が切れます。 詳しくは、「 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)」をご覧ください。  
  
## ユーザーの操作  
 サブスクライバーがデータ変更の受信を再び開始するには、サブスクリプションを再作成して初期化する必要があります。  
  
-   サブスクリプションを作成する方法の詳細については、次を参照してください。 [パブリケーションをサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)します。  
  
-   サブスクリプションの初期化方法の詳細については、次を参照してください。 [サブスクリプションを初期化](../../relational-databases/replication/initialize-a-subscription.md)します。  
  
 使用することができます、サブスクリプション データベースに、パブリッシャーと同期されていない変更が含まれている場合、 [tablediff ユーティリティ](../../tools/tablediff-utility.md) のどの行が、パブリケーションおよびサブスクリプション データベースでは異なるかを判断します。  
  
 サブスクリプションの有効期限が切れないように、パブリケーションの保有期間を長くすることができます。 保有期間に高い値を設定すると、保存されるデータとメタデータの量が増えてパフォーマンスに影響するため注意が必要です。 詳しくは、「 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)」をご覧ください。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  