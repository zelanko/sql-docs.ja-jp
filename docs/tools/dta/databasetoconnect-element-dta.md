---
title: "DatabaseToConnect 要素 (DTA) | Microsoft Docs"
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
  - "DatabaseToConnect 要素"
ms.assetid: 65153a66-3aee-4429-99b7-0816ac23c285
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# DatabaseToConnect 要素 (DTA)
  データベース エンジン チューニング アドバイザーがワークロードのチューニング時に最初に接続するデータベースを指定します。  
  
## 構文  
  
```  
  
    <TuningOptions>  
...code removed here...  
      <DatabaseToConnect>...</DatabaseToConnect>  
```  
  
## 要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|**string**、長さは無制限です。|  
|**既定値**|[なし] :|  
|**個数**|省略可。 **TuningOptions** 要素につき 1 回使用できます。|  
  
## 要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[TuningOptions 要素 &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**子要素**|なし|  
  
## 解説  
 **DatabaseToConnect** は、データベース エンジン チューニング アドバイザーがチューニング セッションの開始時に最初に接続するデータベースの名前を指定するために使用します。 この要素では、データベースを 1 つだけ指定できます。 複数のデータベース名が指定されていると、データベース エンジン チューニング アドバイザーはエラーを返します。  
  
## 例  
 使用例については、「[インライン ワークロードを指定した XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md)」を参照してください。  
  
## 参照  
 [XML 入力ファイル リファレンス &#40;Database Engine Tuning Advisor&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  