---
title: "マージ アーティクルのダミー更新の実行 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sp_mergedummyupdate"
  - "ダミー更新 [SQL Server レプリケーション]"
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# マージ アーティクルのダミー更新の実行 (レプリケーション Transact-SQL プログラミング)
  マージ レプリケーションではレプリケーション処理の中でトリガーを使用します。パブリッシュ済みのテーブルに更新が加えられると、更新トリガーが起動します。 WRITETEXT 操作や UPDATETEXT 操作の際など、トリガーを起動せずにデータを更新できる場合もあります。 このような場合、ダミーの UPDATE ステートメントを明示的に追加して、変更をレプリケートする必要があります。 ダミーの UPDATE ステートメントは、レプリケーション ストアド プロシージャを使用して追加できます。  
  
### ダミーの UPDATE ステートメントを追加するには  
  
1.  ダミーの更新を必要とするマージ パブリッシュ済みテーブルの行に対して、操作 (たとえば UPDATETEXT など) を実行します。  
  
2.  変更が加えられたデータベースのサーバー (パブリッシャーまたはサブスクライバー) で実行 [sp_mergedummyupdate & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql.md)します。 に対して行われた変更テーブルを指定して **@source_object**, 、および変更された行の一意の識別子 **@rowguid**します。  
  
3.  サブスクリプションを同期して、変更された行をレプリケートします。  
  
  