---
title: "スナップショット レプリケーションおよびトランザクション レプリケーションのバックアップと復元の方式 | Microsoft Docs"
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
  - "バックアップ [SQL Server レプリケーション], スナップショット レプリケーション"
  - "復元 [SQL Server レプリケーション], トランザクション レプリケーション"
  - "スナップショット レプリケーション [SQL Server], バックアップと復元"
  - "復元 [SQL Server レプリケーション], スナップショット レプリケーション"
  - "復旧 [SQL Server レプリケーション], トランザクション レプリケーション"
  - "トランザクション レプリケーション, バックアップと復元"
  - "復旧 [SQL Server レプリケーション], スナップショット レプリケーション"
  - "sync with backup [SQL Server レプリケーション]"
  - "バックアップ [SQL Server レプリケーション], トランザクション レプリケーション"
ms.assetid: a8afcdbc-55db-4916-a219-19454f561f9e
caps.latest.revision: 59
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 59
---
# スナップショット レプリケーションおよびトランザクション レプリケーションのバックアップと復元の方式
  スナップショット レプリケーションおよびトランザクション レプリケーションのバックアップと復元の方式を計画する場合には、以下の 3 点を考慮する必要があります。  
  
-   バックアップ対象のデータベース  
  
-   トランザクション レプリケーションのバックアップ設定  
  
-   データベースを復元するために必要な手順。 この手順は、レプリケーションの種類と選択したオプションによって異なります。  
  
 このトピックでは、これらの各項目について、以下の 3 つのセクションで説明します。 Oracle パブリッシングのバックアップと復元については、次を参照してください。 [Oracle パブリッシャーのバックアップと復元](../../../relational-databases/replication/non-sql/backup-and-restore-for-oracle-publishers.md)します。  
  
## データベースのバックアップ  
 スナップショット レプリケーションおよびトランザクション レプリケーションの場合は、以下のデータベースを定期的にバックアップする必要があります。  
  
-   パブリッシャーにあるパブリケーション データベース  
  
-   ディストリビューターにあるディストリビューション データベース  
  
-   サブスクライバーにあるサブスクリプション データベース  
  
-   パブリッシャー、ディストリビューター、およびすべてのサブスクライバーにある **master** および **msdb** システム データベース。 これらのデータベースは、相互に関連するレプリケーション データベースとして、同時にバックアップする必要があります。 たとえば、パブリッシャーでパブリケーション データベースをバックアップするときに、 **master** および **msdb** データベースも同時にバックアップします。 パブリケーション データベースが復元されるときに、 **master** および **msdb** データベースのレプリケーションの構成と設定が、パブリケーション データベースと一致していることを確認します。  
  
 定期的なログ バックアップを実行する場合は、レプリケーション関連の変更をログ バックアップでキャプチャする必要があります。 ログ バックアップを実行しない場合は、レプリケーションに関連する設定を変更するたびに、バックアップを実行する必要があります。 詳細については、「 [Common Actions Requiring an Updated Backup](../../../relational-databases/replication/administration/common-actions-requiring-an-updated-backup.md)」を参照してください。  
  
## トランザクション レプリケーションのバックアップ設定  
 トランザクション レプリケーションには " **sync with backup** " オプションが用意されており、ディストリビューション データベースおよびパブリケーション データベースで設定できます。  
  
-   ディストリビューション データベースでは、常にこのオプションを設定することをお勧めします。  
  
     ディストリビューション データベースでこのオプションを設定すると、パブリケーション データベースのログに記録されたトランザクションは、ディストリビューション データベース内のバックアップが終了するまで切り捨てられることはありません。 ディストリビューション データベースは前回のバックアップに復元できます。失われたトランザクションは、パブリケーション データベースからディストリビューション データベースに配信されます。 レプリケーションは影響を受けることなく継続されます。  
  
     ディストリビューション データベースでこのオプションを設定しても、レプリケーションの待機時間には影響しません。 ただし、ディストリビューション データベース内の対応するトランザクションがバックアップされるまで、パブリケーション データベースでのログの切り捨てが遅延されます  (この結果、パブリケーション データベースのトランザクション ログのサイズが増加する可能性があります)。  
  
-   アプリケーションがレプリケーションの待機時間の延長を許容できる場合は、パブリケーション データベースでこのオプションを設定することをお勧めします。  
  
     パブリケーション データベースでこのオプションを設定すると、パブリケーション データベースでのバックアップが終了するまで、トランザクションがディストリビューション データベースに配信されることはなくなります。 その後、パブリッシャーでパブリケーション データベースを前回のバックアップに復元できます。復元されたパブリケーション データベースにないトランザクションが、ディストリビューション データベースに存在する可能性は一切ありません。  
  
     パブリッシャーでのバックアップが終了するまでの間、トランザクションがディストリビューション データベースに配信されなくなるため、レプリケーションの待機時間とスループットが影響を受けます。 たとえば、トランザクション ログが 5 分ごとにバックアップされる場合、パブリッシャーでトランザクションがコミットされてから、パブリッシャーからディストリビューション データベース、その後サブスクライバーにトランザクションが配信されるまでの間に、さらに 5 分間の待機時間が発生します。  
  
    > [!NOTE]  
    >  " **sync with backup** " オプションを設定すると、パブリケーション データベースとディストリビューション データベースの一貫性が確保されますが、データの損失が発生しなくなるわけではありません。 たとえば、トランザクション ログが見つからない場合、トランザクション ログの前回のバックアップ以降にコミットされたトランザクションを、パブリケーション データベースまたはディストリビューション データベースで利用することはできません。 これは、レプリケートされていないデータベースと同様の動作です。  
  
 **"sync with backup" オプションを設定するには**  
  
-   レプリケーション [!INCLUDE[tsql](../../../includes/tsql-md.md)] プログラミング: [#40; (&)、トランザクション レプリケーションの連携バックアップを有効にします。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../../relational-databases/replication/administration/enable coordinated backups for transactional replication.md)  
  
## レプリケーションに関連するデータベースの復元  
 最新のバックアップが利用可能で適切な手順が実行された場合、レプリケーション トポロジ内のすべてのデータベースを復元できます。 パブリケーション データベースの復元手順は、使用するレプリケーションの種類とオプションによって異なります。ただし、パブリケーション データベース以外のデータベースの復元手順は、レプリケーションの種類とオプションに依存しません。  
  
 レプリケーションでは、レプリケートされたデータベースをバックアップ作成元のサーバーおよびデータベースに復元する操作がサポートされます。 レプリケートされたデータベースのバックアップを別のサーバーまたはデータベースに復元する場合は、レプリケーションの設定は保存できません。 この場合、バックアップの復元後にすべてのパブリケーションおよびサブスクリプションを再作成する必要があります。  
  
### パブリッシャー  
 以下の種類のレプリケーションについては、復元手順が用意されています。  
  
-   スナップショット レプリケーション  
  
-   読み取り専用トランザクション レプリケーション  
  
-   更新サブスクリプションを使用するトランザクション レプリケーション  
  
-   ピア ツー ピア トランザクション レプリケーション  
  
 **msdb** データベースおよび **master** データベースの復元方法についてもこのセクションで説明しますが、上記の 4 種類のレプリケーションについてはすべて同じ方法です。  
  
#### パブリケーション データベース : スナップショット レプリケーション  
  
1.  パブリケーション データベースの最新バックアップを復元します。 手順 2 に進みます。  
  
2.  すべてのパブリケーションおよびサブスクリプションに対する最新の構成がパブリケーション データベースのバックアップに含まれていますか。 答えが「はい」の場合、復元は完了です。 「いいえ」の場合は、手順 3. に進みます。  
  
3.  パブリッシャー、ディストリビューター、およびサブスクライバーで、レプリケーション構成を削除した後、再作成を行います。 復元が完了します。  
  
     レプリケーションを削除する方法の詳細については、次を参照してください。 [sp_removedbreplication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)します。  
  
#### パブリケーション データベース : 読み取り専用トランザクション レプリケーション  
  
1.  パブリケーション データベースの最新バックアップを復元します。 手順 2 に進みます。  
  
2.  障害の発生前に、パブリケーション データベースで " **sync with backup** " 設定が有効になっていましたか。 答えが「はい」の場合は、手順 3 に進みます。「いいえ」の場合は、手順 5 に進みます。  
  
     設定が有効の場合、 `SELECT DATABASEPROPERTYEX('<PublicationDatabaseName>', 'IsSyncWithBackup')` クエリが "1" を返します。  
  
3.  復元されたバックアップは完全かつ最新ですか。 すべてのパブリケーションおよびサブスクリプションに対する最新の構成がこのバックアップに含まれていますか。 答えが「はい」の場合、復元は完了です。 「いいえ」の場合は、手順 4 に進みます。  
  
4.  復元されたパブリケーション データベースの構成情報が最新ではありません。 このため、サブスクライバーで未実行のコマンドがすべてディストリビューション データベースに存在することを確認し、レプリケーション構成の削除と再作成を行う必要があります。  
  
    1.  すべてのサブスクライバーがディストリビューション データベース内の未実行のコマンドと同期するまで、ディストリビューション エージェントを実行します。 使用してすべてのコマンドがサブスクライバーに配信されたことを確認、 **[未配布のコマンド** タブまたは [レプリケーション モニターでクエリを実行して、 [MSdistribution_status](../../../relational-databases/system-views/msdistribution-status-transact-sql.md) ディストリビューション データベースで表示します。 手順 b. に進みます。  
  
         ディストリビューション エージェントを実行する方法の詳細については、次を参照してください。 [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)します。  
  
         コマンドを確認する方法の詳細については、次を参照してください [ビューのレプリケートされたコマンドとディストリビューション データベースと #40; でのその他の情報。レプリケーション TRANSACT-SQL プログラミングと #41;](../../../relational-databases/replication/monitor/view replicated commands and information in distribution database.md)  [情報を表示し、サブスクリプションと #40; に関連付けられているエージェントのタスクを実行レプリケーション モニターと #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)します。  
  
    2.  パブリッシャー、ディストリビューター、およびサブスクライバーで、レプリケーション構成を削除した後、再作成を行います。 サブスクリプションを再作成するときには、サブスクライバーにデータが格納済みであることを指定します。 復元が完了します。  
  
         レプリケーションを削除する方法の詳細については、次を参照してください。 [sp_removedbreplication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)します。  
  
         サブスクライバーにデータが格納済みであることを指定する方法の詳細については、「 [Initialize a Subscription Manually](../../../relational-databases/replication/initialize-a-subscription-manually.md)」を参照してください。  
  
5.  パブリケーション データベースで " **sync with backup** " オプションが設定されていませんでした。 このため、復元されたバックアップに含まれていないトランザクションが、ディストリビューターまたはサブスクライバーに配信された可能性があります。 サブスクライバーで未実行のコマンドがすべてディストリビューション データベースに存在することを確認し、復元されたバックアップに含まれないすべてのトランザクションをパブリケーション データベースに手動で適用する必要があります。  
  
    > [!IMPORTANT]  
    >  この処理を実行することによって、復元対象のパブリッシュされたテーブルを、バックアップから復元されたパブリッシュされていないテーブルよりも新しい状態にすることができます。  
  
    1.  すべてのサブスクライバーがディストリビューション データベース内の未実行のコマンドと同期するまで、ディストリビューション エージェントを実行します。 使用してすべてのコマンドがサブスクライバーに配信されたことを確認、 **[未配布のコマンド** タブまたは [レプリケーション モニターでクエリを実行して、 [MSdistribution_status](../../../relational-databases/system-views/msdistribution-status-transact-sql.md) ディストリビューション データベースで表示します。 手順 b. に進みます。  
  
         ディストリビューション エージェントを実行する方法の詳細については、次を参照してください。 [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)します。  
  
         コマンドを確認する方法の詳細については、次を参照してください [ビューのレプリケートされたコマンドとディストリビューション データベースと #40; でのその他の情報。レプリケーション TRANSACT-SQL プログラミングと #41;](../../../relational-databases/replication/monitor/view replicated commands and information in distribution database.md)  [情報を表示し、サブスクリプションと #40; に関連付けられているエージェントのタスクを実行レプリケーション モニターと #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)します。  
  
    2.  [tablediff ユーティリティ](../../../tools/tablediff-utility.md) またはその他のツールを使用して、パブリッシャーとサブスクライバーを手動で同期します。 これにより、パブリケーション データベースのバックアップに含まれていなかったサブスクリプション データベースのデータを復旧できます。 手順 c. に進みます。  
  
         詳細については、 **tablediff** ユーティリティを参照してください [相違点と #40; のレプリケートされたテーブルの比較レプリケーション プログラミングと #41;](../../../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md)します。  
  
    3.  復元されたバックアップは完全かつ最新ですか。 すべてのパブリケーションおよびサブスクリプションに対する最新の構成がこのバックアップに含まれていますか。 実行する場合は、実行、 [sp_replrestart](../../../relational-databases/system-stored-procedures/sp-replrestart-transact-sql.md) ストアド プロシージャをディストリビューターのメタデータを持つパブリッシャーのメタデータを再同期します。 復元が完了します。 答えが「いいえ」の場合は、手順 d. に進みます。  
  
    4.  パブリッシャー、ディストリビューター、およびサブスクライバーで、レプリケーション構成を削除した後、再作成を行います。 サブスクリプションを再作成するときには、サブスクライバーにデータが格納済みであることを指定します。 復元が完了します。  
  
         レプリケーションを削除する方法の詳細については、次を参照してください。 [sp_removedbreplication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)します。  
  
         サブスクライバーにデータが格納済みであることを指定する方法の詳細については、「 [Initialize a Subscription Manually](../../../relational-databases/replication/initialize-a-subscription-manually.md)」を参照してください。  
  
#### パブリケーション データベース : 更新サブスクリプションを使用するトランザクション レプリケーション  
  
1.  パブリケーション データベースの最新バックアップを復元します。 手順 2 に進みます。  
  
2.  すべてのサブスクライバーがディストリビューション データベース内の未実行のコマンドと同期するまで、ディストリビューション エージェントを実行します。 使用してすべてのコマンドがサブスクライバーに配信されたことを確認、 **[未配布のコマンド** タブまたは [レプリケーション モニターでクエリを実行して、 [MSdistribution_status](../../../relational-databases/system-views/msdistribution-status-transact-sql.md) ディストリビューション データベースで表示します。 手順 3. に進みます。  
  
     ディストリビューション エージェントを実行する方法の詳細については、次を参照してください。 [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)します。  
  
     コマンドを確認する方法の詳細については、次を参照してください [ビューのレプリケートされたコマンドとディストリビューション データベースと #40; でのその他の情報。レプリケーション TRANSACT-SQL プログラミングと #41;](../../../relational-databases/replication/monitor/view replicated commands and information in distribution database.md)  [情報を表示し、サブスクリプションと #40; に関連付けられているエージェントのタスクを実行レプリケーション モニターと #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)します。  
  
3.  使用している場合キュー更新サブスクリプションを各サブスクライバーに接続し、すべての行を削除、 [MSreplication_queue & #40 です。Transact SQL と #41;](../../../relational-databases/system-tables/msreplication-queue-transact-sql.md) サブスクリプション データベース内のテーブル。 手順 4 に進みます。  
  
    > [!NOTE]  
    >  キュー更新サブスクリプションおよび ID 列を含むテーブルを使用している場合は、復元後に正しい ID 範囲が割り当てられていることを確認する必要があります。 詳細については、次を参照してください。 [Id 列のレプリケート](../../../relational-databases/replication/publish/replicate-identity-columns.md)します。  
  
4.  サブスクライバーで未実行のコマンドがすべてディストリビューション データベースに存在することを確認し、復元されたバックアップに含まれないすべてのトランザクションをパブリケーション データベースに手動で適用する必要があります。  
  
    > [!IMPORTANT]  
    >  この処理を実行することによって、復元対象のパブリッシュされたテーブルを、バックアップから復元されたパブリッシュされていないテーブルよりも新しい状態にすることができます。  
  
    1.  すべてのサブスクライバーがディストリビューション データベース内の未実行のコマンドと同期するまで、ディストリビューション エージェントを実行します。 レプリケーション モニターを使用するか、クエリを実行して、すべてのコマンドがサブスクライバーに配信されたことを確認、 [MSdistribution_status](../../../relational-databases/system-views/msdistribution-status-transact-sql.md) ディストリビューション データベースで表示します。 手順 b. に進みます。  
  
    2.   [tablediff Utility](../../../tools/tablediff-utility.md) またはその他のツールを使用して、パブリッシャーとサブスクライバーを手動で同期します。 これにより、パブリケーション データベースのバックアップに含まれていなかったサブスクリプション データベースのデータを復旧できます。 手順 c. に進みます。  
  
         詳細については、 **tablediff** ユーティリティを参照してください [相違点と #40; のレプリケートされたテーブルの比較レプリケーション プログラミングと #41;](../../../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md)します。  
  
    3.  復元されたバックアップは完全かつ最新ですか。 すべてのパブリケーションおよびサブスクリプションに対する最新の構成がこのバックアップに含まれていますか。 実行する場合は、実行、 [sp_replrestart](../../../relational-databases/system-stored-procedures/sp-replrestart-transact-sql.md) ストアド プロシージャをディストリビューターのメタデータを持つパブリッシャーのメタデータを再同期します。 復元が完了します。 答えが「いいえ」の場合は、手順 d. に進みます。  
  
    4.  パブリッシャー、ディストリビューター、およびサブスクライバーで、レプリケーション構成を削除した後、再作成を行います。 サブスクリプションを再作成するときには、サブスクライバーにデータが格納済みであることを指定します。 復元が完了します。  
  
         レプリケーションを削除する方法の詳細については、次を参照してください。 と [sp_removedbreplication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)します。  
  
         サブスクライバーにデータが格納済みであることを指定する方法の詳細については、「 [Initialize a Subscription Manually](../../../relational-databases/replication/initialize-a-subscription-manually.md)」を参照してください。  
  
#### パブリケーション データベース : ピア ツー ピア トランザクション レプリケーション  
 次の手順では、パブリケーション データベースで **A**, 、**B**, 、および **C** 、ピア ツー ピア トランザクション レプリケーション トポロジにします。 データベース **A** およびデータベース **C** はオンラインで正常に動作しています。データベース **B** は復元対象のデータベースです。 ここで説明する処理、特に手順 7、10、および 11 は、ピア ツー ピア トポロジにノードを追加するために必要な処理とよく似ています。 これらの手順を最も簡単に実行する方法は、ピア ツー ピア トポロジ構成ウィザードを使用することです。ただし、ストアド プロシージャも使用できます。  
  
1.  サブスクリプション データベースを同期するディストリビューション エージェントを実行 **A** と **C**します。手順 2 に進みます。  
  
     ディストリビューション エージェントを実行する方法の詳細については、次を参照してください。 [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)します。  
  
2.  ディストリビューション データベースにある場合 **B** 使用は引き続き使用でき、データベース間のサブスクリプションを同期するディストリビューション エージェントを実行 **B** と **A** 、データベース、および B と **C**します。手順 3. に進みます。  
  
3.  メタデータを削除して、配布からをデータベースにある **B** を実行すると、 [sp_removedistpublisherdbreplication](../../../relational-databases/system-stored-procedures/sp-removedistpublisherdbreplication-transact-sql.md) のディストリビューション データベースで **B**します。手順 4 に進みます。  
  
4.  データベースで **A** と **C**, 、データベースのパブリケーションに対するサブスクリプションを削除 **B**します。手順 5 に進みます。  
  
     サブスクリプションを削除する方法の詳細については、「 [Subscribe to Publications](../../../relational-databases/replication/subscribe-to-publications.md)」を参照してください。  
  
5.  ログのバックアップまたはデータベースの完全バックアップを実行 **A**します。手順 6 に進みます。  
  
6.  データベースのバックアップを復元 **A** データベースで **B**します。データベース **B** データベースからのデータが **A**, が、レプリケーションの構成ではありません。 別のサーバーにバックアップを復元するときにレプリケーションは削除されます。そのため、レプリケーションは、データベースから削除されている **B**します。手順 7 に進みます。  
  
7.  データベースでパブリケーションを再作成 **B**, 、データベース間のサブスクリプションを再作成して **A** と **B**します。(サブスクリプション データベースが関係する **C** 後の段階で処理されます。)。  
  
    1.  データベースでパブリケーションを再作成 **B**します。手順 b. に進みます。  
  
    2.  データベースでサブスクリプションを再作成 **B** データベースのパブリケーションに対する **A**, 、バックアップを含む、サブスクリプションを初期化することを指定する (値の **バックアップを使用して初期化** の **@sync_type** のパラメーター [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md))。 手順 c. に進みます。  
  
    3.  データベースでサブスクリプションを再作成 **A** データベースのパブリケーションに対する **B**, 、サブスクライバーがデータを既に持っているを指定する (値の **レプリケーションのサポートのみ** の **@sync_type** のパラメーター [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md))。 手順 8 に進みます。  
  
8.  サブスクリプション データベースを同期するディストリビューション エージェントを実行 **A** と **B**します。パブリッシュされたテーブルに ID 列がある場合は、手順 9. に進みます。 それ以外の場合は、手順 10 に進みます。  
  
9. 復元後、データベース内の各テーブル用に割り当てた id 範囲 **A** データベース内でも使用されます **B**します。確認して、復元されたデータベース **B** 障害が発生したデータベースからすべての変更を受信 **B** が伝達されたデータベースに **A** とデータベース **C**; 各テーブルの id 範囲を再シードされます。  
  
    1.  実行 [sp_requestpeerresponse](../../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) データベースで **B** 出力パラメーターを取得および **@request_id**します。 手順 b. に進みます。  
  
    2.  既定では、ディストリビューション エージェントが連続的に実行されるように設定されているため、すべてのノードに自動的にトークンが送信されます。 ディストリビューション エージェントが連続モードで実行されていない場合は、エージェントを実行します。 詳細については、次を参照してください。 [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) または [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)します。 手順 c. に進みます。  
  
    3.  実行 [sp_helppeerresponses](../../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md), 、提供する、 **@request_id** 手順 b. で値を取得します。 すべてのノードがピア要求を受信するまで待機します。 手順 d. に進みます。  
  
    4.  [DBCC CHECKIDENT](../../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md) を使用してデータベース **B** の各テーブルを再作成し、適切な範囲が使用されていることを確認します。 手順 10 に進みます。  
  
     Id 範囲を管理する方法の詳細については、「手動で id 範囲管理の範囲の割り当て」セクションを参照してください。 [Id 列のレプリケート](../../../relational-databases/replication/publish/replicate-identity-columns.md)します。  
  
10. この時点では、データベース **B** とデータベース **C** 直接接続されていませんが、データベースを使用して変更を **A**します。[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] を実行しているノードがトポロジに含まれている場合は手順 11. に進み、それ以外の場合は手順 12. に進みます。  
  
11. システムを停止し、データベース間のサブスクリプションを再作成 **B** と **C**します。システムを停止するときには、パブリッシュされたテーブルの利用をすべてのノードで停止し、各ノードが他のすべてのノードの変更を受け取っていることを確認します。  
  
    1.  ピア ツー ピア トポロジ内のパブリッシュされたテーブルの処理をすべて停止します。 手順 b. に進みます。  
  
    2.  実行 [sp_requestpeerresponse](../../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) データベースで **B** 出力パラメーターを取得および **@request_id**します。 手順 c. に進みます。  
  
    3.  既定では、ディストリビューション エージェントが連続的に実行されるように設定されているため、すべてのノードに自動的にトークンが送信されます。 ディストリビューション エージェントが連続モードで実行されていない場合は、エージェントを実行します。 手順 d. に進みます。  
  
    4.  実行 [sp_helppeerresponses](../../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md), 、提供する、 **@request_id** 手順 b. で値を取得します。 すべてのノードがピア要求を受信するまで待機します。 手順 e. に進みます。  
  
    5.  データベースでサブスクリプションを再作成 **B** データベースのパブリケーションに対する **C**, 、サブスクライバーがデータを既に持っているかを指定します。 手順 b. に進みます。  
  
    6.  データベースでサブスクリプションを再作成 **C** データベースのパブリケーションに対する **B**, 、サブスクライバーがデータを既に持っているかを指定します。 手順 13 に進みます。  
  
12. データベース間でサブスクリプションを再作成 **B** と **C**:  
  
    1.  データベースで **B**, 、クエリ、 [MSpeer_lsns](../../../relational-databases/system-tables/mspeer-lsns-transact-sql.md) 最新のトランザクションのデータベースをログ シーケンス番号 (LSN) を取得するテーブル **B** がデータベースから受信した **C**します。  
  
    2.  データベースでサブスクリプションを再作成 **B** データベースのパブリケーションに対する **C**, 、LSN に基づいてサブスクリプションを初期化することを指定する (値の **lsn からの初期化** の **@sync_type** のパラメーター [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md))。 手順 b. に進みます。  
  
    3.  データベースでサブスクリプションを再作成 **C** データベースのパブリケーションに対する **B**, 、サブスクライバーがデータを既に持っているかを指定します。 手順 13 に進みます。  
  
13. サブスクリプション データベースを同期するディストリビューション エージェントを実行 **B** と **C**します。復元が完了します。  
  
#### msdb データベース (パブリッシャー)  
  
1.  **msdb** データベースの最新バックアップを復元します。  
  
2.  復元されたバックアップは完全かつ最新ですか。 すべてのパブリケーションおよびサブスクリプションに対する最新の構成がこのバックアップに含まれていますか。 答えが「はい」の場合、復元は完了です。 「いいえ」の場合は、手順 3. に進みます。  
  
3.  レプリケーション スクリプトを使用して、サブスクリプションのクリーンアップ ジョブを再作成します。 復元が完了します。  
  
#### master データベース (パブリッシャー)  
  
1.  **master** データベースの最新バックアップを復元します。  
  
2.  データベースのレプリケーション構成および設定が、パブリケーション データベースと一致していることを確認します。  
  
### ディストリビューターにあるデータベース  
  
#### ディストリビューション データベース  
  
1.  ディストリビューション データベースの最新バックアップを復元します。  
  
2.  障害の発生前に、ディストリビューション データベースで " **sync with backup** " 設定が有効になっていましたか。 答えが「はい」の場合は、手順 3. に進みます。「いいえ」の場合は、手順 4. に進みます。  
  
     設定が有効の場合、 `SELECT DATABASEPROPERTYEX('<DistributionDatabaseName>', 'IsSyncWithBackup')` クエリが "1" を返します。  
  
3.  復元されたバックアップは完全かつ最新ですか。 すべてのパブリケーションおよびサブスクリプションに対する最新の構成がこのバックアップに含まれていますか。 答えが「はい」の場合、復元は完了です。 「いいえ」の場合は、手順 4 に進みます。  
  
4.  復元されたディストリビューション データベースの構成情報が最新では、または **バックアップと同期** ディストリビューション データベースのオプションが設定されませんでした。 (復元後に、パブリッシャーでコミットされた後にサブスクライバーに配信されていないトランザクションは、ディストリビューション データベースで見つからない可能性があります)。レプリケーションの削除および再作成を行ってから検証を実行します。  
  
    1.  パブリッシャー、ディストリビューター、およびサブスクライバーで、レプリケーション構成を削除した後、再作成を行います。 サブスクリプションを再作成するときには、サブスクライバーにデータが格納済みであることを指定します。 手順 b. に進みます。  
  
         レプリケーションを削除する方法の詳細については、次を参照してください。 [sp_removedbreplication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)します。  
  
         サブスクライバーにデータが格納済みであることを指定する方法の詳細については、「 [Initialize a Subscription Manually](../../../relational-databases/replication/initialize-a-subscription-manually.md)」を参照してください。  
  
    2.  検証を行うすべてのパブリケーションにマークを付けます。 検証に失敗したサブスクリプションを再初期化します。 復元が完了します。  
  
         検証の詳細については、「 [Validate Replicated Data](../../../relational-databases/replication/validate-replicated-data.md)」を参照してください。 再初期化の詳細については、次を参照してください。 [サブスクリプションの再初期化](../../../relational-databases/replication/reinitialize-subscriptions.md)します。  
  
#### msdb データベース (ディストリビューター)  
  
1.  **msdb** データベースの最新バックアップを復元します。  
  
2.  復元されたバックアップは完全かつ最新ですか。 すべてのパブリケーションおよびサブスクリプションに対する最新の構成がこのバックアップに含まれていますか。 答えが「はい」の場合、復元は完了です。 「いいえ」の場合は、手順 3. に進みます。  
  
3.  パブリッシャー、ディストリビューター、およびサブスクライバーで、レプリケーション構成を削除した後、再作成を行います。 サブスクリプションを再作成するときには、サブスクライバーにデータが格納済みであることを指定します。 手順 4 に進みます。  
  
     レプリケーションを削除する方法の詳細については、次を参照してください。 [sp_removedbreplication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)します。  
  
     サブスクライバーにデータが格納済みであることを指定する方法の詳細については、「 [Initialize a Subscription Manually](../../../relational-databases/replication/initialize-a-subscription-manually.md)」を参照してください。  
  
4.  検証を行うすべてのパブリケーションにマークを付けます。 検証に失敗したサブスクリプションを再初期化します。 復元が完了します。  
  
     検証の詳細については、「 [Validate Replicated Data](../../../relational-databases/replication/validate-replicated-data.md)」を参照してください。 再初期化の詳細については、次を参照してください。 [サブスクリプションの再初期化](../../../relational-databases/replication/reinitialize-subscriptions.md)します。  
  
#### master データベース (ディストリビューター)  
  
1.  **master** データベースの最新バックアップを復元します。  
  
2.  データベースのレプリケーション構成および設定が、パブリケーション データベースと一致していることを確認します。  
  
### サブスクライバーにあるデータベース  
  
#### サブスクリプション データベース  
  
1.  サブスクリプション データベースの最新バックアップは、ディストリビューション データベースにおけるディストリビューションの最小保有期間の設定よりも新しいですか  (これにより、サブスクライバーを最新状態にするために必要なすべてのコマンドがディストリビューターに存在しているかどうかを判断できます)。答えが「はい」の場合は、手順 2. に進みます。 「いいえ」の場合は、サブスクリプションを再初期化します。 復元が完了します。  
  
     最大ディストリビューション保有期間の設定を確認するのには、実行 [sp_helpdistributiondb](../../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md) から値を取得し、 **max_distretention** 列 (この値は時間単位)。  
  
     サブスクリプションを再初期化する方法の詳細については、「 [Reinitialize a Subscription](../../../relational-databases/replication/reinitialize-a-subscription.md)」を参照してください。  
  
2.  サブスクリプション データベースの最新バックアップを復元します。 手順 3. に進みます。  
  
3.  サブスクリプション データベースにプッシュ サブスクリプションのみが含まれている場合は、手順 4. に進みます。 サブスクリプション データベースにプル サブスクリプションが含まれている場合は、次の質問に答えてください。サブスクリプション情報は最新ですか。 障害発生時に設定されていたすべてのテーブルおよびオプションがデータベースに含まれていますか。 「はい」の場合は、手順 4 に進みます。 「いいえ」の場合は、サブスクリプションを再初期化します。 復元が完了します。  
  
4.  サブスクライバーを同期するには、ディストリビューション エージェントを実行します。 復元が完了します。  
  
     ディストリビューション エージェントを実行する方法の詳細については、次を参照してください。 [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)します。  
  
#### msdb データベース (サブスクライバー)  
  
1.  **msdb** データベースの最新バックアップを復元します。 このサブスクライバーでプル サブスクリプションが使用されていますか。 答えが「いいえ」の場合、復元は完了です。 答えが「はい」の場合は、手順 2. に進みます。  
  
2.  復元されたバックアップは完全かつ最新ですか。 すべてのプル サブスクリプションに対する最新の構成がこのバックアップに含まれていますか。 答えが「はい」の場合、復元は完了です。 「いいえ」の場合は、手順 3. に進みます。  
  
3.  プル サブスクリプションの削除および再作成を行います。 サブスクリプションを再作成するときには、サブスクライバーにデータが格納済みであることを指定します。 復元が完了します。  
  
     サブスクリプションを削除する方法の詳細については、「 [Subscribe to Publications](../../../relational-databases/replication/subscribe-to-publications.md)」を参照してください。  
  
     サブスクライバーにデータが格納済みであることを指定する方法の詳細については、「 [Initialize a Subscription Manually](../../../relational-databases/replication/initialize-a-subscription-manually.md)」を参照してください。  
  
#### master データベース (サブスクライバー)  
  
1.  **master** データベースの最新バックアップを復元します。  
  
2.  データベースのレプリケーション構成および設定が、パブリケーション データベースと一致していることを確認します。  
  
## 参照  
 [SQL Server データベースのバックアップと復元](../../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [レプリケートされたデータベースのバックアップと復元](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [ディストリビューションの構成](../../../relational-databases/replication/configure-distribution.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [パブリケーションのサブスクライブ](../../../relational-databases/replication/subscribe-to-publications.md)   
 [サブスクリプションの初期化](../../../relational-databases/replication/initialize-a-subscription.md)   
 [データの同期](../../../relational-databases/replication/synchronize-data.md)  
  
  