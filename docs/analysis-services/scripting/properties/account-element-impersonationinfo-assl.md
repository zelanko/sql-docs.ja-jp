---
title: アカウントの要素 (ImpersonationInfo) (ASSL) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ce73dcfc07da406c01f1df0edce01da360ecd49a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="account-element-impersonationinfo-assl"></a>Account 要素 (ImpersonationInfo) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  ユーザー アカウントの名前を含む、 [ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)データ型。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ImpersonationInfo  
   ...  
  <Account>...</Account>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値、**アカウント**の値と同様に、要素、[パスワード](../../../analysis-services/scripting/properties/password-element-assl.md)場合権限借用の目的が使用できる要素の値、 [ImpersonationMode](../../../analysis-services/scripting/properties/impersonationmode-element-assl.md)の要素派生した任意の要素、 **ImpersonationInfo**に設定されているデータ型*ImpersonateAccount*です。  
  
## <a name="see-also"></a>参照  
 [DataSourceImpersonationInfo 要素&#40;ASSL&#41;](../../../analysis-services/scripting/properties/datasourceimpersonationinfo-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
