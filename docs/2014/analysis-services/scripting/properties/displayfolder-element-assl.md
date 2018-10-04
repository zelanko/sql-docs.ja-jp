---
title: DisplayFolder 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DisplayFolder Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DisplayFolder
helpviewer_keywords:
- DisplayFolder element
ms.assetid: 55184c02-03e7-4d6c-b87a-d4d34bc11d0e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 73de197b50ebd3636cb97e6a011fee1e8c3a71af
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220102"
---
# <a name="displayfolder-element-assl"></a>DisplayFolder 要素 (ASSL)
  親要素を一覧表示するフォルダーを指定します。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 開発者と管理者向けのアプリケーションでは、複数の要素を視覚的に分類する表示フォルダーの使用をサポート可能性があります。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CalculationProperty> <!-- or Hierarchy, Kpi, Measure, Translation -->  
   ...  
   <DisplayFolder>...</DisplayFolder>  
   ...  
</CalculationProperty>  
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
|親要素|[CalculationProperty](../objects/calculationproperty-element-assl.md)、[階層](../objects/hierarchy-element-assl.md)、 [Kpi](../objects/kpi-element-assl.md)、[メジャー](../objects/measure-element-assl.md)、[翻訳](../objects/translation-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 比較的大きなキューブには、何百ものメジャーと階層が含まれている場合があります。 `DisplayFolder` プロパティは、クライアントにおけるユーザーの外観を定義します。 `DisplayFolder` プロパティの値には、次のいずれかのオプションが含まれている場合があります。  
  
-   空にする - メジャーがフォルダーに所属しないことを示します。  
  
-   単一のフォルダー名を含んでいる - 同じ名前のフォルダーに所属するものとしてメジャーを表示する必要があることを示します。  
  
-   円記号で区切られた複数のフォルダー名が含まれます (\\)、フォルダー階層が埋め込まを示します。  
  
 `DisplayFolder`プロパティに適用される`CalculationProperty`場合にのみ、要素の値[CalculationType](calculationtype-element-assl.md)に設定されている*メンバー*します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで `DisplayFolder` の親に対応する要素は、<xref:Microsoft.AnalysisServices.CalculationProperty>、<xref:Microsoft.AnalysisServices.Hierarchy>、<xref:Microsoft.AnalysisServices.Kpi>、<xref:Microsoft.AnalysisServices.Measure>、および <xref:Microsoft.AnalysisServices.Translation> です。  
  
## <a name="see-also"></a>参照  
 [CalculationProperties 要素&#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [MdxScript 要素&#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [MdxScripts 要素&#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
