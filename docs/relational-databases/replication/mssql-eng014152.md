---
title: "MSSQL_ENG014152 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014152 エラー"
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# MSSQL_ENG014152
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|14152|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|レプリケーション-%s: エージェント %s には再試行のスケジュールが設定されました。 %s|  
  
## 説明  
 指定されたレプリケーション エージェントは、要求された操作を再試行するようにスケジュール設定されました。 ジョブ ステップに設定された再試行の最大回数に達するまで、このプロセスが繰り返し再試行されます。  
  
 通常、再試行は次のいずれかの理由により発生します。  
  
-    **QueryTimeout** 値を超えています。  
  
-    **LoginTimeout** 値を超えています。  
  
-   レプリケーション プロセスがデッドロックの対象として選択される。  
  
## ユーザーの操作  
 この再試行のメッセージの発生頻度が低い場合、ユーザー操作は不要です。  
  
 使用 [sp_help_jobstep](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md) を最大回数の現在の設定を表示する、 **エージェントを実行して** 手順を指定したレプリケーション エージェントは再試行されます。 使用することができます、 **@retry_attempts** のパラメーター、 [sp_update_jobstep](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md) ストアド プロシージャをジョブ ステップが再試行する回数を調整します。  
  
 再試行のメッセージが頻繁に表示される場合は、再試行が発生するメッセージに基づく問題のトラブルシューティングを行います。 エージェントの履歴で、再試行をスケジュール設定する必要があった理由を示すメッセージを確認します。 場合によっては、レプリケーション エージェントに対してより詳細なログ記録を有効にする必要があります。 レプリケーションのログ出力を構成する方法の詳細については、マイクロソフト サポート技術情報の記事を参照してください。 [312292](http://support.microsoft.com/kb/312292)します。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  