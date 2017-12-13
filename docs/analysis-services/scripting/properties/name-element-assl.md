---
title: "要素 (ASSL) の名前を付けます |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Name Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Name
helpviewer_keywords: Name element
ms.assetid: caf2af86-5f9c-4e14-8168-f3a79248b4fe
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 80a083e924e6265689f9852bae46b0c0c184c765
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="name-element-assl"></a>Name 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]親要素の名前が含まれています。  
  
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
|Cardinality|1-1: 回だけ出現する必須要素|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)、[集計](../../../analysis-services/scripting/objects/aggregation-element-assl.md)、 [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)、 [AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)、[注釈](../../../analysis-services/scripting/objects/annotation-element-assl.md)、 [アセンブリ](../../../analysis-services/scripting/objects/assembly-element-assl.md)、 [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)、 [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)、 [CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md)、 [データベース](../../../analysis-services/scripting/objects/database-element-assl.md)、[データソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)、 [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)、[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)、 [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)、[グループ](../../../analysis-services/scripting/objects/group-element-assl.md)、[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)、 [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)、[レベル](../../../analysis-services/scripting/objects/level-element-assl.md)、 [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)、 [メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)、 [MemberProperty](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)、 [MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)、 [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)、[権限](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)、 [パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)、 [PerspectiveCalculation](../../../analysis-services/scripting/data-type/perspectivecalculation-data-type-assl.md)、 [ReportFormatParameter](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md)、 [ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md)、 [ロール](../../../analysis-services/scripting/objects/role-element-assl.md)、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)、 [ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)、[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 オブジェクトを定義するために使用するすべての要素 (のインスタンス[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、階層、属性、やなど) が、**名**プロパティとして要素。 値、**名前**要素には、次の制限。  
  
-   値の先頭または末尾にスペースを含めることはできません。 値の先頭または末尾にスペースが含まれるかどうか、**名前**要素、そのスペースは暗黙的にによって削除されます[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
-   値に制御文字を含めることはできません。 名前には制御文字を含めないでください。制御文字が含まれていると、XML 検証エラーが発生する場合があります。  
  
     使用して作成されたオブジェクトの**GetNewName**メソッド[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]AMO が確認され、先頭のスペース、または名前の末尾のスペース、後で、コントロール文字を削除します。 このためを使用して**GetNewName**オブジェクト名を設定するための推奨アプローチです。  
  
     ただし、設定した場合、**名前**プロパティを直接、チェックは行われません、XML 検証エラーを引き起こす同じ検証します。 エラーが実際に発生するかどうかは、名前に含まれる制御文字によって左右されます。  
  
     オブジェクト名には制御文字を使用しないようにする必要がありますが、Analysis Services では制御文字を明示的に禁止しているわけではありません。 以前のリリースの Analysis Services では、オブジェクト名の制御文字が許容される場合がありました。 このため、SQL Server 2016 Analysis Services して後で以前のソリューションが壊れないように、オブジェクト名の制御文字は無視されます。  
  
-   次の値は予約済みなので使用できません。  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1 ～ COM9 (COM1、COM2、COM3 など)  
  
    -   CON  
  
    -   LPT1 ～ LPT9 (LPT1、LPT2、LPT3 など)  
  
    -   NUL (NUL)  
  
    -   PRN  
  
 次の表に、追加の文字の値の中で使用することはできませんが、**名前**によっては、親要素の要素。  
  
|親要素|無効な文字|  
|--------------------|------------------------|  
|[[サーバー]](../../../analysis-services/scripting/objects/server-element-assl.md)|名前は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows コンピューター名の規則に従う必要があります。 IP アドレスは無効です。|  
|[データ ソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)|:/\\*&#124;?"()[]{}<>|  
|[レベル](../../../analysis-services/scripting/objects/level-element-assl.md)、[要素の属性](../../../analysis-services/scripting/objects/attribute-element-assl.md)|.,;'`:/\\*&#124;?"&%$!+=[]{}<>|  
|他のすべての親要素|.,;'`:/\\*&#124;?"&%$!+=()[]{}<>|  
  
## <a name="see-also"></a>参照  
 [ID 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/id-element-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
