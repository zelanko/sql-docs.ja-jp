---
title: OnlineIndexOperation 要素 (DTA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- OnlineIndexOperation element
ms.assetid: 7c5614cd-09aa-4a59-9591-347aa7d36473
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 93d1f68415954a641c94e4bf107d0da59296a6ae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076550"
---
# <a name="onlineindexoperation-element-dta"></a>OnlineIndexOperation 要素 (DTA)
  データベース エンジン チューニング アドバイザーによって推奨されるインデックス、インデックス付きビュー、またはパーティションがオンラインで作成可能かどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <OnlineIndexOperation>...</OnlineIndexOperation>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|`string`、長さは無制限です。|  
|**指定できる値**|**OFF**<br /> 推奨される物理デザイン構造をオンラインで作成しません。<br /><br /> **ON**<br /> 推奨される物理デザイン構造をすべてオンラインで作成します。<br /><br /> **MIXED**<br /> データベース エンジン チューニング アドバイザーは、可能な場合にオンラインで作成できる物理デザイン構造を推奨します。<br /><br /> この要素では、上記の値のいずれか 1 つを使用してください。 インデックスがオンラインで作成される場合は、オブジェクト定義に **ONLINE = ON** が追加されます。|  
|**既定値**|[なし] :|  
|**個数**|任意。 使用する場合のみ使用できます 1 回の`TuningOptions`要素。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[TuningOptions 要素&#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**子要素**|[なし] :|  
  
## <a name="example"></a>例  
 この要素の使用例については、「[XML 入力ファイルの簡単なサンプル &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  