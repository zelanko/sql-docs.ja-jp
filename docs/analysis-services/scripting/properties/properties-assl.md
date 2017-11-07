---
title: "プロパティ (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- properties [Analysis Services Scripting Language]
- Analysis Services Scripting Language, properties
- ASSL, properties
ms.assetid: 9a38cdc9-a210-421a-90e9-6391876765fa
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fee88a17655823ed00bbcb864dabcf1980663724
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="properties-assl"></a>プロパティ (ASSL)
  このリファレンス セクションでは、Analysis Services スクリプト言語 (ASSL) スキーマでオブジェクト プロパティの役割を果たす各要素の構文と使い方について説明します。  
  
 ASSL スキーマには XML 要素のみが含まれますが、開発者にとって、このセクションで説明する要素はオブジェクトを記述するプロパティに対応しています。  
  
 プロパティは ASSL スキーマのリーフレベル要素で、子要素や独自のプロパティに対応する要素は持っていません。  
  
 プロパティのように見えるスキーマ内のリーフレベル要素は、要素の型がオブジェクト型であるため、オブジェクトとして分類される場合があります。 たとえば、**ソース**の**ディメンション**オブジェクトの型が**DimensionBinding**です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|要素|Description|  
|-------------|-----------------|  
|[Access 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/access-element-assl.md)|与えられるアクセス レベルを示す、 [CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)要素。|  
|[Account 要素 (&) #40";"ImpersonationInfo"&"#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/account-element-impersonationinfo-assl.md)|ユーザー アカウントの名前を含む、 [ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)データ型。|  
|[AccountType 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/accounttype-element-assl.md)|定義されている勘定科目の種類の名前を含む、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。|  
|[ActionID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/actionid-element-assl.md)|名前を含む、[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)要素で定義されている、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素で使用できるよう、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素として、 [PerspectiveAction](../../../analysis-services/scripting/data-type/perspectiveaction-data-type-assl.md)要素。|  
|[要素 &#40; を管理します。ASSL &#41;](../../../analysis-services/scripting/properties/administer-element-assl.md)|関連付けられたアクセス許可を管理する権限が含まれるかどうかを示します、**データベース**要素。|  
|[AggregateFunction 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md)|によって使用される集計関数の種類を定義、[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)要素。|  
|[AggregationDesignID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/aggregationdesignid-element-assl.md)|識別、 [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)要素に関連付けられた、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)要素。|  
|[AggregationFunction 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/aggregationfunction-element-assl.md)|勘定科目の種類に使用する集計関数を格納します。|  
|[AggregationID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/aggregationid-element-assl.md)|集計定義を識別、 **AggregationDesign**集計インスタンスの作成に使用する要素。|  
|[AggregationInstanceSource 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/aggregationinstancesource-element-assl.md)|バインドされているユーザー定義集計インスタンスのデータのソースを識別、**パーティション**要素。|  
|[AggregationPrefix 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/aggregationprefix-element-assl.md)|関連する親要素全体にわたって集計名に使用する共通のプレフィックスを定義します。|  
|[AggregationStorage 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/aggregationstorage-element-assl.md)|集計の保存方法を識別します。|  
|[AggregationType 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/aggregationtype-element-assl.md)|によって格納される集計の種類を定義、**パーティション**要素。|  
|[AggregationUsage 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/aggregationusage-element-assl.md)|コントロール方法で、集計デザイナー [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]集計をデザインします。|  
|[Algorithm 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/algorithm-element-assl.md)|によって使用されるアルゴリズムを定義、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)要素。|  
|[Alias 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/alias-element-assl.md)|別名を定義、[アカウント](../../../analysis-services/scripting/objects/account-element-assl.md)要素。|  
|[AllMemberAggregationUsage 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/allmemberaggregationusage-element-assl.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] の集計デザイナーによる集計のデザインを制御します。|  
|[AllMemberName 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/allmembername-element-assl.md)|すべてのメンバーの既定の言語のキャプションを含む、[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)要素。|  
|[AllowBrowsing 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/allowbrowsing-element-assl.md)|定義するかどうかのメンバー、[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)要素参照権限を持って、 **MiningModel**要素。|  
|[AllowDrillThrough 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md)|親要素に対してドリルスルーが許可されているかどうかを指定します。|  
|[AllowDuplicateNames 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/allowduplicatenames-element-assl.md)|重複する名前が使用できるかどうかを決定する**階層**要素。|  
|[AllowedSet 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/allowedset-element-assl.md)|許可された権限のセットを定義するセット式が含まれています、**ロール**属性上の要素。|  
|[Application 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/application-element-assl.md)|関連付けられているアプリケーションを識別、**アクション**要素。|  
|[AssociatedMeasureGroupID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/associatedmeasuregroupid-element-assl.md)|識別子 (ID) を含む、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)要素に関連付けられた、 [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)要素または[Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)要素。|  
|[AttributeAllMemberName 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/attributeallmembername-element-assl.md)|ディメンションの All メンバーのキャプションを既定の言語で格納します。|  
|[AttributeHierarchyDisplayFolder 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/attributehierarchydisplayfolder-element-assl.md)|関連付けられている属性階層を表示するときに使用するフォルダーを識別します。|  
|[AttributeHierarchyEnabled 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/attributehierarchyenabled-element-assl.md)|属性階層がその属性で有効かどうかを指定します。|  
|[AttributeHierarchyOptimizedState 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/attributehierarchyoptimizedstate-element-assl.md)|属性階層に適用される最適化のレベルを指定します。|  
|[AttributeHierarchyOrdered 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/attributehierarchyordered-element-assl.md)|関連付けられた属性階層に順序付けを行うかどうかを指定します。|  
|[AttributeHierarchyVisible 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/attributehierarchyvisible-element-assl.md)|属性階層をクライアント アプリケーションに対して公開するかどうかを指定します。|  
|[AttributeID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/attributeid-element-assl.md)|親要素に関連付けられている属性の ID を格納します。|  
|[Audit 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/audit-element-assl.md)|指定する、[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)要素は、サーバーのパフォーマンス低下を招く場合でも、すべてのイベントを削除できません。|  
|[AutoRestart 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/autorestart-element-assl.md)|決定するかどうか、**トレース**する場合、要素を自動的に再開する、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]サービスが停止して再起動します。|  
|[BackColor 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/backcolor-element-assl.md)|親要素の色関連の表示特性を記述します。|  
|[CacheMode 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/cachemode-element-assl.md)|マイニング構造の処理中に取得したトレーニング データに使用するキャッシュ メカニズムを指定します。|  
|[CalculationReference 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/calculationreference-element-assl.md)|名前付きセットまたはによって参照される計算されるセルの名前を含む、 **CalculationProperty**要素。|  
|[CalculationType 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/calculationtype-element-assl.md)|関連付けられたで定義されている計算の種類を表します**CalculationProperty**要素。|  
|[CalendarEndDate 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/calendarenddate-element-assl.md)|カレンダー期間の終了日を定義、 [TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)要素。|  
|[CalendarLanguage 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/calendarlanguage-element-assl.md)|使用するカレンダーの言語を定義、 **TimeBinding**要素。|  
|[CalendarStartDate 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/calendarstartdate-element-assl.md)|カレンダー期間の開始日を定義、 **TimeBinding**要素。|  
|[Caption 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/caption-element-assl.md)|関連する親要素のキャプションを格納します。|  
|[CaptionIsMdx 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/captionismdx-element-assl.md)|定義するかどうかのキャプション、**アクション**要素は、多次元式 (MDX) 式です。|  
|[Cardinality 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/cardinality-element-assl.md)|記述されるリレーションシップの基数を示します、 [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)または[RegularMeasureGroupDimension](../../../analysis-services/scripting/data-type/regularmeasuregroupdimension-data-type-assl.md)です。|  
|[CaseCubeDimensionID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/casecubedimensionid-element-assl.md)|データ マイニング ディメンションをメジャー グループに関連付けるキューブ ディメンションの ID を格納します。|  
|[ClassifiedColumnID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/classifiedcolumnid-element-assl.md)|によって分類される関連列の ID が含まれています、 [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)要素。|  
|[Collation 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/collation-element-assl.md)|親要素によって使用される照合順序を指定します。|  
|[ColumnID 要素 & #40 です。ColumnBinding &#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/columnid-element-columnbinding-assl.md)|データ アイテムがバインドされるテーブル内の列の ID を格納します。|  
|[ColumnID 要素 & #40 です。EventColumn &#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/columnid-element-eventcolumn-assl.md)|イベントの一部としてキャプチャされる情報の列の ID が含まれています、**トレース**要素。|  
|[Condition 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/condition-element-assl.md)|指定する MDX 式を含むかどうか、**アクション**親要素がターゲットに適用されます。|  
|[ConnectionString 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/connectionstring-element-assl.md)|暗号化された接続文字列を表す、[データソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)要素。|  
|[ConnectionStringSecurity 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/connectionstringsecurity-element-assl.md)|セキュリティ上の目的で、ユーザーのパスワードをデータ ソースの接続文字列から取り除くかどうかを指定します。|  
|[コンテンツ要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/content-element-assl.md)|内の列のコンテンツについて説明、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)要素。|  
|[CreatedTimestamp 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)|親要素の読み取り専用の作成タイムスタンプを格納します。|  
|[CubeDimensionID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/cubedimensionid-element-assl.md)|識別、 [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)親要素に関連付けられている要素です。|  
|[CubeID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/cubeid-element-assl.md)|識別、**キューブ**要素に関連付けられた、[バインド](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)要素。|  
|[CurrentStorageMode 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/currentstoragemode-element-assl.md)|親要素の現在のストレージ モードを指定します。|  
|[CurrentTimeMember 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/currenttimemember-element-assl.md)|ディメンションに関連付けられている時間の現在のメンバーを定義、 **Kpi**要素。|  
|[DataAggregation 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/dataaggregation-element-assl.md)|インスタンスが永続化されたデータまたはのキャッシュされたデータを集計できるかどうかを判断、 **MeasureGroup**です。|  
|[DatabaseID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/databaseid-element-assl.md)|識別、**データベース**の行外に関連付けられている要素**バインド**要素。|  
|[DataSize 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/datasize-element-assl.md)|バイト単位のサイズが含まれています、 [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)要素。|  
|[DataSourceID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/datasourceid-element-assl.md)|識別、**データソース**親要素に関連付けられている要素です。|  
|[DataSourceImpersonationInfo 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/datasourceimpersonationinfo-element-assl.md)|データ ソースに接続するときに、権限借用の動作を決定するための情報が含まれています、**データベース**要素。|  
|[DataSourceViewID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/datasourceviewid-element-assl.md)|識別、 [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)要素に関連付けられた、**バインド**親要素です。|  
|[DataType 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/datatype-element-assl.md)|関連する要素のデータ型を定義します。|  
|[DbSchemaName 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/dbschemaname-element-assl.md)|によって識別されるテーブル内の親要素によって使用されるスキーマの名前を含む、 [DbTableName](../../../analysis-services/scripting/properties/dbtablename-element-assl.md)要素。|  
|[DbTableName 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/dbtablename-element-assl.md)|親要素がバインドされているテーブルの名前を格納します。|  
|[既定の要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/default-element-assl.md)|決定するかどうか、 **DrillThroughAction**は、既定のドリルスルー アクション。|  
|[DefaultMeasure 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/defaultmeasure-element-assl.md)|既定のメジャーを定義する MDX 言語の式が含まれています、**キューブ**または**パースペクティブ**要素。|  
|[DefaultMember 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/defaultmember-element-assl.md)|親要素の既定のメンバーを識別する MDX 式を格納します。|  
|[DefaultScript 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/defaultscript-element-assl.md)|既定値を識別[MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)内の要素、 [MdxScripts](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)コレクション。|  
|[DefaultValue 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/defaultvalue-element-assl.md)|関連付けられている読み取り専用の既定値を含む[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)要素。|  
|[DeniedSet 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/deniedset-element-assl.md)|関連属性で拒否される権限の一覧を定義するセット式を格納します。|  
|[DependsOnDimensionID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/dependsondimensionid-element-assl.md)|親ディメンションが依存する別のディメンションの ID を格納します。|  
|[Description 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/description-element-assl.md)|親要素の説明を格納します。|  
|[DimensionID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/dimensionid-element-assl.md)|ディメンションの ID を格納します。|  
|[DiscretizationBucketCount 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/discretizationbucketcount-element-assl.md)|分離対象のバケット数を示します。|  
|[DiscretizationMethod 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/discretizationmethod-element-assl.md)|分離に使用するメソッドを定義します。|  
|[DisplayFlag 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/displayflag-element-assl.md)|ユーザー インターフェイス コンポーネントを関連付けられているに表示するかどうかを示す読み取り専用のヒントを含む**ServerProperty**要素。|  
|[DisplayFolder 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/displayfolder-element-assl.md)|親要素を一覧表示するフォルダーを指定します。 開発者および管理者向けの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] アプリケーションでは、表示フォルダーを使用して複数の要素を視覚的に分類できる場合があります。|  
|[Distribution 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/distribution-element-assl.md)|どのようにスカラー値を表すプロバイダー固有の値を含むの列内で分散、 **MiningStructure**要素。|  
|[Edition 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/edition-element-assl.md)|インスタンスの読み取り専用エディションを含む[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]によって表される、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)要素。|  
|[Enabled 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/enabled-element-assl.md)|親要素が有効になっているかどうかを示します。|  
|[EndOfData 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/endofdata-element-assl.md)|受け取ったデータの末尾を示す、 [PushedDataSource](../../../analysis-services/scripting/data-type/pusheddatasource-data-type-assl.md)要素。|  
|[EstimatedCount 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/estimatedcount-element-assl.md)|属性のメンバーの推定数を格納します。|  
|[EstimatedPerformanceGain 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/estimatedperformancegain-element-assl.md)|パーティションの読み取り専用の推定パフォーマンス向上率を格納します。|  
|[EstimatedRows 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/estimatedrows-element-assl.md)|親要素によって表される行の推定数を格納します。|  
|[EstimatedSize 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/estimatedsize-element-assl.md)|親要素の読み取り専用の推定サイズ (バイト単位) を格納します。|  
|[EventID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/eventid-element-assl.md)|一意に識別、[イベント](../../../analysis-services/scripting/objects/event-element-assl.md)の一部としてキャプチャされる要素、**トレース**要素。|  
|[Expression 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/expression-element-assl.md)|親要素のコンテンツを定義する MDX 式を格納します。|  
|[フィルター要素 & #40 です。バインド"&"#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/filter-element-binding-assl.md)|親要素のコンテンツをフィルター処理する MDX 式を格納します。|  
|[フィルター要素 & #40 です。トレース &#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/filter-element-trace-assl.md)|記述する XML ドキュメント フラグメントが含まれています、**トレース**フィルター。|  
|[FirstDayOfWeek 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/firstdayofweek-element-assl.md)|週の最初の日を定義、 **TimeBinding**要素。|  
|[FiscalFirstDayOfMonth 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/fiscalfirstdayofmonth-element-assl.md)|会計月の最初の日を定義、 **TimeBinding**要素。|  
|[FiscalFirstMonth 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/fiscalfirstmonth-element-assl.md)|最初の月の会計期間の定義、 **TimeBinding**要素。|  
|[FiscalYearName 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/fiscalyearname-element-assl.md)|会計年度の名前の命名規則を定義、 **TimeBinding**要素。|  
|[FontFlags 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/fontflags-element-assl.md)|フォントに関連する表示特性を記述、 **CalculationProperty**または**メジャー**親要素です。|  
|[FontName 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/fontname-element-assl.md)|フォントに関連する表示特性を記述、 **CalculationProperty**または**メジャー**親要素です。|  
|[FontSize 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/fontsize-element-assl.md)|フォントに関連する表示特性を記述、 **CalculationProperty**または**メジャー**親要素です。|  
|[ForceRebuildInterval 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/forcerebuildinterval-element-assl.md)|新しい多次元 OLAP (MOLAP) 画像が使用できるようになり、MOLAP 画像処理が無条件で開始されるまでの時間を指定します。|  
|[ForeColor 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/forecolor-element-assl.md)|色関連の表示特性を記述、 **CalculationProperty**または**メジャー**親要素です。|  
|[Format 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/format-element-assl.md)|要求の形式が含まれています、 **DataItem**要素。|  
|[FormatString 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/formatstring-element-assl.md)|表示形式について説明します、 **CalculationProperty**要素または**メジャー**要素。|  
|[Goal 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/goal-element-assl.md)|目標を識別、 **Kpi**要素。|  
|[GranularityAttributeID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/granularityattributeid-element-assl.md)|親に関連付けられている属性の ID を含む[MeasureGroupAttributeBinding](../../../analysis-services/scripting/data-type/measuregroupattributebinding-data-type-out-of-line-assl.md)データ型。|  
|[HideMemberIf 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/hidememberif-element-assl.md)|レベル内のメンバーをクライアント アプリケーションに対して非表示にするかどうかと、そのタイミングを示します。|  
|[HierarchyID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/hierarchyid-element-assl.md)|ID を表す、 [CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md)、 [MeasureGroupHierarchy](../../../analysis-services/scripting/data-type/measuregrouphierarchy-data-type-assl.md)、または[PerspectiveHierarchy](../../../analysis-services/scripting/data-type/perspectivehierarchy-data-type-assl.md)要素。|  
|[HierarchyUniqueNameStyle 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/hierarchyuniquenamestyle-element-assl.md)|一意の名前が決定内に含まれている階層に対して生成される、 **CubeDimension**です。|  
|[ID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/id-element-assl.md)|親要素の一意の ID を格納します。|  
|[IgnoreUnrelatedDimensions 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/ignoreunrelateddimensions-element-assl.md)|メジャー グループに関連付けられていないディメンションのメンバーがクエリに含まれているときに、関連付けられていないディメンションをトップ レベルに強制するかどうかを指定します。|  
|[ImpersonationInfo 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/impersonationinfo-element-assl.md)|アセンブリにアクセスする場合、またはアセンブリを実行する場合の権限借用の動作を決定するために使用する情報を格納します。|  
|[ImpersonationInfoSecurity 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/impersonationinfosecurity-element-assl.md)|指定されるセキュリティ資格情報に変更を行ったかどうかを示す読み取り専用の値が含まれています、 **ImpersonationInfo**データ型。|  
|[ImpersonationMode 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/impersonationmode-element-assl.md)|派生した要素の権限借用の方法を示す値を含む、 **ImpersonationInfo**データ型。|  
|[InstanceSelection 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/instanceselection-element-assl.md)|クライアント アプリケーションにヒントを提供し、一覧の予期されたアイテム数に基づいて、アイテムの一覧の表示方法を提案します。|  
|[IntermediateCubeDimensionID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/intermediatecubedimensionid-element-assl.md)|参照ディメンションをメジャー グループに関連付けるディメンションの ID を格納します。|  
|[IntermediateGranularityAttributeID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/intermediategranularityattributeid-element-assl.md)|参照ディメンションを中間ディメンションに関連付けるために使用される中間キューブ ディメンションにおける粒度属性の ID を格納します。|  
|[InvalidXmlCharacters 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/invalidxmlcharacters-element-assl.md)|ソース データの有効でない XML 文字の処理方法を指定します。|  
|[Invocation 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/invocation-element-assl.md)|指定する方法、**アクション**呼び出す必要があります。|  
|[IsAggregatable 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/isaggregatable-element-assl.md)|指定するかどうかの値、 [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)要素を集計することができます。|  
|[IsKey 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/iskey-element-assl.md)|列が内のケースのキーを提供するかどうかを示す、 **MiningStructure**要素。|  
|[Isolation 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/isolation-element-assl.md)|派生した要素の分離レベルを示す、[データソース](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)データ型。|  
|[KeyDuplicate 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/keyduplicate-element-assl.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] による、処理時に発生した重複キー エラーの処理方法を指定します。|  
|[KeyErrorAction 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/keyerroraction-element-assl.md)|キーでエラーが発生した場合に [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が実行するアクションを指定します。|  
|[KeyErrorLimit 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/keyerrorlimit-element-assl.md)|処理時に許容可能なエラーの数を格納します。|  
|[KeyErrorLimitAction 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/keyerrorlimitaction-element-assl.md)|アクションを指定する[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ときいるキー エラー数がで指定された、 [KeyErrorLimit](../../../analysis-services/scripting/properties/keyerrorlimit-element-assl.md)要素に到達します。|  
|[KeyErrorLogFile 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/keyerrorlogfile-element-assl.md)|処理エラーをログに記録するためのファイル名を格納します。|  
|[KeyNotFound 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/keynotfound-element-assl.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] で参照整合性エラーが発生したときの応答方法を指定します。|  
|[KeyUniquenessGuarantee 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/keyuniquenessguarantee-element-assl.md)|属性のキーと名前の間のリレーションシップ、および関連属性へのリレーションシップが有効であることが保証されるかどうかを示します。|  
|[KpiID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/kpiid-element-assl.md)|関連付ける ID を含む、 **Kpi**を持つ要素を**パースペクティブ**要素。|  
|[言語要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/language-element-assl.md)|親要素の言語識別子を格納します。|  
|[LastProcessed 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md)|親要素が含まれているデータベースが最後に処理された時刻を示す読み取り専用のタイムスタンプを格納します。|  
|[LastSchemaUpdate 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)|親要素の読み取り専用のメタデータ更新タイムスタンプを格納します。|  
|[LastUpdate 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/lastupdate-element-assl.md)|読み取り専用を含むれたときに最後を示すタイムスタンプ、関連付けられている**データベース**データベースが含まれている主要なオブジェクトのいずれかが変更されたか。|  
|[Latency 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/latency-element-assl.md)|最も古い通知と MOLAP イメージが破棄された時点との間の "猶予期間" を定義します。|  
|[LogFileAppend 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/logfileappend-element-assl.md)|指定するかどうか、**トレース**要素を既存のログ ファイルにログ出力を追加するか上書きします。|  
|[LogFileName 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/logfilename-element-assl.md)|ログ ファイルのファイル名を含む、**トレース**要素。|  
|[LogFileRollover 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/logfilerollover-element-assl.md)|指定のログ記録するかどうか**トレース**出力は新しいファイルにロール オーバーするかまたは停止されている最大ログ ファイル サイズとがで指定する必要があります[LogFileSize](../../../analysis-services/scripting/properties/logfilesize-element-assl.md)に到達します。|  
|[LogFileSize 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/logfilesize-element-assl.md)|ログ ファイルの最大サイズを MB 単位で指定します。|  
|[ManagedProvider 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/managedprovider-element-assl.md)|派生した要素によって使用されるマネージ プロバイダーの名前を含む、**データソース**データ型。|  
|[ManufacturingExtraMonthQuarter 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/manufacturingextramonthquarter-element-assl.md)|追加の月が割り当てられる製造期間の月を定義、 **TimeBinding**要素。|  
|[ManufacturingFirstMonth 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/manufacturingfirstmonth-element-assl.md)|最初の製造月を定義、 **TimeBinding**要素。|  
|[ManufacturingFirstWeekOfMonth 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/manufacturingfirstweekofmonth-element-assl.md)|製造月の最初の週を定義、 **TimeBinding**要素。|  
|[MasterDatasourceID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/masterdatasourceid-element-assl.md)|マスター データ ソース ID を含む、**データベース**要素。|  
|[Materialization 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/materialization-element-assl.md)|メジャー グループと参照ディメンションの間のリレーションシップの種類を示します。|  
|[MaxActiveConnections 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/maxactiveconnections-element-assl.md)|派生した要素によって許可される同時接続の最大数を含む、**データソース**データ型。|  
|[MdxMissingMemberMode 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/mdxmissingmembermode-element-assl.md)|欠落しているメンバーを MDX ステートメントでどのように処理するかを指定します。|  
|[MeasureExpression 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/measureexpression-element-assl.md)|メジャーを定義する MDX 式を格納します。|  
|[MeasureGroupID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/measuregroupid-element-assl.md)|関連付けます、 **MeasureGroup**親要素、バインド、または不一致のバインド。|  
|[MeasureID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/measureid-element-assl.md)|関連付けます、**メジャー**要素を親要素です。|  
|[MeasureQualificaton 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/measurequalificaton-element-assl.md)|内のメジャーにプレフィックスが適用されるかどうかを決定、 **MeasureGroup**です。|  
|[MemberNamesUnique 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/membernamesunique-element-assl.md)|親要素に属するメンバー名を一意にする必要があるかどうかを指定します。|  
|[MemberUniqueNameStyle 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/memberuniquenamestyle-element-assl.md)|一意の名前が決定に含まれる階層のメンバーに対して生成される、 **CubeDimension**要素。|  
|[MembersWithData 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/memberswithdata-element-assl.md)|親属性内の非リーフ メンバーのデータ メンバーを表示するかどうかを指定します。|  
|[MembersWithDataCaption 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/memberswithdatacaption-element-assl.md)|システムによって生成されるデータ メンバーのキャプションを作成するためのテンプレート文字列を提供します。|  
|[MimeType 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/mimetype-element-assl.md)|該当する場合、親によって表されるデータの Multipurpose Internet Mail Extensions (MIME) の種類を含む**DataItem**要素。|  
|[MiningModelID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/miningmodelid-element-assl.md)|マイニング モデルをデータ マイニング ディメンションに関連付けます。|  
|[Name 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/name-element-assl.md)|親要素の名前が格納されます。|  
|[NamingTemplate 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md)|構築された親子階層におけるレベルの名前付け方法を定義、 **DimensionAttribute**親要素です。|  
|[NonEmptyBehavior 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/nonemptybehavior-element-assl.md)|親に関連付けられている空でない動作を決定、 **CalculationProperty**要素。|  
|[NotificationTechnique 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/notificationtechnique-element-assl.md)|指定するかどうか[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]または外部クライアント アプリケーションは、通知を処理します。|  
|[NullKeyConvertedToUnknown 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/nullkeyconvertedtounknown-element-assl.md)|NULL 変換エラーが発生した場合の動作を指定します。|  
|[NullKeyNotAllowed 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/nullkeynotallowed-element-assl.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 処理エンジンが処理中に発生した NULL キー エラーをどのように処理するかを指定します。|  
|[NullProcessing 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/nullprocessing-element-assl.md)|NULL 値の処理方法を定義します。|  
|[OnlineMode 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/onlinemode-element-assl.md)|キャッシュの再構築の開始時に直ちにデータベースをオンラインに戻すか、キャッシュの再構築の完了時にのみデータベースをオンラインに戻すかを指定します。|  
|[OptimizedState 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/optimizedstate-element-assl.md)|階層に適用される最適化のレベルを決定します。|  
|[Optionality 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/optionality-element-assl.md)|メンバーがオプションかどうかを示す、 **AttributeRelationship**要素。|  
|[OrderBy 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/orderby-element-assl.md)|属性に含まれているメンバーの順序付け方法を記述します。|  
|[OrderByAttributeID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/orderbyattributeid-element-assl.md)|メンバーの順序付けに使用する別の属性を識別、[ディメンション](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)属性。|  
|[Ordinal 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/ordinal-element-assl.md)|キーおよび翻訳などコレクション内でバインドする序数を示します。|  
|[OverrideBehavior 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/overridebehavior-element-assl.md)|記述されるリレーションシップのオーバーライド動作を示す、 **AttributeRelationship**要素。|  
|[PartitionID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/partitionid-element-assl.md)|関連付けます、**パーティション**親要素、バインド、または不一致のバインドを持つ要素。|  
|[パスワード要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/password-element-assl.md)|ユーザー アカウントのパスワードが含まれています、 **ImpersonationInfo**要素。|  
|[パス要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/path-element-assl.md)|インスタンスによって提供されるように、パスを含む[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]で使用されるレポートの[ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)要素。|  
|[PendingValue 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/pendingvalue-element-assl.md)|読み取り専用の関連付けられた保留値を含む**ServerProperty**要素。|  
|[PermissionSet 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/permissionset-element-assl.md)|関連付けられているアクセス許可セットを識別、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework アセンブリ。|  
|[Persistence 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/persistence-element-assl.md)|調べ、バインドされているソース データのどの部分は動的で指定された頻度を使用して更新プログラムの確認は、 [RefreshPolicy](../../../analysis-services/scripting/properties/refreshpolicy-element-assl.md)要素。|  
|[Process 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/process-element-assl.md)|ユーザーが親要素の所有者を処理できるかどうかを決定します。|  
|[ProcessingMode 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/processingmode-element-assl.md)|処理時または処理後にインスタンスによってインデックス付けまたは集計が行われるかどうかを指定します。|  
|[ProcessingPriority 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/processingpriority-element-assl.md)|レイジー集計、インデックス作成、クラスター化など、バックグラウンド操作中の親オブジェクトの処理の優先順序を決定します。|  
|[ProcessingQuery 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/processingquery-element-assl.md)|増分処理ステータスの通知のために実行するクエリのパラメーター化されたテキストを格納します。|  
|[ProductName 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/productname-element-assl.md)|インスタンスの読み取り専用の製品名を含む[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]と関連付けられている、**サーバー**要素。|  
|[Query 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/query-element-assl.md)|通知の目的で実行するクエリのテキストを格納します。|  
|[QueryDefinition 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/querydefinition-element-assl.md)|関連付けられているクエリの不透過の式が含まれています、**データソース**内の要素、 [QueryBinding](../../../analysis-services/scripting/data-type/querybinding-data-type-assl.md)要素。|  
|[Read 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/read-element-assl.md)|データまたはメタデータの機能を読み取れるかどうかを判断、指定された[CubeDimensionPermission](../../../analysis-services/scripting/data-type/cubedimensionpermission-data-type-assl.md)または[権限](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)要素。|  
|[ReadDefinition 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/readdefinition-element-assl.md)|メンバーがデータベースの定義やデータベース内のオブジェクトの定義を読み取ることができるかどうかを指定します。|  
|[ReadSourceData 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/readsourcedata-element-assl.md)|一意の名前が決定内に含まれている階層に対して生成される、 **CubePermission**です。|  
|[RefreshInterval 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/refreshinterval-element-assl.md)|親要素に関連付けられたバインド データの更新間隔を指定します。|  
|[RefreshPolicy 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/refreshpolicy-element-assl.md)|どのくらいの頻度を決定ディメンションまたはメジャー グループの動的部分 (で指定されたとおり、[永続化](../../../analysis-services/scripting/properties/persistence-element-assl.md)要素) の変更がチェックされます。|  
|[RelationshipType 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/relationshiptype-element-assl.md)|示すかどうかのメンバー リレーションシップ、 **AttributeRelationship**変更できます。|  
|[RemoteDatasourceID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/remotedatasourceid-element-assl.md)|リモート パーティションを格納する [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスを指す OLAP データ ソースの ID を指定します。|  
|[ReportingFirstMonth 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/reportingfirstmonth-element-assl.md)|最初のレポート月を定義、 **TimeBinding**要素。|  
|[ReportingFirstWeekOfMonth 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/reportingfirstweekofmonth-element-assl.md)|レポート月の最初の週を定義、 **TimeBinding**要素。|  
|[ReportingWeekToMonthPattern 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/reportingweektomonthpattern-element-assl.md)|レポートの週から月のパターンを定義、 **TimeBinding**要素。|  
|[ReportServer 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/reportserver-element-assl.md)|名前を含む、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]インスタンスによって使用される、 **ReportAction**です。|  
|[RequiresRestart 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/requiresrestart-element-assl.md)|関連付けられている読み取り専用の値が含まれています、 **ServerProperty**サーバー プロパティの値を変更するには、変更を反映するため、インスタンスを再起動することが必要とするかどうかを決定する要素。|  
|[RoleID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/roleid-element-assl.md)|権限が定義されているロールを識別します。|  
|[ルート要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/root-element-assl.md)|データ ソースのデータ (行セット) を格納します。|  
|[RootMemberIf 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/rootmemberif-element-assl.md)|親属性のルート メンバーまたはメンバーを識別する方法を指定します。|  
|[Schema 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/schema-element-assl.md)|データ ソース ビューのスキーマを格納します。|  
|[ScriptCacheProcessingMode 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/scriptcacheprocessingmode-element-assl.md)|サーバーがスクリプト キャッシュを処理中または処理後のどちらに構築するかを指定します。|  
|[SilenceInterval 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/silenceinterval-element-assl.md)|MOLAP イメージ作成プロセスを開始する前に [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスが一時停止する最短時間を定義します。|  
|[SilenceOverrideInterval 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/silenceoverrideinterval-element-assl.md)|初期通知を受信した後、MOLAP イメージ作成が無条件で開始されるまでに経過する必要のある時間を定義します。|  
|[Slice 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/slice-element-assl.md)|パーティションに含まれているスライスを定義する MDX 式を格納します。|  
|[SolveOrder 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/solveorder-element-assl.md)|解決順序を示す、 **CalculationProperty**要素は、計算されるメンバーまたは計算されるセル定義に適用します。|  
|[Source 要素 & #40 です。バインド"&"#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|親要素がバインドされているデータのソースを識別します。|  
|[Source 要素 & #40 です。ComAssembly &#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/source-element-comassembly-assl.md)|Component Object Model (COM) コンポーネント用のファイル名またはプログラム識別子 (ProgID) を格納します。|  
|[Source 要素 & #40 です。メジャー"&"#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/source-element-measure-assl.md)|値を含むソースの詳細を含む、**メジャー**要素。|  
|[SourceAttributeID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/sourceattributeid-element-assl.md)|基になる属性の ID を含む、[レベル](../../../analysis-services/scripting/objects/level-element-assl.md)要素に基づいています。|  
|[SourceColumnID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/sourcecolumnid-element-assl.md)|先祖である基になるマイニング構造列の ID を含む**MiningStructure**要素。|  
|[State 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/state-element-assl.md)|親要素の現在の処理状態を記述する読み取り専用の値を格納します。|  
|[Status 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/status-element-assl.md)|状態インジケーターを返す MDX 式を含む、 **Kpi**要素。|  
|[StatusGraphic 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/statusgraphic-element-assl.md)|状態を表す推奨グラフィカル表示が含まれています、 **Kpi**要素。|  
|[StopTime 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/stoptime-element-assl.md)|日付と時刻を指定、**トレース**要素を停止する必要があります。|  
|[StorageLocation 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)|親要素のコンテンツを収めるファイル システム ストレージの場所を格納します。|  
|[StorageMode 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/storagemode-element-assl.md)|親要素のストレージ モードを指定します。|  
|[TableID 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/tableid-element-assl.md)|テーブルの ID が含まれています (から、 **DataSourceView**要素)、親要素に関連付けられています。|  
|[ターゲット要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/target-element-assl.md)|対象を識別、**アクション**要素。|  
|[TargetType 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/targettype-element-assl.md)|識別されるアイテムの項目の種類を識別、[ターゲット](../../../analysis-services/scripting/properties/target-element-assl.md)要素。|  
|[テキスト要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/text-element-assl.md)|テキストを含む、[コマンド](../../../analysis-services/scripting/objects/command-element-assl.md)要素。|  
|[Timeout 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/timeout-element-assl.md)|データの取得を試みたときにタイムアウトをレポートするまでの時間を指定します (秒単位)。|  
|[Trend 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/trend-element-assl.md)|傾向インジケーターを返す MDX 式を含む、 **Kpi**要素。|  
|[TrendGraphic 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/trendgraphic-element-assl.md)|傾向の推奨のグラフィカル表示が含まれています、 **Kpi**要素。|  
|[Trimming 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/trimming-element-assl.md)|データ ソースのデータを切り捨てる方法を指定します。|  
|[Type 要素 & #40 です。アクション"&"#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/type-element-action-assl.md)|型を含む、**アクション**要素。|  
|[Type 要素 & #40 です。バインド"&"#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/type-element-binding-assl.md)|属性バインドの型を格納します。|  
|[Type 要素 & #40 です。ClrAssemblyFile &#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/type-element-clrassemblyfile-assl.md)|.NET Framework アセンブリに属しているファイルの 1 つのファイルの種類を指定します。|  
|[Type 要素 (&) #40";"ディメンション"&"#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/type-element-dimension-assl.md)|ディメンションのコンテンツに関する情報を提供します。|  
|[Type 要素 (&) #40";"DimensionAttribute"&"#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/type-element-dimensionattribute-assl.md)|属性の型を示します。|  
|[Type 要素 & #40 です。MeasureGroup &#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/type-element-measuregroup-assl.md)|型を指定します、 **MeasureGroup**です。|  
|[Type 要素 & #40 です。MeasureGroupAttribute &#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/type-element-measuregroupattribute-assl.md)|型を含む、 [MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)要素。|  
|[Type 要素 & #40 です。MiningStructureColumn &#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/type-element-miningstructurecolumn-assl.md)|型を含む、 [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)要素。|  
|[Type 要素 & #40 です。パーティション"&"#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/type-element-partition-assl.md)|型を含む、**パーティション**要素。|  
|[Type 要素 & #40 です。PerspectiveCalculation &#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/type-element-perspectivecalculation-assl.md)|型を示す、 [PerspectiveCalculation](../../../analysis-services/scripting/data-type/perspectivecalculation-data-type-assl.md)要素。|  
|[UnknownMember 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/unknownmember-element-assl.md)|不明なメンバーが表示されるかどうかを示します。|  
|[UnknownMemberName 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/unknownmembername-element-assl.md)|ディメンションの不明メンバーのキャプションをディメンションの既定の言語で格納します。|  
|[Usage 要素 (&) #40";"DimensionAttribute"&"#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md)|属性の使用方法を説明します。|  
|[Usage 要素 & #40 です。MiningModelColumn &#41;& #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/usage-element-miningmodelcolumn-assl.md)|について説明する方法の親に関連付けられた列**MiningStructure**を使用します。|  
|[Value 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/value-element-assl.md)|親要素の値を格納します。|  
|[Version 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/version-element-assl.md)|インスタンスの読み取り専用のバージョン番号を含む[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]によって表される、**サーバー**要素。|  
|[Visibility 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/visibility-element-assl.md)|可視性を定義、[注釈](../../../analysis-services/scripting/objects/annotation-element-assl.md)要素。|  
|[Visible 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/visible-element-assl.md)|親要素の表示を決定します。|  
|[VisualTotals 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/visualtotals-element-assl.md)|この属性のメンバーに対して表示部分の合計を表示するかどうかを指定する MDX 式を格納します。|  
|[書き込み要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/write-element-assl.md)|データまたはメタデータの機能を書き込めるかどうかを決定する、指定された**CubeDimensionPermission**または**権限**要素。|  
|[WriteEnabled 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/writeenabled-element-assl.md)|ディメンションの書き戻しを使用できるかどうかを示します (セキュリティ権限に依存)。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML 要素の階層 & #40 です。ASSL &#41;](../../../analysis-services/scripting/analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  

