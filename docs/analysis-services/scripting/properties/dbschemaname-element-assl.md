---
title: "DbSchemaName 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DbSchemaName Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DbSchemaName
helpviewer_keywords:
- DbSchemaName element
ms.assetid: ae0f0edd-7b76-400d-a288-39a36d2a746b
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 97fa874f546d3ff6a4b8406e1b71c312f609cc1f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dbschemaname-element-assl"></a>DbSchemaName 要素 (ASSL)
  によって識別されるテーブル内の親要素によって使用されるスキーマの名前を含む、 [DbTableName](../../../analysis-services/scripting/properties/dbtablename-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<TableBinding> <!-- or TableNotification -->  
   ...  
   <DbSchemaName>...</DbSchemaName>  
   ...  
</TableBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[TableBinding](../../../analysis-services/scripting/data-type/tablebinding-data-type-assl.md)、 [TableNotification](../../../analysis-services/scripting/objects/tablenotification-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**DbSchemaName**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.TableBinding>と<xref:Microsoft.AnalysisServices.TableNotification>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

