---
title: "ServerMode 要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: c2f8cb39-dad7-433b-b7b7-fb1625f76a84
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 463af850c8af6e6db386f95be510b4eae23a5bbd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="servermode-element"></a>ServerMode 要素
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
  
  
