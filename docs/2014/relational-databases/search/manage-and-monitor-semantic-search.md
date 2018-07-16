---
title: セマンティクス検索の管理および監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], managing
- semantic search [SQL Server], monitoring
ms.assetid: eb5c3b29-da70-42aa-aa97-7d35a3f1eb98
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4dc25a584e7e883ce07040e0d5d0d567995533f1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311462"
---
# <a name="manage-and-monitor-semantic-search"></a>セマンティクス検索の管理および監視
  セマンティック インデックス作成プロセスと、インデックスの管理および監視に関連するタスクについて説明します。  
  
##  <a name="HowToMonitorStatus"></a> 方法: セマンティック インデックス作成の状態を確認します。  
 **セマンティック インデックス作成の最初のフェーズが完了しますか。**  
 動的管理ビュー [sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql) に対してクエリを実行し、**status** 列と **status_description** 列を確認します。  
  
 インデックス作成の最初のフェーズでは、フルテキスト キーワード インデックスおよびセマンティック キー フレーズ インデックスの作成のほか、ドキュメンの類似性データの抽出が行われます。  
  
```tsql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_index_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
 **セマンティック インデックス作成の 2 番目のフェーズが完了しますか。**  
 動的管理ビュー [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql) に対してクエリを実行し、**status** 列と **status_description** 列を確認します。  
  
 インデックス作成の 2 番目のフェーズには、ドキュメントの類似性に関するセマンティック インデックスの作成が含まれます。  
  
```wql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_semantic_similarity_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
##  <a name="HowToCheckSize"></a> 方法: セマンティック インデックスのサイズを確認します。  
 **セマンティック キー フレーズ インデックスまたはセマンティックのドキュメントの類似性インデックスの論理サイズは?**  
 動的管理ビュー [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql) に対してクエリを実行します。  
  
 論理サイズは、インデックス ページの数で表示されます。  
  
```tsql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_db_fts_index_physical_stats WHERE object_id = OBJECT_ID('table_name')  
GO  
```  
  
 **フルテキスト カタログのフルテキストおよびセマンティック インデックスの合計サイズは?**  
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) メタデータ関数の **IndexSize** プロパティに対してクエリを実行します。  
  
```tsql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'IndexSize')  
GO  
```  
  
 **項目の数は、フルテキスト カタログのフルテキストおよびセマンティック インデックスでインデックスを作成しますか。**  
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) メタデータ関数の **ItemCount** プロパティに対してクエリを実行します。  
  
```tsql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'ItemCount')  
GO  
```  
  
##  <a name="HowToForcePopulation"></a> 方法: セマンティック インデックスの作成を強制します。  
 START/STOP/PAUSE 句または RESUME POPULATION 句を使用して、フルテキスト インデックスおよびセマンティック インデックスを強制的に作成できます (これらの句の構文と動作については、フルテキスト インデックスに関する説明に示されています)。 詳細については、「[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)」および「[フルテキスト インデックスの作成](../indexes/indexes.md)」を参照してください。  
  
 セマンティック インデックス作成はフルテキスト インデックス作成に依存しているため、セマンティック インデックスは関連するフルテキスト インデックスが作成されたときにのみ作成されます。  
  
 **例: フルテキスト インデックスとセマンティック インデックスの完全作成を開始する**  
  
 次の例では、AdventureWorks2012 サンプル データベースの **Production.Document** テーブルの既存のフルテキスト インデックスを変更することにより、フルテキスト インデックスとセマンティック インデックスの両方の完全作成を開始します。  
  
```vb  
USE AdventureWorks2012  
GO  
  
ALTER FULLTEXT INDEX ON Production.Document  
    START FULL POPULATION  
GO  
```  
  
##  <a name="HowToDisableIndexing"></a> 方法: 無効にするか、セマンティック インデックス作成を再度有効にします。  
 ENABLE/DISABLE 句を使用して、フルテキスト インデックスまたはセマンティック インデックスの作成を有効または無効にすることができます (これらの句の構文と動作については、フルテキスト インデックスに関する説明に示されています)。 詳細については、「[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)」を参照してください。  
  
 セマンティック インデックスの作成が無効化または中断された後でもセマンティック データに対するクエリは正常に動作し、以前にインデックスが作成されたデータを返します。 この動作は、フルテキスト検索の動作と一致しません。  
  
```tsql  
-- To disable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name DISABLE  
GO  
  
-- To re-enable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name ENABLE  
GO  
```  
  
##  <a name="SemanticIndexing"></a> セマンティック インデックス作成のフェーズ  
 セマンティック検索では、セマンティック検索が有効なそれぞれの列に対して、次の 2 種類のデータに関するインデックスが作成されます。  
  
1.  **キー フレーズ**  
  
2.  **ドキュメントの類似性**  
  
 セマンティック インデックス作成は、フルテキスト インデックス作成との関連において 2 つのフェーズで行われます。  
  
1.  **フェーズ 1:** フルテキスト キーワード インデックスとセマンティック キー フレーズ インデックスが同時に作成されます。 ドキュメントの類似性に関するインデックスを作成するのに必要なデータもこのとき抽出されます。  
  
2.  **フェーズ 2:** ドキュメントの類似性に関するセマンティック インデックスが作成されます。 このインデックスは、前のフェーズで作成された 2 つのインデックスに依存します。  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="ProblemNotPopulated"></a> 問題点: セマンティック インデックスが作成されません。  
 **関連付けられた、フルテキスト インデックスが作成されますか。**  
 セマンティック インデックス作成はフルテキスト インデックス作成に依存しているため、セマンティック インデックスは関連するフルテキスト インデックスが作成されたときにのみ作成されます。  
  
 **フルテキスト検索とセマンティック検索のインストールし、構成ですか。**  
 詳細については、「 [セマンティック検索のインストールと構成](install-and-configure-semantic-search.md)」を参照してください。  
  
 **FDHOST サービスをご利用いただけません、フルテキストのインデックスが失敗する原因となるもう 1 つの条件ではありますか。**  
 詳細については、「 [フルテキスト インデックスの作成のトラブルシューティング](troubleshoot-full-text-indexing.md)」を参照してください。  
  
  
