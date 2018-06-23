---
title: 書式設定要素 (ASSL) |Microsoft ドキュメント
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b7434ba5d6e2db8d2a2e665fa333799b6b2e9eb8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176497"
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
 使用できる値、`Format`要素は、Microsoft Office Excel 形式および文字列*TrimRight*、 *TrimLeft*、 *TrimAll*、および*TrimNone*です。 トリミングの*TrimRight*既定値です。  
  
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
  
  