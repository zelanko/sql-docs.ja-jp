---
title: "MSSQL_ENG021075 | Microsoft Docs"
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
  - "MSSQL_ENG021075 エラー"
ms.assetid: c8c29543-d1f6-49d5-b6c8-e8c3aa373090
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG021075
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21075|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|パブリケーション '%s' の初期スナップショットはまだ使用できません。|  
  
## 説明  
 エラー MSSQL_ENG021075 は、スナップショット エージェントがスナップショットの生成を終える前にディストリビューション エージェントまたはマージ エージェントが開始されると発生します。  
  
## ユーザーの操作  
 サブスクリプションが作成されてから、または最後にサブスクリプションの再初期化を選択してから、一度もパブリケーションのスナップショット エージェントが開始されていない場合は、スナップショット エージェントを開始し、完了した後でディストリビューション エージェントまたはマージ エージェントを開始します。 詳細については、次を参照してください。 [を作成し、スナップショットの適用](../../relational-databases/replication/create-and-apply-the-snapshot.md)します。  
  
 スナップショット エージェントが完了しない場合は、スナップショット エージェントの履歴でエラーを確認して対応します。 レプリケーション モニターでエージェントの状態やエラーの詳細を表示する方法については、次を参照してください。 [情報を表示したりタスクを実行するエージェント関連付けられていると、パブリケーションと #40 です。レプリケーション モニターと #41;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)します。  
  
 エラーの発生が継続する場合は、エージェントのログ記録を増やし、ログの出力ファイルを指定します。 エラーのコンテキストによっては、エラーや他のエラー メッセージにつながる手順が示される可能性もあります。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  