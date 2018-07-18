---
title: プロパティ (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- properties [Analysis Services Scripting Language]
- Analysis Services Scripting Language, properties
- ASSL, properties
ms.assetid: 9a38cdc9-a210-421a-90e9-6391876765fa
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8a000f4f4c9a73698f04a0bd88882db55b8661e1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37173503"
---
# <a name="properties-assl"></a>プロパティ (ASSL)
  このリファレンス セクションでは、Analysis Services スクリプト言語 (ASSL) スキーマでオブジェクト プロパティの役割を果たす各要素の構文と使い方について説明します。  
  
 ASSL スキーマには XML 要素のみが含まれますが、開発者にとって、このセクションで説明する要素はオブジェクトを記述するプロパティに対応しています。  
  
 プロパティは ASSL スキーマのリーフレベル要素で、子要素や独自のプロパティに対応する要素は持っていません。  
  
 プロパティのように見えるスキーマ内のリーフレベル要素は、要素の型がオブジェクト型であるため、オブジェクトとして分類される場合があります。 たとえば、`Source` オブジェクトの `Dimension` は、`DimensionBinding` 型です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|要素|説明|  
|-------------|-----------------|  
|[要素にアクセス&#40;ASSL&#41;](access-element-assl.md)|与えられるアクセス レベルを示します、 [CellPermission](../objects/cellpermission-element-assl.md)要素。|  
|[要素をアカウント&#40;ImpersonationInfo&#41; &#40;ASSL&#41;](account-element-impersonationinfo-assl.md)|ユーザー アカウントの名前を含む、 [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)データ型。|  
|[AccountType 要素&#40;ASSL&#41;](accounttype-element-assl.md)|定義されている勘定科目の種類の名前を含む、[データベース](../objects/database-element-assl.md)要素。|  
|[ActionID 要素&#40;ASSL&#41;](id-element-assl.md)|名前を含む、[アクション](../objects/action-element-assl.md)要素で定義されている、[キューブ](../objects/cube-element-assl.md)で利用可能になっている要素を[パースペクティブ](../objects/perspective-element-assl.md)要素として、 [PerspectiveAction](../data-type/action-data-type-assl.md)要素。|  
|[Administer 要素&#40;ASSL&#41;](administer-element-assl.md)|関連付けられた権限に `Database` 要素を管理する権限が含まれているかどうかを示します。|  
|[AggregateFunction 要素&#40;ASSL&#41;](aggregatefunction-element-assl.md)|によって使用される集計関数の種類を定義、[メジャー](../objects/measure-element-assl.md)要素。|  
|[AggregationDesignID 要素&#40;ASSL&#41;](aggregationdesignid-element-assl.md)|識別、 [AggregationDesign](../objects/aggregationdesign-element-assl.md)要素に関連付けられている、[パーティション](../objects/partition-element-assl.md)要素。|  
|[AggregationFunction 要素&#40;ASSL&#41;](aggregationfunction-element-assl.md)|勘定科目の種類に使用する集計関数を格納します。|  
|[AggregationID 要素&#40;ASSL&#41;](aggregationid-element-assl.md)|集計インスタンスの作成に使用される `AggregationDesign` 要素から集計定義を識別します。|  
|[AggregationInstanceSource 要素&#40;ASSL&#41;](aggregationinstancesource-element-assl.md)|`Partition` 要素にバインドされているユーザー定義集計インスタンスのデータ ソースを識別します。|  
|[AggregationPrefix 要素&#40;ASSL&#41;](aggregationprefix-element-assl.md)|関連する親要素全体にわたって集計名に使用する共通のプレフィックスを定義します。|  
|[AggregationStorage 要素&#40;ASSL&#41;](aggregationstorage-element-assl.md)|集計の保存方法を識別します。|  
|[AggregationType 要素&#40;ASSL&#41;](aggregationtype-element-assl.md)|`Partition` 要素によって格納される集計の種類を定義します。|  
|[AggregationUsage 要素&#40;ASSL&#41;](aggregationusage-element-assl.md)|コントロール方法で集計デザイナー [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]集計をデザインします。|  
|[Algorithm 要素&#40;ASSL&#41;](algorithm-element-assl.md)|使用されるアルゴリズムを定義、 [MiningModel](../objects/miningmodel-element-assl.md)要素。|  
|[Alias 要素&#40;ASSL&#41;](alias-element-assl.md)|別名を定義、[アカウント](../objects/account-element-assl.md)要素。|  
|[AllMemberAggregationUsage 要素&#40;ASSL&#41;](allmemberaggregationusage-element-assl.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] の集計デザイナーによる集計のデザインを制御します。|  
|[AllMemberName 要素&#40;ASSL&#41;](name-element-assl.md)|すべてのメンバーの既定の言語でキャプションを含む、[階層](../objects/hierarchy-element-assl.md)要素。|  
|[AllowBrowsing 要素&#40;ASSL&#41;](allowbrowsing-element-assl.md)|定義するかどうかのメンバー、[ロール](../objects/role-element-assl.md)要素参照権限を持って、`MiningModel`要素。|  
|[AllowDrillThrough 要素&#40;ASSL&#41;](allowdrillthrough-element-assl.md)|親要素に対してドリルスルーが許可されているかどうかを指定します。|  
|[AllowDuplicateNames 要素&#40;ASSL&#41;](allowduplicatenames-element-assl.md)|`Hierarchy` 要素内で重複した名前を使用できるかどうかを指定します。|  
|[AllowedSet 要素&#40;ASSL&#41;](allowedset-element-assl.md)|`Role` 要素の許可された権限セットを属性に対して定義するセット式を格納します。|  
|[Application 要素&#40;ASSL&#41;](application-element-assl.md)|`Action` 要素に関連付けられたアプリケーションを識別します。|  
|[AssociatedMeasureGroupID 要素&#40;ASSL&#41;](measuregroupid-element-assl.md)|識別子 (ID) を含む、 [MeasureGroup](../objects/group-element-assl.md)要素に関連付けられている、 [CalculationProperty](../objects/calculationproperty-element-assl.md)要素または[Kpi](../objects/kpi-element-assl.md)要素。|  
|[AttributeAllMemberName 要素&#40;ASSL&#41;](attributeallmembername-element-assl.md)|ディメンションの All メンバーのキャプションを既定の言語で格納します。|  
|[AttributeHierarchyDisplayFolder 要素&#40;ASSL&#41;](displayfolder-element-assl.md)|関連付けられている属性階層を表示するときに使用するフォルダーを識別します。|  
|[AttributeHierarchyEnabled 要素&#40;ASSL&#41;](enabled-element-assl.md)|属性階層がその属性で有効かどうかを指定します。|  
|[AttributeHierarchyOptimizedState 要素&#40;ASSL&#41;](state-element-assl.md)|属性階層に適用される最適化のレベルを指定します。|  
|[AttributeHierarchyOrdered 要素&#40;ASSL&#41;](attributehierarchyordered-element-assl.md)|関連付けられた属性階層に順序付けを行うかどうかを指定します。|  
|[AttributeHierarchyVisible 要素&#40;ASSL&#41;](visible-element-assl.md)|属性階層をクライアント アプリケーションに対して公開するかどうかを指定します。|  
|[AttributeID 要素&#40;ASSL&#41;](attributeid-element-assl.md)|親要素に関連付けられている属性の ID を格納します。|  
|[要素の監査&#40;ASSL&#41;](audit-element-assl.md)|指定します、[トレース](../objects/trace-element-assl.md)要素は、サーバーのパフォーマンス低下を招く場合でも、すべてのイベントを削除できません。|  
|[AutoRestart 要素&#40;ASSL&#41;](autorestart-element-assl.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サービスが停止して再開された場合に `Trace` 要素を自動的に再開する必要があるかどうかを指定します。|  
|[BackColor 要素&#40;ASSL&#41;](backcolor-element-assl.md)|親要素の色関連の表示特性を記述します。|  
|[CacheMode 要素&#40;ASSL&#41;](cachemode-element-assl.md)|マイニング構造の処理中に取得したトレーニング データに使用するキャッシュ メカニズムを指定します。|  
|[CalculationReference 要素&#40;ASSL&#41;](calculationreference-element-assl.md)|`CalculationProperty` 要素によって参照される、名前付きセットまたは計算されるセルの名前を格納します。|  
|[CalculationType 要素&#40;ASSL&#41;](calculationtype-element-assl.md)|関連付けられている `CalculationProperty` 要素に定義されている計算の種類を記述します。|  
|[CalendarEndDate 要素&#40;ASSL&#41;](calendarenddate-element-assl.md)|カレンダー期間の終了日を定義、 [TimeBinding](../data-type/binding-data-type-assl.md)要素。|  
|[CalendarLanguage 要素&#40;ASSL&#41;](language-element-assl.md)|`TimeBinding` 要素で使用するカレンダーの言語を定義します。|  
|[CalendarStartDate 要素&#40;ASSL&#41;](calendarstartdate-element-assl.md)|`TimeBinding` 要素のカレンダー期間の開始日を定義します。|  
|[要素のキャプション&#40;ASSL&#41;](caption-element-assl.md)|関連する親要素のキャプションを格納します。|  
|[CaptionIsMdx 要素&#40;ASSL&#41;](captionismdx-element-assl.md)|`Action` 要素のキャプションが多次元式 (MDX) であるかどうかを定義します。|  
|[Cardinality 要素&#40;ASSL&#41;](cardinality-element-assl.md)|記述されるリレーションシップのカーディナリティを示します、 [AttributeRelationship](../objects/attributerelationship-element-assl.md)または[RegularMeasureGroupDimension](../data-type/dimension-data-type-assl.md)します。|  
|[CaseCubeDimensionID 要素&#40;ASSL&#41;](dimensionid-element-assl.md)|データ マイニング ディメンションをメジャー グループに関連付けるキューブ ディメンションの ID を格納します。|  
|[ClassifiedColumnID 要素&#40;ASSL&#41;](classifiedcolumnid-element-assl.md)|によって分類される関連列の ID を含む、 [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)要素。|  
|[Collation 要素&#40;ASSL&#41;](collation-element-assl.md)|親要素によって使用される照合順序を指定します。|  
|[ColumnID 要素&#40;ColumnBinding&#41; &#40;ASSL&#41;](columnid-element-columnbinding-assl.md)|データ アイテムがバインドされるテーブル内の列の ID を格納します。|  
|[ColumnID 要素&#40;EventColumn&#41; &#40;ASSL&#41;](columnid-element-eventcolumn-assl.md)|`Trace` 要素の一部としてイベントに対してキャプチャされる情報列の ID を格納します。|  
|[要素の条件&#40;ASSL&#41;](condition-element-assl.md)|`Action` 親要素が対象に適用されるかどうかを指定する MDX 式を格納します。|  
|[ConnectionString 要素&#40;ASSL&#41;](connectionstring-element-assl.md)|暗号化された接続文字列を含む、 [DataSource](../objects/datasource-element-assl.md)要素。|  
|[ConnectionStringSecurity 要素&#40;ASSL&#41;](connectionstringsecurity-element-assl.md)|セキュリティ上の目的で、ユーザーのパスワードをデータ ソースの接続文字列から取り除くかどうかを指定します。|  
|[要素のコンテンツ&#40;ASSL&#41;](content-element-assl.md)|内の列のコンテンツについて説明します、 [MiningStructure](../objects/miningstructure-element-assl.md)要素。|  
|[Source 要素&#40;ComAssembly&#41; &#40;ASSL&#41;](createdtimestamp-element-assl.md)|親要素の読み取り専用の作成タイムスタンプを格納します。|  
|[Source 要素&#40;メジャー&#41; &#40;ASSL&#41;](cubedimensionid-element-assl.md)|識別、 [CubeDimension](../data-type/cubedimension-data-type-assl.md)親要素に関連付けられた要素。|  
|[SourceAttributeID 要素&#40;ASSL&#41;](cubeid-element-assl.md)|基になる属性の ID を含む、`Cube`レベル[要素に基づきます。|  
|[SourceColumnID 要素&#40;ASSL&#41;](storagemode-element-assl.md)|親要素の現在のストレージ モードを指定します。|  
|[要素の状態&#40;ASSL&#41;](../objects/member-element-assl.md)|`Kpi` 要素に関連付けられている時間ディメンションの現在のメンバーを定義します。|  
|[StatusGraphic 要素&#40;ASSL&#41;](../objects/aggregation-element-assl.md)|そのインスタンスで、`MeasureGroup` の持続データを集計するか、またはキャッシュされているデータを集計するかを指定します。|  
|[StopTime 要素&#40;ASSL&#41;](databaseid-element-assl.md)|不一致 `Database` 要素に関連付けられている `Binding` 要素を識別します。|  
|[StorageLocation 要素&#40;ASSL&#41;](datasize-element-assl.md)|バイト単位のサイズが含まれています、 [DataItem](../data-type/dataitem-data-type-assl.md)要素。|  
|[StorageMode 要素&#40;ASSL&#41;](datasourceid-element-assl.md)|親要素に関連付けられている `DataSource` 要素を識別します。|  
|[DataSourceImpersonationInfo 要素&#40;ASSL&#41;](impersonationinfo-element-assl.md)|`Database` 要素のデータ ソースに接続するときの権限借用動作の指定に使用される情報を格納します。|  
|[TableID 要素&#40;ASSL&#41;](datasourceviewid-element-assl.md)|Target 要素&#40;ASSL&#41;|  
|[TargetType 要素&#40;ASSL&#41;](datatype-element-assl.md)|関連する要素のデータ型を定義します。|  
|[識別される項目の項目の種類を識別、[ターゲット](dbschemaname-element-assl.md)要素。](dbschemaname-element-assl.md)|によって識別されるテーブル内の親要素によって使用されるスキーマの名前を含む、 [DbTableName](dbtablename-element-assl.md)要素。|  
|[テキスト要素&#40;ASSL&#41;](dbtablename-element-assl.md)|親要素がバインドされているテーブルの名前を格納します。|  
|[Timeout 要素&#40;ASSL&#41;](default-element-assl.md)|`DrillThroughAction` が既定のドリルスルー アクションであるかどうかを指定します。|  
|[TrendGraphic 要素&#40;ASSL&#41;](defaultmeasure-element-assl.md)|`Cube` または `Perspective` 要素の既定のメジャーを定義する MDX 言語の式を格納します。|  
|[Trimming 要素&#40;ASSL&#41;](defaultmember-element-assl.md)|親要素の既定のメンバーを識別する MDX 式を格納します。|  
|[Type 要素&#40;アクション&#41; &#40;ASSL&#41;](defaultscript-element-assl.md)|Type 要素&#40;バインド&#41; &#40;ASSL&#41;|  
|[Type 要素&#40;ClrAssemblyFile&#41; &#40;ASSL&#41;](value-element-assl.md)|関連付けられている、読み取り専用の既定値が含まれる[ServerProperty](../objects/serverproperty-element-assl.md)要素。|  
|[.NET Framework アセンブリに属しているファイルの 1 つのファイルの種類を指定します。](deniedset-element-assl.md)|関連属性で拒否される権限の一覧を定義するセット式を格納します。|  
|[Type 要素&#40;ディメンション&#41; &#40;ASSL&#41;](dependsondimensionid-element-assl.md)|親ディメンションが依存する別のディメンションの ID を格納します。|  
|[Type 要素&#40;DimensionAttribute&#41; &#40;ASSL&#41;](description-element-assl.md)|親要素の説明を格納します。|  
|[Type 要素&#40;MeasureGroup&#41; &#40;ASSL&#41;](dimensionid-element-assl.md)|ディメンションの ID を格納します。|  
|[型を指定します、[します。](discretizationbucketcount-element-assl.md)|分離対象のバケット数を示します。|  
|[Type 要素&#40;MeasureGroupAttribute&#41; &#40;ASSL&#41;](discretizationmethod-element-assl.md)|分離に使用するメソッドを定義します。|  
|[型を含む、 [MeasureGroupAttribute](displayflag-element-assl.md)要素。](displayflag-element-assl.md)|関連付けられている `ServerProperty` 要素をユーザー インターフェイス コンポーネントで表示する必要があるかどうかを示す読み取り専用のヒントを格納します。|  
|[Type 要素&#40;MiningStructureColumn&#41; &#40;ASSL&#41;](displayfolder-element-assl.md)|親要素を一覧表示するフォルダーを指定します。 開発者および管理者向けの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] アプリケーションでは、表示フォルダーを使用して複数の要素を視覚的に分類できる場合があります。|  
|[型を含む、 [MiningStructureColumn](distribution-element-assl.md)要素。](distribution-element-assl.md)|`MiningStructure` 要素の列内でスカラー値を分散する方法を記述したプロバイダー固有の値を格納します。|  
|[Edition 要素&#40;ASSL&#41;](edition-element-assl.md)|Type 要素&#40;パーティション&#41; &#40;ASSL&#41;|  
|[Type 要素&#40;PerspectiveCalculation&#41; &#40;ASSL&#41;](enabled-element-assl.md)|親要素が有効になっているかどうかを示します。|  
|[UnknownMember 要素&#40;ASSL&#41;](../objects/data-element-assl.md)|Usage 要素&#40;DimensionAttribute&#41; &#40;ASSL&#41;|  
|[Usage 要素&#40;MiningModelColumn&#41; &#40;ASSL&#41;](estimatedcount-element-assl.md)|属性のメンバーの推定数を格納します。|  
|[Version 要素&#40;ASSL&#41;](estimatedperformancegain-element-assl.md)|パーティションの読み取り専用の推定パフォーマンス向上率を格納します。|  
|[Visibility 要素&#40;ASSL&#41;](estimatedrows-element-assl.md)|親要素によって表される行の推定数を格納します。|  
|[Visible 要素&#40;ASSL&#41;](estimatedsize-element-assl.md)|親要素の読み取り専用の推定サイズ (バイト単位) を格納します。|  
|[VisualTotals 要素&#40;ASSL&#41;](eventid-element-assl.md)|要素を書き込む&#40;ASSL&#41;|  
|[WriteEnabled 要素&#40;ASSL&#41;](expression-element-assl.md)|親要素のコンテンツを定義する MDX 式を格納します。|  
|[Filter 要素&#40;バインド&#41; &#40;ASSL&#41;](filter-element-binding-assl.md)|親要素のコンテンツをフィルター処理する MDX 式を格納します。|  
|[Filter 要素&#40;トレース&#41; &#40;ASSL&#41;](filter-element-trace-assl.md)|`Trace` フィルターを記述する XML ドキュメント フラグメントを格納します。|  
|[FirstDayOfWeek 要素&#40;ASSL&#41;](firstdayofweek-element-assl.md)|`TimeBinding` 要素に対して週の最初の曜日を定義します。|  
|[FiscalFirstDayOfMonth 要素&#40;ASSL&#41;](fiscalfirstdayofmonth-element-assl.md)|`TimeBinding` 要素に対して会計月の最初の日を定義します。|  
|[FiscalFirstMonth 要素&#40;ASSL&#41;](fiscalfirstmonth-element-assl.md)|`TimeBinding` 要素に対して会計期間の最初の月を定義します。|  
|[FiscalYearName 要素&#40;ASSL&#41;](fiscalyearname-element-assl.md)|会計年度の名前の命名規則を定義、`TimeBinding`要素。|  
|[FontFlags 要素&#40;ASSL&#41;](fontflags-element-assl.md)|`CalculationProperty` または `Measure` 親要素のフォント関連の表示特性を記述します。|  
|[FontName 要素&#40;ASSL&#41;](fontname-element-assl.md)|`CalculationProperty` または `Measure` 親要素のフォント関連の表示特性を記述します。|  
|[FontSize 要素&#40;ASSL&#41;](fontsize-element-assl.md)|`CalculationProperty` または `Measure` 親要素のフォント関連の表示特性を記述します。|  
|[ForceRebuildInterval 要素&#40;ASSL&#41;](forcerebuildinterval-element-assl.md)|新しい多次元 OLAP (MOLAP) 画像が使用できるようになり、MOLAP 画像処理が無条件で開始されるまでの時間を指定します。|  
|[ForeColor 要素&#40;ASSL&#41;](forecolor-element-assl.md)|`CalculationProperty` または `Measure` 親要素の色関連の表示特性を記述します。|  
|[要素を書式設定&#40;ASSL&#41;](format-element-assl.md)|`DataItem` 要素の必須の形式を格納します。|  
|[FormatString 要素&#40;ASSL&#41;](formatstring-element-assl.md)|`CalculationProperty` 要素または `Measure` 要素の表示形式を記述します。|  
|[Goal 要素&#40;ASSL&#41;](goal-element-assl.md)|`Kpi` 要素の目標を指定します。|  
|[GranularityAttributeID 要素&#40;ASSL&#41;](granularityattributeid-element-assl.md)|親に関連付けられている属性の ID を含む[MeasureGroupAttributeBinding](../data-type/measuregroupattributebinding-data-type-out-of-line-assl.md)データ型。|  
|[HideMemberIf 要素&#40;ASSL&#41;](hidememberif-element-assl.md)|レベル内のメンバーをクライアント アプリケーションに対して非表示にするかどうかと、そのタイミングを示します。|  
|[HierarchyID 要素&#40;ASSL&#41;](hierarchyid-element-assl.md)|ID を含む、 [CubeHierarchy](../data-type/hierarchy-data-type-assl.md)、 [MeasureGroupHierarchy](../data-type/measuregrouphierarchy-data-type-assl.md)、または[PerspectiveHierarchy](../data-type/perspectivehierarchy-data-type-assl.md)要素。|  
|[HierarchyUniqueNameStyle 要素&#40;ASSL&#41;](hierarchyuniquenamestyle-element-assl.md)|`CubeDimension` に含まれている階層に対して一意の名前を生成する方法を指定します。|  
|[ID 要素&#40;ASSL&#41;](id-element-assl.md)|親要素の一意の ID を格納します。|  
|[IgnoreUnrelatedDimensions 要素&#40;ASSL&#41;](../collections/dimensions-element-assl.md)|メジャー グループに関連付けられていないディメンションのメンバーがクエリに含まれているときに、関連付けられていないディメンションをトップ レベルに強制するかどうかを指定します。|  
|[ImpersonationInfo 要素&#40;ASSL&#41;](impersonationinfo-element-assl.md)|アセンブリにアクセスする場合、またはアセンブリを実行する場合の権限借用の動作を決定するために使用する情報を格納します。|  
|[ImpersonationInfoSecurity 要素&#40;ASSL&#41;](impersonationinfosecurity-element-assl.md)|`ImpersonationInfo` データ型で指定されるセキュリティ資格情報が変更されたかどうかを示す読み取り専用の値を格納します。|  
|[ImpersonationMode 要素&#40;ASSL&#41;](impersonationmode-element-assl.md)|`ImpersonationInfo` データ型から派生した要素の権限借用の方法を示す値を格納します。|  
|[InstanceSelection 要素&#40;ASSL&#41;](instanceselection-element-assl.md)|クライアント アプリケーションにヒントを提供し、一覧の予期されたアイテム数に基づいて、アイテムの一覧の表示方法を提案します。|  
|[IntermediateCubeDimensionID 要素&#40;ASSL&#41;](intermediatecubedimensionid-element-assl.md)|参照ディメンションをメジャー グループに関連付けるディメンションの ID を格納します。|  
|[IntermediateGranularityAttributeID 要素&#40;ASSL&#41;](intermediategranularityattributeid-element-assl.md)|参照ディメンションを中間ディメンションに関連付けるために使用される中間キューブ ディメンションにおける粒度属性の ID を格納します。|  
|[InvalidXmlCharacters 要素&#40;ASSL&#41;](invalidxmlcharacters-element-assl.md)|ソース データの有効でない XML 文字の処理方法を指定します。|  
|[Invocation 要素&#40;ASSL&#41;](invocation-element-assl.md)|`Action` を呼び出す方法を指定します。|  
|[IsAggregatable 要素&#40;ASSL&#41;](isaggregatable-element-assl.md)|指定するかどうかの値、 [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)要素を集計することができます。|  
|[IsKey 要素&#40;ASSL&#41;](iskey-element-assl.md)|列が `MiningStructure` 要素のケースにキーを提供するかどうかを示します。|  
|[Isolation 要素&#40;ASSL&#41;](isolation-element-assl.md)|派生した要素の分離レベルを示します、 [DataSource](../data-type/datasource-data-type-assl.md)データ型。|  
|[KeyDuplicate 要素&#40;ASSL&#41;](keyduplicate-element-assl.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] による、処理時に発生した重複キー エラーの処理方法を指定します。|  
|[KeyErrorAction 要素&#40;ASSL&#41;](keyerroraction-element-assl.md)|キーでエラーが発生した場合に [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が実行するアクションを指定します。|  
|[KeyErrorLimit 要素&#40;ASSL&#41;](keyerrorlimit-element-assl.md)|処理時に許容可能なエラーの数を格納します。|  
|[KeyErrorLimitAction 要素&#40;ASSL&#41;](keyerrorlimitaction-element-assl.md)|アクションを指定する[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ときいるキー エラー数がで指定された、 [KeyErrorLimit](keyerrorlimit-element-assl.md)要素に到達します。|  
|[KeyErrorLogFile 要素&#40;ASSL&#41;](../objects/file-element-assl.md)|処理エラーをログに記録するためのファイル名を格納します。|  
|[KeyNotFound 要素&#40;ASSL&#41;](keynotfound-element-assl.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] で参照整合性エラーが発生したときの応答方法を指定します。|  
|[KeyUniquenessGuarantee 要素&#40;ASSL&#41;](keyuniquenessguarantee-element-assl.md)|属性のキーと名前の間のリレーションシップ、および関連属性へのリレーションシップが有効であることが保証されるかどうかを示します。|  
|[KpiID 要素&#40;ASSL&#41;](kpiid-element-assl.md)|`Kpi` 要素を `Perspective` 要素と関連付ける ID を格納します。|  
|[言語要素&#40;ASSL&#41;](language-element-assl.md)|親要素の言語識別子を格納します。|  
|[LastProcessed 要素&#40;ASSL&#41;](lastprocessed-element-assl.md)|親要素が含まれているデータベースが最後に処理された時刻を示す読み取り専用のタイムスタンプを格納します。|  
|[LastSchemaUpdate 要素&#40;ASSL&#41;](lastschemaupdate-element-assl.md)|親要素の読み取り専用のメタデータ更新タイムスタンプを格納します。|  
|[LastUpdate 要素&#40;ASSL&#41;](lastupdate-element-assl.md)|データベースが格納する、関連付けられた `Database` オブジェクトまたはその他の主要なオブジェクトが最後に変更された日時を示す読み取り専用のタイムスタンプを格納します。|  
|[Latency 要素&#40;ASSL&#41;](latency-element-assl.md)|最も古い通知と MOLAP イメージが破棄された時点との間の "猶予期間" を定義します。|  
|[LogFileAppend 要素&#40;ASSL&#41;](logfileappend-element-assl.md)|`Trace` 要素のログ出力を既存のログ ファイルに追加するか上書きするかを指定します。|  
|[LogFileName 要素&#40;ASSL&#41;](logfilename-element-assl.md)|`Trace` 要素のログ ファイルのファイル名を格納します。|  
|[LogFileRollover 要素&#40;ASSL&#41;](logfilerollover-element-assl.md)|指定のログ記録するかどうか`Trace`出力は、新しいファイルにロール オーバーする必要がありますまたはで指定されている最大ログ ファイル サイズときに停止してください[LogFileSize](logfilesize-element-assl.md)に到達します。|  
|[LogFileSize 要素&#40;ASSL&#41;](logfilesize-element-assl.md)|ログ ファイルの最大サイズを MB 単位で指定します。|  
|[ManagedProvider 要素&#40;ASSL&#41;](managedprovider-element-assl.md)|ph x="1" /&gt; データ型から派生した要素によって使用されているマネージド プロバイダーの名前を格納します。|  
|[ManufacturingExtraMonthQuarter 要素&#40;ASSL&#41;](manufacturingextramonthquarter-element-assl.md)|`TimeBinding` 要素について追加の月を割り当てる製造期間の月を定義します。|  
|[ManufacturingFirstMonth 要素&#40;ASSL&#41;](manufacturingfirstmonth-element-assl.md)|`TimeBinding` 要素の最初の製造月を定義します。|  
|[ManufacturingFirstWeekOfMonth 要素&#40;ASSL&#41;](manufacturingfirstweekofmonth-element-assl.md)|`TimeBinding` 要素に対して製造月の最初の週を定義します。|  
|[MasterDatasourceID 要素&#40;ASSL&#41;](masterdatasourceid-element-assl.md)|`Database` 要素のマスター データ ソース ID を格納します。|  
|[Materialization 要素&#40;ASSL&#41;](materialization-element-assl.md)|メジャー グループと参照ディメンションの間のリレーションシップの種類を示します。|  
|[MaxActiveConnections 要素&#40;ASSL&#41;](maxactiveconnections-element-assl.md)|`DataSource` データ型から派生した要素によって許可されている同時接続の最大数を格納します。|  
|[MdxMissingMemberMode 要素&#40;ASSL&#41;](mdxmissingmembermode-element-assl.md)|欠落しているメンバーを MDX ステートメントでどのように処理するかを指定します。|  
|[MeasureExpression 要素&#40;ASSL&#41;](measureexpression-element-assl.md)|メジャーを定義する MDX 式を格納します。|  
|[MeasureGroupID 要素&#40;ASSL&#41;](measuregroupid-element-assl.md)|親要素、バインド、または不一致バインドに `MeasureGroup` を関連付けます。|  
|[MeasureID 要素&#40;ASSL&#41;](measureid-element-assl.md)|`Measure` 要素を親要素に関連付けます。|  
|[MeasureQualificaton 要素&#40;ASSL&#41;](measurequalificaton-element-assl.md)|プレフィックスが `MeasureGroup` のメジャーに適用されるかどうかを指定します。|  
|[MemberNamesUnique 要素&#40;ASSL&#41;](membernamesunique-element-assl.md)|親要素に属するメンバー名を一意にする必要があるかどうかを指定します。|  
|[MemberUniqueNameStyle 要素&#40;ASSL&#41;](memberuniquenamestyle-element-assl.md)|`CubeDimension` 要素に含まれている階層のメンバーに使用する一意の名前の生成方法を指定します。|  
|[MembersWithData 要素&#40;ASSL&#41;](memberswithdata-element-assl.md)|親属性内の非リーフ メンバーのデータ メンバーを表示するかどうかを指定します。|  
|[MembersWithDataCaption 要素&#40;ASSL&#41;](memberswithdatacaption-element-assl.md)|システムによって生成されるデータ メンバーのキャプションを作成するためのテンプレート文字列を提供します。|  
|[MimeType 要素&#40;ASSL&#41;](mimetype-element-assl.md)|該当する場合、親である `DataItem` 要素で表されるデータの Multipurpose Internet Mail Extensions (MIME) の種類を格納します。|  
|[MiningModelID 要素&#40;ASSL&#41;](miningmodelid-element-assl.md)|マイニング モデルをデータ マイニング ディメンションに関連付けます。|  
|[要素名を指定&#40;ASSL&#41;](name-element-assl.md)|親要素の名前が格納されます。|  
|[NamingTemplate 要素&#40;ASSL&#41;](namingtemplate-element-assl.md)|`DimensionAttribute` 親要素から構築された親子階層内におけるレベルの名前付け方法を定義します。|  
|[NonEmptyBehavior 要素&#40;ASSL&#41;](nonemptybehavior-element-assl.md)|`CalculationProperty` 要素の親に関連付けられる空でない動作を指定します。|  
|[NotificationTechnique 要素&#40;ASSL&#41;](notificationtechnique-element-assl.md)|指定するかどうか[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]または外部クライアント アプリケーションは、通知を処理します。|  
|[NullKeyConvertedToUnknown 要素&#40;ASSL&#41;](nullkeyconvertedtounknown-element-assl.md)|NULL 変換エラーが発生した場合の動作を指定します。|  
|[NullKeyNotAllowed 要素&#40;ASSL&#41;](nullkeynotallowed-element-assl.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 処理エンジンが処理中に発生した NULL キー エラーをどのように処理するかを指定します。|  
|[NullProcessing 要素&#40;ASSL&#41;](nullprocessing-element-assl.md)|NULL 値の処理方法を定義します。|  
|[OnlineMode 要素&#40;ASSL&#41;](onlinemode-element-assl.md)|キャッシュの再構築の開始時に直ちにデータベースをオンラインに戻すか、キャッシュの再構築の完了時にのみデータベースをオンラインに戻すかを指定します。|  
|[OptimizedState 要素&#40;ASSL&#41;](state-element-assl.md)|階層に適用される最適化のレベルを決定します。|  
|[Optionality 要素&#40;ASSL&#41;](optionality-element-assl.md)|`AttributeRelationship` 要素のメンバーがオプションかどうかを示します。|  
|[OrderBy 要素&#40;ASSL&#41;](orderby-element-assl.md)|属性に含まれているメンバーの順序付け方法を記述します。|  
|[OrderByAttributeID 要素&#40;ASSL&#41;](orderbyattributeid-element-assl.md)|メンバーの順序付けに使用する別の属性を識別、[ディメンション](../data-type/dimensionattribute-data-type-assl.md)属性。|  
|[Ordinal 要素&#40;ASSL&#41;](ordinal-element-assl.md)|キーおよび翻訳などコレクション内でバインドする序数を示します。|  
|[OverrideBehavior 要素&#40;ASSL&#41;](overridebehavior-element-assl.md)|`AttributeRelationship` 要素で記述されるリレーションシップのオーバーライド動作を示します。|  
|[PartitionID 要素&#40;ASSL&#41;](partitionid-element-assl.md)|親属性、バインド、または不一致バインドに `Partition` 要素を関連付けます。|  
|[パスワード要素&#40;ASSL&#41;](password-element-assl.md)|`ImpersonationInfo` 要素のユーザー アカウントのパスワードを格納します。|  
|[Path 要素&#40;ASSL&#41;](path-element-assl.md)|インスタンスによって提供されるように、パスを含む[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]で使用されるレポートの[ReportAction](../data-type/reportaction-data-type-assl.md)要素。|  
|[PendingValue 要素&#40;ASSL&#41;](pendingvalue-element-assl.md)|関連する `ServerProperty` 要素の読み取り専用の保留値を格納します。|  
|[PermissionSet 要素&#40;ASSL&#41;](permissionset-element-assl.md)|関連付けられているアクセス許可セットを識別、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework アセンブリ。|  
|[Persistence 要素&#40;ASSL&#41;](persistence-element-assl.md)|バインドされているソース データのどの部分は動的でありで指定された頻度で更新のチェックを決定、 [RefreshPolicy](refreshpolicy-element-assl.md)要素。|  
|[要素を処理&#40;ASSL&#41;](process-element-assl.md)|ユーザーが親要素の所有者を処理できるかどうかを決定します。|  
|[ProcessingMode 要素&#40;ASSL&#41;](processingmode-element-assl.md)|処理時または処理後にインスタンスによってインデックス付けまたは集計が行われるかどうかを指定します。|  
|[ProcessingPriority 要素&#40;ASSL&#41;](processingpriority-element-assl.md)|レイジー集計、インデックス作成、クラスター化など、バックグラウンド操作中の親オブジェクトの処理の優先順序を決定します。|  
|[ProcessingQuery 要素&#40;ASSL&#41;](query-element-assl.md)|増分処理ステータスの通知のために実行するクエリのパラメーター化されたテキストを格納します。|  
|[ProductName 要素&#40;ASSL&#41;](productname-element-assl.md)|`Server` 要素に関連付けられている [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスの読み取り専用の製品名を格納します。|  
|[要素を照会&#40;ASSL&#41;](query-element-assl.md)|通知の目的で実行するクエリのテキストを格納します。|  
|[QueryDefinition 要素&#40;ASSL&#41;](querydefinition-element-assl.md)|関連付けられているクエリの不透過の式が含まれています、`DataSource`内の要素を[QueryBinding](../data-type/querybinding-data-type-assl.md)要素。|  
|[要素を読み取る&#40;ASSL&#41;](read-element-assl.md)|データまたはメタデータの読み取りができるかどうかを決定を指定した[CubeDimensionPermission](../data-type/permission-data-type-assl.md)または[権限](../data-type/permission-data-type-assl.md)要素。|  
|[ReadDefinition 要素&#40;ASSL&#41;](readdefinition-element-assl.md)|メンバーがデータベースの定義やデータベース内のオブジェクトの定義を読み取ることができるかどうかを指定します。|  
|[ReadSourceData 要素&#40;ASSL&#41;](readsourcedata-element-assl.md)|`CubePermission` に含まれている階層に対して一意の名前を生成する方法を指定します。|  
|[RefreshInterval 要素&#40;ASSL&#41;](refreshinterval-element-assl.md)|親要素に関連付けられたバインド データの更新間隔を指定します。|  
|[RefreshPolicy 要素&#40;ASSL&#41;](refreshpolicy-element-assl.md)|どのくらいの頻度を決定します。 ディメンションまたはメジャー グループの動的な部分 (で指定されたとおり、[永続化](persistence-element-assl.md)要素) が変更されています。|  
|[RelationshipType 要素&#40;ASSL&#41;](relationshiptype-element-assl.md)|`AttributeRelationship` のメンバー リレーションシップを変更できるかどうかを示します。|  
|[RemoteDatasourceID 要素&#40;ASSL&#41;](remotedatasourceid-element-assl.md)|リモート パーティションを格納する [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスを指す OLAP データ ソースの ID を指定します。|  
|[ReportingFirstMonth 要素&#40;ASSL&#41;](reportingfirstmonth-element-assl.md)|`TimeBinding` 要素の最初のレポート月を定義します。|  
|[ReportingFirstWeekOfMonth 要素&#40;ASSL&#41;](reportingfirstweekofmonth-element-assl.md)|`TimeBinding` 要素のレポート月の最初の週を定義します。|  
|[ReportingWeekToMonthPattern 要素&#40;ASSL&#41;](reportingweektomonthpattern-element-assl.md)|`TimeBinding` 要素の週から月のレポート パターンを定義します。|  
|[ReportServer 要素&#40;ASSL&#41;](reportserver-element-assl.md)|`ReportAction` で使用される [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] インスタンスの名前を格納します。|  
|[RequiresRestart 要素&#40;ASSL&#41;](requiresrestart-element-assl.md)|サーバー プロパティの値を変更する場合、変更内容を有効にするにはインスタンスを再起動する必要があるかどうかを指定する `ServerProperty` 要素に関連付けられた読み取り専用の値を格納します。|  
|[RoleID 要素&#40;ASSL&#41;](roleid-element-assl.md)|権限が定義されているロールを識別します。|  
|[ルート要素&#40;ASSL&#41;](root-element-assl.md)|データ ソースのデータ (行セット) を格納します。|  
|[RootMemberIf 要素&#40;ASSL&#41;](rootmemberif-element-assl.md)|親属性のルート メンバーまたはメンバーを識別する方法を指定します。|  
|[スキーマ要素&#40;ASSL&#41;](schema-element-assl.md)|データ ソース ビューのスキーマを格納します。|  
|[ScriptCacheProcessingMode 要素&#40;ASSL&#41;](scriptcacheprocessingmode-element-assl.md)|サーバーがスクリプト キャッシュを処理中または処理後のどちらに構築するかを指定します。|  
|[SilenceInterval 要素&#40;ASSL&#41;](silenceinterval-element-assl.md)|MOLAP イメージ作成プロセスを開始する前に [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスが一時停止する最短時間を定義します。|  
|[SilenceOverrideInterval 要素&#40;ASSL&#41;](silenceoverrideinterval-element-assl.md)|初期通知を受信した後、MOLAP イメージ作成が無条件で開始されるまでに経過する必要のある時間を定義します。|  
|[要素をスライス&#40;ASSL&#41;](slice-element-assl.md)|パーティションに含まれているスライスを定義する MDX 式を格納します。|  
|[SolveOrder 要素&#40;ASSL&#41;](solveorder-element-assl.md)|計算されるメンバーまたは計算されるセル定義に `CalculationProperty` 要素を適用する解決順序を示します。|  
|[Source 要素&#40;バインド&#41; &#40;ASSL&#41;](source-element-binding-assl.md)|親要素がバインドされているデータのソースを識別します。|  
|[Source 要素&#40;ComAssembly&#41; &#40;ASSL&#41;](source-element-comassembly-assl.md)|Component Object Model (COM) コンポーネント用のファイル名またはプログラム識別子 (ProgID) を格納します。|  
|[Source 要素&#40;メジャー&#41; &#40;ASSL&#41;](source-element-measure-assl.md)|`Measure` 要素の値を含んでいるソースの詳細を格納します。|  
|[SourceAttributeID 要素&#40;ASSL&#41;](sourceattributeid-element-assl.md)|基になる属性の ID を含む、[レベル](../objects/level-element-assl.md)要素に基づきます。|  
|[SourceColumnID 要素&#40;ASSL&#41;](sourcecolumnid-element-assl.md)|先祖である `MiningStructure` 要素のソース マイニング構造列の ID を格納します。|  
|[要素の状態&#40;ASSL&#41;](state-element-assl.md)|親要素の現在の処理状態を記述する読み取り専用の値を格納します。|  
|[Status 要素&#40;ASSL&#41;](status-element-assl.md)|`Kpi` 要素の状態インジケーターを返す MDX 式を格納します。|  
|[StatusGraphic 要素&#40;ASSL&#41;](statusgraphic-element-assl.md)|`Kpi` 要素のステータスを表す推奨グラフィカル表示を格納します。|  
|[StopTime 要素&#40;ASSL&#41;](stoptime-element-assl.md)|`Trace` 要素の停止日時を指定します。|  
|[StorageLocation 要素&#40;ASSL&#41;](storagelocation-element-assl.md)|親要素のコンテンツを収めるファイル システム ストレージの場所を格納します。|  
|[StorageMode 要素&#40;ASSL&#41;](storagemode-element-assl.md)|親要素のストレージ モードを指定します。|  
|[TableID 要素&#40;ASSL&#41;](tableid-element-assl.md)|親要素に関連付けられているテーブル (`DataSourceView` 要素のテーブル) の ID を格納します。|  
|[Target 要素&#40;ASSL&#41;](target-element-assl.md)|`Action` 要素の対象を識別します。|  
|[TargetType 要素&#40;ASSL&#41;](targettype-element-assl.md)|識別される項目の項目の種類を識別、[ターゲット](target-element-assl.md)要素。|  
|[テキスト要素&#40;ASSL&#41;](text-element-assl.md)|テキストを含む、[コマンド](../objects/command-element-assl.md)要素。|  
|[Timeout 要素&#40;ASSL&#41;](timeout-element-assl.md)|データの取得を試みたときにタイムアウトをレポートするまでの時間を指定します (秒単位)。|  
|[要素の傾向&#40;ASSL&#41;](trend-element-assl.md)|`Kpi` 要素の傾向インジケーターを返す MDX 式を格納します。|  
|[TrendGraphic 要素&#40;ASSL&#41;](trendgraphic-element-assl.md)|`Kpi` 要素の傾向を表す推奨グラフィカル表示を格納します。|  
|[Trimming 要素&#40;ASSL&#41;](trimming-element-assl.md)|データ ソースのデータを切り捨てる方法を指定します。|  
|[Type 要素&#40;アクション&#41; &#40;ASSL&#41;](type-element-action-assl.md)|`Action` 要素の型を格納します。|  
|[Type 要素&#40;バインド&#41; &#40;ASSL&#41;](type-element-binding-assl.md)|属性バインドの型を格納します。|  
|[Type 要素&#40;ClrAssemblyFile&#41; &#40;ASSL&#41;](type-element-clrassemblyfile-assl.md)|.NET Framework アセンブリに属しているファイルの 1 つのファイルの種類を指定します。|  
|[Type 要素&#40;ディメンション&#41; &#40;ASSL&#41;](type-element-dimension-assl.md)|ディメンションのコンテンツに関する情報を提供します。|  
|[Type 要素&#40;DimensionAttribute&#41; &#40;ASSL&#41;](type-element-dimensionattribute-assl.md)|属性の型を示します。|  
|[Type 要素&#40;MeasureGroup&#41; &#40;ASSL&#41;](type-element-measuregroup-assl.md)|型を指定します、`MeasureGroup`します。|  
|[Type 要素&#40;MeasureGroupAttribute&#41; &#40;ASSL&#41;](type-element-measuregroupattribute-assl.md)|型を含む、 [MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md)要素。|  
|[Type 要素&#40;MiningStructureColumn&#41; &#40;ASSL&#41;](type-element-miningstructurecolumn-assl.md)|型を含む、 [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)要素。|  
|[Type 要素&#40;パーティション&#41; &#40;ASSL&#41;](type-element-partition-assl.md)|`Partition` 要素の型を格納します。|  
|[Type 要素&#40;PerspectiveCalculation&#41; &#40;ASSL&#41;](type-element-perspectivecalculation-assl.md)|型を示す、 [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md)要素。|  
|[UnknownMember 要素&#40;ASSL&#41;](unknownmember-element-assl.md)|不明なメンバーが表示されるかどうかを示します。|  
|[UnknownMemberName 要素&#40;ASSL&#41;](unknownmembername-element-assl.md)|ディメンションの不明メンバーのキャプションをディメンションの既定の言語で格納します。|  
|[Usage 要素&#40;DimensionAttribute&#41; &#40;ASSL&#41;](usage-element-dimensionattribute-assl.md)|属性の使用方法を説明します。|  
|[Usage 要素&#40;MiningModelColumn&#41; &#40;ASSL&#41;](usage-element-miningmodelcolumn-assl.md)|親である `MiningStructure` における関連付けられた列の使用方法を記述します。|  
|[要素の値&#40;ASSL&#41;](value-element-assl.md)|親要素の値を格納します。|  
|[Version 要素&#40;ASSL&#41;](version-element-assl.md)|`Server` 要素によって表される [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスの読み取り専用のバージョン番号を格納します。|  
|[Visibility 要素&#40;ASSL&#41;](visibility-element-assl.md)|可視性を定義、[注釈](../objects/annotation-element-assl.md)要素。|  
|[Visible 要素&#40;ASSL&#41;](visible-element-assl.md)|親要素の表示を決定します。|  
|[VisualTotals 要素&#40;ASSL&#41;](visualtotals-element-assl.md)|この属性のメンバーに対して表示部分の合計を表示するかどうかを指定する MDX 式を格納します。|  
|[要素を書き込む&#40;ASSL&#41;](write-element-assl.md)|特定の `CubeDimensionPermission` 要素または `Permission` 要素に対して、データまたはメタデータの書き込みが可能であるかどうかを指定します。|  
|[WriteEnabled 要素&#40;ASSL&#41;](writeenabled-element-assl.md)|ディメンションの書き戻しを使用できるかどうかを示します (セキュリティ権限に依存)。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML 要素階層&#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
