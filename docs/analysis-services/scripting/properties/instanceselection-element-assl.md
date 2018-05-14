---
title: InstanceSelection 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 1f00127f58bb1f8c5a6792bec3ddcb8420f0d24b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="instanceselection-element-assl"></a>InstanceSelection 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  クライアント アプリケーションにヒントを提供し、一覧の予期されたアイテム数に基づいて、アイテムの一覧の表示方法を提案します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <InstanceSelection>...</InstanceSelection>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*なし*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*なし*|選択一覧は表示されません。 ユーザーは値を直接入力できます。|  
|*ドロップダウン リスト*|アイテム数は、ドロップダウン リストに表示できる数です。|  
|*一覧*|ドロップダウン リストに表示するにはアイテム数が多すぎますが、フィルターする必要はありません。|  
|*FilteredList*|アイテム数が多すぎるので、ユーザーはアイテムを表示できるようにフィルターする必要があります。|  
|*MandatoryFilter*|アイテム数が多すぎるので、表示を常にフィルターする必要があります。|  
  
 許可される値に対応する列挙**InstanceSelection**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.InstanceSelection>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
