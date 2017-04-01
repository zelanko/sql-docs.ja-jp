---
title: "MSSQL_ENG021286 | Microsoft Docs"
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
  - "MSSQL_ENG021286 エラー"
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# MSSQL_ENG021286
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21286|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|競合テーブル '%s' が存在しません。|  
  
## 説明  
 アーティクルの競合テーブルが表示されている場合、このエラーは発生 [sysmergearticles & #40 です。Transact SQL と #41;](../../relational-databases/system-tables/sysmergearticles-transact-sql.md) 実際には存在しません。 このエラーは、マージ レプリケーション用にパブリッシュされたテーブルへの列の追加または削除を試みたときに発生することがあります。  
  
## ユーザーの操作  
 実行 [DBCC CHECKDB と #40 です。Transact SQL と #41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) 競合テーブルが見つからないことを確認すると、データベースでは、データ一貫性の問題はありません。  
  
 サブスクライバーに競合テーブルがない場合は、サブスクリプションを削除し、再作成します。 パブリッシャーに競合テーブルがない場合は、すべてのサブスクリプションを削除し、パブリケーションを削除してから、パブリケーションおよびすべてのサブスクリプションを再作成します。 詳細については、次を参照してください。 [発行データおよびデータベース オブジェクト](../../relational-databases/replication/publish/publish-data-and-database-objects.md) と [パブリケーションをサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)します。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  