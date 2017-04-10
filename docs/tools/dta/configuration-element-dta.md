---
title: "Configuration 要素 (DTA) | Microsoft Docs"
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
  - "Configuration 要素"
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# Configuration 要素 (DTA)
  ワークロードのチューニング時にデータベース エンジン チューニング アドバイザーが分析する、既存の仮想物理設計構造から成るユーザー指定の構成を指定します。  
  
## 構文  
  
```  
  
<DTAInput>  
    <Server>...</Server>  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions  
    <Configuration [SpecificationMode="Relative" | "Absolute"]>  
    ...code removed here...  
    </Configuration>  
</DTAInput>  
```  
  
## 要素の属性  
  
|Configuration の属性|説明|  
|-----------------------------|-----------------|  
|**SpecificationMode**|省略可。 データベース エンジン チューニング アドバイザーが、指定された構成を既存の構成との関連で分析を行うか、それともまったく新しい独立した構成として分析を行うかを指定します。 この属性を指定するには **string** データ型を使用します。指定できる値は次のいずれかです。<br /><br /> **Relative**:<br />                  指定された構成を、チューニングしているデータベースにある物理設計構造の現在の既存構成 (インデックス、インデックス付きビュー、パーティション) との関連で評価します。 例:<br /><br /> `<Configuration SpecificationMode="Relative">`<br /><br /> **Absolute**:<br />                  指定された構成を、独立した構成として評価します。 Absolute が指定されると、データベース エンジン チューニング アドバイザーは既存の構成を考慮しません。 例:<br /><br /> `<Configuration SpecificationMode="Absolute">`|  
  
## 要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|省略可。 **DTAInput** 要素につき 1 回使用できます。|  
  
## 要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[DTAInput 要素 &#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)|  
|**子要素**|[Configuration の Server 要素 &#40;DTA&#41;](../../tools/dta/server-element-for-configuration-dta.md)|  
  
## 例  
 この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。  
  
## 参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  