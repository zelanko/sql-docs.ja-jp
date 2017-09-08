---
title: "AccountType 要素 (ASSL) |Microsoft ドキュメント"
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
- AccountType Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AccountType
helpviewer_keywords:
- AccountType element
ms.assetid: 4fdf17d3-cd84-4bf6-9baf-21e15d4bf71e
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cdb339861e5b12a9f020af51fe96847fe8ca9b36
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="accounttype-element-assl"></a>AccountType 要素 (ASSL)
  定義されている勘定科目の種類の名前を含む、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Account>  
   ...  
   <AccountType>...</AccountType>  
   ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アカウント](../../../analysis-services/scripting/objects/account-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*収入*|勘定科目は収益勘定です。|  
|*経費*|勘定科目は費用勘定です。|  
|*フロー*|勘定科目はキャッシュ フロー勘定です。|  
|*残高*|勘定科目は残高勘定です。|  
|*資産*|勘定科目は資産勘定です。|  
|*責任*|勘定科目は負債勘定です。|  
|*統計*|勘定科目は統計勘定です。|  
  
 許可される値に対応する列挙**AccountType**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.AccountTypes>します。  
  
## <a name="see-also"></a>参照  
 [Accounts 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
