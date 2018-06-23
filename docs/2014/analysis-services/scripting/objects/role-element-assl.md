---
title: Role 要素 (ASSL) |Microsoft ドキュメント
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
- Role Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ROLE
helpviewer_keywords:
- Role element
ms.assetid: 56f52462-a7fd-4b51-a7fb-4311134439e9
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ce56ee33ea5e79fcd5390e392c52506e2a270676
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175615"
---
# <a name="role-element-assl"></a>Role 要素 (ASSL)
  セキュリティ ロールに関する情報を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Roles>  
      <Role>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreateTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <Members>...</Members>  
      <Annotations>...</Annotations>  
   </Role>  
</Roles>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Roles](../collections/roles-element-assl.md)|  
|子要素|[注釈](../collections/annotations-element-assl.md)、 [CreatedTimestamp](../properties/createdtimestamp-element-assl.md)、[説明](../properties/description-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md)、[メンバー](../collections/members-element-assl.md)、[名](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 ロールの定義には、そのロールのメンバーであるユーザーが含まれています。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Role>します。  
  
## <a name="see-also"></a>参照  
 [Database 要素&#40;ASSL&#41;](database-element-assl.md)   
 [サーバー要素&#40;ASSL&#41;](server-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  