---
title: コレクション (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4bf48fd86c22940697edb0499fa80bbbbdb3bc78
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34036489"
---
# <a name="collections-assl"></a>コレクション (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  このリファレンス セクションでは、Analysis Services スクリプト言語 (ASSL) スキーマでコレクションの役割を果たす各要素の構文と使い方について説明します。  
  
 ASSL スキーマには、開発者の観点からの XML 要素のみが含まれていますが、このセクションで説明する要素などに対応して、オブジェクトのコレクション、**ディメンション**と**キューブ**コレクション。  
  
 コレクションは複数形の名詞がコレクションを指定する、オブジェクト要素のコレクションではほとんどの場合 (例については、**キューブ**)、コレクションに同じ名詞の単数で指定された要素が含まれています (たとえば、 **キューブ**)。  
  
 場合によっては、スキーマがこの一般的な規則に従っていないことがあります。 たとえば、 **ClassifiedColumns**コレクションを含む**ClassifiedColumnID**要素。  
  
 また、コレクションにはオブジェクトでなくオブジェクト プロパティに対応する要素が含まれている場合もあります。 たとえば、**エイリアス**コレクションが含まれます**エイリアス**プロパティ、それぞれが単純な文字列値です。  
  
|要素|Description|  
|-------------|-----------------|  
|[要素をアカウント&#40;ASSL&#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)|定義されている勘定科目の種類のコレクションを格納、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[Actions 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/actions-element-assl.md)|動作のコレクションが含まれています、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)または[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素。|  
|[AggregationDesigns 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/aggregationdesigns-element-assl.md)|データベースの複数のパーティションで共有できる集計デザインのコレクションを格納します。|  
|[AggregationInstances 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/aggregationinstances-element-assl.md)|定義されている集計インスタンスのコレクションを格納、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)要素。|  
|[Aggregations 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/aggregations-element-assl.md)|に対して定義された集計のコレクションを格納、 [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)要素。|  
|[AlgorithmParameters 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/algorithmparameters-element-assl.md)|使用されるアルゴリズムのパラメーターのコレクションが含まれています、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)要素。|  
|[Aliases 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/aliases-element-assl.md)|コレクションを格納[エイリアス](../../../analysis-services/scripting/properties/alias-element-assl.md)要素に関連付けられた、[アカウント](../../../analysis-services/scripting/objects/account-element-assl.md)要素|  
|[AllMemberTranslations 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/allmembertranslations-element-assl.md)|コレクションを格納[翻訳](../../../analysis-services/scripting/objects/translation-element-assl.md)要素の All メンバーのキャプションに対する、[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)要素。|  
|[Annotations 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/annotations-element-assl.md)|コレクションを格納[注釈](../../../analysis-services/scripting/objects/annotation-element-assl.md)親要素に関連付けられている要素です。|  
|[Assemblies 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)|コレクションを格納[アセンブリ](../../../analysis-services/scripting/objects/assembly-element-assl.md)要素に関連付けられた、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)要素または[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[AttributeAllMemberTranslations 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/attributeallmembertranslations-element-assl.md)|ディメンションの All メンバーのキャプションに対する翻訳のコレクションを格納します。|  
|[AttributePermissions 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/attributepermissions-element-assl.md)|個々 の属性の権限のコレクションを格納[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)の特定のディメンション上の要素、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。|  
|[AttributeRelationships 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/attributerelationships-element-assl.md)|コレクションを格納[AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)属性用の要素。|  
|[要素の属性&#40;ASSL&#41;](../../../analysis-services/scripting/collections/attributes-element-assl.md)|関連付けられているディメンションの属性のコレクションを格納します。|  
|[要素はブロック&#40;ASSL&#41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)|ブロックのバイナリの内容を表すバイナリ データのコレクションを格納、 [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)要素。|  
|[CalculationProperties 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)|コレクションを格納[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)要素に関連付けられた、 [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)要素。|  
|[Calculations 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/calculations-element-assl.md)|コレクションを格納[PerspectiveCalculation](../../../analysis-services/scripting/data-type/perspectivecalculation-data-type-assl.md)要素に関連付けられた、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素。|  
|[CellPermissions 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/cellpermissions-element-assl.md)|セルの関連付けられている権限のコレクションを格納[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。|  
|[ClassifiedColumns 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md)|によって分類される関連列のコレクションを格納、 [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)要素。|  
|[Columns 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/columns-element-assl.md)|親要素に関連付けられた列のコレクションを格納します。|  
|[要素をコマンド&#40;ASSL&#41;](../../../analysis-services/scripting/collections/commands-element-assl.md)|[MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md) 要素に関連付けられた [Command](../../../analysis-services/scripting/objects/command-element-assl.md) 要素のコレクションを格納します。|  
|[CubePermissions 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/cubepermissions-element-assl.md)|適用できる権限のコレクションを格納、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。|  
|[要素はキューブ&#40;ASSL&#41;](../../../analysis-services/scripting/collections/cubes-element-assl.md)|コレクションを格納[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素に関連付けられた、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[DatabasePermissions 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/databasepermissions-element-assl.md)|コレクションを格納[DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md)要素に関連付けられた、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[要素をデータベース&#40;ASSL&#41;](../../../analysis-services/scripting/collections/databases-element-assl.md)|コレクションを格納[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素に関連付けられた、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)要素。|  
|[DataSources 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/datasources-element-assl.md)|コレクションを格納[DataSourcePermission](../../../analysis-services/scripting/objects/datasourcepermission-element-assl.md)要素に関連付けられた、[データソース](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)データ型。|  
|[DataSourcePermissions 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/datasourcepermissions-element-assl.md)|コレクションを格納[データソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)要素に関連付けられた、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[DataSourceViews 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/datasourceviews-element-assl.md)|コレクションを格納[DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)要素に関連付けられた、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[DimensionPermissions 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/dimensionpermissions-element-assl.md)|適用できる権限のコレクションを格納、[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)要素または[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)要素。|  
|[要素の寸法&#40;ASSL&#41;](../../../analysis-services/scripting/collections/dimensions-element-assl.md)|親要素に関連付けられたディメンションのコレクションを格納します。|  
|[Events 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/events-element-assl.md)|によってキャプチャされる Event 要素のコレクションを定義、[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)です。|  
|[要素をファイル&#40;ASSL&#41;](../../../analysis-services/scripting/collections/files-element-assl.md)|コレクションを格納[ファイル](../../../analysis-services/scripting/objects/file-element-assl.md)を構成する要素、 [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)要素。|  
|[ForeignKeyColumns 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/foreignkeycolumns-element-assl.md)|リレーショナル データ ソースの親テーブルへの結合を識別する列のコレクションを格納します。|  
|[Groups 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/groups-element-assl.md)|属性にバインドされるメンバーのグループのコレクションを格納します。|  
|[Hierarchies 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/hierarchies-element-assl.md)|親要素に関連付けられた [Hierarchy](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) 要素のコレクションを格納します。|  
|[IncrementalProcessingNotifications 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/incrementalprocessingnotifications-element-assl.md)|コレクションを格納[IncrementalProcessingNotification](../../../analysis-services/scripting/objects/incrementalprocessingnotification-element-assl.md)要素に情報を提供する、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)の進行状況を判断するために実行するクエリについて要素増分処理します。|  
|[KeyColumns 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)|コレクションを格納[KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)親オブジェクトの要素の定義。|  
|[Kpis 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/kpis-element-assl.md)|コレクションを格納[Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)親要素に関連付けられている要素です。|  
|[要素のレベル&#40;ASSL&#41;](../../../analysis-services/scripting/collections/levels-element-assl.md)|コレクションを格納[レベル](../../../analysis-services/scripting/objects/level-element-assl.md)内の要素、[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)要素。|  
|[MdxScripts 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)|コレクションを格納[MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)要素に関連付けられた、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。|  
|[MeasureGroups 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/measuregroups-element-assl.md)|コレクションを格納[MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)親要素に関連付けられている要素です。|  
|[要素の測定&#40;ASSL&#41;](../../../analysis-services/scripting/collections/measures-element-assl.md)|コレクションを格納[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)親要素に関連付けられている要素です。|  
|[Members 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/members-element-assl.md)|コレクションを格納[メンバー](../../../analysis-services/scripting/objects/member-element-assl.md)親要素の要素。|  
|[MiningModelPermissions 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/miningmodelpermissions-element-assl.md)|権限のコレクションが含まれています、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)要素。|  
|[MiningModels 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/miningmodels-element-assl.md)|コレクションを格納[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)要素に関連付けられた、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)です。|  
|[MiningStructurePermissions 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md)|権限のコレクションが含まれています、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)要素。|  
|[MiningStructures 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/miningstructures-element-assl.md)|コレクションを格納[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)内の要素、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[ModelingFlags 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/modelingflags-element-assl.md)|コレクションを格納[ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md)要素内の列に、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)または[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)です。|  
|[NamingTemplateTranslations 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/namingtemplatetranslations-element-assl.md)|ローカライズされた変換のコレクションを提供、 [NamingTemplate](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md)の親要素[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)です。|  
|[要素をパーティション分割&#40;ASSL&#41;](../../../analysis-services/scripting/collections/partitions-element-assl.md)|コレクションを格納[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)によって使用される要素、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)要素、またはの不一致を構成するパーティション バインドのコレクション[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)要素。|  
|[Perspectives 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/perspectives-element-assl.md)|コレクションを格納[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素に関連付けられた、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。|  
|[QueryNotifications 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/querynotifications-element-assl.md)|コレクションを格納[QueryNotification](../../../analysis-services/scripting/objects/querynotification-element-assl.md)要素に情報を提供する、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)データ ソースが変更されているかどうかを判断するために実行するクエリについて要素。|  
|[ReportFormatParameters 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/reportformatparameters-element-assl.md)|コレクションを格納[ReportFormatParameter](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md)用の要素、 [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)要素。|  
|[ReportParameters 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/reportparameters-element-assl.md)|コレクションを格納[ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md)用の要素、 [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)要素。|  
|[Roles 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/roles-element-assl.md)|親要素の下に定義された [Role](../../../analysis-services/scripting/objects/role-element-assl.md) 要素のコレクションを格納します。|  
|[ServerProperties 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)|コレクションを格納[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)要素に関連付けられた、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)要素。|  
|[TableNotifications 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/tablenotifications-element-assl.md)|コレクションを格納[TableNotification](../../../analysis-services/scripting/objects/tablenotification-element-assl.md)要素に情報を提供する、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)テーブルまたは変更されているデータ ソース内のビューについての要素。|  
|[要素をトレース&#40;ASSL&#41;](../../../analysis-services/scripting/collections/traces-element-assl.md)|[Server](../../../analysis-services/scripting/objects/server-element-assl.md) 要素に関連付けられた [Trace](../../../analysis-services/scripting/objects/trace-element-assl.md) 要素のコレクションを格納します。|  
|[Translations 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/translations-element-assl.md)|コレクションを格納[翻訳](../../../analysis-services/scripting/objects/translation-element-assl.md)親要素に関連付けられている要素です。|  
|[UnknownMemberTranslations 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/unknownmembertranslations-element-assl.md)|キャプションに対する翻訳のコレクションが含まれています、 [UnknownMember](../../../analysis-services/scripting/properties/unknownmember-element-assl.md)ディメンションの要素。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML 要素の階層 & #40 です。ASSL & #41;](../../../analysis-services/scripting/analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
