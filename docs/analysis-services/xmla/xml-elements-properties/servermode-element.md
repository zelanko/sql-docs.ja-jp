---
title: ServerMode 要素 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 362e91994f4c195a6fe2d48a798444041d6855e8
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="servermode-element"></a>ServerMode 要素
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  **ServerMode**サーバー要素は、動作中のサーバー モードを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Server>  
...  
   <ddl300:ServerMode>...</ddl300:ServerMode>  
...  
</Server>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|(なし)|  
|Cardinality|0-1: 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[サーバー]](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 サーバーは、次のモードのいずれかで動作します。  
  
|値|Description|  
|-----------|-----------------|  
|*多次元*|多次元モードおよびデータ マイニング モード|  
|*表形式*|テーブル モード|  
|*SharePoint*|SharePoint モード|  
  
## <a name="see-also"></a>参照  
 [[サーバー]](../../../analysis-services/scripting/objects/server-element-assl.md)  
  
  
