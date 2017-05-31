---
title: "インメモリ OLTP に対してサポートされていない SQL Server の機能 | Microsoft Docs"
ms.custom: 
ms.date: 10/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c39f03a7-e223-4fd7-bd30-142e28f51654
caps.latest.revision: 55
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e1b1d4a26616fe83a241267bc87b9e799d883e26
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="unsupported-sql-server-features-for-in-memory-oltp"></a>インメモリ OLTP に対してサポートされていない SQL Server の機能
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能で、メモリ最適化オブジェクトと共に使用できないものについて説明します。  
  
## <a name="includessnoversionincludesssnoversion-mdmd-features-not-supported-for-in-memory-oltp"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インメモリ OLTP に対してサポートされない機能  
 次に示す [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能は、(メモリ最適化データ ファイル グループを含む) メモリ最適化オブジェクトを持つデータベースでサポートされません。  
  
|サポートされない機能|機能の説明|  
|-------------------------|-------------------------|  
|メモリ最適化テーブルに対するデータ圧縮。|データ圧縮機能を使用することにより、データベース内のデータを圧縮したり、データベースのサイズを小さくすることができます。 詳細については、「 [Data Compression](../../relational-databases/data-compression/data-compression.md)」を参照してください。|  
|メモリ最適化テーブルと HASH インデックスのパーティション分割、および非クラスター化インデックス。|パーティション テーブルとパーティション インデックスのデータは、データベース内の複数のファイル グループに分散できるように、複数の単位に分割されます。 詳細については、「 [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md)」を参照してください。|  
|レプリケーション|サブスクライバー上でのメモリ最適化されたテーブルに対するトランザクション レプリケーションを除き、他のレプリケーション構成は、メモリ最適化されたテーブルを参照するテーブルまたはビューと互換性がありません。 メモリ最適化ファイル グループがある場合、sync_mode='database snapshot' を使用したレプリケーションはサポートされません。 詳細については、「 [メモリ最適化テーブル サブスクライバーへのレプリケーション](../../relational-databases/replication/replication-to-memory-optimized-table-subscribers.md)」を参照してください。|  
|ミラーリング|データベース ミラーリングは、MEMORY_OPTIMIZED_DATA ファイル グループのデータベースではサポートされていません。 ミラーリングの詳細については、「[データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)」を参照してください。|  
|ログの再構築|ログの再構築は、MEMORY_OPTIMIZED_DATA ファイル グループのデータベースでは、アタッチと ALTER DATABASE のいずれによるものでもサポートされていません。|  
|Linked Server|メモリ最適化テーブルと同じクエリまたはトランザクションで、リンク サーバーにアクセスすることはできません。 詳しくは、「[リンク サーバー &#40;データベース エンジン&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)」を参照してください。|  
|一括ログ記録|データベースの復旧モデルにかかわらず、持続性のあるメモリ最適化テーブル上のすべての操作は、常に完全にログに記録されます。|  
|最小ログ記録|最小ログ記録は、メモリ最適化テーブルではサポートされていません。 最小ログ記録の詳細については、「[トランザクション ログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)」および「[一括インポートで最小ログ記録を行うための前提条件](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)」を参照してください。|  
|変更の追跡|変更の追跡は、インメモリ OLTP オブジェクトを含むデータベースで有効にすることができます。 ただし、メモリ最適化テーブルの変更は追跡されません。|  
|DDL トリガー|インメモリ OLTP テーブルおよびネイティブ コンパイル モジュールでは、データベースレベルおよびサーバーレベルの DDL トリガーはどちらもサポートされません。|  
|変更データ キャプチャ (CDC)|CDC の内部では DROP TABLE に DDL トリガーが使用されているため、メモリ最適化テーブルが含まれるデータベースでこの CDC を使用できません。|  
|ファイバー モード|ファイバー モードは、メモリ最適化テーブルではサポートされていません。<br /><br /> ファイバー モードがアクティブであれば、メモリ最適化ファイル グループが含まれたデータベースの作成や、既存データベースへのメモリ最適化ファイル グループの追加を行うことはできません。<br /><br /> メモリ最適化ファイル グループが含まれたデータベースを使用している場合に、ファイバー モードを有効にすることはできます。 ただし、ファイバー モードを有効にするには、サーバーを再起動する必要があります。 この場合、メモリ最適化ファイル グループが含まれたデータベースは復旧されず、メモリ最適化ファイル グループが含まれたデータベースを使用するにはファイバー モードを無効にするように勧めるエラー メッセージが表示されます。<br /><br /> ファイバー モードがアクティブであれば、メモリ最適化ファイル グループが含まれたデータベースのアタッチおよび復元は失敗します。 また、データベースが SUSPECT としてマークされます。<br /><br /> <br /><br /> 詳細については、「 [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)」を参照してください。|  
|Service Broker の制限事項|ネイティブ コンパイル ストアド プロシージャからキューにアクセスできません。<br /><br /> メモリ最適化テーブルにアクセスするトランザクションでリモート データベースのキューにアクセスできません。|  
|サブスクライバーでのレプリケーション|サブスクライバー上でのメモリ最適化テーブルに対するトランザクション レプリケーションはサポートされていますが、いくつかの制限があります。 詳細については、「 [メモリ最適化テーブル サブスクライバーへのレプリケーション](../../relational-databases/replication/replication-to-memory-optimized-table-subscribers.md)」を参照してください。|  
  
 一部の例外を除き、複数データベースにまたがるトランザクションはサポートされません。 次の表では、サポートされるケースと、対応する制限について説明します (「 [複数データベースにまたがるクエリ](../../relational-databases/in-memory-oltp/cross-database-queries.md)」も参照してください。)  
  
|データベース|Allowed|説明|  
|---------------|-------------|-----------------|  
|ユーザー データベース、model、および msdb|いいえ|複数のデータベースにまたがるクエリおよびトランザクションはサポートされません。<br /><br /> メモリ最適化テーブルまたはネイティブ コンパイル ストアド プロシージャにアクセスするクエリおよびトランザクションは、システム データベースの master (読み取り専用アクセス) と tempdb を除き、他のデータベースにアクセスできません。|  
|resource データベース、tempdb|可|シングル ユーザー データベース以外に resource データベースと tempdb のみを使用する複数のデータベースにまたがるトランザクションに関する制限はありません。|  
|master|読み取り専用|インメモリ OLTP と master データベースを使用する複数のデータベースにまたがるトランザクションは、master データベースへの書き込みが含まれる場合にコミットに失敗します。 master に対して読み取り操作のみを実行し、ユーザー データベースを 1 つだけ使用する複数のデータベースにまたがるトランザクションは許可されます。|  
  
## <a name="scenarios-not-supported"></a>サポートされていないシナリオ  
  
-   データベースの包含 ([包含データベース](../../relational-databases/databases/contained-databases.md)) は、インメモリ OLTP ではサポートされていません。 Contained database authentication がサポートされます。 ただし、すべてのインメモリ OLTP オブジェクトは、DMV dm_db_uncontained_entities で "breaking containment" とマークされています。  
  
-   CLR ストアド プロシージャ内からのコンテキスト接続を使用したメモリ最適化テーブルへのアクセス。  
  
-   メモリ最適化テーブルにアクセスするクエリでのキーセットと動的カーソル。 これらのカーソルは静的および読み取り専用に降格されます。  
  
-   **target***が指定された* MERGE INTO *target* はメモリ最適化テーブルです。 **MERGE USING***source* は、メモリ最適化テーブルでサポートされます。  
  
-   ROWVERSION (TIMESTAMP) データ型はサポートされていません。 詳細については、「[FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)」を参照してください。  
  
-   自動終了は、MEMORY_OPTIMIZED_DATA ファイル グループのあるデータベースではサポートされていません。  
  
-   データベース スナップショットは、MEMORY_OPTIMIZED_DATA ファイル グループのあるデータベースではサポートされていません。  
  
-   トランザクション DDL。 インメモリ OLTP オブジェクトの CREATE/ALTER/DROP は、ユーザー トランザクション内ではサポートされていません。  
  
-   イベント通知。  
  
-   ポリシー ベースの管理 (PBM)。 PBM の "回避" モードと "ログのみ" モードはサポートされません。 サーバーにこのようなポリシーが存在すると、インメモリ OLTP の DDL が正常に実行されないことがあります。 "要求時" モードと "スケジュールで実行" モードはサポートされます。  
  
## <a name="see-also"></a>参照  
 [SQL Server によるインメモリ OLTP のサポート](../../relational-databases/in-memory-oltp/sql-server-support-for-in-memory-oltp.md)  
  
  

