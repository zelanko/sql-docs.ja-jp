---
title: アカウントの要素 (ImpersonationInfo) (ASSL) |Microsoft ドキュメント
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
- Account Element (ImpersonationInfo)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Account element
ms.assetid: aa3a1281-e42a-4926-875b-e6b81f4599c3
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 454e46b3515ebd6b5ad8e8193edbc2a9aea14562
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076061"
---
# <a name="account-element-impersonationinfo-assl"></a>Account 要素 (ImpersonationInfo) (ASSL)
  ユーザー アカウントの名前を含む、 [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)データ型。  
  
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
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 値、`Account`の値と同様に、要素、[パスワード](password-element-assl.md)場合権限借用の目的が使用できる要素の値、 [ImpersonationMode](impersonationmode-element-assl.md)から派生した要素の`ImpersonationInfo`に設定されているデータ型*ImpersonateAccount*です。  
  
## <a name="see-also"></a>参照  
 [DataSourceImpersonationInfo 要素&#40;ASSL&#41;](impersonationinfo-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  