---
title: アカウントの要素 (ASSL) |Microsoft ドキュメント
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
- Accounts Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Accounts
helpviewer_keywords:
- Accounts element
ms.assetid: 3ec62f58-c19b-4b15-b040-8941521a389b
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 30fcd1815ac785ab71c90a935b9392ab5e85e98b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070815"
---
# <a name="accounts-element-assl"></a>Accounts 要素 (ASSL)
  定義されている勘定科目の種類のコレクションを格納、[データベース](../objects/database-element-assl.md)要素。  
  
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
|親要素|[[データベース]](../objects/database-element-assl.md)|  
|子要素|[アカウント](../objects/account-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 ディメンションが[型](../properties/type-element-dimension-assl.md)要素に設定されている*アカウント*できます収益や費用などのアカウントの種類を指定する属性を持つに表示され、ディメンションのメンバーによって表される。 勘定科目の種類を使用して[メジャー](../objects/measure-element-assl.md)要素が[AggregationFunction](../properties/aggregatefunction-element-assl.md)要素に設定されている*ByAccount*、ときに使用する集計関数が決定そのディメンションのメンバーを集計します。 `Accounts` 要素は、勘定科目の種類と各種類で使用される集計関数を表す `Account` 要素のコレクションを保持します。  
  
 集計関数がによって使用される既定値と異なる場合は、勘定科目の種類を表示されている必要があります[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]各アカウントの種類。  
  
 有効な勘定科目の種類のセットは固定されています。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AccountCollection>します。  
  
## <a name="see-also"></a>参照  
 [AccountType 要素&#40;ASSL&#41;](../properties/accounttype-element-assl.md)   
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  