---
title: 要素 (ASSL) の名前を付けます |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Name Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Name
helpviewer_keywords:
- Name element
ms.assetid: caf2af86-5f9c-4e14-8168-f3a79248b4fe
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 72a9dc3d252848a987e62c392f91086d0b62cc19
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083392"
---
# <a name="name-element-assl"></a>Name 要素 (ASSL)
  親要素の名前が格納されます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Action> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Name>...</Name>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (最大 100 文字)|  
|既定値|異なります|  
|Cardinality|1-1: 必須要素で、1 回だけ出現します。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アクション](../objects/action-element-assl.md)、[集計](../objects/aggregation-element-assl.md)、 [AggregationDesign](../objects/aggregationdesign-element-assl.md)、 [AlgorithmParameter](../objects/algorithmparameter-element-assl.md)、[注釈](../objects/annotation-element-assl.md)、 [アセンブリ](../objects/assembly-element-assl.md)、 [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)、[キューブ](../objects/cube-element-assl.md)、 [CubeDimension](../data-type/dimension-data-type-assl.md)、 [CubeHierarchy](../data-type/hierarchy-data-type-assl.md)、 [データベース](../objects/database-element-assl.md)、 [DataSource](../objects/datasource-element-assl.md)、 [DataSourceView](../objects/datasourceview-element-assl.md)、[ディメンション](../objects/dimension-element-assl.md)、 [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)、[グループ](../objects/group-element-assl.md)、[階層](../objects/hierarchy-element-assl.md)、 [Kpi](../objects/kpi-element-assl.md)、[レベル](../objects/level-element-assl.md)、 [MdxScript](../objects/mdxscript-element-assl.md)、 [メジャー](../objects/measure-element-assl.md)、 [MeasureGroup](../objects/measuregroup-element-assl.md)、 [MemberProperty](../objects/attributerelationship-element-assl.md)、 [MiningModel](../objects/miningmodel-element-assl.md)、 [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)、 [MiningStructure](../objects/miningstructure-element-assl.md)、 [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)、[パーティション](../objects/partition-element-assl.md)、[権限](../data-type/permission-data-type-assl.md)、 [パースペクティブ](../objects/perspective-element-assl.md)、 [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md)、 [ReportFormatParameter](../objects/reportformatparameter-element-asl.md)、 [ReportParameter](../objects/reportparameter-element-assl.md)、 [ロール](../objects/role-element-assl.md)、 [Server](../objects/server-element-assl.md)、 [ServerProperty](../objects/serverproperty-element-assl.md)、[トレース](../objects/trace-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 オブジェクト ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンス、階層、属性など) を定義するために使用されるすべての要素は、プロパティとして `Name` 要素を持ちます。 `Name` 要素の値には次の制限があります。  
  
-   値の先頭または末尾にスペースを含めることはできません。 `Name` 要素の値の先頭または末尾にスペースが含まれている場合、そのスペースは [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] によって暗黙的に削除されます。  
  
-   値に制御文字を含めることはできません。 名前には制御文字を含めないでください。制御文字が含まれていると、XML 検証エラーが発生する場合があります。  
  
     [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] の `GetNewName` メソッドを使用してオブジェクトを作成すると、AMO は名前に制御文字、先頭のスペース、または末尾のスペースが含まれているかどうかをチェックし、それらを削除します。 そのため、オブジェクト名を設定する際には `GetNewName` を使用することをお勧めします。  
  
     `Name` プロパティを直接設定した場合は、この検証チェックが実行されないため、XML 検証エラーが発生する可能性があります。 エラーが実際に発生するかどうかは、名前に含まれる制御文字によって左右されます。  
  
     オブジェクト名には制御文字を使用しないようにする必要がありますが、Analysis Services では制御文字を明示的に禁止しているわけではありません。 以前のリリースの Analysis Services では、オブジェクト名の制御文字が許容される場合がありました。 そのため、[!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] では、古いソリューションが壊れないように、オブジェクト名の制御文字は無視されます。  
  
-   次の値は予約済みなので使用できません。  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1 ～ COM9 (COM1、COM2、COM3 など)  
  
    -   CON  
  
    -   LPT1 ～ LPT9 (LPT1、LPT2、LPT3 など)  
  
    -   NUL (NUL)  
  
    -   PRN  
  
 次の表は、親要素によっては `Name` 要素の値に使用できないその他の文字を示しています。  
  
|親要素|無効な文字|  
|--------------------|------------------------|  
|[[サーバー]](../objects/server-element-assl.md)|名前は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows コンピューター名の規則に従う必要があります。 IP アドレスは無効です。|  
|[DataSource](../objects/datasource-element-assl.md)|:/\\*&#124;?"(){}<>|  
|[レベル](../objects/level-element-assl.md)、[要素の属性](../objects/attribute-element-assl.md)|.,;'`:/\\*&#124;?"& % $! + ={}<>|  
|他のすべての親要素|.,;'`:/\\*&#124;?"& % $! + = (){}<>|  
  
## <a name="see-also"></a>参照  
 [ID 要素&#40;ASSL&#41;](id-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
