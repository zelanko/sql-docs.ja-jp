---
title: "MSSQL_REPL020011 | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_REPL020011 エラー"
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_REPL020011
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|20011|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|プロセスは、'%1' を '%2' で実行できませんでした。|  
  
## 説明  
 このエラーは、トランザクション レプリケーションのログ リーダー エージェントが実行される場合など、処理中にさまざまな状況で発生する **sp_replcmds** (で 'sp_replcmds' が、プロセスでは実行できませんでした \< ServerName>) または **sp_repldone** (プロセスでは 'sp_repldone' を実行できませんでした \< ServerName>)。  
  
## ユーザーの操作  
 バックアップから復元したデータベースでは、このエラーが発生する場合は、実行などのバックアップと復元のドキュメントに記載されている手順を実行していることを確認 **sp_replrestart** 該当する場合。 詳細については、次を参照してください。 [データベースのバックアップおよび復元するスナップショットおよびトランザクション レプリケーションのための戦略](../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)します。  
  
 このエラーは内部処理エラーであり、復元以外の状況で発生した場合は、一般的にレプリケーションを削除して再構成する必要があることを示しています。 レプリケーションを削除できない場合は、カスタマー サポートにお問い合わせください。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [sp_replcmds & #40 です。Transact SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone & #40 です。Transact SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)  
  
  