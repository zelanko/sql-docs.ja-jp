---
title: MiningModelingFlag データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MiningModelingFlag Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModelingFlag
helpviewer_keywords:
- MiningModelingFlag data type
ms.assetid: aaa72ba8-051e-4b01-b1e9-9c8d83b8b752
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ece92d63c0d66c1ef845ce2d28d3317b2f65d66f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167523"
---
# <a name="miningmodelingflag-data-type-assl"></a>MiningModelingFlag データ型 (ASSL)
  使用可能なモデリング フラグを表すプリミティブ データ型を定義、 [ModelingFlag](../objects/modelingflag-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningModelingFlag>...</MiningModelingFlag>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|String (列挙型)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|なし|  
|派生要素|[ModelingFlag](../objects/modelingflag-element-assl.md) ([ModelingFlags](../collections/modelingflags-element-assl.md)のコレクション[MiningModelColumn](miningmodelcolumn-data-type-assl.md)または[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>コメント  
 フラグ名には空白文字が含まれている場合があります。 次の表に、ネイティブ サポートされている値の一覧を示します。  
  
|値|説明|  
|-----------|-----------------|  
|*MODEL_EXISTENCE_ONLY*|列の値にかかわらず、列には欠落と非欠落という 2 つの状態があるようにモデル化されている必要があります。 入れ子になったテーブルの列で、ケース全体の値がスパースである場合に特に有効です。|  
|*NOT NULL します。*|列には NULL 値を指定できません。|  
|*リグレッサー*|列はテスト ケースのリグレッサー値を提供します。|  
  
 インスタンスでサード パーティの OLE DB またはデータ マイニング プロバイダーが集計された場合、追加のプロバイダー固有フラグを使用できます[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで密接に関連する要素は、<xref:Microsoft.AnalysisServices.MiningModelingFlags> です。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
