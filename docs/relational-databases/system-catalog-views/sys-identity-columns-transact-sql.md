---
title: sys.identity_columns (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- identity_columns
- sys.identity_columns
- sys.identity_columns_TSQL
- identity_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.identity_columns catalog view
ms.assetid: 97ee01e6-9c9e-4fd9-884b-68b4084669d5
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 7117374ced64a6ed130d84b70de3f1334d8d7ca7
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39543362"
---
# <a name="sysidentitycolumns-transact-sql"></a>sys.identity_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ID 列ごとに 1 行のデータを保持します。  
  
 **Sys.identity_columns**ビューから行を継承する、 **sys.columns**ビュー。 **Sys.identity_columns**ビュー内の列を返します、 **sys.columns**ビューだけでなく、 **seed_value**、 **increment_value**、 **last_value**、および**is_not_for_replication**列。 詳細については、「[カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)」を参照してください。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**\<sys.columns から継承された列 >**||**Sys.identity_columns**ビューは、すべての列を返します、 **sys.columns**ビュー。 また、次に示す追加の列も返します。 列の説明を**sys.identity_columns**ビューが継承**sys.columns**を参照してください[sys.columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)します。|  
|**seed_value**|**sql_variant**|この ID 列に対するシード値です。 シード値のデータ型は、列自体のデータ型と同じです。|  
|**increment_value**|**sql_variant**|この ID 列に対する増分値です。 シード値のデータ型は、列自体のデータ型と同じです。|  
|**last_value**|**sql_variant**|この ID 列に対して生成された最後の値です。 シード値のデータ型は、列自体のデータ型と同じです。|  
|**is_not_for_replication**|**bit**|ID 列は NOT FOR REPLICATION と宣言されます。|  
  
> [!NOTE]  
>  複数のテーブルで使用できる自動的に増分する番号、またはテーブルを参照せずにアプリケーションから呼び出すことができる自動的に増分する番号を作成するには、「[シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
