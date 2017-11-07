---
title: "エイリアス要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Alias Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Alias
helpviewer_keywords:
- Alias element
ms.assetid: 674fdb06-e33c-4f35-bd6a-d9bbb13ececa
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 114a3c8a022ef55a221e2c6474f3f34ce9733f0e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alias-element-assl"></a>Alias 要素 (ASSL)
  別名を定義、[アカウント](../../../analysis-services/scripting/objects/account-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Aliases>  
      <Alias>...</Alias>  
</Aliases>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[エイリアス](../../../analysis-services/scripting/collections/aliases-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値、**エイリアス**要素がによって定義されたアカウントの代替名として使用される、**アカウント**親要素、およびユーザー アカウントの種類と集計関数の組み合わせを識別するために役立ちますインターフェイスです。  
  
 親に対応する要素、**エイリアス**分析管理オブジェクト (AMO) オブジェクト モデルのコレクションが<xref:Microsoft.AnalysisServices.Account>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

