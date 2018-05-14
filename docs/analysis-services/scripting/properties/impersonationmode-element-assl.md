---
title: ImpersonationMode 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 786bc8e9ededa556d6d66d75e8e2cc52315cc62a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="impersonationmode-element-assl"></a>ImpersonationMode 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  派生した要素の権限借用の方法を示す値を含む、 [ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)データ型。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ImpersonationInfo>  
   ...  
   <ImpersonationMode>...</ImpersonationMode>  
  
</ImpersonationInfo>...  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*[Default]*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*[Default]*|親は、権限借用を使用するコンテキストに最適な権限借用方法を使用します。|  
|*権限借用アカウント*|親は、親要素で指定されているユーザー アカウントの資格情報を使用します。|  
|*ImpersonateAnonymous*|親は、匿名ユーザーの資格情報を使用します。|  
|*ImpersonateCurrentUser*|親は、現在のユーザーの資格情報を使用します。|  
|*ImpersonateServiceAccount*|親のインスタンスに関連付けられているサービス アカウントの資格情報を使用して[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。|  
  
 許可される値に対応する列挙**ImpersonationMode**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ImpersonationLevel>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
