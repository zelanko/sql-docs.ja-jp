---
title: "Aliases 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
- Aliases Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Aliases
helpviewer_keywords:
- Aliases element
ms.assetid: 9de9e683-d30d-4d61-b32d-c5a946825742
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a2c0b1eb29df31046b0cb8175be382af50a920a3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="aliases-element-assl"></a>Aliases 要素 (ASSL)
  コレクションを格納[エイリアス](../../../analysis-services/scripting/properties/alias-element-assl.md)要素に関連付けられた、[アカウント](../../../analysis-services/scripting/objects/account-element-assl.md)要素  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Account>  
      ...  
   <Aliases>  
      <Alias>...</Alias>  
      </Aliases>  
      ...  
</Account>  
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
|親要素|[アカウント](../../../analysis-services/scripting/objects/account-element-assl.md)|  
|子要素|[[エイリアス]](../../../analysis-services/scripting/properties/alias-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**エイリアス**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Account>します。  
  
## <a name="see-also"></a>参照  
 [Accounts 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [Database 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [コレクション & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

