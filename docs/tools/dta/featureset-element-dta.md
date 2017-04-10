---
title: "FeatureSet 要素 (DTA) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "XML"
helpviewer_keywords: 
  - "FeatureSet 要素"
ms.assetid: f2070c53-4a5c-4c11-ac38-96ee200c84f0
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# FeatureSet 要素 (DTA)
  データベース エンジン チューニング アドバイザーでの分析時に使用する物理設計構造 (インデックス、インデックス付きビュー) が含まれます。  
  
## 構文  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <FeatureSet>...</FeatureSet>  
```  
  
## 要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|**string**、長さは無制限です。|  
|**指定できる値**|**IDX_IV**<br /> インデックスおよびインデックス付きビュー。<br /><br /> **IDX**<br /> インデックスのみ。<br /><br /> **IV**<br /> インデックス付きビューのみ。<br /><br /> **NCL_IDX**<br /> 非クラスター化インデックスのみ。<br /><br /> この要素では、上記の値のいずれか 1 つを使用してください。|  
|**既定値**|**IDX**|  
|**個数**|**TuningOptions** 要素につき 1 回の出現が必要です。ただし、**DropOnlyMode** 要素を使用している場合は別です。 **DropOnlyMode** を使用している場合は、**FeatureSet** を使用できません。 これらの要素を同時に指定することはできません。|  
  
## 要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[TuningOptions 要素 &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**子要素**|[なし] :|  
  
## 例  
 この要素の使用例については、「[XML 入力ファイルの簡単なサンプル &#40;DTA&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md)」を参照してください。  
  
## 参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  