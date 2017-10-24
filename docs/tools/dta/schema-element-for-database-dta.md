---
title: "Schema 要素 (DTA) データベースの |Microsoft ドキュメント"
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
- Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3362d2c40f4f62ae7529bfcfb8eb4a3ee68795dc
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="schema-element-for-database-dta"></a>Database の Schema 要素 (DTA)
  チューニングするデータベースのスキーマを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|**Server** 要素の下に指定する **Database** 要素につき 1 回の出現が必要です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[サーバー (&) #40";"DTA"&"#41; の database 要素](../../tools/dta/database-element-for-server-dta.md)|  
|**子要素**|[スキーマ (&) #40; DTA &#41; の name 要素](../../tools/dta/name-element-for-schema-dta.md)<br /><br /> [スキーマ (&) #40; DTA &#41; の table 要素](../../tools/dta/table-element-for-schema-dta.md)|  
  
## <a name="example"></a>例  
 この要素の使用例については、「[Server 要素 &#40;DTA&#41;](../../tools/dta/server-element-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

