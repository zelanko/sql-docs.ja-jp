---
title: "MSSQL_ENG020596 | Microsoft Docs"
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
  - "MSSQL_ENG020596 エラー"
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG020596
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|20596|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|'%s' または db_owner のメンバーだけが匿名エージェントを削除できます。|  
  
## 説明  
 匿名サブスクリプションのエージェントを削除するために必要な権限がありません。 呼び出すときに使用されるログイン [sp_dropanonymousagent & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql.md) メンバーである必要があります、 **sysadmin** 、ディストリビューター側の固定サーバー ロールまたは **db_owner** ディストリビューション データベースまたはユーザーの固定データベース ロールは、エージェントの最初の実行を開始した人である必要があります。  
  
## ユーザーの操作  
 適切な資格情報を使用してログインし、実行 **sp_dropanonymousagent**します。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  