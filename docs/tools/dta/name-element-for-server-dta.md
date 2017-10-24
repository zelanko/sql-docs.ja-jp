---
title: "サーバー (DTA) の要素の名前を付けます |Microsoft ドキュメント"
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
- Name element
ms.assetid: 4c94754d-6d62-4357-8ce7-f107ebf90c71
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 98b9748db2c405491ed94568de25525e208c2ff4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="name-element-for-server-dta"></a>Server の Name 要素 (DTA)
  チューニングするデータベースが置かれているサーバーの名前が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
  
...code removed here...  
<Server>  
    <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|**string**、1 ～ 255 文字。|  
|**既定値**|[なし] :|  
|**個数**|**Server** 要素につき 1 回の出現が必要です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Server 要素 & #40";"DTA"&"#41;](../../tools/dta/server-element-dta.md)|  
|**子要素**|[なし] :|  
  
## <a name="example"></a>例  
 この **Name** 要素の使用例については、「[Server 要素 &#40;DTA&#41;](../../tools/dta/server-element-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

