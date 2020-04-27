---
title: オンラインの Indexoperation 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- OnlineIndexOperation element
ms.assetid: 7c5614cd-09aa-4a59-9591-347aa7d36473
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9bb877ae48153d4fabae13170eb5f072218012d6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62657217"
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
  
|特徴|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|`string`。最大長はありません。|  
|**指定できる値**|**OFF**<br /> 推奨される物理デザイン構造をオンラインで作成しません。<br /><br /> **ON**<br /> 推奨される物理デザイン構造をすべてオンラインで作成します。<br /><br /> **混合**<br /> データベース エンジン チューニング アドバイザーは、可能な場合にオンラインで作成できる物理デザイン構造を推奨します。<br /><br /> この要素では、上記の値のいずれか 1 つを使用してください。 インデックスがオンラインで作成される場合は、オブジェクト定義に **ONLINE = ON** が追加されます。|  
|**既定値**|[なし] :|  
|**個数**|省略可能。 使用する場合は、`TuningOptions` 要素に 1 回使用できます。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[TuningOptions 要素 &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**子要素**|[なし] :|  
  
## <a name="example"></a>例  
 この要素の使用例については、「[XML 入力ファイルの簡単なサンプル &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
