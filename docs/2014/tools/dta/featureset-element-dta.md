---
title: FeatureSet 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- FeatureSet element
ms.assetid: f2070c53-4a5c-4c11-ac38-96ee200c84f0
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fb596ca38310bce4b9be6f1061952ebc2756fc73
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37226512"
---
# <a name="featureset-element-dta"></a>FeatureSet 要素 (DTA)
  データベース エンジン チューニング アドバイザーでの分析時に使用する物理設計構造 (インデックス、インデックス付きビュー) が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <FeatureSet>...</FeatureSet>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|`string`、長さは無制限です。|  
|**指定できる値**|**IDX_IV**<br /> インデックスおよびインデックス付きビュー。<br /><br /> **IDX**<br /> インデックスのみ。<br /><br /> **IV**<br /> インデックス付きビューのみ。<br /><br /> **NCL_IDX**<br /> 非クラスター化インデックスのみ。<br /><br /> この要素では、上記の値のいずれか 1 つを使用してください。|  
|**既定値**|**IDX**|  
|**個数**|ごとに 1 回行えば済む`TuningOptions`要素、しない限り、`DropOnlyMode`要素を使用します。 場合`DropOnlyMode`は使用できません、`FeatureSet`します。 これらの要素を同時に指定することはできません。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[TuningOptions 要素&#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**子要素**|[なし] :|  
  
## <a name="example"></a>例  
 この要素の使用例については、「[XML 入力ファイルの簡単なサンプル &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
