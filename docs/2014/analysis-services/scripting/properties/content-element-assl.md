---
title: コンテンツの要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Content Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Content
helpviewer_keywords:
- Content element
ms.assetid: 221addef-2f88-49c5-b8f5-9eee330497a9
caps.latest.revision: 42
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bd9e3c237d8009ac153e8c69033ce9cce958aba3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267478"
---
# <a name="content-element-assl"></a>Content 要素 (ASSL)
  内の列のコンテンツについて説明します、 [MiningStructure](../objects/miningstructure-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ScalarMiningStructureColumn>  
   ...  
   <Content>...</Content>  
   ...  
</ScalarMiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この列挙は、マイニング構造列によって表されるコンテンツの種類を示します。マイニング アルゴリズム プロバイダーでの必要に応じて拡張することができます。 コンテンツの種類の詳細については、「[コンテンツの種類 (データ マイニング)](../../data-mining/content-types-data-mining.md)」を参照してください。  
  
 すべてのマイニング アルゴリズム プロバイダーで一般的にサポートされる値を次の表に示します。  
  
|値|説明|  
|-----------|-----------------|  
|*不連続*|列に不連続値が含まれています。|  
|*継続的です*|列の値により、一連の連続する数値データが定義されています。|  
|*分離*|この列の値は、連続した列から派生した値のグループ (またはバケット) を表します。|  
|*順序付け*|列の値は順序付けされたセットを定義しています。|  
|*Cyclical*|列の値は循環順序付けされたセットを定義しています。|  
|*確率*|列の値に含まれる列の確率を指定する、 [ClassifiedColumns](../collections/columns-element-assl.md)要素の親の`ScalarMiningStructureColumn`します。|  
|*Variance*|この列の値は、親である `ClassifiedColumns` の `ScalarMiningStructureColumn` 要素に含まれている列の分散を指定します。|  
|*StdDev*|この列の値は、親である `ClassifiedColumns` の `ScalarMiningStructureColumn` 要素に含まれている列の標準偏差を指定します。|  
|*ProbabilityVariance*|この列の値は、親である `ClassifiedColumns` の `ScalarMiningStructureColumn` 要素に含まれている列の確率の分散を指定します。|  
|*ProbabilityStdDev*|この列の値は、親である `ClassifiedColumns` の `ScalarMiningStructureColumn` 要素に含まれている列の確率の標準偏差を指定します。|  
|*サポート*|この列の値は、親である `ClassifiedColumns` の `ScalarMiningStructureColumn` 要素に含まれている列のサポート情報を指定します。 **注:** この列は、サード パーティ製のマイニング アルゴリズム プロバイダーの標準の一部として提供されます。 **注:** Microsoft 提供のアルゴリズムには、この列の使用はありません。 <br /><br /> .|  
|*[キー]*|列はキー列です。 **注:** このコンテンツの種類は、キー列にのみ適用されます、`IsKey`要素に設定されて`True`します。|  
  
 これらの標準値に加えてマイニング アルゴリズムのプロバイダーに含まれている[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]次の表の値がサポートされます。  
  
|値|説明|  
|-----------|-----------------|  
|*キーのシーケンス*|その列はキー列です。列の値がイベントの順序を表します。 **注:** このコンテンツの種類は、キー列にのみ適用されます、`IsKey`要素に設定されて`True`します。|  
|*[キー時刻]*|その列はキー列です。列の値は時間計測の単位を表します。 **注:** このコンテンツの種類は、キー列にのみ適用されます、`IsKey`要素に設定されて`True`します。|  
|*Sequence*|列の値がイベントの順序を表します。|  
|*[時刻]*|この列の値は、時間単位を表します。|  
  
 許容された値に対応する列挙`Content`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>します。  
  
## <a name="see-also"></a>参照  
 [ClassifiedColumns 要素&#40;ASSL&#41;](../collections/columns-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
