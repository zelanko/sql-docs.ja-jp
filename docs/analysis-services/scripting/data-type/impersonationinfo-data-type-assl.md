---
title: "ImpersonationInfo データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ImpersonationInfo Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: ImpersonationInfo data type
ms.assetid: 8a6b55fe-1f02-4519-bdc2-4553b576b2f3
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5aa38a49881e9d22cb5b4ad8b074ca4a2350a392
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="impersonationinfo-data-type-assl"></a>ImpersonationInfo データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]ユーザーを偽装するための情報を表すプリミティブ データ型を定義します。  
  
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
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
