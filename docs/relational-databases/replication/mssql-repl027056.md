---
title: "MSSQL_REPL027056 | Microsoft Docs"
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
  - "MSSQL_REPL027056 エラー"
ms.assetid: 92d62f3c-b8ae-482e-a348-2e9a8ee9786e
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_REPL027056
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|27056|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|マージ プロセスが、'%1' で生成履歴を変更できませんでした。 トラブルシューティングを行うには、詳細な履歴ログとの同期を再開して、書き込み先の出力ファイルを指定してください。|  
  
## 説明  
 通常このエラーは、極端に大きくなったマージ レプリケーション システム テーブルにおける競合の結果として発生します。 一般的にシステム テーブルは、パブリケーションの保有期間が長いと大きくなります。これは、保有期間が終了するまでメタデータを格納しておく必要があるためです。  
  
## ユーザーの操作  
 **問題を解決するには、以下の操作を実行します。**  
  
1.  値を小さく-**DownloadGenerationsPerBatch** と **- UploadGenerationsPerBatch** 続行、基になるに対処する間に処理できるようにするマージ エージェントのパラメーターは、エラーの原因を発行します。 エージェント パラメーターは、エージェント プロファイルおよびコマンド ラインで指定できます。 詳細については、以下をご覧ください。  
  
    -   [Work with Replication Agent Profiles](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [表示および変更のレプリケーション エージェント コマンド プロンプト パラメーターと #40 です。SQL Server Management Studio と #41 です。](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [レプリケーション エージェント実行可能ファイルの概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)します。  
  
2.  パブリケーションの保有期間をできるだけ短く設定します。 詳しくは、「 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)」をご覧ください。  
  
3.  マージ レプリケーションのメンテナンスの一環として、マージ レプリケーションに関連付けられているシステム テーブルの増大をときどき確認: **MSmerge_contents**, 、**MSmerge_genhistory**, 、および **MSmerge_tombstone**, 、**MSmerge_current_partition_mappings**, 、および **MSmerge_past_partition_mappings**します。 定期的にこれらのテーブルのインデックスを再設定します。 詳細については、次を参照してください。 [の再構成とインデックスの再構築](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)します。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  