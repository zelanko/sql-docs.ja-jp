---
title: "DimensionPermission データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
apiname: DimensionPermission Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DimensionPermission data type
ms.assetid: 066405ff-903f-467a-b0d5-e58653952c52
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a9d16cbd8e19b4af5b61e68cf43685b6482419e0
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="dimensionpermission-data-type-assl"></a>DimensionPermission データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]データベース ディメンションへのアクセス許可を表す派生データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionPermission>  
   <!-- The following elements extend Permission -->  
   <AttributePermissions>...</AttributePermissions>  
   <AllowedRowsExpression>...</AllowedRowsExpression>  
</DimensionPermission>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[アクセス許可](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[AttributePermissions](../../../analysis-services/scripting/collections/attributepermissions-element-assl.md)、 [AllowedRowsExpression](../../../analysis-services/scripting/collections/attributepermissions-element-assl.md)|  
|派生要素|[DimensionPermission](../../../analysis-services/scripting/objects/dimensionpermission-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 DeploymentMode の値が 2 (テーブル サーバー モード) の場合、この要素には次の検証が適用されます。  
  
-   *AttributePermission*属性を空にする必要がありますまたはエラーが発生します。  
  
 DeploymentMode の値が 0 (OLAP) の場合、この要素には次の検証が適用されます。  
  
-   *AllowedRowsExpression*属性を空にする必要がありますまたはエラーが発生します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DimensionPermission>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
