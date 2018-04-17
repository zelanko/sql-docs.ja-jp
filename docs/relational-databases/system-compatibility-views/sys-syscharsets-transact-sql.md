---
title: sys.syscharsets (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.syscharsets
- syscharsets
- sys.syscharsets_TSQL
- syscharsets_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syscharsets system table
- sys.syscharsets compatibility view
ms.assetid: f16d987c-bd19-4668-9ef7-785b8fb9ff5b
caps.latest.revision: 42
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d3516e9d2ea65862ece3e0008cbe2848dbd66f13
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="syssyscharsets-transact-sql"></a>sys.syscharsets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  文字セットおよび並べ替え順序の定義で使用するための 1 つの行が含まれています、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]です。 マークされている並べ替え順のいずれかが**sysconfigures**として既定の並べ替え順序。 実際はこの並べ替え順だけが使用されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**type**|**smallint**|この行で表されるエンティティの種類。<br /><br /> 1001 = 文字セット<br /><br /> 2001 = 並べ替え順|  
|**id**|**tinyint**|文字セットまたは並べ替え順を表す一意な ID。 並べ替え順と文字セットで同じ ID を使用することはできません。 1 ～ 240 の ID は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]が使用するために予約されています。|  
|**csid**|**tinyint**|文字セットを表す行の場合、このフィールドは使用されません。 並べ替え順を表す行の場合は、その並べ替え順が適用される文字セットの ID になります。 この ID の文字セットの行が、このテーブルに存在していることが前提となります。|  
|**ステータス**|**smallint**|内部システム状態の情報ビット。|  
|**name**|**sysname**|文字セットまたは並べ替え順を表す一意な名前。 このフィールドには、A ～ Z および a ～ z の文字、0 ～ 9 の数字、アンダースコア (_) のみが格納されます。名前は必ず文字で始まる必要があります。|  
|**説明**|**nvarchar (255)**|文字セットまたは並べ替え順の特徴を表す任意の説明。|  
|**binarydefinition**|**varbinary(6000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**definition**|**image**|文字セットまたは並べ替え順の内部定義。 このフィールドのデータ構造は、この行が文字セットまたは並べ替え順のどちらを表すかによって異なります。|  
  
## <a name="see-also"></a>参照  
 [システム ビューへのシステム テーブルのマッピング&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
