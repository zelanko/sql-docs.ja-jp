---
title: CubeDimensionPermission データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8329ba160ce4739ea1efdf91a85f75528e7b86cb
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="cubedimensionpermission-data-type-assl"></a>CubeDimensionPermission データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  キューブ内の特定のディメンションにおける 1 つのロールの権限を表すプリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeDimensionPermission>  
   <CubeDimensionID>...</CubeDimensionID>  
   <Description>...</Description>  
   <Read>...</Read>  
   <Write>...</Write>  
   <AttributePermissions>...</AttributePermissions>  
   <Annotations>...</Annotations>  
</CubeDimensionPermission>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [AttributePermissions](../../../analysis-services/scripting/collections/attributepermissions-element-assl.md)、 [CubeDimensionID](../../../analysis-services/scripting/properties/cubedimensionid-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、[読み取り](../../../analysis-services/scripting/properties/read-element-assl.md)、 [書き込み](../../../analysis-services/scripting/properties/write-element-assl.md)|  
|派生要素|[DimensionPermission](../../../analysis-services/scripting/objects/dimensionpermission-element-assl.md) ([DimensionPermissions](../../../analysis-services/scripting/collections/dimensionpermissions-element-assl.md)のコレクション[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)または[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md))|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.CubeDimensionPermission>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
