---
title: "アカウントの要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
apiname:
- Account Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Account
helpviewer_keywords:
- Account element
ms.assetid: 0bb7d06c-0158-4ab2-b2b1-cb50ba24f7c0
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7a8e821817e523d518410c70028fd3a34a18e442
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="account-element-assl"></a>Account 要素 (ASSL)
  内の勘定科目の種類に関する詳細を含む、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Accounts>  
   <Account>  
      <AccountType>...</AccountType>  
      <AggregationFunction>...</AggregationFunction>  
            <Aliases>...</Aliases>  
            <Annotations>...</Annotations>  
   </Account>  
</Accounts>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Accounts](../../../analysis-services/scripting/collections/accounts-element-assl.md)|  
|子要素|[AccountType](../../../analysis-services/scripting/properties/accounttype-element-assl.md)、 [AggregationFunction](../../../analysis-services/scripting/properties/aggregationfunction-element-assl.md)、[エイリアス](../../../analysis-services/scripting/collections/aliases-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 ディメンションが[型](../../../analysis-services/scripting/properties/type-element-dimension-assl.md)要素に設定されている*アカウント、*ディメンションのメンバーによって表される、収益や費用などのアカウントの種類を指定する属性を持つことができます。 勘定科目の種類を使用して[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)要素が[AggregationFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md)要素に設定されている*ByAccount*、ときに使用する集計関数が決定そのディメンションのメンバーを集計します。 **アカウント**要素は、1 つのアカウントの種類とそのようなメジャーで使用される集計関数を表します。  
  
 集計関数がによって使用される既定値と異なる場合は、勘定科目の種類を表示されている必要があります[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]各アカウントの種類。  
  
 有効な勘定科目の種類のセットは固定されています。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Account>します。  
  
## <a name="see-also"></a>参照  
 [Database 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

