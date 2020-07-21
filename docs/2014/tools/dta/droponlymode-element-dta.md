---
title: DropOnlyMode 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 72c3ada0e524287073f1ecf0d5a2fa633566a6c3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85000311"
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
  
|特徴|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|省略可能。 `TuningOptions` 要素につき 1 回だけ使用できます。 `TuningOptions` 要素内で以下の要素を指定する場合には使用できません。<br /><br /> [FeatureSet 要素 &#40;DTA&#41;](featureset-element-dta.md)<br /><br /> [Partitioning 要素 &#40;DTA&#41;](partitioning-element-dta.md)<br /><br /> [KeepExisting 要素 &#40;DTA&#41;](keepexisting-element-dta.md) が **ALL** に設定されている|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[TuningOptions 要素 &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**子要素**|[なし] :|  
  
## <a name="example"></a>例  
 次の例は、データベース エンジン チューニング アドバイザーの XML 入力ファイルの、`TuningOptions` が指定された `DropOnlyMode` セクションを示しています。 この例では、チューニング時間は 24 時間 (1440 分) に制限されており、既存のクラスター化インデックスおよび非クラスター化インデックスはすべて削除することが検討されます。  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
