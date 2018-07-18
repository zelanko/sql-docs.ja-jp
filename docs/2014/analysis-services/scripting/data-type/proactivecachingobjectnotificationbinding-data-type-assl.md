---
title: ProactiveCachingObjectNotificationBinding データ型 (ASSL) |Microsoft Docs
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
- ProactiveCachingObjectNotificationBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingObjectNotificationBinding data type
ms.assetid: b3cf5fb6-6121-4f25-8de6-f171792c440d
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 72b45eae800790497b661a82e079255651bec4d5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37330332"
---
# <a name="proactivecachingobjectnotificationbinding-data-type-assl"></a>ProactiveCachingObjectNotificationBinding データ型 (ASSL)
  情報を表す抽象派生データ型を定義、 [ProactiveCaching](../objects/proactivecaching-element-assl.md)データ ソースの変更が指定されたテーブルおよびビューまたはテーブルおよびビューの既存のデータ バインドを介して識別されるいずれかの要素キャッシュの再構築を必要とします。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ProactiveCachingObjectNotificationBinding>  
   <!-- The following elements extend ProactiveCachingBinding -->  
   <NotificationTechnique>...</NotificationTechnique>  
</ProactiveCachingObjectNotificationBinding>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[ProactiveCachingBinding](binding-data-type-assl.md)|  
|派生データ型|[ProactiveCachingInheritedBinding](inheritedbinding-data-type-assl.md)、 [ProactiveCachingTablesBinding](proactivecachingtablesbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[NotificationTechnique](../properties/notificationtechnique-element-assl.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>コメント  
 詳細については、`ProactiveCachingBinding`の継承階層のテーブルを含む、型`ProactiveCachingBinding`型を参照してください[ProactiveCachingBinding データ型&#40;ASSL&#41;](binding-data-type-assl.md)します。  
  
 詳細については、`Binding`の Analysis Services スクリプト言語 (ASSL) オブジェクトのテーブルを含む、型、`Binding`型との継承階層`Binding`型を参照してください[データ型のバインド&#40;ASSL&#41;](binding-data-type-assl.md).  
  
 ASSL でのデータ バインドの概要については、次を参照してください。[データ ソースとバインド&#40;SSAS 多次元&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ProactiveCachingObjectNotificationBinding>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
