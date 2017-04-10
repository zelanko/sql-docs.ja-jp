---
title: "ピア ツー ピア トポロジの管理 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "トランザクション レプリケーション、ピアツーピア レプリケーション"
ms.assetid: 4d0fa941-f9ea-4a14-aed9-34df593fc6f2
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# ピア ツー ピア トポロジの管理 (レプリケーション Transact-SQL プログラミング)
  ピア ツー ピア トポロジの管理は通常のトランザクション レプリケーション トポロジの管理と似ていますが、特別な考慮が必要な部分が数多くあります。 ピア ツー ピア トポロジの管理の主な相違点がいくつかの変更があるシステムを必要と *休止*します。 システムを停止するときには、すべてのノードでパブリッシュ済みテーブルの利用を停止し、各ノードが他のすべてのノードの変更を受け取っていることを確認します。 詳細については、次を参照してください。 [休止レプリケーション トポロジと #40 です。レプリケーション TRANSACT-SQL プログラミングと #41;](../../../relational-databases/replication/administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)します。  
  
> [!NOTE]  
>  ピア ツー ピア トポロジでは、ディストリビューターはプル サブスクライバーより前の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のバージョンを使用できません。  
  
### 既存の構成にアーティクルを追加するには  
  
1.  システムを停止します。  
  
2.  トポロジ内の各ノードでディストリビューション エージェントを停止します。 詳細については、次を参照してください。 [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) または [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)します。  
  
3.  CREATE TABLE ステートメントを実行して、トポロジ内の各ノードに新しいテーブルを追加します。  
  
4.  [bcp ユーティリティ](../../../tools/bcp-utility.md)を使用して、全ノードの新しいテーブルにデータを一括コピーします。  
  
5.  実行 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) 、トポロジ内の各ノードに新しいアーティクルを作成します。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
    > [!NOTE]  
    >  後 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) が実行すると、レプリケーションを自動的に追加資料トポロジ内のサブスクリプション。  
  
6.  トポロジ内の各ノードでディストリビューション エージェントを再起動します。  
  
### パブリケーション データベースのスキーマを変更するには  
  
1.  システムを停止します。  
  
2.  データ定義言語 (DDL) ステートメントを実行して、パブリッシュ済みテーブルのスキーマを変更します。 サポートされるスキーマ変更の詳細については、次を参照してください。 [パブリケーション データベースでスキーマ変更を行う](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)します。  
  
3.  パブリッシュ済みテーブルの利用を再開する前に、再びシステムを停止します。 これにより、新しいデータ変更がレプリケートされる前に、すべてのノードでスキーマ変更が受け取られます。  
  
## 例  
 次の例は、2 つのノードを持つ既存のピア ツー ピア レプリケーション トポロジに新しいテーブル アーティクルを追加する方法を示しています。  
  
 [!code-sql[HowTo#sp_addp2particle_createtables](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_1.sql)]  
  
 [!code-sql[HowTo#sp_addp2particle_cmdline](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_2.sql)]  
  
 [!code-sql[HowTo#sp_addp2particle_createarticle](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_3.sql)]  
  
## 参照  
 [管理と #40 です。レプリケーションと #41 です。](../../../relational-databases/replication/administration/administration-replication.md)   
 [SQL Server データベースのバックアップと復元](../../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [ピア ツー ピア トランザクション レプリケーション](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  