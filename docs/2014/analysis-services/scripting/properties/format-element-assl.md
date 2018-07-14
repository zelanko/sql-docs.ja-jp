---
title: 要素 (ASSL) を書式設定 |Microsoft Docs
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
- Format Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Format
helpviewer_keywords:
- Format element
ms.assetid: 881ea707-52a7-46f7-ba16-ac2ec44eca22
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b8b5fdae50b38c81ad29143887717b412084c2c2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169503"
---
# <a name="format-element-assl"></a>Format 要素 (ASSL)
  要求の形式が含まれています、 [DataItem](../data-type/dataitem-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataItem>  
   ...  
   <Format>...</Format>  
      ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 使用できる値、`Format`要素は、Microsoft Office Excel 形式および文字列*TrimRight*、 *TrimLeft*、 *TrimAll*、および*TrimNone*します。 トリミングの*TrimRight*既定値です。  
  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|Excel の書式設定文字列|データは、指定された名前付き書式設定文字列またはカスタム書式設定文字列に従ってフォーマットされます。 Excel によってサポートされている書式設定文字列を指定できます。|  
|*TrimAll*|データの左側と右側が切り捨てられます。|  
|*TrimLeft*|データの左側が切り捨てられます。|  
|*TrimNone*|データは切り捨てられません。|  
|*TrimRight*|データの右側が切り捨てられます。|  
  
 親に対応する要素`Format`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DataItem>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
