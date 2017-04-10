---
title: "Column の Name 要素 (DTA) | Microsoft Docs"
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
  - "Name 要素"
ms.assetid: f93b61de-01fe-4237-ada4-f1e481550564
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# Column の Name 要素 (DTA)
  ユーザー指定の構成におけるインデックス列の名前を指定します。  
  
## 構文  
  
```  
  
<Index>  
    <Column>  
        <Name>...</Name>  
```  
  
## 要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|**string**、長さは無制限です。|  
|**既定値**|[なし] :|  
|**個数**|**Column** 要素につき 1 回の出現が必要です。|  
  
## 要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Index の Column 要素 &#40;DTA&#41;](../../tools/dta/column-element-for-index-dta.md)|  
|**子要素**|[なし] :|  
  
## 例  
 この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。  
  
## 参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  