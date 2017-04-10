---
title: "MSSQL_ENG014160 | Microsoft Docs"
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
  - "MSSQL_ENG014160 エラー"
ms.assetid: d0f3855e-d095-4a81-a5bd-9d7ad51f2c77
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# MSSQL_ENG014160
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|14160|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|パブリケーション [%s] のしきい値 [%s:%s] が設定されています。 このパブリケーションに対する 1 つ以上のサブスクリプションの有効期限が切れています。|  
  
## 説明  
 レプリケーションでは、いくつかの条件に対して警告を有効にできます。 こうした条件には、サブスクリプションの有効期限の残り時間などがあります。 同期されない場合、サブスクリプションが期限切れとなります内で、指定した *保有期間*します。 詳しくは、「 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)」をご覧ください。  
  
 レプリケーション モニターを使用して、警告を有効にすると、または [sp_replmonitorchangepublicationthreshold](../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md), 、警告がトリガーされたときを決定するしきい値を指定します。 指定したしきい値に達するか、そのしきい値を超えた場合、警告がレプリケーション モニターに表示され、イベントが Windows イベント ログに書き込まれます。 しきい値に達した時点で、SQL Server エージェントの警告を表示させることもできます。 詳細については、次を参照してください。 [しきい値の設定とレプリケーション モニターで警告](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md) と [プログラムでレプリケーションの監視](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)します。  
  
## ユーザーの操作  
 この問題の解決策は、警告が発生した原因によって異なります。  
  
-   しきい値を超えても、サブスクリプションの有効期限が切れていない場合は、そのサブスクリプションを同期します。 詳細については、次を参照してください。 [データの同期](../../relational-databases/replication/synchronize-data.md)します。  
  
-   エージェントが実行されていても、変更が適切にレプリケートされていない場合は、サブスクリプションの有効期限が切れる可能性があります。 トランザクション レプリケーションの場合は、ディストリビューション エージェントとログ リーダー エージェントが実行されていることを確認します。 マージ レプリケーションの場合は、マージ エージェントが実行されていることを確認します。 これらのエージェントを開始する方法については、次を参照してください。 [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  [レプリケーション エージェント実行可能ファイルの概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)します。  
  
-   サブスクリプションの有効期限が切れている場合、サブスクリプションの種類と期限切れになってからの期間によって、再初期化するか、削除して再作成する必要があります。 詳しくは、「 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)」をご覧ください。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  