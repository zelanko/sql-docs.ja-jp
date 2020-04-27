---
title: SQL Server 2014 | の非推奨のフルテキスト検索機能Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- deprecated features [full-text search]
- full-text search [SQL Server], deprecated features
- full-text queries [SQL Server], proximity
ms.assetid: ab0d799c-ba79-4459-837b-c4862730dafd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1a49d7db68fe32d9794e89db66020d7f90555508
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66011399"
---
# <a name="deprecated-full-text-search-features-in-sql-server-2014"></a>SQL Server 2014 の非推奨のフルテキスト検索機能
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でまだ使用できるものの、非推奨のフルテキスト検索機能について説明します。 これらの機能は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の今後のリリースで削除される予定です。 非推奨の機能を新しいアプリケーションで使用しないでください。  
  
 非推奨の機能の使用は、**SQL Server:Deprecated Features** オブジェクトのパフォーマンス カウンターおよびトレース イベントを使用して監視できます。 詳細については、「 [SQL Server オブジェクトの使用](../performance-monitor/use-sql-server-objects.md)」を参照してください。  
  
## <a name="features-not-supported-in-the-next-version-of-sql-server"></a>SQL Server の次のバージョンでサポートされない機能  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の次のバージョンでは、次のフルテキスト検索機能はサポートされません。  
  
|非推奨の機能|代替|機能名|機能 ID|  
|------------------------|-----------------|------------------|----------------|  
|FULLTEXTCATALOGPROPERTY プロパティ: LogSize|なし。|FULLTEXTCATALOGPROPERTY **(' LogSize ')**|211|  
|FULLTEXTSERVICEPROPERTY プロパティ<br /><br /> ConnectTimeout<br /><br /> DataTimeout|なし。|FULLTEXTSERVICEPROPERTY **(' Connecttimeout ')**<br /><br /> FULLTEXTSERVICEPROPERTY **(' DataTimeout '**)|210<br /><br /> 209|  
|sp_fulltext_catalog|CREATE FULL CATALOG<br /><br /> ALTER FULLTEXT CATALOG<br /><br /> DROP FULLTEXT CATALOG|sp_fulltext_catalog|84|  
|sp_fulltext_column<br /><br /> sp_fulltext_database<br /><br /> sp_fulltext_table|CREATE FULL INDEX<br /><br /> ALTER FULLTEXT INDEX<br /><br /> DROP FULLTEXT INDEX|sp_fulltext_column<br /><br /> sp_fulltext_database<br /><br /> sp_fulltext_table|86<br /><br /> 87<br /><br /> 85|  
|sp_help_fulltext_catalogs<br /><br /> sp_help_fulltext_catalog_components<br /><br /> sp_help_fulltext_catalogs_cursor<br /><br /> sp_help_fulltext_columns<br /><br /> sp_help_fulltext_columns_cursor<br /><br /> sp_help_fulltext_tables<br /><br /> sp_help_fulltext_tables_cursor|sys.fulltext_catalogs<br /><br /> sys.fulltext_index_columns<br /><br /> sys.fulltext_indexes|sp_help_fulltext_catalogs<br /><br /> sp_help_fulltext_catalog_components<br /><br /> sp_help_fulltext_catalogs_cursor<br /><br /> sp_help_fulltext_columns<br /><br /> sp_help_fulltext_columns_cursor<br /><br /> sp_help_fulltext_table<br /><br /> sp_help_fulltext_tables_cursor|88<br /><br /> 203<br /><br /> 90<br /><br /> 92<br /><br /> 93<br /><br /> 91<br /><br /> 89|  
|sp_fulltext_service アクションの値: clean_up、connect_timeout、および data_timeout は 0 を返します|None|sp_fulltext_service @action=clean_up<br /><br /> sp_fulltext_service @action=connect_timeout<br /><br /> sp_fulltext_service @action=data_timeout|116<br /><br /> 117<br /><br /> 118|  
|sys.dm_fts_active_catalogs 列<br /><br /> is_paused<br /><br /> previous_status<br /><br /> previous_status_description<br /><br /> row_count_in_thousands<br /><br /> status<br /><br /> status_description<br /><br /> worker_count|なし。|dm_fts_active_catalogs.is_paused<br /><br /> dm_fts_active_catalogs.previous_status<br /><br /> dm_fts_active_catalogs.previous_status_description<br /><br /> dm_fts_active_catalogs.row_count_in_thousands<br /><br /> dm_fts_active_catalogs.status<br /><br /> dm_fts_active_catalogs.status_description<br /><br /> dm_fts_active_catalogs.worker_count|218<br /><br /> 221<br /><br /> 222<br /><br /> 224<br /><br /> 219<br /><br /> 220<br /><br /> 223|  
|sys.dm_fts_memory_buffers 列<br /><br /> row_count|なし。|dm_fts_memory_buffers.row_count|225|  
|sys.fulltext_catalogs 列<br /><br /> パス<br /><br /> data_space_id<br /><br /> file_id 列|なし。|fulltext_catalogs.path<br /><br /> fulltext_catalogs.data_space_id<br /><br /> fulltext_catalogs.file_id|215<br /><br /> 216<br /><br /> 217|  
  
## <a name="features-not-supported-in-a-future-version-of-sql-server"></a>SQL Server の今後のバージョンでサポートされない機能  
 以下のフルテキスト検索機能は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の次のバージョンではサポートされますが、その後のバージョンでは削除されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のどのバージョンであるかは決定していません。  
  
 **機能名** の値は、トレース イベントには ObjectName として表示され、パフォーマンス カウンターおよび sys.dm_os_performance_counters にはインスタンス名として表示されます。 **機能 ID** の値は、トレース イベントに ObjectId として表示されます。  
  
|非推奨の機能|代替|機能名|機能 ID|  
|------------------------|-----------------|------------------|----------------|  
|CONTAINS および CONTAINSTABLE 汎用 NEAR 演算子<br /><br /> {<simple_term> &#124; <prefix_term>}<br /><br /> {<br /><br /> { { NEAR &#124; ~ }    {<simple_term> &#124; <prefix_term>} } [...*n*]<br /><br /> }|カスタム NEAR 演算子<br /><br /> NEAR(<br /><br /> {   {<simple_term> &#124; <prefix_term>} [ ,...*n* ]<br /><br /> &#124; ( {<simple_term> &#124; <prefix_term>} [,...*n*] )<br /><br /> [、\<距離> [、\<注文>]]<br /><br /> }<br /><br /> )<br /><br /> \<距離>:: = {*整数*&#124;**最大**}<br /><br /> \<order>:: = {TRUE &#124; **FALSE**}|FULLTEXT_OLD_NEAR_SYNTAX|247|  
|CREATE FULLTEXT CATALOG オプション<br /><br /> パス '*rootpath*' 内<br /><br /> ON FILEGROUP *filegroup*|なし。|CREATE FULLTEXT CATLOG IN PATH<br /><br /> なし*|237<br /><br /> 存在.<sup>*</sup>|  
|DATABASEPROPERTYEX プロパティ : IsFullTextEnabled|なし。|DATABASEPROPERTYEX **(' IsFullTextEnabled ')**|202|  
|sp_detach_db オプション<br /><br /> [ @keepfulltextindexfile = ] '*KeepFulltextIndexFile*'|なし。|sp_detach_db @keepfulltextindexfile|226|  
|sp_fulltext_service アクションの値: resource_usage には機能がありません。|None|sp_fulltext_service @action=resource_usage|200|  
  
 \***SQL Server:Deprecated Features** オブジェクトは、CREATE FULLTEXT CATLOG ON FILEGROUP *filegroup*の使用を監視しません。  
  
## <a name="see-also"></a>参照  
 [SQL Server、非推奨の機能オブジェクト](../performance-monitor/sql-server-deprecated-features-object.md)   
 [フルテキスト検索の重大な変更](../../database-engine/breaking-changes-to-full-text-search.md)   
 [SQL Server 2014 データベース エンジンの非推奨の機能](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
