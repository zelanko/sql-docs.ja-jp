---
title: AccountType 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AccountType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AccountType
helpviewer_keywords:
- AccountType element
ms.assetid: 4fdf17d3-cd84-4bf6-9baf-21e15d4bf71e
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ff7203d2882689b21a6ab3171880c26a8d385f7b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173804"
---
# <a name="accounttype-element-assl"></a>AccountType 要素 (ASSL)
  定義されている勘定科目の種類の名前を含む、[データベース](../objects/database-element-assl.md)要素。  
  
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
|親要素|[アカウント](../objects/account-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*収入*|勘定科目は収益勘定です。|  
|*経費*|勘定科目は費用勘定です。|  
|*フロー*|勘定科目はキャッシュ フロー勘定です。|  
|*残高*|勘定科目は残高勘定です。|  
|*資産*|勘定科目は資産勘定です。|  
|*責任*|勘定科目は負債勘定です。|  
|*統計*|勘定科目は統計勘定です。|  
  
 許可される値に対応する列挙`AccountType`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.AccountTypes>します。  
  
## <a name="see-also"></a>参照  
 [要素をアカウント&#40;ASSL&#41;](../collections/accounts-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  