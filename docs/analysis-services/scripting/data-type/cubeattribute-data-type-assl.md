---
title: CubeAttribute データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 11a45e49fa902554aaa2b7be1486fb976f03c580
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="cubeattribute-data-type-assl"></a>CubeAttribute データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  関連付けられている属性を表すプリミティブ データ型を定義、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeAttribute>  
   <AttributeID>...</AttributeID>  
   <AggregationUsage>...</AggregationUsage>  
   <AttributeHierarchyOptimizedState>...</AttributeHierarchyOptimizedState>  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   <Annotations>...</Annotations>  
</CubeAttribute>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[AggregationUsage](../../../analysis-services/scripting/properties/aggregationusage-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [AttributeHierarchyEnabled](../../../analysis-services/scripting/properties/attributehierarchyenabled-element-assl.md)、 [AttributeHierarchyOptimizedState](../../../analysis-services/scripting/properties/attributehierarchyoptimizedstate-element-assl.md)、 [AttributeHierarchyVisible](../../../analysis-services/scripting/properties/attributehierarchyvisible-element-assl.md)、 [AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md)|  
|派生要素|[属性](../../../analysis-services/scripting/objects/attribute-element-assl.md)([属性](../../../analysis-services/scripting/collections/attributes-element-assl.md)のコレクション[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md))|  
  
## <a name="remarks"></a>解説  
 *AttributeHierarchyOptimizedState* 1 または 2 の DeploymentMode 構成プロパティの値で、サービスを実行する場合、要素がサポートされていません (SharePoint モードまたはテーブル モードで実行するために使用[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]と表形式モデルデータベースの場合)。  
  
 階層のレベルとして属性を追加することはできませんとプロパティは、 *AtttributeHierarchyEnabled*FALSE に設定されている DeploymentMode 1 または 2 (SharePoint モードまたは表形式サーバー モード) インスタンスが動作しています。  
  
 属性で、 [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)要素で明示的に含まれていない、[属性](../../../analysis-services/scripting/collections/attributes-element-assl.md)に割り当てられる既定値を使用して、コレクションの一部をコレクションになります。 属性によって返される属性をコレクションに追加したら、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドです。  
  
 [AggregationUsage](../../../analysis-services/scripting/properties/aggregationusage-element-assl.md)要素コントロール方法[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]自動的に、属性の集計をデザインします。 **AggregationUsage**要素は、キューブに対して手動で作成されるすべての集計を制限しません。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.CubeAttribute>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
