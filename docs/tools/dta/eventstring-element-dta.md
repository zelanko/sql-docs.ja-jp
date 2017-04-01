---
title: "EventString 要素 (DTA) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
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
  - "EventString 要素"
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# EventString 要素 (DTA)
  [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ワークロードを XML 入力ファイルで直接指定します。  
  
## 構文  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## 要素の属性  
  
|属性|説明|  
|---------------|-----------------|  
|**Weight**|省略可。 対象のイベントに関するクエリの重み係数 (重要度の係数) を指定します。 重み係数の指定には、 **float** データ型を使用します。 たとえば、**Weight**="100.01" のようにします。 **Weight** に指定できる最小値は「0」です。|  
  
## 要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|**string**、長さは無制限です。|  
|**既定値**|[なし] :|  
|**個数**|他の種類のワークロードが指定されていない場合は、1 回の出現が必要です。 **EventString**親要素に対しては、 **File**、 **Database** 、または **Workload** 子要素を指定する必要がありますが、使用できるのは 1 種類だけです。 たとえば、 **EventString** 要素を使用してワークロードを指定した場合は、同じ XML 入力ファイル内でワークロードを **File** 要素で指定することはできません。|  
  
## 要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Workload 要素 &#40;DTA&#41;](../../tools/dta/workload-element-dta.md)|  
|**子要素**|[なし] :|  
  
## 例  
 この要素の使用例については、「[インライン ワークロードを使用した XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md)」を参照してください。  
  
## 参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  