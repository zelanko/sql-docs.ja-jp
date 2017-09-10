---
title: "LastUpdate 要素 (ASSL) |Microsoft ドキュメント"
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
- LastUpdate Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- LastUpdate element
ms.assetid: 639db733-a082-4f57-868d-a3bcd5e7a4f6
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0674fa178abad4b9c791a2f8db1199b1651c5957
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lastupdate-element-assl"></a>LastUpdate 要素 (ASSL)
  読み取り専用を含むれたときに最後を示すタイムスタンプ、関連付けられている[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)データベースが含まれている主要なオブジェクトのいずれかが変更されたか。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Database> <!-- or one of the elements that are listed in the Element Relationships table -->  
   ...  
   <LastUpdate>...</LastUpdate>  
   ...  
</Assembly>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|DateTime|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**LastUpdate**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.Dimension>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
