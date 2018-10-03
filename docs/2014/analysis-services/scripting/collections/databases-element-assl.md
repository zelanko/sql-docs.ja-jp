---
title: Databases 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Databases Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Databases
helpviewer_keywords:
- Databases element
ms.assetid: 2806a074-d47e-4434-9599-04888783770f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3af81be44fa860f3db6e226078b51f29b0cb54ff
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172942"
---
# <a name="databases-element-assl"></a>Databases 要素 (ASSL)
  コレクションを格納[データベース](../objects/database-element-assl.md)要素に関連付けられた、 [Server](../objects/server-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Server>  
      ...  
   <Databases>  
      <Database>...</Database>  
      </Databases>  
   ...  
</Server>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[サーバー]](../objects/server-element-assl.md)|  
|子要素|[[データベース]](../objects/database-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DatabaseCollection>します。  
  
## <a name="see-also"></a>関連項目  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
