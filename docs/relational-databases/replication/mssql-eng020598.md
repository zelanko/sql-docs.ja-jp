---
title: "MSSQL_ENG020598 | Microsoft Docs"
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
  - "MSSQL_ENG020598 エラー"
ms.assetid: 1c3032f2-23d1-4ead-94ee-16ac4d75cd0c
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG020598
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|20598|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|レプリケートされたコマンドを適用しているときに、サブスクライバーで行が見つかりませんでした。|  
  
## 説明  
 このエラーは、トランザクション レプリケーションで、ディストリビューション エージェントがサブスクライバーの行を更新しようとしたときに、行が削除されていたり、行の主キーが変更されている場合に発生します。 既定では、変更はパブリッシャーには反映されないため、トランザクション パブリケーションに対するサブスクライバーは読み取り専用として処理されます。 トランザクション レプリケーションでは、更新可能なサブスクリプションまたはピア ツー ピア レプリケーションが使用されている場合にのみ、ユーザーの変更をサブスクライバーで行う必要があります。 これらのオプションについては、次を参照してください。 [トランザクション レプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md) と [ピア ツー ピア トランザクション レプリケーション](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)します。  
  
## ユーザーの操作  
 **この問題を解決するには、次のようにします。**  
  
1.  パラメーターを指定する場合は、エラーの原因を特定している間に、レプリケーションを続行する必要があります、 **-skiperrors 20598** 、ディストリビューション エージェントです。 このパラメーターを指定すると、エージェントはエラー 20598 の原因となった変更をスキップし、他の変更をレプリケートできるようになります。  
  
2.  削除されている行、またはパブリッシャーの対応する行とは異なる主キーを持っているサブスクライバーの行を特定します。 使用することができます、 [tablediff ユーティリティ](../../tools/tablediff-utility.md) のどの行が、パブリケーションおよびサブスクリプション データベースでは異なるかを判断します。 レプリケートされたデータベースでこのユーティリティを使用する方法については、次を参照してください [相違点と #40; のレプリケートされたテーブルの比較。レプリケーション プログラミングと #41;](../../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md)します。  
  
3.  サブスクライバーを使用して、行を修正、 **tablediff** ユーティリティまたは別の方法です。  
  
4.  (省略可能)削除、 **-skiperrors** パラメーター。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  