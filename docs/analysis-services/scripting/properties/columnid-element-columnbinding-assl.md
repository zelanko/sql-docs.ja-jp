---
title: "ColumnID 要素 (ColumnBinding) (ASSL) |Microsoft ドキュメント"
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
apiname: ColumnID Element (ColumnBinding)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ColumnID
helpviewer_keywords: ColumnID element
ms.assetid: f4edf532-7e40-4ee2-9b5e-48b3c3de7a74
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8770dff41d52939a3d8c311674d816bb1a16257f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="columnid-element-columnbinding-assl"></a>ColumnID 要素 (ColumnBinding) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]データ項目がバインドされているテーブル内の列の識別子 (ID) が含まれています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ColumnBinding>  
   ...  
   <ColumnID>...</ColumnID>  
   ...  
</ColumnBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**ColumnID**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ColumnBinding>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
