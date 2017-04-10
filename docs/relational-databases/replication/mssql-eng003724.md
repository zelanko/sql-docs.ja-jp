---
title: "MSSQL_ENG003724 | Microsoft Docs"
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
  - "MSSQL_ENG003724 エラー"
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# MSSQL_ENG003724
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3724|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|%S_MSG '%.*ls' を %S_MSG できません。レプリケーションに使用されています。|  
  
## 説明  
 データベース内のオブジェクトがレプリケートされるときにマークされているシステム テーブルにレプリケートされると **sysarticles** (スナップショット レプリケーションおよびトランザクション パブリケーション) 用または **sysmergearticles** (マージ パブリケーション用)。 レプリケート済みのオブジェクトを削除しようとした場合に、このエラーが発生します。  
  
## ユーザーの操作  
 データベース オブジェクトを削除する前に、そのオブジェクトがレプリケートされていないことを確認します。 例:  
  
-   パブリケーション データベースでエラーが発生した場合、オブジェクトを削除する前にパブリケーションからアーティクルを削除します。 詳細については、次を参照してください。 [にアーティクルを追加し、既存のパブリケーションからアーティクルを削除](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)します。  
  
-   サブスクリプション データベースでエラーが発生した場合、オブジェクトを削除する前にそのサブスクリプションを削除します。 詳細については、次を参照してください。 [パブリケーションをサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)します。 トランザクション パブリケーションに対するサブスクリプションの場合、パブリケーション全体を削除するのではなく、個々のアーティクルに対するサブスクリプションを削除することができます。 詳細については、次を参照してください。 [sp_dropsubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)します。  
  
 このエラーは、レプリケートされていない、データベースで発生する場合は、実行 [sp_removedbreplication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) データベース内のオブジェクトがレプリケートされるとマークされていないことを確認します。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  