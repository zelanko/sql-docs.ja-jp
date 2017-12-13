---
title: "CubeDimensionPermission データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: CubeDimensionPermission Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: CubeDimensionPermission
helpviewer_keywords: CubeDimensionPermission data type
ms.assetid: d9d39859-5f33-48bc-a402-0071755918de
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a2720972e89c41af585de2f4e95e109c15b44030
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="cubedimensionpermission-data-type-assl"></a>CubeDimensionPermission データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]キューブ内の特定のディメンション上の単一ロールのアクセス許可を表すプリミティブ データ型を定義します。  
  
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
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
