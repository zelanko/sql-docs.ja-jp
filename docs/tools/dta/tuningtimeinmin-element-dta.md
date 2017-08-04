---
title: "TuningTimeInMin 要素 (DTA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- TuningTimeInMin element
ms.assetid: 4973d9ac-20fd-4ac3-bc9f-5d60e39fdb7d
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 534f7868de00a0e102ba6f80c8663f0aaa7bf279
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="tuningtimeinmin-element-dta"></a>TuningTimeInMin 要素 (DTA)
  チューニング セッションの最大の長さを分単位で指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <TuningTimeInMin>...</TuningTimeInMin>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|**unsignedInt**、長さは無制限です。|  
|**既定値**|480 分 (8 時間)。|  
|**個数**|**NumberOfEvents** 要素に値が指定されていない限り、必須です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[TuningOptions 要素 & #40";"DTA"&"#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**子要素**|なし|  
  
## <a name="example"></a>例  
  
## <a name="description"></a>説明  
 次のコード例は、最大チューニング時間を 12 時間に設定する方法を示します。  
  
## <a name="code"></a>コード  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <TuningTimeInMin>720</TuningTimeInMin>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
