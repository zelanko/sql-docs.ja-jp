---
title: "StorageBoundInMB 要素 (DTA) | Microsoft Docs"
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
  - "StorageBoundInMB 要素"
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# StorageBoundInMB 要素 (DTA)
  データベース エンジン チューニング アドバイザーのチューニング推奨設定 (インデックスとパーティション分割のセット) で使用できる最大容量を MB 単位で指定します。  
  
## 構文  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## 要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|**unsignedInt**、長さは無制限です。|  
|**既定値**|[なし] :|  
|**個数**|省略可。 **TuningOptions** 要素に 1 回だけ使用できます。|  
  
## 要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[TuningOptions 要素 &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**子要素**|なし|  
  
## 解説  
 複数のデータベースをチューニングする場合は、すべてのデータベースの推奨設定が容量計算の対象になります。 データベース エンジン チューニング アドバイザーは、既定で以下の記憶領域サイズのうちの小さい方を使用します。  
  
-   現在の生データのサイズの 3 倍 (テーブルのヒープとクラスター化インデックスの合計サイズも含まれる)  
  
-   アタッチ先のすべてのディスク ドライブの空き容量に生データのサイズを加算した値  
  
 既定の記憶領域サイズには、非クラスター化インデックスとインデックス付きビューは含まれません。  
  
 **StorageBoundInMB** 要素に指定した値が実際のディスク容量のサイズを超えている場合は、データベース エンジン チューニング アドバイザーからエラーが返されますが、チューニング自体は続行されます。 チューニングの完了後に、推奨設定を実装することにした場合はディスク容量を追加できます。  
  
## 例  
  
## 説明  
 次のコード例では、チューニングの推奨設定で使用できる最大ディスク領域として 1500 MB の制限を設定する方法を示します。  
  
## コード  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## 参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  