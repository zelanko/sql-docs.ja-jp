---
title: "Configuration の Server 要素 (DTA) | Microsoft Docs"
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
  - "Server 要素"
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Configuration の Server 要素 (DTA)
  データベース エンジン チューニング アドバイザーで仮想的な構成 (**Configuration** 要素で指定する構成) を評価する対象のサーバーの識別情報が含まれます。  
  
## 構文  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## 要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|必須。**Configuration** 要素につき 1 個。|  
  
## 要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Configuration 要素 &#40;DTA&#41;](../../tools/dta/configuration-element-dta.md)|  
|**子要素**|[Server の Name 要素 &#40;DTA&#41;](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [Configuration の Database 要素 &#40;DTA&#41;](../../tools/dta/database-element-for-configuration-dta.md)|  
  
## 解説  
 **Server** 要素は、**Configuration** 要素に 1 個だけ指定できます。 この要素は、[データベース エンジン チューニング アドバイザー XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)の **ServerTypecomplexType** の名前です。 この **Server** 要素を **DTAInput** 要素の子要素と混同しないでください。 詳しくは、「[Server 要素 &#40;DTA&#41;](../../tools/dta/server-element-dta.md)」を参照してください。  
  
## 例  
 使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。  
  
## 参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  