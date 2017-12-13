---
title: "ServerMode 要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
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
ms.openlocfilehash: fed7da390c26a970b0407a13698bb5623c01a320
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="servermode-element"></a>ServerMode 要素
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]**ServerMode**サーバー要素は、動作中のサーバー モードを指定します。  
  
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
  
  
