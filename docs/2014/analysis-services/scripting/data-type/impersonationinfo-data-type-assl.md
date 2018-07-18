---
title: ImpersonationInfo データ型 (ASSL) |Microsoft Docs
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
- ImpersonationInfo Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ImpersonationInfo data type
ms.assetid: 8a6b55fe-1f02-4519-bdc2-4553b576b2f3
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 25321c491db72fb61770b48a3d75743cf50276bd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37310732"
---
# <a name="impersonationinfo-data-type-assl"></a>ImpersonationInfo データ型 (ASSL)
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
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[アカウント](../properties/account-element-impersonationinfo-assl.md)、 [ImpersonationInfoSecurity](../properties/impersonationinfosecurity-element-assl.md)、 [ImpersonationMode](../properties/impersonationmode-element-assl.md)、[パスワード](../properties/password-element-assl.md)|  
|派生要素|[DataSourceImpersonationInfo](../properties/impersonationinfo-element-assl.md)、 [ImpersonationInfo](../properties/impersonationinfo-element-assl.md)|  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
