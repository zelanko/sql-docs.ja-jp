---
title: dm_db_fts_index_physical_stats (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_fts_index_physical_stats_TSQL
- dm_db_fts_index_physical_stats
- dm_db_fts_index_physical_stats_TSQL
- sys.dm_db_fts_index_physical_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_fts_index_physical_stats dynamic management view
ms.assetid: 997c3278-3630-47f6-ada3-190b6c16ce0e
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4394483cd17510c998126a70c12f4d669c9282aa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68264494"
---
# <a name="sysdm_db_fts_index_physical_stats-transact-sql"></a>dm_db_fts_index_physical_stats (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  フルテキストインデックスまたはセマンティックインデックスが関連付けられている各テーブルのフルテキストインデックスまたはセマンティックインデックスごとに1行の値を返します。  
  
||||  
|-|-|-|  
|**列名**|**Type**|**説明**|  
|**object_id**|INT|インデックスを含むテーブルのオブジェクト ID。|  
|**fulltext_index_page_count**|**bigint**|インデックスページ数における抽出の論理サイズ。|  
|**keyphrase_index_page_count**|**bigint**|インデックスページ数における抽出の論理サイズ。|  
|**similarity_index_page_count**|**bigint**|インデックスページ数における抽出の論理サイズ。|  
  
## <a name="general-remarks"></a>全般的な解説  
 詳細については、「[セマンティック検索の管理と監視](../../relational-databases/search/manage-and-monitor-semantic-search.md)」を参照してください。  
  
## <a name="metadata"></a>Metadata  
 セマンティックインデックス作成の状態の詳細については、次の動的管理ビューに対してクエリを実行します。  
  
-   [dm_fts_index_population &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)  
  
-   [dm_fts_semantic_similarity_population &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)  
  
## <a name="permissions"></a>アクセス許可

で[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]は、 `VIEW SERVER STATE`権限が必要です。   
Premium [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルでは、データベース`VIEW DATABASE STATE`の権限が必要です。 Standard [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルおよび Basic レベルでは、**サーバー管理**者または**Azure Active Directory 管理者**アカウントが必要です。   

## <a name="examples"></a>例  
 次の例では、フルテキストインデックスまたはセマンティックインデックスが関連付けられているすべてのテーブル内の各フルテキストインデックスまたはセマンティックインデックスの論理サイズを照会する方法を示します。  
  
```  
SELECT * FROM sys.dm_db_fts_index_physical_stats;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セマンティクス検索の管理および監視](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
