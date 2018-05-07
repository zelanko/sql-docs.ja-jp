---
title: ImpersonationInfo データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 49dc485a9a25bd1bfceda6517dc2f7bcb3149eb2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="impersonationinfo-data-type-assl"></a>ImpersonationInfo データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  ユーザーの権限を借用するために使用される情報を表すプリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ImpersonationInfo>  
   <ImpersonationMode>...</ImpersonationMode>  
   <Account>...</Account>  
   <Password>   </Password>  
   <ImpersonationInfoSecurity>...</ImpersonationInfoSecurity>  
</ImpersonationInfo>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[アカウント](../../../analysis-services/scripting/properties/account-element-impersonationinfo-assl.md)、 [ImpersonationInfoSecurity](../../../analysis-services/scripting/properties/impersonationinfosecurity-element-assl.md)、 [ImpersonationMode](../../../analysis-services/scripting/properties/impersonationmode-element-assl.md)、[パスワード](../../../analysis-services/scripting/properties/password-element-assl.md)|  
|派生要素|[DataSourceImpersonationInfo](../../../analysis-services/scripting/properties/datasourceimpersonationinfo-element-assl.md)、 [ImpersonationInfo](../../../analysis-services/scripting/properties/impersonationinfo-element-assl.md)|  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
