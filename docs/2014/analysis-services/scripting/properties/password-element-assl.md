---
title: Password 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Password Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Password element
ms.assetid: ee756b01-fb08-4a9a-8c2a-7c04af0f8658
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fcaf2b19e885577559d00337349d77cb8f732fcb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224792"
---
# <a name="password-element-assl"></a>Password 要素 (ASSL)
  ユーザー アカウントのパスワードを含む、 [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ImpersonationInfo  
   ...  
  <Password>...</Password>  
   ...  
</ImpersonationInfo>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>Remarks  
 値、`Password`の値と同様に、要素、[アカウント](account-element-impersonationinfo-assl.md)場合、偽装のために、要素が使用される値の[ImpersonationMode](impersonationmode-element-assl.md)から派生した任意の要素の要素、`ImpersonationInfo`に設定されているデータ型*ImpersonateAccount*します。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスのサーバー管理者ロールのメンバーのみが、`Password` 要素に空白の値を指定できます。  
  
## <a name="see-also"></a>関連項目  
 [DataSourceImpersonationInfo 要素&#40;ASSL&#41;](impersonationinfo-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
