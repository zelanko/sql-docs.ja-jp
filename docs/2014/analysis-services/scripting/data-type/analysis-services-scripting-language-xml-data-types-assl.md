---
title: Analysis Services スクリプト言語 XML データ型 (ASSL) |Microsoft ドキュメント
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
- Analysis Services Scripting Language XML Data Types
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ASSL, data types
- Analysis Services Scripting Language, data types
- data types [Analysis Services Scripting Language]
ms.assetid: 8e527916-932e-48ec-9010-f22cd4b721e2
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3420e553b1391fb9645f7e3bffa884e255a90897
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164695"
---
# <a name="analysis-services-scripting-language-xml-data-types-assl"></a>Analysis Services スクリプト言語の XML データ型 (ASSL)
  このリファレンス セクションでは、Analysis Services スクリプト言語 (ASSL) スキーマで型の役割を果たす各要素の構文と使い方について説明します。  
  
 ASSL スキーマには XML 要素のみが含まれますが、開発者にとって、このセクションで説明する要素は、他のオブジェクトの子要素およびプロパティを定義するのに使用される `Binding` や `Permission` などの型に対応しています。  
  
 型要素は、オブジェクト要素と同じように、ASSL スキーマのリーフ レベル要素ではありませんが、子要素とオブジェクト プロパティに対応する要素を含んでいます。  
  
 ただし、type 要素は表示されませんを定義または記述するスクリプト内の要素として[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]オブジェクト。 他のオブジェクト要素の型として使用されるのではなく、通常、`type` または `xsi:type` を使用して XML スキーマのインスタンス スキーマの `xs:type` 属性と共にデザインされます。 たとえば、 `<Assembly xsi:type="ClrAssembly">...</Assembly>`のようにします。  
  
 型は、別の型から派生する場合もあります。 たとえば、`CubeBinding` 型は、親である `Binding` 型から派生します。  
  
|要素|説明|  
|-------------|-----------------|  
|[Action データ型&#40;ASSL&#41;](action-data-type-assl.md)|内のアクションを表す抽象プリミティブ データ型を定義、[キューブ](../objects/cube-element-assl.md)要素または[パースペクティブ](../objects/perspective-element-assl.md)要素。|  
|[AggregationAttribute データ型&#40;ASSL&#41;](aggregationattribute-data-type-assl.md)|間の関連付けを表すプリミティブ データ型を定義、[集計](../objects/aggregation-element-assl.md)要素と属性。|  
|[AggregationDesignAttribute データ型&#40;ASSL&#41;](aggregationdesignattribute-data-type-assl.md)|属性の間の関連付けを表すプリミティブ データ型を定義し、 [AggregationDesignDimension](dimension-data-type-assl.md)要素。|  
|[AggregationDesignDimension データ型&#40;ASSL&#41;](dimension-data-type-assl.md)|キューブ ディメンションの間のリレーションシップを表すプリミティブ データ型を定義し、 [AggregationDesign](../objects/aggregationdesign-element-assl.md)要素。|  
|[AggregationDimension データ型&#40;ASSL&#41;](aggregationdimension-data-type-assl.md)|ディメンションの間のリレーションシップを表すプリミティブ データ型を定義し、[集計](../objects/aggregation-element-assl.md)要素。|  
|[AggregationInstanceAttribute データ型&#40;ASSL&#41;](aggregationinstanceattribute-data-type-assl.md)|集計インスタンスによって使用される属性に関する情報を表すプリミティブ データ型を定義します。|  
|[AggregationInstanceCubeDimension データ型&#40;ASSL&#41;](cubedimension-data-type-assl.md)|集計インスタンスによって使用されるキューブ ディメンションに関する情報を表すプリミティブ データ型を定義します。|  
|[AggregationInstanceMeasure データ型&#40;ASSL&#41;](aggregationinstancemeasure-data-type-assl.md)|集計インスタンスによって使用されるメジャーに関する情報を表すプリミティブ データ型を定義します。|  
|[Assembly データ型&#40;ASSL&#41;](assembly-data-type-assl.md)|表す抽象プリミティブ データ型を定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリまたは COM ダイナミック リンク ライブラリ (DLL) に関連付けられている、[サーバー](../objects/server-element-assl.md)または[データベース](../objects/database-element-assl.md)要素。|  
|[AttributeBinding データ型&#40;ASSL&#41;](binding-data-type-assl.md)|バインドを表す派生データ型を定義、[属性](../objects/attribute-element-assl.md)要素。|  
|[AttributeTranslation データ型&#40;ASSL&#41;](translation-data-type-assl.md)|関連付けられている翻訳を表す派生データ型を定義、[属性](../objects/attribute-element-assl.md)要素|  
|[Binding データ型&#40;ASSL&#41;](binding-data-type-assl.md)|あるオブジェクトのデータまたはメタデータがバインド対象オブジェクトのデータまたはメタデータに依存している 2 つのオブジェクト間の依存関係を表す抽象プリミティブ データ型を定義します。|  
|[ClrAssembly データ型&#40;ASSL&#41;](clrassembly-data-type-assl.md)|表す派生データ型を定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリに関連付けられている、[データベース](../objects/database-element-assl.md)または[サーバー](../objects/server-element-assl.md)要素|  
|[ClrAssemblyFile データ型&#40;ASSL&#41;](clrassemblyfile-data-type-assl.md)|構成するファイルのいずれかを表すプリミティブ データ型を定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリ ([ClrAssembly](clrassembly-data-type-assl.md)要素)。|  
|[ColumnBinding データ型&#40;ASSL&#41;](columnbinding-data-type-assl.md)|データ ソース ビュー内の列のバインドを表す派生データ型を定義、 [DataItem](dataitem-data-type-assl.md)要素。|  
|[ComAssembly データ型&#40;ASSL&#41;](comassembly-data-type-assl.md)|関連付けられた COM ライブラリを表す派生データ型を定義、[サーバー](../objects/server-element-assl.md)または[データベース](../objects/database-element-assl.md)要素。|  
|[CubeAttribute データ型&#40;ASSL&#41;](cubeattribute-data-type-assl.md)|関連付けられている属性を表すプリミティブ データ型を定義、[キューブ](../objects/cube-element-assl.md)要素。|  
|[CubeAttributeBinding データ型&#40;ASSL&#41;](cubebinding-data-type-out-of-line-assl.md)|アクションまたはマイニング構造列に対するキューブ ディメンションの属性のバインドを表す派生データ型を定義します。|  
|[CubeBinding データ型&#40;不一致の&#41; &#40;ASSL&#41;](cubebinding-data-type-out-of-line-assl.md)|間のリレーションシップを表すプリミティブ データ型を定義、[キューブ](../objects/cube-element-assl.md)要素、および[データソース](../objects/datasource-element-assl.md)要素。|  
|[CubeDimension データ型&#40;ASSL&#41;](cubedimension-data-type-assl.md)|ディメンションとキューブの関係を表すプリミティブ データ型を定義します。|  
|[CubeDimensionBinding データ型&#40;ASSL&#41;](dimensionbinding-data-type-assl.md)|バインディングを表す派生データ型を定義、[ディメンション](../objects/dimension-element-assl.md)、[メジャー](../objects/measure-element-assl.md)、または[MiningModel](../objects/miningmodel-element-assl.md)キューブ ディメンションへの要素。|  
|[CubeDimensionPermission データ型&#40;ASSL&#41;](permission-data-type-assl.md)|キューブ内の特定のディメンションにおける 1 つのロールの権限を表すプリミティブ データ型を定義します。|  
|[CubeHierarchy データ型&#40;ASSL&#41;](hierarchy-data-type-assl.md)|に関する情報を表すプリミティブ データ型を定義、[階層](../objects/hierarchy-element-assl.md)内の要素、[キューブ](../objects/cube-element-assl.md)要素。|  
|[DataBlock データ型&#40;ASSL&#41;](datablock-data-type-assl.md)|バイナリ コンテンツを格納するために使用するデータ ブロックのコレクションを表すプリミティブ データ型を定義、 [ClrAssemblyFile](clrassemblyfile-data-type-assl.md)要素。|  
|[DataItem データ型&#40;ASSL&#41;](dataitem-data-type-assl.md)|列や属性などのデータ アイテムのデータ関連の特性を表すプリミティブ データ型を定義します。|  
|[DataMiningMeasureGroupDimension データ型&#40;ASSL&#41;](measuregroupdimension-data-type-assl.md)|メジャー グループとデータ マイニング ディメンションの間のリレーションシップを表す派生データ型を定義します。|  
|[DataSource データ型&#40;ASSL&#41;](datasource-data-type-assl.md)|内のデータ ソースを表す抽象プリミティブ データ型を定義、[データベース](../objects/database-element-assl.md)要素。|  
|[DataSourceViewBinding データ型&#40;ASSL&#41;](datasourceviewbinding-data-type-assl.md)|データ ソース ビューと親要素の間のバインドを表す派生データ型を定義します。|  
|[DegenerateMeasureGroupDimension データ型&#40;ASSL&#41;](degeneratemeasuregroupdimension-data-type-assl.md)|逆ディメンション (つまり、ファクト ディメンション) とメジャー グループとの間のリレーションシップを表す派生データ型を定義します。|  
|[データ型をディメンション&#40;ASSL&#41;](dimension-data-type-assl.md)|データベース ディメンションを表すプリミティブ データ型を定義します。|  
|[DimensionAttribute データ型&#40;ASSL&#41;](dimensionattribute-data-type-assl.md)|ディメンション内の属性を表すプリミティブ データ型を定義します。|  
|[DimensionBinding データ型&#40;ASSL&#41;](dimensionbinding-data-type-assl.md)|データ ソースの間のバインドを表す派生データ型を定義し、[ディメンション](../objects/dimension-element-assl.md)要素。|  
|[DimensionPermission データ型&#40;ASSL&#41;](permission-data-type-assl.md)|データベース ディメンションに割り当てられている権限を表す派生データ型を定義します。|  
|[DrillThroughAction データ型&#40;ASSL&#41;](drillthroughaction-data-type-assl.md)|ドリルスルー アクションを表す派生データ型を定義します。|  
|[DSVTableBinding データ型&#40;ASSL&#41;](tablebinding-data-type-assl.md)|テーブル間のバインドを表す派生データ型を定義し、 [DataSourceView](../objects/datasourceview-element-assl.md)要素。|  
|[EventColumn データ型&#40;ASSL&#41;](eventcolumn-data-type-assl.md)|キャプチャされる情報の列を表すプリミティブ データ型を定義、[イベント](../objects/event-element-assl.md)要素の一部として、[トレース](../objects/trace-element-assl.md)要素。|  
|[Hierarchy データ型&#40;ASSL&#41;](hierarchy-data-type-assl.md)|ディメンション内の階層を表すプリミティブ データ型を定義します。|  
|[ImpersonationInfo データ型&#40;ASSL&#41;](impersonationinfo-data-type-assl.md)|ユーザーの権限を借用するために使用される情報を表すプリミティブ データ型を定義します。|  
|[IncrementalProcessingNotification データ型&#40;ASSL&#41;](incrementalprocessingnotification-data-type-assl.md)|情報を表す派生データ型を定義、 [ProactiveCaching](../objects/proactivecaching-element-assl.md)増分処理の進行状況を判断するために実行するクエリについて要素。|  
|[InheritedBinding データ型&#40;ASSL&#41;](inheritedbinding-data-type-assl.md)|示す派生データ型を定義、 [MeasureGroupAttribute](measuregroupattribute-data-type-assl.md)要素は、属性からバインドを継承します。|  
|[ManyToManyMeasureGroupDimension データ型&#40;ASSL&#41;](manytomanymeasuregroupdimension-data-type-assl.md)|多対多ディメンションとメジャー グループとの間のリレーションシップを表す派生データ型を定義します。|  
|[MeasureBinding データ型&#40;ASSL&#41;](measurebinding-data-type-assl.md)|親要素へのメジャーのバインドを表す派生データ型を定義します。|  
|[MeasureGroupAttribute データ型&#40;ASSL&#41;](measuregroupattribute-data-type-assl.md)|属性とメジャー グループとの間のリレーションシップを表すプリミティブ データ型を定義します。|  
|[MeasureGroupBinding データ型&#40;ASSL&#41;](measuregroupbinding-data-type-assl.md)|バインドを表す派生データ型を定義、 [MeasureGroup](../objects/group-element-assl.md)要素。|  
|[MeasureGroupBinding データ型&#40;不一致の&#41; &#40;ASSL&#41;](measuregroupbinding-data-type-out-of-line-assl.md)|メジャー グループへのバインドを表すプリミティブ データ型を定義します。|  
|[MeasureGroupDimension データ型&#40;ASSL&#41;](measuregroupdimension-data-type-assl.md)|ディメンションとメジャー グループとの間のリレーションシップを表す抽象プリミティブ データ型を定義します。|  
|[MeasureGroupDimensionBinding データ型&#40;ASSL&#41;](measuregroupdimensionbinding-data-type-assl.md)|ディメンションとメジャー グループとのバインドを表す派生データ型を定義します。|  
|[MeasureGroupHierarchy データ型&#40;ASSL&#41;](measuregrouphierarchy-data-type-assl.md)|メジャー グループの階層に関する情報を表すプリミティブ データ型を定義します。|  
|[MiningModelColumn データ型&#40;ASSL&#41;](miningmodelcolumn-data-type-assl.md)|内の列に関する情報を表すプリミティブ データ型を定義、 [MiningModel](../objects/miningmodel-element-assl.md)要素。|  
|[MiningModelingFlag データ型&#40;ASSL&#41;](miningmodelingflag-data-type-assl.md)|使用可能なモデリング フラグを表すプリミティブ データ型を定義、 [ModelingFlag](../objects/modelingflag-element-assl.md)要素。|  
|[MiningStructureColumn データ型&#40;ASSL&#41;](miningstructurecolumn-data-type-assl.md)|内の列に関する情報を表す抽象プリミティブ データ型を定義、 [MiningStructure](../objects/miningstructure-element-assl.md)要素。|  
|[OlapDataSource データ型&#40;ASSL&#41;](olapdatasource-data-type-assl.md)|マルチ ディメンションを表す派生データ型を定義[データソース](../objects/datasource-element-assl.md)要素。|  
|[PartitionBinding データ型&#40;ASSL&#41;](partitionbinding-data-type-assl.md)|バインドを表す派生データ型を定義、[パーティション](../objects/partition-element-assl.md)要素。|  
|[Permission データ型&#40;ASSL&#41;](permission-data-type-assl.md)|個別の権限についての情報を表す抽象プリミティブ データ型を定義します。|  
|[PerspectiveAction データ型&#40;ASSL&#41;](perspectiveaction-data-type-assl.md)|内のアクションに関する情報を表すプリミティブ データ型を定義、[パースペクティブ](../objects/perspective-element-assl.md)要素。|  
|[PerspectiveAttribute データ型&#40;ASSL&#41;](perspectiveattribute-data-type-assl.md)|内の属性に関する情報を表すプリミティブ データ型を定義、 [PerspectiveDimension](perspectivedimension-data-type-assl.md)要素。|  
|[PerspectiveCalculation データ型&#40;ASSL&#41;](perspectivecalculation-data-type-assl.md)|計算間のリレーションシップを表すプリミティブ データ型を定義し、[パースペクティブ](../objects/perspective-element-assl.md)要素。|  
|[PerspectiveDimension データ型&#40;ASSL&#41;](perspectivedimension-data-type-assl.md)|パースペクティブ内のディメンションに関する情報を表すプリミティブ データ型を定義します。|  
|[PerspectiveHierarchy データ型&#40;ASSL&#41;](perspectivehierarchy-data-type-assl.md)|内の階層に関する情報を表すプリミティブ データ型を定義、 [PerspectiveDimension](perspectivedimension-data-type-assl.md)要素。|  
|[PerspectiveKpi データ型&#40;ASSL&#41;](perspectivekpi-data-type-assl.md)|主要業績評価指標 (KPI) に関する情報を表すプリミティブ データ型を定義、[パースペクティブ](../objects/perspective-element-assl.md)要素。|  
|[PerspectiveMeasure データ型&#40;ASSL&#41;](perspectivemeasure-data-type-assl.md)|内のメジャーに関する情報を表すプリミティブ データ型を定義、 [PerspectiveMeasureGroup](perspectivemeasuregroup-data-type-assl.md)要素。|  
|[PerspectiveMeasureGroup データ型&#40;ASSL&#41;](perspectivemeasuregroup-data-type-assl.md)|内のメジャー グループに関する情報を表すプリミティブ データ型を定義、[パースペクティブ](../objects/perspective-element-assl.md)要素。|  
|[ProactiveCachingBinding データ型&#40;ASSL&#41;](proactivecachingbinding-data-type-assl.md)|情報を表す抽象派生データ型を定義、 [ProactiveCaching](../objects/proactivecaching-element-assl.md)要素をキャッシュの再構築を必要とするデータ ソースの変更や再構築プロセスの状態に関するします。|  
|[ProactiveCachingIncrementalProcessingBinding データ型&#40;ASSL&#41;](proactivecachingincrementalprocessingbinding-data-type-assl.md)|バインドを表す派生データ型を定義、 [ProactiveCaching](../objects/proactivecaching-element-assl.md)キャッシュの再構築プロセスの状態に関する要素。|  
|[ProactiveCachingInheritedBinding データ型&#40;ASSL&#41;](proactivecachinginheritedbinding-data-type-assl.md)|情報を表す派生データ型を定義、 [ProactiveCaching](../objects/proactivecaching-element-assl.md)テーブルおよびビューをキャッシュの再構築を必要とする既存のデータ バインドを介して識別されるデータ ソース変更に関して要素。|  
|[ProactiveCachingObjectNotificationBinding データ型&#40;ASSL&#41;](proactivecachingobjectnotificationbinding-data-type-assl.md)|情報を表す抽象派生データ型を定義、 [ProactiveCaching](../objects/proactivecaching-element-assl.md)テーブルおよびビューの既存のデータ バインドを介して識別されるまたは指定されたテーブルおよびビューで、データ ソース変更に関して要素キャッシュの再構築する必要があります。|  
|[ProactiveCachingQueryBinding データ型&#40;ASSL&#41;](querybinding-data-type-assl.md)|情報を表す派生データ型を定義、 [ProactiveCaching](../objects/proactivecaching-element-assl.md)テーブルおよびビュー、キャッシュの再構築を必要とする指定されたクエリの実行を介して識別されるデータ ソース変更に関して要素。|  
|[ProactiveCachingTablesBinding データ型&#40;ASSL&#41;](proactivecachingtablesbinding-data-type-assl.md)|情報を表す派生データ型を定義、 [ProactiveCaching](../objects/proactivecaching-element-assl.md)指定されたテーブルおよびビューをキャッシュの再構築を必要とするデータ ソース変更に関して要素。|  
|[PushedDataSource データ型&#40;ASSL&#41;](pusheddatasource-data-type-assl.md)|データ ソースを表すプリミティブ データ型を定義 (など、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]パッケージ) へのデータを「プッシュ」するために使用される、[キューブ](../objects/cube-element-assl.md)要素。|  
|[QueryBinding データ型&#40;ASSL&#41;](querybinding-data-type-assl.md)|関連付けを表す派生データ型を定義、[データソース](../objects/datasource-element-assl.md)を持つ要素を[QueryDefinition](../properties/querydefinition-element-assl.md)要素。|  
|[ReferenceMeasureGroupDimension データ型&#40;ASSL&#41;](referencemeasuregroupdimension-data-type-assl.md)|中間ディメンションを介してファクト テーブルに間接的に関連するディメンションを表す派生データ型を定義します  (たとえば、Sales メジャー グループは、Customer ディメンションを介して関連する Geography ディメンションを参照できます)。|  
|[RegularMeasureGroupDimension データ型&#40;ASSL&#41;](regularmeasuregroupdimension-data-type-assl.md)|ディメンションとメジャー グループの間の標準のリレーションシップを表す派生データ型を定義します。|  
|[RelationalDataSource データ型&#40;ASSL&#41;](relationaldatasource-data-type-assl.md)|表す派生データ型を定義、[データソース](../objects/datasource-element-assl.md)要素は、リレーショナル データ ソースに基づきます。|  
|[ReportAction データ型&#40;ASSL&#41;](reportaction-data-type-assl.md)|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] レポートを生成するアクションを表す派生データ型を定義します。|  
|[RowBinding データ型&#40;ASSL&#41;](rowbinding-data-type-assl.md)|内のテーブルの行へのバインディングを表す派生データ型を定義、 [DataSourceView](../objects/datasourceview-element-assl.md)要素。|  
|[ScalarMiningStructureColumn データ型&#40;ASSL&#41;](scalarminingstructurecolumn-data-type-assl.md)|表す派生データ型を定義、 [MiningStructureColumn](miningstructurecolumn-data-type-assl.md)要素に関連付けられている入れ子になったテーブルではなく、スカラー値を含む、 [TableMiningStructureColumn](tableminingstructurecolumn-data-type-assl.md)要素入れ子になったテーブルが含まれています。|  
|[StandardAction データ型&#40;ASSL&#41;](standardaction-data-type-assl.md)|いずれかを表す派生データ型を定義[アクション](../objects/action-element-assl.md)以外の要素、 [DrillThroughAction](drillthroughaction-data-type-assl.md)要素または[ReportAction](reportaction-data-type-assl.md)要素。|  
|[TableBinding データ型&#40;ASSL&#41;](tablebinding-data-type-assl.md)|テーブルへのバインドを表す派生データ型を定義します。|  
|[TableMiningStructureColumn データ型&#40;ASSL&#41;](tableminingstructurecolumn-data-type-assl.md)|表す派生データ型を定義、 [MiningStructureColumn](miningstructurecolumn-data-type-assl.md)要素に関連付けられているスカラー値ではなく、入れ子になったテーブルを含む、 [ScalarMiningStructureColumn](scalarminingstructurecolumn-data-type-assl.md)要素スカラー値が含まれています。|  
|[TabularBinding データ型&#40;ASSL&#41;](tabularbinding-data-type-assl.md)|テーブルやキューブ ディメンションなどの表アイテムへのバインドを表す抽象派生データ型を定義します。|  
|[TimeAttributeBinding データ型&#40;ASSL&#41;](timebinding-data-type-assl.md)|「プレース ホルダー」バインドの属性のキー列など、サーバー時間ディメンションで生成されたデータ項目を表す派生データ型を定義します。|  
|[TimeBinding データ型&#40;ASSL&#41;](timebinding-data-type-assl.md)|期間へのバインドを表す派生データ型を定義します。|  
|[Translation データ型&#40;ASSL&#41;](translation-data-type-assl.md)|ローカライズされた翻訳を表すプリミティブ データ型を定義します。|  
|[UserDefinedGroupBinding データ型&#40;ASSL&#41;](userdefinedgroupbinding-data-type-assl.md)|属性のユーザー定義のグループ化を表す派生データ型を定義します。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML 要素階層&#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  