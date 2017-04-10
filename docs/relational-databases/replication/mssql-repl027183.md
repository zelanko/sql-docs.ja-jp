---
title: "MSSQL_REPL027183 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_REPL027183 エラー"
ms.assetid: 52c271ac-1a0e-43d5-85d4-35886d1efd32
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_REPL027183
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|27183|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|マージ処理で、パラメーター化された行フィルターを使用して、アーティクル内の変更情報を列挙できませんでした。 このエラーが継続して発生する場合、このプロセスのクエリ タイムアウト値を増やし、パブリケーションの保有期間を減少し、パブリッシュされたテーブルのインデックスを強化してください。|  
  
## 説明  
 このエラーは、フィルター選択されたパブリケーションでの変更を処理中に、マージ エージェント タイムアウトになると発生します。 このタイムアウトは、次のいずれかの問題点により生じた可能性があります。  
  
-   事前計算済みパーティションの最適化の未使用  
  
-   フィルター選択に使用される列のインデックスの断片化  
  
-   大規模なマージ メタデータ テーブルなど、 **MSmerge_tombstone**, 、**MSmerge_contents**, 、および **MSmerge_genhistory**します。  
  
-   一意キーで結合されていないフィルター選択されたテーブルや多くのテーブルを含む結合フィルター  
  
## ユーザーの操作  
 問題を解決するには、以下の操作を実行します。  
  
-   値を大きく、 **-querytimeout** 続行、基になるに対処する間に処理できるようにするマージ エージェントのパラメーターは、エラーの原因を発行します。 エージェント パラメーターは、エージェント プロファイルおよびコマンド ラインで指定できます。 詳細については、以下をご覧ください。  
  
    -   [Work with Replication Agent Profiles](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [表示および変更のレプリケーション エージェント コマンド プロンプト パラメーターと #40 です。SQL Server Management Studio と #41 です。](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [レプリケーション エージェント実行可能ファイルの概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)します。  
  
-   可能であれば、事前計算済みパーティションの最適化を使用します。 既定では、この最適化は、多くのパブリケーションの要件が満たされている場合に使用されます。 これらの要件の詳細については、次を参照してください。 [事前計算済みパーティションを持つパラメーター化されたフィルター パフォーマンスの最適化](../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md)します。 パブリケーションがこれらの要件を満たしていない場合は、パブリケーションを再設計することを検討してください。  
  
-   パブリケーションの保有期間をできる限り低い設定に指定します。保有期間に達するまで、レプリケーションはパブリケーション データベースおよびサブスクリプション データベースでメタデータをクリーンアップできません。 詳しくは、「 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)」をご覧ください。  
  
-   マージ レプリケーションのメンテナンスの一環として、マージ レプリケーションに関連付けられているシステム テーブルの増大をときどき確認: **MSmerge_contents**, 、**MSmerge_genhistory**, 、および **MSmerge_tombstone**, 、**MSmerge_current_partition_mappings**, 、および **MSmerge_past_partition_mappings**します。 定期的にこれらのテーブルのインデックスを再設定します。 詳細については、次を参照してください。 [の再構成とインデックスの再構築](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)します。  
  
-   フィルター選択に使用する列のインデックスが適切であることを確認し、必要に応じてインデックスを再構築します。 詳細については、次を参照してください。 [の再構成とインデックスの再構築](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)します。  
  
-   設定、 **join_unique_key** 一意の列に基づいて結合フィルターのプロパティです。 詳しくは、「 [Join Filters](../../relational-databases/replication/merge/join-filters.md)」をご覧ください。  
  
-   結合フィルター階層のテーブル数を制限します。 テーブルが 5 つ以上の結合フィルターを生成する場合は、小さなテーブル、変更されないテーブル、プライマリ参照テーブルはフィルター選択しないという別の解決策を検討してください。 結合フィルターは、サブスクリプション間でパーティション分割する必要のあるテーブル間でのみ使用します。  
  
-   同期を行うまでの間はフィルター選択されたテーブルへの変更を少なくするか、マージ エージェントをより頻繁に実行します。 同期スケジュールの設定の詳細については、次を参照してください。 [同期スケジュールの指定](../../relational-databases/replication/specify-synchronization-schedules.md)します。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  