---
title: DbTableName 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DbTableName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DbTableName
helpviewer_keywords:
- DbTableName element
ms.assetid: 842cae85-ab9c-4c75-ab44-51a4d9b1b943
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 84c0b6ecb600a21eec059b2d1ddc7184c1c46e14
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297382"
---
# <a name="dbtablename-element-assl"></a>DbTableName 要素 (ASSL)
  親要素がバインドされているテーブルの名前を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<TableBinding> <!-- or TableNotification -->  
   ...  
   <DbTableName>...</DbTableName>  
   ...  
</TableBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[TableBinding](../data-type/binding-data-type-assl.md)、 [TableNotification](../objects/tablenotification-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`DbTableName`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.TableBinding>と<xref:Microsoft.AnalysisServices.TableNotification>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
