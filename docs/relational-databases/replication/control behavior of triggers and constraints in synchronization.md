---
title: "同期中にトリガーと制約の動作を制御する (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/29/2017"
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
  - "ID [SQL Server レプリケーション]"
  - "制約 [SQL Server], レプリケーション"
  - "トリガー [SQL Server], レプリケーション"
  - "トリガー [SQL Server レプリケーション]"
  - "制約 [SQL Server レプリケーション]"
  - "NOT FOR REPLICATION オプション"
  - "NFR オプション"
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# 同期中にトリガーと制約の動作を制御する (レプリケーション Transact-SQL プログラミング)
  同期時に、レプリケーション エージェントが実行 [挿入 & #40 です。Transact SQL と #41;](../../t-sql/statements/insert-transact-sql.md), 、[更新 & #40 です。Transact SQL と #41;](../../t-sql/queries/update-transact-sql.md), 、および [DELETE & #40 です。Transact SQL と #41;](../../t-sql/statements/delete-transact-sql.md) 発生するデータ操作言語 (DML) トリガーを実行するこれらのテーブルのレプリケートされたテーブルに対するステートメント。 同期中はこれらのトリガーが起動しないようにしたり、制約が適用されないようにすることが必要になる場合があります。 このときの動作は、トリガーまたは制約がどのように作成されたかによって異なります。  
  
### 同期中にトリガーが実行されないようにするには  
  
1.  新しいトリガーを作成するときの NOT FOR REPLICATION オプションを指定 [CREATE TRIGGER と #40 です。Transact SQL と #41;](../../t-sql/statements/create-trigger-transact-sql.md)します。  
  
2.  既存のトリガーの NOT FOR REPLICATION オプションを指定 [ALTER TRIGGER と #40 です。Transact SQL と #41;](../../t-sql/statements/alter-trigger-transact-sql.md)します。  
  
### 同期中に制約が適用されないようにするには  
  
1.  新しい CHECK 制約または FOREIGN KEY 制約を作成する場合は、CHECK NOT FOR REPLICATION オプションを指定の制約定義で [テーブルの作成と #40 です。Transact SQL と #41;](../../t-sql/statements/create-table-transact-sql.md)します。  
  
## 参照  
 [テーブルと #40; データベース エンジン (& r) #41 です。](../../relational-databases/tables/create-tables-database-engine.md)  
  
  