---
title: "Oracle パブリッシャーのバックアップと復元 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "復旧 [SQL Server レプリケーション], Oracle パブリッシング"
  - "バックアップ [SQL Server レプリケーション], Oracle パブリッシング"
  - "Oracle パブリッシング [SQL Server レプリケーション], バックアップおよび復元"
  - "復元 [SQL Server レプリケーション], Oracle パブリッシング"
ms.assetid: e5f181d0-cacf-442b-8b7a-202b3cfc358b
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Oracle パブリッシャーのバックアップと復元
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  バックアップと復元を実行する場合は、次のガイドラインに従ってください。  
  
-   パブリッシャーのバックアップ中は、ログ リーダー エージェントを実行したり、パブリッシュされたテーブルでその他のデータベースの処理を実行しないようにします。  
  
-   パブリッシャーとディストリビューターは同時にバックアップします。  
  
-   パブリッシャーまたはディストリビューターを復元する必要がある場合は、すべてのサブスクリプションを再初期化します。  
  
-   バックアップからサブスクライバーを復元するには (サブスクリプションの再初期化は不要)、前回のサブスクリプション データベースのバックアップ完了後にディストリビューション データベースに配信されたトランザクションも使用できる必要があります。 トランザクションが使用できる時間の長さは、ディストリビューションの保有期間の設定によって異なります。 これらの設定については、次を参照してください。 [サブスクリプションの有効期限と非アクティブ化](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)します。  
  
-   データベースを復元した結果、パブリッシャーまたはディストリビューターが同期しなくなった場合は、レプリケーション エージェントによってエラー メッセージが記録されます。 この時点で、関連するパブリケーションとサブスクリプションをすべて削除して再作成する必要があります。  
  
    1.  パブリケーションおよびサブスクリプションの定義のスクリプトを作成します。 詳しくは、「 [Scripting Replication](../../../relational-databases/replication/scripting-replication.md)」をご覧ください。  
  
         パブリッシャーとディストリビューターの状態のバージョン間でパブリケーションの定義が変更された場合は、スクリプトを変更する必要があります。  
  
    2.  パブリケーションとサブスクリプションを削除します。  
  
    3.  手順 1. で作成したスクリプトを実行します。  
  
     パブリッシャーを削除して再構成する必要があります、削除、 **MSSQLSERVERDISTRIBUTOR** パブリック シノニムと構成した Oracle レプリケーション ユーザーを **CASCADE** Oracle パブリッシャーからすべてのレプリケーション オブジェクトを削除するオプションです。  
  
## 参照  
 [レプリケートされたデータベースのバックアップと復元](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [Oracle パブリッシャーの構成](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Oracle パブリッシングの概要](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  