---
title: DISCOVER_KEYWORDS 行セット (OLE DB for OLAP) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d4ba6c7ee41c8018af30635d7d28d1e7871f81b9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="discoverkeywords-rowset-ole-db-for-olap"></a>DISCOVER_KEYWORDS 行セット (OLE DB for OLAP)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  プロバイダーの予約語の一覧を列挙します。  
  
## <a name="rowset-columns"></a>行セットの列  
 DISCOVER_KEYWORDS 行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**Keyword**|**DBTYPE_WSTR**||予約キーワード。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 DISCOVER_KEYWORDS 行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**Keyword**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
