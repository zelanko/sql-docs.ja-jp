---
title: RoleID 要素 (ASSL) |Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 710306c1a31a188bea19b7bf53e7ac2c7324c00d
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38007224"
---
# <a name="roleid-element-assl"></a>RoleID 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  権限が定義されているロールを識別します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Permission> <!-- or one of the listed below in the Element Relationships table -->  
   ...  
   <RoleID>...</RoleID>  
   ...  
</Permission>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)、 [DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md)、 [DimensionPermission](../../../analysis-services/scripting/objects/dimensionpermission-element-assl.md)、 [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md)、 [MiningStructurePermission](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)、[アクセス許可](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素**RoleID**分析管理オブジェクト (AMO) オブジェクト モデルは、 <xref:Microsoft.AnalysisServices.CubePermission>、 <xref:Microsoft.AnalysisServices.DatabasePermission>、 <xref:Microsoft.AnalysisServices.DimensionPermission>、 <xref:Microsoft.AnalysisServices.MiningModelPermission>、 <xref:Microsoft.AnalysisServices.MiningStructurePermission>、および<xref:Microsoft.AnalysisServices.Permission>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
