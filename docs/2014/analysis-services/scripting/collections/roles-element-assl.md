---
title: Roles 要素 (ASSL) |Microsoft Docs
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
- Roles Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Roles
helpviewer_keywords:
- Roles element
ms.assetid: 4191b7ce-bae4-4200-8550-3904420efafd
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b6227c72cc4fdd20b8c739bcb6019a83fbaaaa58
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37295582"
---
# <a name="roles-element-assl"></a>Roles 要素 (ASSL)
  親要素の下に定義された [Role](../objects/role-element-assl.md) 要素のコレクションを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Database> <!-- or Server -->  
   ...  
   <Roles>  
      <Role>...</Role>  
   </Roles>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Database](../objects/database-element-assl.md)、 [Server](../objects/server-element-assl.md)|  
|子要素|[ロール](../objects/role-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 `Roles` 要素に関連付けられた `Server` 要素は、サーバー管理者ロールを表す Administrators という単一のロールだけを格納します。 サーバー管理者ロールを変更または削除したり、さらにロールをコレクションに追加したりすることはできません。  
  
 `Roles` 要素に関連付けられた `Database` 要素は、そのデータベースに対して定義されたロールを格納します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.RoleCollection>します。  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
