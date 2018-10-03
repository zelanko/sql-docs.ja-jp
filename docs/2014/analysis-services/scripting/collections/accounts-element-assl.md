---
title: 要素 (ASSL) のアカウント |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d0dd0fabf7ebfc6ee020a533149b73e72f7a8a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126142"
---
# <a name="accounts-element-assl"></a>Accounts 要素 (ASSL)
  定義されている勘定科目の種類のコレクションを格納する[データベース](../objects/database-element-assl.md)要素。  
  
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
 ディメンションが[型](../properties/type-element-dimension-assl.md)要素に設定されて*アカウント*できます収益、経費などのアカウントの種類を指定する属性をしていて、そのディメンションのメンバーによって表されます。 は、アカウントの種類を使用して[メジャー](../objects/measure-element-assl.md)要素が[AggregationFunction](../properties/aggregatefunction-element-assl.md)要素に設定されて*ByAccount*、ときに使用する集計関数が決定するにはそのディメンションのメンバーを集計します。 `Accounts` 要素は、勘定科目の種類と各種類で使用される集計関数を表す `Account` 要素のコレクションを保持します。  
  
 集計関数がで使用される既定値と異なる場合は、勘定科目の種類を表示する必要があります[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]各アカウントの種類。  
  
 有効な勘定科目の種類のセットは固定されています。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AccountCollection>します。  
  
## <a name="see-also"></a>参照  
 [AccountType 要素&#40;ASSL&#41;](../properties/accounttype-element-assl.md)   
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
