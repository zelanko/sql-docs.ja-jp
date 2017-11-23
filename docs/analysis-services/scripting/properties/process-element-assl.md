---
title: "要素 (ASSL) の処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Process Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Process
helpviewer_keywords: Process element
ms.assetid: 4aa08718-be44-4781-92cf-7b32b20f862c
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7d05a61a362245c7810259c0ca01c31c374bf523
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
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
|親要素|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)、 [DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md)、 [DimensionPermission](../../../analysis-services/scripting/objects/dimensionpermission-element-assl.md)、 [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md)、 [MiningStructurePermission](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)、[権限](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**プロセス**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.CubePermission>、 <xref:Microsoft.AnalysisServices.DatabasePermission>、 <xref:Microsoft.AnalysisServices.DimensionPermission>、 <xref:Microsoft.AnalysisServices.MiningModelPermission>、 <xref:Microsoft.AnalysisServices.MiningStructurePermission>、および<xref:Microsoft.AnalysisServices.Permission>です。  
  
## <a name="see-also"></a>参照  
 [Role 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
