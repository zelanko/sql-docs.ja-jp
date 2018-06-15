---
title: 書式設定要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 34220d27f4a0ca1f30b67b5066f5a06877816652
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34035093"
---
# <a name="format-element-assl"></a>Format 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  要求の形式が含まれています、 [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)要素。  
  
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
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 使用できる値、**形式**要素は、Microsoft Office Excel 形式および文字列*TrimRight*、 *TrimLeft*、 *TrimAll*、および*TrimNone*です。 トリミングの*TrimRight*既定値です。  
  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|Excel の書式設定文字列|データは、指定された名前付き書式設定文字列またはカスタム書式設定文字列に従ってフォーマットされます。 Excel によってサポートされている書式設定文字列を指定できます。|  
|*TrimAll*|データの左側と右側が切り捨てられます。|  
|*TrimLeft*|データの左側が切り捨てられます。|  
|*TrimNone*|データは切り捨てられません。|  
|*TrimRight*|データの右側が切り捨てられます。|  
  
 親に対応する要素**形式**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DataItem>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
