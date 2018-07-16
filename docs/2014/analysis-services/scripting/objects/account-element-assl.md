---
title: 要素 (ASSL) のアカウント |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Account Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Account
helpviewer_keywords:
- Account element
ms.assetid: 0bb7d06c-0158-4ab2-b2b1-cb50ba24f7c0
caps.latest.revision: 41
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d763b75cfb357554948565a59f5348d7fd3b725a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321174"
---
# <a name="account-element-assl"></a>Account 要素 (ASSL)
  内で勘定科目の種類に関する詳細を含む、[データベース](database-element-assl.md)要素。  
  
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
|親要素|[Accounts](../collections/accounts-element-assl.md)|  
|子要素|[AccountType](../properties/accounttype-element-assl.md)、 [AggregationFunction](../properties/aggregationfunction-element-assl.md)、[エイリアス](../collections/aliases-element-assl.md)、[注釈](../collections/annotations-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 ディメンションが[型](../properties/type-element-dimension-assl.md)要素に設定されて*アカウント、* ディメンションのメンバーに、収入、経費などのアカウントの種類を指定し、表される属性を持つことができます。 は、アカウントの種類を使用して[メジャー](measure-element-assl.md)要素が[AggregationFunction](../properties/aggregatefunction-element-assl.md)要素に設定されて*ByAccount*、ときに使用する集計関数が決定するにはそのディメンションのメンバーを集計します。 `Account` 要素は、1 つの勘定科目の種類と、このようなメジャーで使用する必要のある集計関数を表します。  
  
 集計関数がで使用される既定値と異なる場合は、勘定科目の種類を表示する必要があります[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]各アカウントの種類。  
  
 有効な勘定科目の種類のセットは固定されています。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Account>します。  
  
## <a name="see-also"></a>参照  
 [Database 要素&#40;ASSL&#41;](database-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
