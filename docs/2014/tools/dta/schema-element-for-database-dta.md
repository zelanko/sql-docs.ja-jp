---
title: Schema 要素 (DTA) データベースの |Microsoft ドキュメント
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
- Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 4bcdcba472eb2a439d7786898f30b09d7e1dc50f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164479"
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
|**親要素**|[Server の database 要素&#40;DTA&#41;](database-element-for-server-dta.md)|  
|**子要素**|[スキーマの要素の名前を付けます&#40;DTA&#41;](name-element-for-schema-dta.md)<br /><br /> [スキーマの要素をテーブル&#40;DTA&#41;](table-element-for-schema-dta.md)|  
  
## <a name="example"></a>例  
 この要素の使用例については、「[Server 要素 &#40;DTA&#41;](server-element-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  