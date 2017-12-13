---
title: "Type 要素 (Dimension) (ASSL) |Microsoft ドキュメント"
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
apiname: Type Element (Dimension)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TYPE
helpviewer_keywords: Type element
ms.assetid: 6a2798b1-26c7-49d8-b556-e681c69d9574
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f11755a12e1876c1883b08f2460a7d8cc264dc25
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="type-element-dimension-assl"></a>Type 要素 (Dimension) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]ディメンションの内容に関する情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Dimension>  
      ...  
   <Type>...</Type>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*通常*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値によって**型**、たとえば*アカウント*、特定の動作を決定します。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*通常*|ディメンションは標準ディメンションです。|  
|*[時刻]*|ディメンションは時間ディメンションです。<br /><br /> 注: この値は、ディメンションが時間ディメンションに固有の機能をサポートしていることを示します。|  
|*Geography*|ディメンションに地域属性が含まれています。|  
|*組織*|ディメンションに組織属性が含まれています。|  
|*BillOfMaterials*|ディメンションに部品表属性が含まれています。|  
|*Accounts*|ディメンションに勘定科目関連の属性が含まれています。<br /><br /> 注: この値は、ディメンションに勘定科目ディメンションに固有の機能がサポートしていることを示します。|  
|*顧客*|ディメンションに顧客関連の属性が含まれています。|  
|*製品*|ディメンションに製品関連の属性が含まれています。|  
|*シナリオ*|ディメンションにシナリオ関連の属性が含まれています。|  
|*定量的*|ディメンションに数量属性が含まれています。|  
|*Utility*|ディメンションにユーティリティ属性が含まれています。|  
|*通貨*|ディメンションに通貨属性が含まれています。|  
|*レート*|ディメンションに換算レート属性が含まれています。|  
|*Channel*|ディメンションにチャネル属性が含まれています。|  
|*プロモーション*|ディメンションにプロモーション関連の属性が含まれています。|  
  
 許可される値に対応する列挙**型**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DimensionType>します。  
  
 親に対応する要素**型**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Dimension>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
