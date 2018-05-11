---
title: コンテンツの要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e0efd6cc31b00c4029e88adab40b56aa88f50dc8
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="content-element-assl"></a>Content 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  内の列のコンテンツについて説明、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)要素。  
  
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
|親要素|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この列挙は、マイニング構造列によって表されるコンテンツの種類を示します。マイニング アルゴリズム プロバイダーでの必要に応じて拡張することができます。 コンテンツの種類の詳細については、「[コンテンツの種類 (データ マイニング)](../../../analysis-services/data-mining/content-types-data-mining.md)」を参照してください。  
  
 すべてのマイニング アルゴリズム プロバイダーで一般的にサポートされる値を次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|*不連続*|列に不連続値が含まれています。|  
|*継続的です*|列の値により、一連の連続する数値データが定義されています。|  
|*分離*|この列の値は、連続した列から派生した値のグループ (またはバケット) を表します。|  
|*順序付け*|列の値は順序付けされたセットを定義しています。|  
|*Cyclical*|列の値は循環順序付けされたセットを定義しています。|  
|*確率*|列の値に含まれる列の確率を指定する、 [ClassifiedColumns](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md)の親要素**ScalarMiningStructureColumn**です。|  
|*Variance*|列の値に含まれる列の分散が指定されて、 **ClassifiedColumns**の親要素**ScalarMiningStructureColumn**です。|  
|*StdDev*|列の値に含まれる列の標準偏差が指定されて、 **ClassifiedColumns**の親要素**ScalarMiningStructureColumn**です。|  
|*ProbabilityVariance*|列の値に含まれる列の確率の分散を指定する、 **ClassifiedColumns**の親要素**ScalarMiningStructureColumn**です。|  
|*ProbabilityStdDev*|列の値に含まれる列の確率標準偏差が指定されて、 **ClassifiedColumns**の親要素**ScalarMiningStructureColumn**です。|  
|*サポート*|列の値に含まれる列のサポート情報の指定、 **ClassifiedColumns**の親要素**ScalarMiningStructureColumn**です。<br /><br /> 注: サード パーティ製マイニング アルゴリズム プロバイダーは、この列を標準の一部として提供されます。 Microsoft が提供するアルゴリズムを行わないのこの列を使用します。|  
|*[キー]*|列はキー列です。<br /><br /> 注: このコンテンツの種類は、キー列にのみ適用されます、 **IsKey**要素に設定されている**True**です。|  
  
 これらの標準値に加えてマイニング アルゴリズム プロバイダーに含まれている[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]次の表に、値をサポートします。  
  
|値|Description|  
|-----------|-----------------|  
|*キーのシーケンス*|その列はキー列です。列の値がイベントの順序を表します。<br /><br /> 注: このコンテンツの種類は、キー列にのみ適用されます、 **IsKey**要素に設定されている**True**です。|  
|*[キー時刻]*|その列はキー列です。列の値は時間計測の単位を表します。<br /><br /> 注: このコンテンツの種類は、キー列にのみ適用されます、 **IsKey**要素に設定されている**True**です。|  
|*シーケンス*|列の値がイベントの順序を表します。|  
|*[時刻]*|この列の値は、時間単位を表します。|  
  
 許可される値に対応する列挙**コンテンツ**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>します。  
  
## <a name="see-also"></a>参照  
 [ClassifiedColumns 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
