---
title: "セマンティック検索の DDL、関数、ストアド プロシージャ、およびビュー | Microsoft Docs"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-search
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: semantic search [SQL Server], database objects
ms.assetid: 182f395f-3168-48a4-b723-ef4403544f9f
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b54e6187b386220fd6f9026358ef22522390ea94
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="semantic-search-ddl-functions-stored-procedures-and-views"></a>セマンティック検索の DDL、関数、ストアド プロシージャ、およびビュー
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の統計的セマンティック検索をサポートする Transact-SQL ステートメントおよびデータベース オブジェクトの一覧を示します。  
  
 フルテキスト検索をサポートするステートメントおよびデータベース オブジェクトの一覧については、「 [フルテキスト検索の DDL、関数、ストアド プロシージャ、およびビュー](../../relational-databases/search/full-text-search-ddl-functions-stored-procedures-and-views.md)」を参照してください。  
  
##  <a name="ddl"></a> データ定義言語 (DDL) ステートメント  
  
|オブジェクト|その他の情報|  
|------------|----------------------|  
|[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)|[テーブルおよび列に対するセマンティック検索の有効化](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)|[テーブルおよび列に対するセマンティック検索の有効化](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
  
##  <a name="func"></a> システム関数  
  
|オブジェクト|その他の情報|  
|------------|----------------------|  
|[semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md)|[セマンティック検索を使用したドキュメント内のキー フレーズの検索](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md)|  
|[semanticsimilaritydetailstable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md)|[セマンティック検索による類似および関連したドキュメントの取得](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)|  
|[semanticsimilaritytable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md)|[セマンティック検索による類似および関連したドキュメントの取得](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)|  
  
##  <a name="meta"></a> システム メタデータ関数  
  
|オブジェクト|その他の情報|  
|------------|----------------------|  
|[COLUMNPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/columnproperty-transact-sql.md)|[テーブルおよび列に対するセマンティック検索の有効化](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)|[テーブルおよび列に対するセマンティック検索の有効化](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)|[セマンティクス検索の管理および監視](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[INDEXPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)|[セマンティクス検索の管理および監視](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/objectpropertyex-transact-sql.md)|[テーブルおよび列に対するセマンティック検索の有効化](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)|[セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)|  
  
##  <a name="sproc"></a> システム ストアド プロシージャ  
  
|オブジェクト|その他の情報|  
|------------|----------------------|  
|[sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql.md)|[セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)|  
|[sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql.md)|[セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)|  
  
##  <a name="cv"></a> カタログ ビュー  
  
|オブジェクト|その他の情報|  
|------------|----------------------|  
|[sys.fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)|[セマンティクス検索の管理および監視](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md)|[セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)|  
|[sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql.md)|[セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)|  
  
##  <a name="dmv"></a> 動的管理ビュー  
  
|オブジェクト|その他の情報|  
|------------|----------------------|  
|[sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md)|[セマンティクス検索の管理および監視](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)|[セマンティクス検索の管理および監視](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)|[セマンティクス検索の管理および監視](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
  
## <a name="see-also"></a>参照  
 [セマンティクス検索の管理および監視](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
