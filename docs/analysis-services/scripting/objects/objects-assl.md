---
title: "オブジェクト (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ASSL, objects
- objects [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
ms.assetid: 0f672b93-c317-47e5-b44d-ecea9b587c98
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 749c363a814590705b61d0821f1fee44ea93d488
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="objects-assl"></a>オブジェクト (ASSL)
  このリファレンス セクションでは、Analysis Services スクリプト言語 (ASSL) スキーマでオブジェクトの役割を果たす各要素の構文と使い方について説明します。  
  
 ASSL スキーマには、開発者の観点からの XML 要素のみが含まれていますが、このセクションで説明する要素などに対応して、オブジェクト**データベース**、**キューブ**、および**ディメンション**のインスタンスに含まれるオブジェクトの階層内のオブジェクト[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
 オブジェクトは ASSL スキーマのリーフレベル要素にはなりませんが、子要素とオブジェクト プロパティに対応する要素を持ちます。  
  
 プロパティのように見えるスキーマ内のリーフレベル要素は、要素の型がオブジェクト型であるため、オブジェクトとして分類される場合があります。 たとえば、**ソース**の**ディメンション**オブジェクトの型が**DimensionBinding**です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|要素|Description|  
|-------------|-----------------|  
|[Account 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/account-element-assl.md)|内の勘定科目の種類に関する詳細を含む、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[Action 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/action-element-assl.md)|使用できるアクションに関する情報が含まれています、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素または[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素。|  
|[Aggregation 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/aggregation-element-assl.md)|1 つの集計を定義、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)要素。|  
|[AggregationDesign 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)|データベース内の複数のパーティションで共有できる一連の集計定義を定義します。|  
|[AggregationInstance 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)|パーティションに対して集計インスタンスを定義します。|  
|[AlgorithmParameter 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)|使用されるアルゴリズムのパラメーターを定義、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)要素。|  
|[AllMemberTranslation 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/allmembertranslation-element-assl.md)|すべてのメンバーのキャプションの翻訳が含まれています、[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)要素。|  
|[Annotation 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/annotation-element-assl.md)|ASSL スキーマを拡張するために使用される要素を格納します。|  
|[Assembly 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)|表す、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリまたは COM ダイナミック リンク ライブラリ (DLL) に関連付けられている、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)要素または[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[Attribute 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/attribute-element-assl.md)|属性の説明を格納します。|  
|[AttributeAllMemberTranslation 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/attributeallmembertranslation-element-assl.md)|すべてのメンバーのキャプションの翻訳が含まれています、 [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)要素。|  
|[AttributePermission 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/attributepermission-element-assl.md)|メンバーがアクセス権を定義、[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)で個々 のディメンションの属性に要素がある、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。|  
|[AttributeRelationship 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)|2 つの属性間のリレーションシップに関する詳細を提供します。|  
|[Block 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/block-element-assl.md)|またはのバイナリ コンテンツの一部が含まれています、 [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)要素。|  
|[Calculation 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/calculation-element-assl.md)|計算 Asssociates、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素。|  
|[CalculationProperty 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)|使用する計算のユーザー インターフェイスのプロパティのコレクションを格納、 [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)要素。|  
|[CaptionColumn 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/captioncolumn-element-assl.md)|属性のキャプションを指定する列を定義します。|  
|[CellPermission 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)|メンバーがアクセス許可を示します、[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)要素が個々 のセル内にある、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。|  
|[Column 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/column-element-assl.md)|親要素に関連付けられた列コレクション内の列を記述します。|  
|[Command 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/command-element-assl.md)|Commands コレクションの親要素のコンテキスト内で使用できるコマンドを定義します。|  
|[Cube 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)|通常、仮想、またはリンク キューブを定義、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[CubePermission 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)|特定のメンバーの権限を定義[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)要素に、特定の[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。|  
|[CustomRollupColumn 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/customrollupcolumn-element-assl.md)|カスタム ロールアップ式を指定する列の詳細を定義します。|  
|[CustomRollupPropertiesColumn 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/customrolluppropertiescolumn-element-assl.md)|カスタム ロールアップ式のプロパティを指定する列の詳細を定義します。|  
|[データ要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/data-element-assl.md)|含まれています (子のコレクションで**ブロック**要素) のバイナリ コンテンツ、 [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)要素。|  
|[Database 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベースを定義します。|  
|[DatabasePermission 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/databasepermission-element-assl.md)|既定のアクセス許可を定義、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)、特定の要素[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)要素。|  
|[DataSource 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/datasource-element-assl.md)|データ ソースを定義、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[DataSourcePermission 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/datasourcepermission-element-assl.md)|既定のアクセス許可を定義、[データソース](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)、特定のデータ型[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)要素。|  
|[DataSourceView 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)|によって使用されるデータ ソース ビューの定義、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[Dimension 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)|ディメンションを定義します。|  
|[DimensionPermission 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/dimensionpermission-element-assl.md)|特定に属しているアクセス許可を定義[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)特定のデータベース ディメンションまたはキューブ ディメンションの要素。|  
|[ErrorConfiguration 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|親要素が処理されるときに発生する可能性があるエラーを処理するための設定を指定します。|  
|[Event 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/event-element-assl.md)|一部としてキャプチャするイベントを定義、[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)要素。|  
|[File 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/file-element-assl.md)|構成するファイルのいずれかを定義、 [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)要素。|  
|[ForeignKeyColumn 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/foreignkeycolumn-element-assl.md)|リレーショナル データ ソースの親テーブルへの結合を識別します。|  
|[グループ要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/group-element-assl.md)|属性にバインドされているメンバーのグループを定義します。|  
|[Hierarchy 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)|ディメンションの階層を定義します。|  
|[IncrementalProcessingNotification 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/incrementalprocessingnotification-element-assl.md)|情報が含まれています、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)増分処理の進行状況を判断するために実行するクエリについて要素。|  
|[KeyColumn 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)|属性のキーまたはその一部である、列の定義を格納します。|  
|[Kpi 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/kpi-element-assl.md)|内で主要業績評価指標 (KPI) を定義する、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素または[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素。|  
|[Level 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/level-element-assl.md)|内のレベルを定義、[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)要素。|  
|[MdxScript 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)|関連付けられている多次元式 (MDX) スクリプトに関する情報が含まれています、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。|  
|[Measure 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/measure-element-assl.md)|メジャーを定義します。|  
|[MeasureGroup 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|同じレベルの粒度でメジャーのセットを定義します。|  
|[Member 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/member-element-assl.md)|メンバーの名前を含む、[グループ](../../../analysis-services/scripting/objects/group-element-assl.md)要素であるかの[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)要素。|  
|[MiningModel 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|単一のデータ マイニング モデルを定義します。|  
|[MiningModelPermission 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md)|アクセス許可のメンバーを定義、[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)、個別の要素がある[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)要素。|  
|[MiningStructure 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|マイニング モデルのセットの構造を定義します。|  
|[MiningStructurePermission 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)|メンバーがアクセス権を定義、[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)、個別の要素がある[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)要素。|  
|[ModelingFlag 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/modelingflag-element-assl.md)|マイニング構造またはマイニング モデル内の列のモデリング フラグを格納します。|  
|[NameColumn 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/namecolumn-element-assl.md)|親要素の名前を指定する列を示します。|  
|[NamingTemplateTranslation 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/namingtemplatetranslation-element-assl.md)|ローカライズされた翻訳を提供、 **NamingTemplate**要素の親を[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)データ型。|  
|[Partition 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)|パーティションを定義、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)要素またはの行外でのパーティション バインド[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)要素。|  
|[Perspective 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/perspective-element-assl.md)|詳細のパースペクティブを定義、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。|  
|[ProactiveCaching 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)|親要素のプロアクティブ キャッシュの設定を定義します。|  
|[QueryNotification 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/querynotification-element-assl.md)|情報が含まれています、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)データ ソースが変更されているかどうかを判断するために実行するクエリについて要素。|  
|[ReportFormatParameter 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md)|指定するパラメーターの値と名前を含む方法、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]実行時にレポートを書式設定します。|  
|[ReportParameter 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/reportparameter-element-assl.md)|実行時に [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] レポートに渡されるパラメーターの名前および値を格納します。|  
|[Role 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)|セキュリティ ロールに関する情報を格納します。|  
|[Server 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスを記述します。|  
|[ServerProperty 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|関連付けられているサーバーのプロパティを定義、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)要素。|  
|[SkippedLevelsColumn 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/skippedlevelscolumn-element-assl.md)|各メンバーとその親の間でスキップされた (空の) レベルの数を格納する列の詳細を指定します。|  
|[SourceMeasureGroup 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/sourcemeasuregroup-element-assl.md)|マイニング構造列のデータ ソースとして機能するメジャー グループを識別します。|  
|[TableNotification 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/tablenotification-element-assl.md)|情報が含まれています、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)テーブルまたはビューが変更されているデータ ソース内の要素。|  
|[Trace 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/trace-element-assl.md)|クエリできるトレースを定義します。|  
|[Translation 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/translation-element-assl.md)|親のローカライズされた翻訳を提供、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)コレクション。|  
|[UnaryOperatorColumn 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/unaryoperatorcolumn-element-assl.md)|単項演算子を指定する列の詳細を定義します。|  
|[UnknownMemberTranslation 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/unknownmembertranslation-element-assl.md)|キャプションの翻訳が含まれています、 [UnknownMember](../../../analysis-services/scripting/properties/unknownmember-element-assl.md)要素を[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)要素。|  
|[ValueColumn 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/valuecolumn-element-assl.md)|親要素の値を指定する列を識別します。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML 要素の階層 &#40;です。ASSL &#41;](../../../analysis-services/scripting/analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  

