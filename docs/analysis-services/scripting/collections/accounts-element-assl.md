---
title: "アカウントの要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
apiname: Accounts Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Accounts
helpviewer_keywords: Accounts element
ms.assetid: 3ec62f58-c19b-4b15-b040-8941521a389b
caps.latest.revision: "44"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f4ba4f5b4334908f96c952d9676ecdb059b4a0e6
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="accounts-element-assl"></a>Accounts 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]定義されている勘定科目の種類のコレクションを格納、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Database>  
   ...  
   <Accounts>  
      <Account>...</Account>  
   </Accounts>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし (コレクション型)|  
|既定値|なし (コレクション型)|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)|  
|子要素|[アカウント](../../../analysis-services/scripting/objects/account-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 ディメンションが[型](../../../analysis-services/scripting/properties/type-element-dimension-assl.md)要素に設定されている*アカウント*できます収益や費用などのアカウントの種類を指定する属性を持つに表示され、ディメンションのメンバーによって表される。 勘定科目の種類を使用して[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)要素が[AggregationFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md)要素に設定されている*ByAccount*、ときに使用する集計関数が決定そのディメンションのメンバーを集計します。 **Accounts** 要素は、勘定科目の種類と各種類で使用される集計関数を表す **Account** 要素のコレクションを保持します。  
  
 集計関数がによって使用される既定値と異なる場合は、勘定科目の種類を表示されている必要があります[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]各アカウントの種類。  
  
 有効な勘定科目の種類のセットは固定されています。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AccountCollection>します。  
  
## <a name="see-also"></a>参照  
 [AccountType 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/accounttype-element-assl.md)   
 [コレクション &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
