---
title: 要素 (ASSL) の処理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Process Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Process
helpviewer_keywords:
- Process element
ms.assetid: 4aa08718-be44-4781-92cf-7b32b20f862c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af200735a07812720110df6665cffcfbdf34db10
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216610"
---
# <a name="process-element-assl"></a>Process 要素 (ASSL)
  ユーザーが親要素の所有者を処理できるかどうかを決定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Permission> <-- or one of the other elements contained in the Element Relationships table -->  
   ...  
   <Process>...</Process>  
   ...  
</Permission>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|False|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubePermission](../objects/cubepermission-element-assl.md)、 [DatabasePermission](../objects/databasepermission-element-assl.md)、 [DimensionPermission](../objects/dimensionpermission-element-assl.md)、 [MiningModelPermission](../objects/miningmodelpermission-element-assl.md)、 [MiningStructurePermission](../objects/miningstructurepermission-element-assl.md)、[アクセス許可](../data-type/permission-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで `Process` の親に対応する要素は、<xref:Microsoft.AnalysisServices.CubePermission>、<xref:Microsoft.AnalysisServices.DatabasePermission>、<xref:Microsoft.AnalysisServices.DimensionPermission>、<xref:Microsoft.AnalysisServices.MiningModelPermission>、<xref:Microsoft.AnalysisServices.MiningStructurePermission>、および <xref:Microsoft.AnalysisServices.Permission> です。  
  
## <a name="see-also"></a>参照  
 [Role 要素&#40;ASSL&#41;](../objects/role-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
