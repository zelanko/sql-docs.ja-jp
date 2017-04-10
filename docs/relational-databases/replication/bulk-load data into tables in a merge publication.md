---
title: "マージ レプリケーション内のテーブルにデータを一括読み込みする (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
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
  - "一括読み込み [SQL Server レプリケーション]"
  - "マージ レプリケーションの一括読み込み [SQL Server レプリケーション]"
  - "sp_addtabletocontents"
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# マージ レプリケーション内のテーブルにデータを一括読み込みする (レプリケーション Transact-SQL プログラミング)
  使用してテーブルにデータが読み込まれる場合、 [bcp ユーティリティ](../../tools/bcp-utility.md) または [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) 内の追跡データを維持するマージ レプリケーション トリガーを既定では、コマンド、 [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) システム テーブルは起動しません。 データが読み込まれたときにマージ レプリケーション トリガーを強制的に起動するか、一括コピー操作の後にレプリケーション ストアド プロシージャを使用して、生成されたレプリケーション メタデータをプログラムによって挿入できます。  
  
### マージ レプリケーションによってパブリッシュされたテーブルに bcp ユーティリティを使用してデータを一括読み込みするには  
  
1.  マージ レプリケーションを使用してパブリッシュされたテーブルにデータを挿入するには、パブリッシャーまたはサブスクライバーで [bcp Utility](../../tools/bcp-utility.md) または [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) を実行します。  
  
2.  挿入されたデータ用のレプリケーション メタデータが生成されようにするには、次のいずれかの方法を使用します。  
  
    -   FIRE_TRIGGERS オプションを使用して一括コピーを実行する。  
  
    -   データが挿入されたデータベースについて実行 [sp_addtabletocontents & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql.md)します。 データが挿入のテーブル名を指定 **@table_name**します。  
  
  