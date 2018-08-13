---
title: sys.syscharsets (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 6ae1eb1439decfdf5c42d42f42c1063916f551ac
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39562856"
---
# <a name="syssyscharsets-transact-sql"></a>sys.syscharsets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  1 つの行を含みます。 各文字を設定し、並べ替え順序の定義で使用するための、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]します。 マークされている並べ替え順序のいずれかが**sysconfigures**として既定の並べ替え順序。 実際はこの並べ替え順だけが使用されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**type**|**smallint**|この行で表されるエンティティの種類。<br /><br /> 1001 = 文字セット<br /><br /> 2001 = 並べ替え順|  
|**id**|**tinyint**|文字セットまたは並べ替え順を表す一意な ID。 並べ替え順と文字セットで同じ ID を使用することはできません。 1 ～ 240 の ID は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]が使用するために予約されています。|  
|**csid**|**tinyint**|文字セットを表す行の場合、このフィールドは使用されません。 並べ替え順を表す行の場合は、その並べ替え順が適用される文字セットの ID になります。 この ID の文字セットの行が、このテーブルに存在していることが前提となります。|  
|**status**|**smallint**|内部システム状態の情報ビット。|  
|**name**|**sysname**|文字セットまたは並べ替え順を表す一意な名前。 このフィールドには、A ～ Z および a ～ z の文字、0 ～ 9 の数字、アンダースコア (_) のみが格納されます。名前は必ず文字で始まる必要があります。|  
|**description**|**nvarchar (255)**|文字セットまたは並べ替え順の特徴を表す任意の説明。|  
|**binarydefinition**|**varbinary(6000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**definition**|**image**|文字セットまたは並べ替え順の内部定義。 このフィールドのデータ構造は、この行が文字セットまたは並べ替え順のどちらを表すかによって異なります。|  
  
## <a name="see-also"></a>参照  
 [システム ビューへのシステム テーブルのマッピング&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
