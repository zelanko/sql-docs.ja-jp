---
title: "MiningModelingFlag データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MiningModelingFlag Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MiningModelingFlag
helpviewer_keywords:
- MiningModelingFlag data type
ms.assetid: aaa72ba8-051e-4b01-b1e9-9c8d83b8b752
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bab055eef15474bfa22adefdc8ea6709659af978
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="miningmodelingflag-data-type-assl"></a>MiningModelingFlag データ型 (ASSL)
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
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
