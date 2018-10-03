---
title: Alias 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Alias Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Alias
helpviewer_keywords:
- Alias element
ms.assetid: 674fdb06-e33c-4f35-bd6a-d9bbb13ececa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b894b9883fc2146ba234bccf543a0d08d436bf86
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104262"
---
# <a name="alias-element-assl"></a>Alias 要素 (ASSL)
  別名を定義、[アカウント](../objects/account-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Aliases>  
      <Alias>...</Alias>  
</Aliases>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[エイリアス](../collections/aliases-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Alias` 要素の値は、`Account` 親要素で定義された勘定科目の代替名として使用され、ユーザー インターフェイスで勘定科目の種類と集計関数の組み合わせを識別する際に役立ちます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで `Aliases` コレクションの親に対応する要素は、<xref:Microsoft.AnalysisServices.Account> です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
