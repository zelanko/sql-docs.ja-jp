---
title: MiningModelingFlag データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ffbf5b43efb72e32b49cf70a1a114a4b2c07b3de
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="miningmodelingflag-data-type-assl"></a>MiningModelingFlag データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  使用可能なモデリング フラグを表すプリミティブ データ型を定義、 [ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md)要素。  
  
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
|派生要素|[ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) ([ModelingFlags](../../../analysis-services/scripting/collections/modelingflags-element-assl.md)のコレクション[MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)または[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>解説  
 フラグ名には空白文字が含まれている場合があります。 次の表に、ネイティブ サポートされている値の一覧を示します。  
  
|値|Description|  
|-----------|-----------------|  
|*MODEL_EXISTENCE_ONLY*|列の値にかかわらず、列には欠落と非欠落という 2 つの状態があるようにモデル化されている必要があります。 入れ子になったテーブルの列で、ケース全体の値がスパースである場合に特に有効です。|  
|*NOT NULL します。*|列には NULL 値を指定できません。|  
|*リグレッサー*|列はテスト ケースのリグレッサー値を提供します。|  
  
 インスタンスでサード パーティの OLE DB、またはデータ マイニング プロバイダーが集計された場合、追加のプロバイダー固有フラグを使用することがあります[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで密接に関連する要素は、<xref:Microsoft.AnalysisServices.MiningModelingFlags> です。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
