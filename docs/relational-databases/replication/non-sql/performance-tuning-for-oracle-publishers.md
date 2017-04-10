---
title: "Oracle パブリッシャーのパフォーマンス チューニング | Microsoft Docs"
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
  - "Oracle パブリッシング [SQL Server レプリケーション], パフォーマンス チューニング"
ms.assetid: 32c0b4ec-c166-45a3-b41e-38a30fd56813
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Oracle パブリッシャーのパフォーマンス チューニング
  Oracle のパブリッシング アーキテクチャがに似ていますが、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリッシング アーキテクチャです。 したがって Oracle レプリケーションのパフォーマンスをチューニングする最初の手順が必要にについては、次の一般的なチューニングの推奨事項 [一般的なレプリケーション パフォーマンスの向上](../../../relational-databases/replication/administration/enhance-general-replication-performance.md)します。  
  
 それに加えて、Oracle パブリッシャーには、パフォーマンスに関連するオプションが 2 つあります。  
  
-   パブリッシング オプションとして、[Oracle (完全)] または [Oracle (ゲートウェイ)] のいずれか適切な方を指定します。  
  
-   パブリッシャーの変更を適切な間隔で処理するようにトランザクション セット ジョブを構成します。  
  
## 適切なパブリッシング オプションの指定  
 [Oracle (ゲートウェイ)] を選択すると、[Oracle (完全)] より高いパフォーマンスが得られますが、このオプションは、複数のトランザクション パブリケーションで同じテーブルをパブリッシュする場合は使用できません。 テーブルを表示できるのは、最大で 1 つのトランザクション パブリケーションと、任意の数のスナップショット パブリケーションになります。 複数のトランザクション パブリケーションで同じテーブルをパブリッシュする必要がある場合は、[Oracle (完全)] を選択します。 このオプションは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターで Oracle パブリッシャーを識別する際に指定します。 詳細については、次を参照してください。 [Oracle データベースからパブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)します。  
  
## トランザクション セット ジョブの構成  
 パブリッシュされた Oracle テーブルに対する変更は、トランザクション セットと呼ばれるグループで処理されます。 トランザクションの一貫性を確保するために、各トランザクション セットはディストリビューション データベースで 1 つのトランザクションとしてコミットされます。 トランザクション セットが大きくなりすぎると、1 つのトランザクションとして効率的に処理できなくなります。  
  
 既定では、トランザクション セットはログ リーダー エージェントによってのみ作成されます。 変更が頻繁に行われているときにログ リーダー エージェントが実行されていなかったり、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターから Oracle パブリッシャーに接続できなかったりすると、トランザクション セットが極端に大きくなる可能性があります。 この問題を防ぐには、ログ リーダー エージェントが実行されていなかったり Oracle パブリッシャーに接続できなかったりしてもトランザクション セットが定期的に作成されるようにします。  
  
 トランザクション セットは、Xactset ジョブ (レプリケーションによってインストールされる Oracle データベース ジョブ) で作成できます。Xactset ジョブは、ログ リーダー エージェントと同じメカニズムを使ってトランザクション セットを作成します。 このジョブが実行されるたびに、新しいトランザクション セットが作成されます。 次にログ リーダー エージェントが実行されたときに、それまでに作成されたトランザクション セットが処理されます。 既存のトランザクション セットがすべて処理された後にまだ保留中の変更がある場合は、ログ リーダー エージェントが 1 つ以上のトランザクション セットを追加で作成して処理します。  
  
 トランザクション セット ジョブを構成するのを参照してください [#40; (&)、Oracle パブリッシャーのトランザクション セット ジョブを構成します。。レプリケーション TRANSACT-SQL プログラミングと #41;](../../../relational-databases/replication/administration/configure the transaction set job for an oracle publisher.md)します。  
  
## 参照  
 [Oracle パブリッシャーの構成](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Oracle パブリッシングの概要](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  