---
title: AccountType 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5258ff60c8dfafefbf81f87d3538c396c085ccac
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="accounttype-element-assl"></a>AccountType 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|*Income*|勘定科目は収益勘定です。|  
|*[Expense]*|勘定科目は費用勘定です。|  
|*[Flow]*|勘定科目はキャッシュ フロー勘定です。|  
|*バランス*|勘定科目は残高勘定です。|  
|*[Asset]*|勘定科目は資産勘定です。|  
|*[Liability]*|勘定科目は負債勘定です。|  
|*統計*|勘定科目は統計勘定です。|  
  
 許可される値に対応する列挙**AccountType**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.AccountTypes>します。  
  
## <a name="see-also"></a>参照  
 [要素をアカウント&#40;ASSL&#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
