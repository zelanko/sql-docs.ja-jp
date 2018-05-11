---
title: Type 要素 (Dimension) (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4455b2f18f19f3e884be07ed4bed344bf1485bd1
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="type-element-dimension-assl"></a>Type 要素 (Dimension) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  ディメンションのコンテンツに関する情報を提供します。  
  
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
|既定値|*Regular*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値によって**型**、たとえば*アカウント*、特定の動作を決定します。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*Regular*|ディメンションは標準ディメンションです。|  
|*[時刻]*|ディメンションは時間ディメンションです。<br /><br /> 注: この値は、ディメンションが時間ディメンションに固有の機能をサポートしていることを示します。|  
|*Geography*|ディメンションに地域属性が含まれています。|  
|*組織*|ディメンションに組織属性が含まれています。|  
|*BillOfMaterials*|ディメンションに部品表属性が含まれています。|  
|*Accounts*|ディメンションに勘定科目関連の属性が含まれています。<br /><br /> 注: この値は、ディメンションに勘定科目ディメンションに固有の機能がサポートしていることを示します。|  
|*Customers*|ディメンションに顧客関連の属性が含まれています。|  
|*製品*|ディメンションに製品関連の属性が含まれています。|  
|*シナリオ*|ディメンションにシナリオ関連の属性が含まれています。|  
|*Quantitative*|ディメンションに数量属性が含まれています。|  
|*Utility*|ディメンションにユーティリティ属性が含まれています。|  
|*Currency*|ディメンションに通貨属性が含まれています。|  
|*レート*|ディメンションに換算レート属性が含まれています。|  
|*Channel*|ディメンションにチャネル属性が含まれています。|  
|*Promotion*|ディメンションにプロモーション関連の属性が含まれています。|  
  
 許可される値に対応する列挙**型**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DimensionType>します。  
  
 親に対応する要素**型**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Dimension>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
