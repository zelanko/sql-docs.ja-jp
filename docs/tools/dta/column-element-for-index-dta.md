---
title: "Index の Column 要素 (DTA) | Microsoft Docs"
ms.custom: ""
ms.date: "03/09/2017"
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
  - "Column 要素"
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# Index の Column 要素 (DTA)
  ユーザー指定の構成で、インデックスを作成する列を指定します。  
  
## 構文  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## 要素の属性  
  
 **Type**: 省略可。 インデックスの列の種類を指定します。 この属性を指定するには **string** データ型を使用します。指定できる値は次のいずれかです。  
  
-   **KeyColumn**  
  
     列がインデックス キーによって参照されていることを指定します。 この属性を設定するには、以下の構文を使用します。  
  
    ```  
    <Column Type="KeyColumn">  
    ```  
  
     キー列の詳細については、「[クラスター化インデックスと非クラスター化インデックスの概念](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)」を参照してください。  
  
-   **IncludedColumn**  
  
     列がキー列ではなく、付加列であることを指定します。 この属性を設定するには、以下の構文を使用します。  
  
    ```  
    <Column Type="IncludedColumn">  
    ```  
  
     付加列の詳細については、「[付加列インデックスの作成](../../relational-databases/indexes/create-indexes-with-included-columns.md)」を参照してください。  
  
 **SortOrder**: 省略可。 列の並べ替え順を指定します。 **string** データ型を使用して、**"Ascending"** または **"Descending"** の並べ替え順のいずれかを以下のように指定します。  
  
```  
<Column SortOrder="Ascending">  
```  
  
## 要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|**Index** 要素につき 1024 列まで指定できます。|  
  
## 要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Index 要素 &#40;DTA&#41;](../../tools/dta/index-element-dta.md)|  
|**子要素**|[Column の Name 要素 &#40;DTA&#41;](../../tools/dta/name-element-for-column-dta.md)|  
  
## 例  
 この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。  
  
## 参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  