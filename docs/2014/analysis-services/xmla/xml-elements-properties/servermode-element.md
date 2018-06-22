---
title: ServerMode 要素 |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c2f8cb39-dad7-433b-b7b7-fb1625f76a84
caps.latest.revision: 6
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 8448e5ac3111f4c1683ae3dd62dcaef992f3f0e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071032"
---
# <a name="servermode-element"></a>ServerMode 要素
  `ServerMode` サーバー要素は、サーバーが動作しているモードを指定します。  
  
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
|親要素|[[サーバー]](../../scripting/objects/server-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 サーバーは、次のモードのいずれかで動作します。  
  
|値|説明|  
|-----------|-----------------|  
|*多次元*|多次元モードおよびデータ マイニング モード|  
|*表形式*|テーブル モード|  
|*SharePoint*|SharePoint モード|  
  
## <a name="see-also"></a>参照  
 [[サーバー]](../../scripting/objects/server-element-assl.md)  
  
  