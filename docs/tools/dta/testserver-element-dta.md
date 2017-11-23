---
title: "TestServer 要素 (DTA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: TestServer element
ms.assetid: caa3547a-2cd5-47ad-ace2-a36752835cfe
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0a8814a0447b6494adeb58a6de9897cd68137a4b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="testserver-element-dta"></a>TestServer 要素 (DTA)
  実稼働サーバーのチューニング時に使用するテスト サーバーを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<TuningOptions>  
  <TestServer>...</TestServer>  
   ...code removed here...  
</TuningOptions>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|**string**、長さは無制限です。|  
|**既定値**|[なし] :|  
|**個数**|省略可。 **TuningOptions** 要素につき 1 回使用できます。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[TuningOptions 要素 &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**子要素**|[なし] :|  
  
## <a name="example"></a>例  
 この要素の使用例では、次を参照してください。 [実稼働サーバーのチューニング負荷を軽減](../../relational-databases/performance/reduce-the-production-server-tuning-load.md)します。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
