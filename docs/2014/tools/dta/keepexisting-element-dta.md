---
title: KeepExisting 要素 (DTA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- KeepExisting element
ms.assetid: e67aae61-d06d-4a03-85ba-6516c3502dce
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a74552aa4cf5b18273c42250f85bc48a794e1731
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085123"
---
# <a name="keepexisting-element-dta"></a>KeepExisting 要素 (DTA)
  データベース エンジン チューニング アドバイザーが、推奨設定を生成するときに保持しなければならない物理設計構造 (インデックス、インデックス付きビュー、パーティション分割) を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <KeepExisting>...</KeepExisting>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|`string`。長さの制限は、サーバーによって決まります。|  
|**指定できる値**|**NONE**<br /> 既存の構造を保持しません。<br /><br /> **ALL**<br /> 既存の構造をすべて保持します。<br /><br /> **ALIGNED**<br /> パーティションで固定された構造をすべて保持します。<br /><br /> **CL_IDX**<br /> テーブルのクラスター化インデックスをすべて保持します。<br /><br /> **IDX**<br /> テーブルのクラスター化インデックスと非クラスター化インデックスをすべて保持します。<br /><br /> この要素では、上記の値のいずれか 1 つを使用してください。|  
|**既定値**|[なし] :|  
|**個数**|任意。 につき 1 回だけ使用できます`TuningOptions`要素。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[TuningOptions 要素&#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**子要素**|[なし] :|  
  
## <a name="example"></a>例  
 この要素の使用例については、「[XML 入力ファイルの簡単なサンプル &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  