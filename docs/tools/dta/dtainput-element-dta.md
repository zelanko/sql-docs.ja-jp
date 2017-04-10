---
title: "DTAInput 要素 (DTA) | Microsoft Docs"
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
  - "DTAInput 要素"
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# DTAInput 要素 (DTA)
  データベース エンジン チューニング アドバイザーに対する XML 入力の定義が含まれます。  
  
## 構文  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## 要素の特性  
  
|特性|説明|  
|---------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|**DTAXML** 要素につき 1 回 (省略可)。|  
  
## 要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[DTAXML 要素 &#40;DTA&#41;](../../tools/dta/dtaxml-element-dta.md)|  
|**子要素**|[Server 要素 &#40;DTA&#41;](../../tools/dta/server-element-dta.md)<br /><br /> [Workload 要素 &#40;DTA&#41;](../../tools/dta/workload-element-dta.md)<br /><br /> [TuningOptions 要素 &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)<br /><br /> [Configuration 要素 &#40;DTA&#41;](../../tools/dta/configuration-element-dta.md)|  
  
## 解説  
 この要素は、データベース エンジン チューニング アドバイザーの入力スキーマ階層のルートです。 データベース エンジン チューニング アドバイザーへの入力としては、チューニング対象のデータベースのサーバー、ワークロード、チューニング オプション、ユーザー指定の構成などを指定した引数を使用できます。  
  
## 例  
 **DTAInput** 要素の使用例については、「[XML 入力ファイルの簡単なサンプル &#40;DTA&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md)」を参照してください。  
  
## 参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  