---
title: オブジェクト (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- ASSL, objects
- objects [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
ms.assetid: 0f672b93-c317-47e5-b44d-ecea9b587c98
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 302ad689a3e54a7a9937929b9c20f975fc3cd98f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079612"
---
# <a name="objects-assl"></a>オブジェクト (ASSL)
  このリファレンス セクションでは、Analysis Services スクリプト言語 (ASSL) スキーマでオブジェクトの役割を果たす各要素の構文と使い方について説明します。  
  
 このセクションで説明する要素が、オブジェクトになど対応 ASSL スキーマに開発者の観点からの XML 要素のみが含まれますが`Database`、 `Cube`、および`Dimension`に含まれるオブジェクトの階層内のオブジェクトをインスタンス[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
 オブジェクトは ASSL スキーマのリーフレベル要素にはなりませんが、子要素とオブジェクト プロパティに対応する要素を持ちます。  
  
 プロパティのように見えるスキーマ内のリーフレベル要素は、要素の型がオブジェクト型であるため、オブジェクトとして分類される場合があります。 たとえば、`Source` オブジェクトの `Dimension` は、`DimensionBinding` 型です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|要素|説明|  
|-------------|-----------------|  
|[要素をアカウント&#40;ASSL&#41;](account-element-assl.md)|内で勘定科目の種類に関する詳細を含む、[データベース](database-element-assl.md)要素。|  
|[Action 要素&#40;ASSL&#41;](action-element-assl.md)|使用できるアクションに関する情報を格納する[キューブ](cube-element-assl.md)要素または[パースペクティブ](perspective-element-assl.md)要素。|  
|[Aggregation 要素&#40;ASSL&#41;](aggregation-element-assl.md)|1 つの集計を定義、[パーティション](partition-element-assl.md)要素。|  
|[AggregationDesign 要素&#40;ASSL&#41;](aggregationdesign-element-assl.md)|データベース内の複数のパーティションで共有できる一連の集計定義を定義します。|  
|[AggregationInstance 要素&#40;ASSL&#41;](aggregationinstance-element-assl.md)|パーティションに対して集計インスタンスを定義します。|  
|[AlgorithmParameter 要素&#40;ASSL&#41;](algorithmparameter-element-assl.md)|使用されるアルゴリズムのパラメーターを定義、 [MiningModel](miningmodel-element-assl.md)要素。|  
|[AllMemberTranslation 要素&#40;ASSL&#41;](translation-element-assl.md)|すべてのメンバーのキャプションの翻訳が含まれています、[階層](hierarchy-element-assl.md)要素。|  
|[Annotation 要素&#40;ASSL&#41;](annotation-element-assl.md)|ASSL スキーマを拡張するために使用される要素を格納します。|  
|[Assembly 要素&#40;ASSL&#41;](assembly-element-assl.md)|表す、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]アセンブリまたは COM ダイナミック リンク ライブラリ (DLL) に関連付けられている、 [Server](server-element-assl.md)要素または[データベース](database-element-assl.md)要素。|  
|[要素の属性&#40;ASSL&#41;](attribute-element-assl.md)|属性の説明を格納します。|  
|[AttributeAllMemberTranslation 要素&#40;ASSL&#41;](attributeallmembertranslation-element-assl.md)|すべてのメンバーのキャプションの翻訳が含まれています、 [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)要素。|  
|[AttributePermission 要素&#40;ASSL&#41;](attributepermission-element-assl.md)|そのメンバーのアクセス許可を定義、[ロール](role-element-assl.md)で個々 のディメンションの属性に要素がある、[キューブ](cube-element-assl.md)要素。|  
|[AttributeRelationship 要素&#40;ASSL&#41;](attributerelationship-element-assl.md)|2 つの属性間のリレーションシップに関する詳細を提供します。|  
|[要素のブロック&#40;ASSL&#41;](block-element-assl.md)|すべてまたは一部のバイナリ コンテンツが含まれています、 [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)要素。|  
|[Calculation 要素&#40;ASSL&#41;](calculation-element-assl.md)|計算を関連付けます Asssociates、[パースペクティブ](perspective-element-assl.md)要素。|  
|[CalculationProperty 要素&#40;ASSL&#41;](calculationproperty-element-assl.md)|使用される計算のユーザー インターフェイスのプロパティのコレクションを格納する[MdxScript](mdxscript-element-assl.md)要素。|  
|[CaptionColumn 要素&#40;ASSL&#41;](column-element-assl.md)|属性のキャプションを指定する列を定義します。|  
|[CellPermission 要素&#40;ASSL&#41;](cellpermission-element-assl.md)|そのメンバーのアクセス許可を示します、[ロール](role-element-assl.md)内の各セルに要素がある、[キューブ](cube-element-assl.md)要素。|  
|[Column 要素&#40;ASSL&#41;](column-element-assl.md)|親要素に関連付けられた列コレクション内の列を記述します。|  
|[要素をコマンド&#40;ASSL&#41;](command-element-assl.md)|Commands コレクションの親要素のコンテキスト内で使用できるコマンドを定義します。|  
|[キューブ要素&#40;ASSL&#41;](cube-element-assl.md)|通常、仮想、またはリンク キューブを定義、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [データベース](database-element-assl.md)要素。|  
|[CubePermission 要素&#40;ASSL&#41;](cubepermission-element-assl.md)|特定のメンバーの権限を定義します[ロール](role-element-assl.md)要素にある特定[キューブ](cube-element-assl.md)要素。|  
|[CustomRollupColumn 要素&#40;ASSL&#41;](customrollupcolumn-element-assl.md)|カスタム ロールアップ式を指定する列の詳細を定義します。|  
|[CustomRollupPropertiesColumn 要素&#40;ASSL&#41;](customrolluppropertiescolumn-element-assl.md)|カスタム ロールアップ式のプロパティを指定する列の詳細を定義します。|  
|[データ要素&#40;ASSL&#41;](data-element-assl.md)|含まれています (子のコレクションで`Block`要素) のバイナリ コンテンツを[ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)要素。|  
|[Database 要素&#40;ASSL&#41;](database-element-assl.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベースを定義します。|  
|[DatabasePermission 要素&#40;ASSL&#41;](databasepermission-element-assl.md)|既定の権限を定義、[データベース](database-element-assl.md)、特定の要素[ロール](role-element-assl.md)要素。|  
|[DataSource 要素&#40;ASSL&#41;](datasource-element-assl.md)|データ ソースを定義、[データベース](database-element-assl.md)要素。|  
|[DataSourcePermission 要素&#40;ASSL&#41;](datasourcepermission-element-assl.md)|既定の権限を定義、 [DataSource](../data-type/datasource-data-type-assl.md) 、特定のデータ型[ロール](role-element-assl.md)要素。|  
|[DataSourceView 要素&#40;ASSL&#41;](datasourceview-element-assl.md)|によって使用されるデータ ソース ビューの定義、[データベース](database-element-assl.md)要素。|  
|[ディメンション要素&#40;ASSL&#41;](dimension-element-assl.md)|ディメンションを定義します。|  
|[DimensionPermission 要素&#40;ASSL&#41;](dimensionpermission-element-assl.md)|特定に属する権限を定義します[ロール](role-element-assl.md)特定のデータベース ディメンションまたはキューブ ディメンションの要素。|  
|[ErrorConfiguration 要素&#40;ASSL&#41;](errorconfiguration-element-assl.md)|親要素が処理されるときに発生する可能性があるエラーを処理するための設定を指定します。|  
|[Event 要素&#40;ASSL&#41;](event-element-assl.md)|一部としてキャプチャされるイベントを定義、[トレース](trace-element-assl.md)要素。|  
|[要素が&#40;ASSL&#41;](file-element-assl.md)|構成するファイルのいずれかを定義、 [ClrAssembly](../data-type/assembly-data-type-assl.md)要素。|  
|[ForeignKeyColumn 要素&#40;ASSL&#41;](keycolumn-element-assl.md)|リレーショナル データ ソースの親テーブルへの結合を識別します。|  
|[要素をグループ化&#40;ASSL&#41;](group-element-assl.md)|属性にバインドされているメンバーのグループを定義します。|  
|[Hierarchy 要素&#40;ASSL&#41;](hierarchy-element-assl.md)|ディメンションの階層を定義します。|  
|[IncrementalProcessingNotification 要素&#40;ASSL&#41;](incrementalprocessingnotification-element-assl.md)|情報が含まれています、 [ProactiveCaching](proactivecaching-element-assl.md)増分処理の進行状況を判断するために実行するクエリについての要素。|  
|[KeyColumn 要素&#40;ASSL&#41;](keycolumn-element-assl.md)|属性のキーまたはその一部である、列の定義を格納します。|  
|[Kpi 要素&#40;ASSL&#41;](kpi-element-assl.md)|内で主要業績評価指標 (KPI) を定義する、[キューブ](cube-element-assl.md)要素または[パースペクティブ](perspective-element-assl.md)要素。|  
|[上位の要素&#40;ASSL&#41;](level-element-assl.md)|内のレベルを定義、[階層](hierarchy-element-assl.md)要素。|  
|[MdxScript 要素&#40;ASSL&#41;](mdxscript-element-assl.md)|関連付けられている多次元式 (MDX) スクリプトに関する情報を格納する[キューブ](cube-element-assl.md)要素。|  
|[要素の測定&#40;ASSL&#41;](measure-element-assl.md)|メジャーを定義します。|  
|[MeasureGroup 要素&#40;ASSL&#41;](measuregroup-element-assl.md)|同じレベルの粒度でメジャーのセットを定義します。|  
|[Member 要素&#40;ASSL&#41;](member-element-assl.md)|メンバーの名前を含む、[グループ](group-element-assl.md)要素またはを[ロール](role-element-assl.md)要素。|  
|[MiningModel 要素&#40;ASSL&#41;](miningmodel-element-assl.md)|単一のデータ マイニング モデルを定義します。|  
|[MiningModelPermission 要素&#40;ASSL&#41;](miningmodelpermission-element-assl.md)|メンバーのアクセス許可を定義、[ロール](role-element-assl.md)要素は、個々 のケースが[MiningModel](miningmodel-element-assl.md)要素。|  
|[MiningStructure 要素&#40;ASSL&#41;](miningstructure-element-assl.md)|マイニング モデルのセットの構造を定義します。|  
|[MiningStructurePermission 要素&#40;ASSL&#41;](miningstructurepermission-element-assl.md)|そのメンバーのアクセス許可を定義、[ロール](role-element-assl.md)要素は、個々 のケースが[MiningStructure](miningstructure-element-assl.md)要素。|  
|[ModelingFlag 要素&#40;ASSL&#41;](modelingflag-element-assl.md)|マイニング構造またはマイニング モデル内の列のモデリング フラグを格納します。|  
|[NameColumn 要素&#40;ASSL&#41;](namecolumn-element-assl.md)|親要素の名前を指定する列を示します。|  
|[NamingTemplateTranslation 要素&#40;ASSL&#41;](namingtemplatetranslation-element-assl.md)|ローカライズされた翻訳を提供します、`NamingTemplate`親要素[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)データ型。|  
|[要素をパーティション分割&#40;ASSL&#41;](partition-element-assl.md)|パーティションを定義、 [MeasureGroup](measuregroup-element-assl.md)要素またはの行外でのパーティション バインド[MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)要素。|  
|[Perspective 要素&#40;ASSL&#41;](perspective-element-assl.md)|パースペクティブの詳細を定義、[キューブ](cube-element-assl.md)要素。|  
|[ProactiveCaching 要素&#40;ASSL&#41;](proactivecaching-element-assl.md)|親要素のプロアクティブ キャッシュの設定を定義します。|  
|[QueryNotification 要素&#40;ASSL&#41;](querynotification-element-assl.md)|情報が含まれています、 [ProactiveCaching](proactivecaching-element-assl.md)データ ソースが変更されているかどうかを判断するために実行するクエリについての要素。|  
|[ReportFormatParameter 要素&#40;ASSL&#41;](reportformatparameter-element-asl.md)|名を指定するパラメーターの値を含む方法、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]実行時にレポートを書式設定します。|  
|[ReportParameter 要素&#40;ASSL&#41;](reportparameter-element-assl.md)|実行時に [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] レポートに渡されるパラメーターの名前および値を格納します。|  
|[Role 要素&#40;ASSL&#41;](role-element-assl.md)|セキュリティ ロールに関する情報を格納します。|  
|[Server 要素&#40;ASSL&#41;](server-element-assl.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスを記述します。|  
|[ServerProperty 要素&#40;ASSL&#41;](serverproperty-element-assl.md)|関連付けられているサーバーのプロパティを定義、 [Server](server-element-assl.md)要素。|  
|[SkippedLevelsColumn 要素&#40;ASSL&#41;](skippedlevelscolumn-element-assl.md)|各メンバーとその親の間でスキップされた (空の) レベルの数を格納する列の詳細を指定します。|  
|[SourceMeasureGroup 要素&#40;ASSL&#41;](sourcemeasuregroup-element-assl.md)|マイニング構造列のデータ ソースとして機能するメジャー グループを識別します。|  
|[TableNotification 要素&#40;ASSL&#41;](tablenotification-element-assl.md)|情報が含まれています、 [ProactiveCaching](proactivecaching-element-assl.md)テーブルまたはビューが変更されたデータ ソース内の要素。|  
|[Trace 要素&#40;ASSL&#41;](trace-element-assl.md)|クエリできるトレースを定義します。|  
|[Translation 要素&#40;ASSL&#41;](translation-element-assl.md)|親のローカライズされた翻訳を提供します、[翻訳](../collections/translations-element-assl.md)コレクション。|  
|[UnaryOperatorColumn 要素&#40;ASSL&#41;](unaryoperatorcolumn-element-assl.md)|単項演算子を指定する列の詳細を定義します。|  
|[UnknownMemberTranslation 要素&#40;ASSL&#41;](unknownmembertranslation-element-assl.md)|キャプションの翻訳が含まれています、 [UnknownMember](../properties/unknownmember-element-assl.md)の要素を[ディメンション](dimension-element-assl.md)要素。|  
|[ValueColumn 要素&#40;ASSL&#41;](valuecolumn-element-assl.md)|親要素の値を指定する列を識別します。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML 要素階層&#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
