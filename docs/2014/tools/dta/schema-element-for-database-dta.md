---
title: Database の Schema 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 74e72deb65d3f693e309926870174ebe72817c3e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63273328"
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
  
|特徴|[説明]|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|**Server** 要素の下に指定する **Database** 要素につき 1 回の出現が必要です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Server の Database 要素 &#40;DTA&#41;](database-element-for-server-dta.md)|  
|**子要素**|[Schema の Name 要素 &#40;DTA&#41;](name-element-for-schema-dta.md)<br /><br /> [Schema の Table 要素 &#40;DTA&#41;](table-element-for-schema-dta.md)|  
  
## <a name="example"></a>例  
 この要素の使用例については、「[Server 要素 &#40;DTA&#41;](server-element-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
