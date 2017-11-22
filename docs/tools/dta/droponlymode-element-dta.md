---
title: "DropOnlyMode 要素 (DTA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4ac3f3b750a5c2c5e9395900163a1db4e07c3691
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="droponlymode-element-dta"></a>DropOnlyMode 要素 (DTA)
  データベース エンジン チューニング アドバイザーのチューニング セッションで、既存のインデックス、インデックス付きビュー、パーティションの削除だけを対象にすることを指定します。 このチューニング オプションを指定すると、新しい物理設計構造は考慮の対象になりません。  
  
## <a name="syntax"></a>構文  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <DropOnlyMode>...</DropOnlyMode>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
 **データ型と長さ**  
  
 **既定値**  
  
 **出現回数**: 省略可能。 **TuningOptions** 要素につき 1 回のみ使用できます。 **TuningOptions** 要素内で以下の要素を指定する場合には使用できません。  
  
-   [FeatureSet 要素 &#40;DTA&#41;](../../tools/dta/featureset-element-dta.md)  
  
-   [Partitioning 要素 &#40;DTA&#41;](../../tools/dta/partitioning-element-dta.md)  
  
-   [KeepExisting 要素 &#40;DTA&#41;](../../tools/dta/keepexisting-element-dta.md) が **ALL** に設定されている  
  
## <a name="element-relationships"></a>要素の関係  
 **親要素**: [TuningOptions 要素 &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)  
  
 **子要素**  
  
## <a name="example"></a>例  
 次の例は、データベース エンジン チューニング アドバイザーの XML 入力ファイルの、 **DropOnlyMode** が指定された **TuningOptions** セクションを示しています。 この例では、チューニング時間は 24 時間 (1440 分) に制限されており、既存のクラスター化インデックスおよび非クラスター化インデックスはすべて削除することが検討されます。  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
