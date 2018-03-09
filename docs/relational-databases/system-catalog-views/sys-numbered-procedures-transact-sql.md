---
title: "sys.numbered_procedures (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.numbered_procedures_TSQL
- numbered_procedures
- sys.numbered_procedures
- numbered_procedures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.numbered_procedures catalog view
ms.assetid: 5b6d6498-bac6-4266-94b9-d16ef5089cf0
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e6a8dbd0f26b39c4fda367d2057cb9eb361586c5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysnumberedprocedures-transact-sql"></a>sys.numbered_procedures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  番号付きプロシージャとして作成された SQL Server ストアド プロシージャごとに 1 行のデータを保持します。 ベース ストアド プロシージャ (番号が 1 のもの) に対する行は表示されません。 ベース ストアド プロシージャのエントリは含まれてビューなど**sys.objects**と**sys.procedures**です。  
  
> [!IMPORTANT]  
>  番号付きプロシージャは使用されなくなりました。 番号付きプロシージャの使用はお勧めしません。 このカタログ ビューを使用するクエリをコンパイルすると、DEPRECATION_ANNOUNCEMENT イベントが発生します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ストアド プロシージャのオブジェクト ID です。|  
|**procedure_number**|**smallint**|オブジェクト内のプロシージャの番号 (2 以降)。|  
|**定義**|**nvarchar(max)**|このプロシージャを定義する SQL Server のテキストです。<br /><br /> NULL = 暗号化します。|  
  
> [!NOTE]  
>  XML および CLR パラメーターは、番号付きプロシージャではサポートされていません。  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
