---
title: "PH timeout サーバー構成オプション | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "プロトコル ハンドラーの待機時間の制限 [SQL Server]"
  - "タイムアウト オプション [SQL Server]、PH timeout オプション"
  - "プロトコル [SQL Server]、タイムアウト"
  - "ph timeout オプション"
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# PH timeout サーバー構成オプション
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  PH timeout オプションは、フルテキスト プロトコル ハンドラーが、データベースへの接続をタイムアウトするまで待機する時間を秒単位で指定します。 既定値は 60 秒です。 一時的なネットワークの問題により接続試行がタイムアウトする場合は、ph timeout 値を大きくします。  
  
 フルテキスト プロトコル ハンドラーは、フィルター デーモン ホストでホストされ、フルテキスト インデックスの作成対象データを SQL Server からフェッチする場合に使用されます。 フルテキスト検索コンポーネントの詳細については、「[フルテキスト検索](../../relational-databases/search/full-text-search.md)」を参照してください。  
  
 データ行をフェッチすると、指定した時間内にプロトコル ハンドラーが SQL Server に接続できない場合、その行に対するタイムアウト エラーが報告されます。 その行のフェッチは、後でフルテキストの Gatherer により再試行されます。 フルテキストの Gatherer の詳細については、「[フルテキスト インデックスの作成](../../relational-databases/search/populate-full-text-indexes.md)」を参照してください。  
  
## 参照  
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  