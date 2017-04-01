---
title: "MSSQL_ENG003165 | Microsoft Docs"
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
  - "MSSQL_ENG003165 エラー"
ms.assetid: 707d33dd-644e-4cc9-ac51-dddd49031530
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_ENG003165
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3165|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|データベース '%ls' は復元されましたが、レプリケーションの復元または削除中にエラーが発生しました。 データベースはオフラインのままです。 SQL Server オンライン ブックのトピック「MSSQL_ENG003165」を参照してください。|  
  
## 説明  
 このエラーは、レプリケートされたデータベースのバックアップの復元で問題が生じた場合に発生します。  
  
-   バックアップをその作成元と同じデータベースおよびサーバーに復元している場合、このエラーは、レプリケーション設定を適切に復元できなかったことを示します。  
  
-   バックアップを異なるデータベースまたはサーバーに復元している場合、このエラーは、レプリケーション設定を適切に削除できなかったことを示します (既定では、データベースまたはサーバーが異なる場合、レプリケーション設定は削除されます)。  
  
 エラーは、復元されたデータベースの状態とレプリケーション メタデータを含む 1 つまたは複数のシステム データベース間の不一致の結果である可能性があります: **msdb**, 、**マスター**, 、またはディストリビューション データベースです。  
  
## ユーザーの操作  
 この問題を解決するには、次の手順を実行します。  
  
1.  ALTER DATABASE を実行し、データベースをオンラインにします。たとえば、「`ALTER DATABASE AdventureWorks SET ONLINE`」と実行します。 詳細については、次を参照してください。 [ALTER DATABASE & #40 です。Transact SQL と #41;](../../t-sql/statements/alter-database-transact-sql.md)します。 レプリケーションの設定を保存する場合は、手順 2. に進みます。 それ以外の場合は、手順 3. に進みます。  
  
2.  実行 [sp_restoredbreplication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-restoredbreplication-transact-sql.md)します。 このストアド プロシージャの実行に成功した場合、復元は完了です。 実行に失敗した場合は、手順 3. に進んでください。  
  
3.  実行 [sp_removedbreplication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) すべてのレプリケーション設定を削除します。  
  
     必要に応じて、レプリケーションを再構成します。 推奨どおりにレプリケーション トポロジのスクリプトを作成している場合は、スクリプトを使用してトポロジを再構成してください。  
  
## 参照  
 [SQL Server データベースのバックアップと復元](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [レプリケートされたデータベースのバックアップと復元](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  