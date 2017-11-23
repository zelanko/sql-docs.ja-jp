---
title: "sys.sql_dependencies (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sql_dependencies
- sql_dependencies_TSQL
- sys.sql_dependencies_TSQL
- sys.sql_dependencies
dev_langs: TSQL
helpviewer_keywords: sys.sql_dependencies catalog view
ms.assetid: 1779aa87-a0b8-470a-a286-d7cc0b93ad2e
caps.latest.revision: "31"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ae071c927ab60f5b93e69a43d7ad443d333aa856
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syssqldependencies-transact-sql"></a>sys.sql_dependencies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  それぞれの依存関係の参照先エンティティの行が含まれています、[!INCLUDE[tsql](../../includes/tsql-md.md)]式またはその他の参照元オブジェクトを定義するステートメント。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して[sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)代わりにします。  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**クラス**|**tinyint**|参照先エンティティのクラスを識別します。<br /><br /> 0 = オブジェクトまたは列 (非スキーマ バインド参照のみ)<br /><br /> 1 = オブジェクトまたは列 (スキーマ バインド参照)<br /><br /> 2 = 型 (スキーマ バインド参照)<br /><br /> 3 = XML スキーマ コレクション (スキーマ バインド参照)<br /><br /> 4 = パーティション関数 (スキーマ バインド参照)|  
|**class_desc**|**nvarchar (60)**|参照先エンティティのクラスの説明です。<br /><br /> **OBJECT_OR_COLUMN_REFERENCE_NON_SCHEMA_BOUND**<br /><br /> **OBJECT_OR_COLUMN_REFERENCE_SCHEMA_BOUND**<br /><br /> **TYPE_REFERENCE**<br /><br /> **XML_SCHEMA_COLLECTION_REFERENCE**<br /><br /> **PARTITION_FUNCTION_REFERENCE**|  
|**object_id**|**int**|参照元オブジェクトの ID です。|  
|**column_id**|**int**|参照元の ID が列の場合、参照元の列の ID です。それ以外の場合は 0 です。|  
|**referenced_major_id**|**int**|次の定義に従ってクラスの値によって解釈される、参照先エンティティの ID です。<br /><br /> 0、1 = オブジェクトまたは列のオブジェクト ID<br /><br /> 2 = 型 ID<br /><br /> 3 = XML スキーマ コレクション ID|  
|**referenced_minor_id**|**int**|クラスの値によって次に示すように解釈される、参照先エンティティの補助 ID です。<br /><br /> この値は、class の値によって異なります。<br /><br /> 0、 **referenced_minor_id**は列 ID です。 または、列ではない場合は 0 です。<br /><br /> 1、 **referenced_minor_id**は列 ID です。 または、列ではない場合は 0 です。<br /><br /> それ以外の場合、 **referenced_minor_id** 0 を = です。|  
|**is_selected**|**bit**|オブジェクトまたは列が選択されています。|  
|**is_updated**|**bit**|オブジェクトまたは列が更新されています。|  
|**is_select_all**|**bit**|オブジェクトが SELECT * 句で使用されています (オブジェクトレベルのみ)。|  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
