---
title: Trimming 要素 (ASSL) |Microsoft Docs
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
- Trimming Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Trimming
helpviewer_keywords:
- Trimming element
ms.assetid: 8b3bbf89-8309-4d00-9aea-a5918f0c7027
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d34a2b559dfcace0a8334916f66031b130763182
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37326542"
---
# <a name="trimming-element-assl"></a>Trimming 要素 (ASSL)
  データ ソースのデータを切り捨てる方法を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataItem>  
   ...  
   <Trimming>...</Trimming>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*そうです*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*左*|データの左側が切り捨てられます。|  
|*そうです*|データの右側が切り捨てられます。|  
|*LeftRight*|データの左側と右側が切り捨てられます。|  
|*なし*|データは切り捨てられません。|  
  
 許容された値に対応する列挙体`Trimming`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Trimming>します。  
  
 親に対応する要素`Trimming`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DataItem>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
