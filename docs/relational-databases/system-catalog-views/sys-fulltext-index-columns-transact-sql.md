---
title: "sys.fulltext_index_columns (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.fulltext_index_columns
- fulltext_index_columns
- sys.fulltext_index_columns_TSQL
- fulltext_index_columns_TSQL
dev_langs: TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], columns
- sys.fulltext_index_columns catalog view
- full-text indexes [SQL Server], properties
ms.assetid: c34b8625-e53c-4281-ace6-d46230d5cb84
caps.latest.revision: "27"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ea0b235c347f9d06f0ea87462c62e5d02629ccd7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysfulltextindexcolumns-transact-sql"></a>sys.fulltext_index_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  フルテキスト インデックスの一部となっている列ごとに 1 行のデータを格納します。    
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|列が属するオブジェクトの ID。|  
|**column_id**|**int**|フルテキスト インデックスの一部となっている列の ID。|  
|**type_column_id**|**int**|特定の行にあるドキュメント関するユーザー指定ドキュメント ファイル拡張子 (".doc"、".xls" など) を格納する型列の ID。 型列は、フルテキスト インデックスの作成中にフィルター選択する必要のあるデータを含む列に対してのみ指定されます。 該当しない場合は NULL になります。 詳細については、「 [検索用フィルターの構成と管理](../../relational-databases/search/configure-and-manage-filters-for-search.md)」を参照してください。|  
|**language_id**|**int**|このフルテキスト列にインデックスを付けるために使用するワード ブレーカーの言語の LCID。<br /><br /> 0 = ニュートラル。<br /><br /> 詳細については、次を参照してください。 [sys.fulltext_languages &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).|  
|**statistical_semantics**|**int**|1 = この列では、フルテキスト インデックス作成に加えて、統計的セマンティクスが有効になっています。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
