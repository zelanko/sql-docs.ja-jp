---
title: "Analysis Services スクリプト言語 XML データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Analysis Services Scripting Language XML Data Types
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ASSL, data types
- Analysis Services Scripting Language, data types
- data types [Analysis Services Scripting Language]
ms.assetid: 8e527916-932e-48ec-9010-f22cd4b721e2
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9baa60a57d8ef59bb7bb24afc82c0a3e5435a56d
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="analysis-services-scripting-language-xml-data-types-assl"></a>Analysis Services スクリプト言語の XML データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
このリファレンス セクションでは、Analysis Services スクリプト言語 (ASSL) スキーマで型の役割を果たす各要素の構文と使い方について説明します。  
  
 ASSL スキーマには、開発者の観点からの XML 要素のみが含まれていますが、このセクションで説明する要素などに対応して型、**バインド**と**権限**、するために使用されます。子要素およびその他のオブジェクトのプロパティを定義します。  
  
 型要素は、オブジェクト要素と同じように、ASSL スキーマのリーフ レベル要素ではありませんが、子要素とオブジェクト プロパティに対応する要素を含んでいます。  
  
 ただし、type 要素は表示されませんを定義または記述するスクリプト内の要素として[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]オブジェクト。 代わりに、通常を指定したその他のオブジェクト要素の型として表示されます、**型**から XML スキーマ インスタンスのスキーマを使用して、属性**xsi:type**または**xs:type**です。 たとえば、 `<Assembly xsi:type="ClrAssembly">...</Assembly>`のようにします。  
  
 型は、別の型から派生する場合もあります。 たとえば、 **CubeBinding**親からの型の派生**バインド**型です。  
  
|要素|Description|  
|-------------|-----------------|  
|[Action データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/action-data-type-assl.md)|内のアクションを表す抽象プリミティブ データ型を定義、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素または[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素。|  
|[AggregationAttribute データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationattribute-data-type-assl.md)|間の関連付けを表すプリミティブ データ型を定義、[集計](../../../analysis-services/scripting/objects/aggregation-element-assl.md)要素と属性。|  
|[AggregationDesignAttribute データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationdesignattribute-data-type-assl.md)|属性の間の関連付けを表すプリミティブ データ型を定義し、 [AggregationDesignDimension](../../../analysis-services/scripting/data-type/aggregationdesigndimension-data-type-assl.md)要素。|  
|[AggregationDesignDimension データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationdesigndimension-data-type-assl.md)|キューブ ディメンションの間のリレーションシップを表すプリミティブ データ型を定義し、 [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)要素。|  
|[AggregationDimension データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationdimension-data-type-assl.md)|ディメンションの間のリレーションシップを表すプリミティブ データ型を定義し、[集計](../../../analysis-services/scripting/objects/aggregation-element-assl.md)要素。|  
|[AggregationInstanceAttribute データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationinstanceattribute-data-type-assl.md)|集計インスタンスによって使用される属性に関する情報を表すプリミティブ データ型を定義します。|  
|[AggregationInstanceCubeDimension データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationinstancecubedimension-data-type-assl.md)|集計インスタンスによって使用されるキューブ ディメンションに関する情報を表すプリミティブ データ型を定義します。|  
|[AggregationInstanceMeasure データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationinstancemeasure-data-type-assl.md)|集計インスタンスによって使用されるメジャーに関する情報を表すプリミティブ データ型を定義します。|  
|[Assembly データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/assembly-data-type-assl.md)|表す抽象プリミティブ データ型を定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリまたは COM ダイナミック リンク ライブラリ (DLL) に関連付けられている、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)または[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[AttributeBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|バインドを表す派生データ型を定義、[属性](../../../analysis-services/scripting/objects/attribute-element-assl.md)要素。|  
|[AttributeTranslation データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)|関連付けられている翻訳を表す派生データ型を定義、[属性](../../../analysis-services/scripting/objects/attribute-element-assl.md)の要素|  
|[バインディング データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|あるオブジェクトのデータまたはメタデータがバインド対象オブジェクトのデータまたはメタデータに依存している 2 つのオブジェクト間の依存関係を表す抽象プリミティブ データ型を定義します。|  
|[ClrAssembly データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)|表す派生データ型を定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリに関連付けられている、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)または[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)要素|  
|[ClrAssemblyFile データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)|構成するファイルのいずれかを表すプリミティブ データ型を定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリ ([ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)要素)。|  
|[ColumnBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|データ ソース ビュー内の列のバインドを表す派生データ型を定義、 [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)要素。|  
|[ComAssembly データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)|[Server](../../../analysis-services/scripting/objects/server-element-assl.md) 要素または [Database](../../../analysis-services/scripting/objects/database-element-assl.md) 要素に関連付けられた COM ライブラリを表す派生データ型を定義します。|  
|[CubeAttribute データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md)|関連付けられている属性を表すプリミティブ データ型を定義、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。|  
|[CubeAttributeBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md)|アクションまたはマイニング構造列に対するキューブ ディメンションの属性のバインドを表す派生データ型を定義します。|  
|[CubeBinding データ型 &#40;不一致の&#41;&#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md)|間のリレーションシップを表すプリミティブ データ型を定義、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素、および[データソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)要素。|  
|[CubeDimension データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|ディメンションとキューブの関係を表すプリミティブ データ型を定義します。|  
|[CubeDimensionBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md)|バインディングを表す派生データ型を定義、[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)、[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)、または[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)キューブ ディメンションへの要素。|  
|[CubeDimensionPermission データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/cubedimensionpermission-data-type-assl.md)|キューブ内の特定のディメンションにおける 1 つのロールの権限を表すプリミティブ データ型を定義します。|  
|[CubeHierarchy データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md)|に関する情報を表すプリミティブ データ型を定義、[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)内の要素、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。|  
|[DataBlock データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)|バイナリ コンテンツを格納するために使用するデータ ブロックのコレクションを表すプリミティブ データ型を定義、 [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)要素。|  
|[DataItem データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|列や属性などのデータ アイテムのデータ関連の特性を表すプリミティブ データ型を定義します。|  
|[DataMiningMeasureGroupDimension データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/dataminingmeasuregroupdimension-data-type-assl.md)|メジャー グループとデータ マイニング ディメンションの間のリレーションシップを表す派生データ型を定義します。|  
|[DataSource データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)|内のデータ ソースを表す抽象プリミティブ データ型を定義、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[DataSourceViewBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/datasourceviewbinding-data-type-assl.md)|データ ソース ビューと親要素の間のバインドを表す派生データ型を定義します。|  
|[DegenerateMeasureGroupDimension データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/degeneratemeasuregroupdimension-data-type-assl.md)|逆ディメンション (つまり、ファクト ディメンション) とメジャー グループとの間のリレーションシップを表す派生データ型を定義します。|  
|[Dimension データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/dimension-data-type-assl.md)|データベース ディメンションを表すプリミティブ データ型を定義します。|  
|[DimensionAttribute データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|ディメンション内の属性を表すプリミティブ データ型を定義します。|  
|[DimensionBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)|データ ソースの間のバインドを表す派生データ型を定義し、[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)要素。|  
|[DimensionPermission データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/dimensionpermission-data-type-assl.md)|データベース ディメンションに割り当てられている権限を表す派生データ型を定義します。|  
|[DrillThroughAction データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)|ドリルスルー アクションを表す派生データ型を定義します。|  
|[DSVTableBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/dsvtablebinding-data-type-assl.md)|テーブル間のバインドを表す派生データ型を定義し、 [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)要素。|  
|[EventColumn データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/eventcolumn-data-type-assl.md)|キャプチャされる情報の列を表すプリミティブ データ型を定義、[イベント](../../../analysis-services/scripting/objects/event-element-assl.md)要素の一部として、[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)要素。|  
|[Hierarchy データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/hierarchy-data-type-assl.md)|ディメンション内の階層を表すプリミティブ データ型を定義します。|  
|[ImpersonationInfo データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)|ユーザーの権限を借用するために使用される情報を表すプリミティブ データ型を定義します。|  
|[IncrementalProcessingNotification データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/incrementalprocessingnotification-data-type-assl.md)|情報を表す派生データ型を定義、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)増分処理の進行状況を判断するために実行するクエリについて要素。|  
|[InheritedBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/inheritedbinding-data-type-assl.md)|示す派生データ型を定義、 [MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)要素は、属性からバインドを継承します。|  
|[ManyToManyMeasureGroupDimension データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/manytomanymeasuregroupdimension-data-type-assl.md)|多対多ディメンションとメジャー グループとの間のリレーションシップを表す派生データ型を定義します。|  
|[MeasureBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|親要素へのメジャーのバインドを表す派生データ型を定義します。|  
|[MeasureGroupAttribute データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)|属性とメジャー グループとの間のリレーションシップを表すプリミティブ データ型を定義します。|  
|[MeasureGroupBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|バインドを表す派生データ型を定義、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)要素。|  
|[MeasureGroupBinding データ型 &#40;不一致の&#41;&#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|メジャー グループへのバインドを表すプリミティブ データ型を定義します。|  
|[MeasureGroupDimension データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/measuregroupdimension-data-type-assl.md)|ディメンションとメジャー グループとの間のリレーションシップを表す抽象プリミティブ データ型を定義します。|  
|[MeasureGroupDimensionBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/measuregroupdimensionbinding-data-type-assl.md)|ディメンションとメジャー グループとのバインドを表す派生データ型を定義します。|  
|[MeasureGroupHierarchy データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/measuregrouphierarchy-data-type-assl.md)|メジャー グループの階層に関する情報を表すプリミティブ データ型を定義します。|  
|[MiningModelColumn データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)|内の列に関する情報を表すプリミティブ データ型を定義、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)要素。|  
|[MiningModelingFlag データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/miningmodelingflag-data-type-assl.md)|使用可能なモデリング フラグを表すプリミティブ データ型を定義、 [ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md)要素。|  
|[MiningStructureColumn データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)|内の列に関する情報を表す抽象プリミティブ データ型を定義、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)要素。|  
|[OlapDataSource データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/olapdatasource-data-type-assl.md)|マルチ ディメンションを表す派生データ型を定義[データソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)要素。|  
|[PartitionBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/partitionbinding-data-type-assl.md)|バインドを表す派生データ型を定義、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)要素。|  
|[Permission データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|個別の権限についての情報を表す抽象プリミティブ データ型を定義します。|  
|[PerspectiveAction データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/perspectiveaction-data-type-assl.md)|内のアクションに関する情報を表すプリミティブ データ型を定義、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素。|  
|[PerspectiveAttribute データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/perspectiveattribute-data-type-assl.md)|内の属性に関する情報を表すプリミティブ データ型を定義、 [PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md)の要素。|  
|[PerspectiveCalculation データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/perspectivecalculation-data-type-assl.md)|計算間のリレーションシップを表すプリミティブ データ型を定義し、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素。|  
|[PerspectiveDimension データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md)|パースペクティブ内のディメンションに関する情報を表すプリミティブ データ型を定義します。|  
|[PerspectiveHierarchy データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/perspectivehierarchy-data-type-assl.md)|内の階層に関する情報を表すプリミティブ データ型を定義、 [PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md)要素。|  
|[PerspectiveKpi データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/perspectivekpi-data-type-assl.md)|主要業績評価指標 (KPI) に関する情報を表すプリミティブ データ型を定義、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素。|  
|[PerspectiveMeasure データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/perspectivemeasure-data-type-assl.md)|内のメジャーに関する情報を表すプリミティブ データ型を定義、 [PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)要素。|  
|[PerspectiveMeasureGroup データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)|内のメジャー グループに関する情報を表すプリミティブ データ型を定義、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素。|  
|[ProactiveCachingBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)|情報を表す抽象派生データ型を定義、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)要素をキャッシュの再構築を必要とするデータ ソースの変更や再構築プロセスの状態に関するします。|  
|[ProactiveCachingIncrementalProcessingBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/proactivecachingincrementalprocessingbinding-data-type-assl.md)|バインドを表す派生データ型を定義、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)キャッシュの再構築プロセスの状態に関する要素。|  
|[ProactiveCachingInheritedBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/proactivecachinginheritedbinding-data-type-assl.md)|情報を表す派生データ型を定義、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)テーブルおよびビューをキャッシュの再構築を必要とする既存のデータ バインドを介して識別されるデータ ソース変更に関して要素。|  
|[ProactiveCachingObjectNotificationBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/proactivecachingobjectnotificationbinding-data-type-assl.md)|情報を表す抽象派生データ型を定義、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)データ ソース変更に関して、要素で指定されたテーブルおよびビューまたはテーブルとビューを介して識別される既存のデータ キャッシュの再構築が必要なバインドです。|  
|[ProactiveCachingQueryBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/proactivecachingquerybinding-data-type-assl.md)|情報を表す派生データ型を定義、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)テーブルおよびビュー、キャッシュの再構築を必要とする指定されたクエリの実行を介して識別されるデータ ソース変更に関して要素。|  
|[ProactiveCachingTablesBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/proactivecachingtablesbinding-data-type-assl.md)|情報を表す派生データ型を定義、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)指定されたテーブルおよびビューをキャッシュの再構築を必要とするデータ ソース変更に関して要素。|  
|[PushedDataSource データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/pusheddatasource-data-type-assl.md)|データ ソースを表すプリミティブ データ型を定義 (など、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]パッケージ) へのデータを「プッシュ」するために使用される、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。|  
|[QueryBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/querybinding-data-type-assl.md)|関連付けを表す派生データ型を定義、[データソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)を持つ要素を[QueryDefinition](../../../analysis-services/scripting/properties/querydefinition-element-assl.md)要素。|  
|[ReferenceMeasureGroupDimension データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/referencemeasuregroupdimension-data-type-assl.md)|中間ディメンションを介してファクト テーブルに間接的に関連するディメンションを表す派生データ型を定義します  (たとえば、Sales メジャー グループは、Customer ディメンションを介して関連する Geography ディメンションを参照できます)。|  
|[RegularMeasureGroupDimension データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/regularmeasuregroupdimension-data-type-assl.md)|ディメンションとメジャー グループの間の標準のリレーションシップを表す派生データ型を定義します。|  
|[RelationalDataSource データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/relationaldatasource-data-type-assl.md)|表す派生データ型を定義、[データソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)要素は、リレーショナル データ ソースに基づきます。|  
|[ReportAction データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] レポートを生成するアクションを表す派生データ型を定義します。|  
|[RowBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/rowbinding-data-type-assl.md)|内のテーブルの行へのバインディングを表す派生データ型を定義、 [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)要素。|  
|[ScalarMiningStructureColumn データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|表す派生データ型を定義、 [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)要素に関連付けられている入れ子になったテーブルではなく、スカラー値を含む、 [TableMiningStructureColumn](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)を入れ子になったテーブルを含む要素です。|  
|[StandardAction データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|いずれかを表す派生データ型を定義[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)以外の要素、 [DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)要素または[ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)要素。|  
|[TableBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/tablebinding-data-type-assl.md)|テーブルへのバインドを表す派生データ型を定義します。|  
|[TableMiningStructureColumn データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)|表す派生データ型を定義、 [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)要素に関連付けられているスカラー値ではなく、入れ子になったテーブルを含む、 [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)スカラー値を含む要素です。|  
|[TabularBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md)|テーブルやキューブ ディメンションなどの表アイテムへのバインドを表す抽象派生データ型を定義します。|  
|[TimeAttributeBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/timeattributebinding-data-type-assl.md)|「プレース ホルダー」バインドの属性のキー列など、サーバー時間ディメンションで生成されたデータ項目を表す派生データ型を定義します。|  
|[TimeBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|期間へのバインドを表す派生データ型を定義します。|  
|[Translation データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/translation-data-type-assl.md)|ローカライズされた翻訳を表すプリミティブ データ型を定義します。|  
|[UserDefinedGroupBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/userdefinedgroupbinding-data-type-assl.md)|属性のユーザー定義のグループ化を表す派生データ型を定義します。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML 要素の階層 &#40;です。ASSL &#41;](../../../analysis-services/scripting/analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
