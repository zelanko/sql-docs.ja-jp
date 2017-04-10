---
title: "Recommendation 要素 (DTA) | Microsoft Docs"
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
  - "Recommendation 要素"
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Recommendation 要素 (DTA)
  ユーザー指定の構成の一部である仮想インデックスについての情報が含まれます。  
  
## 構文  
  
```  
  
<Configuration>  
    ...code removed here...  
    <Table>  
      <Name>...</Name>  
      <Recommendation>  
      ...code removed here...  
      </Recommendation>  
```  
  
## 要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|省略可。 **Table** 要素につき 1 回使用できます。|  
  
## 要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Schema の Table 要素 &#40;DTA&#41;](../../tools/dta/table-element-for-schema-dta.md)|  
|**子要素**|[Create 要素 &#40;DTA&#41;](../../tools/dta/create-element-dta.md)<br /><br /> **Drop** 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)を参照してください。|  
  
## 解説  
 この要素は、データベース エンジン チューニング アドバイザー XML スキーマの **RecommendationTypecomplexType** の名前です。 仮想的な構成でのインデックスを指定するために使用します。 この **Recommendation** 要素を、パーティション分割を指定するための **RecommendationPType** や、ビューを指定するための **RecommendationViewType** という他の種類の要素と混同しないでください。 このような他の種類の **Recommendation** 要素の詳細については、[データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)を参照してください。  
  
## 例  
 この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。  
  
## 参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  