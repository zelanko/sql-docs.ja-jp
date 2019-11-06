---
title: 多次元モデルの Power View の理解 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d0558cae-8209-4242-80c5-2c95981b88b9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 70ccd24e72671255ea0c929b19110794e1c0412a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66072667"
---
# <a name="understanding-power-view-for-multidimensional-models"></a>多次元モデルの Power View について
  この記事では、Power View では、Microsoft SQL Server 2014 では、多次元モデル機能について説明し、BI プロフェッショナルと管理者向けの多次元モデルでの Power View を実装するために重要な情報を提供します、組織。  
  
 多次元モデルには、業界最高レベルの OLAP データ モデリング、ストレージ、および分析ソリューションが用意されています。 Microsoft SQL Server 2014 の多次元モデルでは、Microsoft Power View を使用したアドホック データ分析、探索、およびビジュアル化がサポートされます。  
  
 Power View とは、SharePoint ライブラリの共有レポート データ ソース (.rsds) ファイルからブラウザーで起動できるシン Web クライアントです。 レポート データ ソースは、クライアントとバックエンドのデータ ソースとの間の橋渡しの役割を果たします。 バックエンドのデータ ソースには、SharePoint の PowerPivot ブック、表形式モードで実行している Analysis Services サーバーの表形式モデル、または多次元モードで実行している Analysis Services サーバーの多次元モデルを指定できます。 Power View レポートは、SharePoint ライブラリまたはギャラリーに保存して、組織内の他のメンバーと共有できます。  
  
 **多次元モデルの Power View のアーキテクチャ**  
  
 ![Power View の多次元モデル アーキテクチャ](../media/daxmd-architecture.gif "Power View の多次元モデルのアーキテクチャ")  
  
## <a name="prerequisites"></a>前提条件  
 **サーバーの要件**  
  
-   多次元モードで実行されている SQL Server 2014 Enterprise または Business Intelligence エディションと Analysis Services。  
  
-   SQL Server 2014 Reporting Services アドインの Microsoft SharePoint Server 2010 または 2013 Enterprise Edition。  
  
 **クライアントの要件**  
  
-   Power View クライアント機能には、Microsoft Silverlight 5 が必要です。 詳細については、次を参照してください。 [Reporting Services と Power View のブラウザー サポートの計画&#40;Reporting Services 2014&#41;](../../reporting-services/browser-support-for-reporting-services-and-power-view.md)します。  
  
## <a name="features"></a>機能  
 **Power View のネイティブ サポート**  
  
 このリリースでは、多次元モデルで、SharePoint モードの Power View を使用した分析とビジュアル化がサポートされています。 多次元モデルで特別な構成は必要ありません。 ただし、Microsoft Excel や Microsoft Performance Point など、その他のクライアント ツールと比較すると、Power View での多次元モデル オブジェクトの表示形式にはいくつか違いがあります。 このリリースでは、Excel 2013 の Power View を使用した多次元モデルの分析とビジュアル化はサポートされていません。  
  
 **DAX クエリのネイティブ サポート**  
  
 このリリースでは、多次元モデルで、従来の MDX クエリに加えて DAX クエリと DAX 関数がサポートされています。 PATH などの一部の DAX 関数は、多次元モデリングでは使用できません。 DAX の詳細、および DAX と MDX の比較については、「 [Data Analysis Expressions および MDX](https://msdn.microsoft.com/library/ff487170\(SQL.105\).aspx)」を参照してください。  
  
## <a name="multidimensional-to-tabular-object-mapping"></a>多次元オブジェクトと表形式オブジェクトのマッピング  
 Analysis Services には、多次元モデルの表形式モデル メタデータ表現が用意されています。 多次元モデルのオブジェクトは、Power View、および BI 注釈付きの CSDL の出力では表形式オブジェクトとして表されます。  
  
 **オブジェクト マッピングの概要**  
  
|多次元オブジェクト|表形式オブジェクト|  
|-----------------------------|--------------------|  
|Cube|[モデル]|  
|キューブ ディメンション|テーブル|  
|ディメンション属性 (キー、名前)|[列]|  
|[メジャー グループ]|テーブル|  
|[メジャー]|[メジャー]|  
|メジャー グループのないメジャー|Measures という名前のテーブル内|  
|メジャー グループとキューブ ディメンションのリレーションシップ|リレーションシップ|  
|Perspective|Perspective|  
|KPI (KPI)|KPI (KPI)|  
|ユーザー階層/親子階層|Hieararchy|  
|表示フォルダー|表示フォルダー|  
  
## <a name="measures-measure-groups-and-kpis"></a>メジャー、メジャー グループ、および KPI  
  
> [!NOTE]  
>  この記事にある一部の画像とテキストでは、SQL Server 2012 サンプル データベースの Adventure Works 多次元モデルが使用されています。  
  
 多次元キューブ内のメジャー グループは、シグマ (∑) 記号付きのテーブルとして Power View のフィールド リストに表示されます。  
  
 **Power View のフィールド リスト内のメジャー グループ**  
  
 ![フィールドの一覧で、Power View](../media/daxmd-powerviewfieldlist.gif "フィールドの Power View での一覧")  
  
 メジャー グループ内のメジャーは、メジャーとして表示されます。 メジャー グループに関連付けられていない計算されるメジャーがある場合、そのメジャーは Measures と呼ばれる特殊なテーブルでグループ化されます。  
  
 複雑な多次元モデルを簡素化するために、モデルの作成者は、表示フォルダー内に配置するようにキューブ内の一連のメジャーまたは KPI を定義できます。 Power View では、表示フォルダー、およびその中のメジャーと KPI を表示できます。  
  
 **メジャー グループ内のメジャーと KPI**  
  
 ![Power View のフィールド リスト内のメジャー グループ](../media/daxmd-fieldlist-group.gif "Power View のフィールド リスト内のメジャー グループ")  
  
### <a name="measures-as-variants"></a>variant 型のメジャー  
 多次元モデル内のメジャーは variant 型です。 つまり、メジャーは厳密に型指定されていないため、さまざまなデータ型を使用できます。 たとえば、下の画像の既定 Financial Reporting テーブルの Amount メジャーが通貨のデータ型がサブ文字列データ型は、"Statistical Accounts"の合計の文字列値"NA"があります。 Power View は、特定のメジャーを variant 型として認識し、さまざまな視覚エフェクトで適切な値と書式設定を表示します。  
  
 **variant 型のメジャー**  
  
 ![Power View での集計可能ではない階層](../media/daxmd-nonaggrattrib.gif "Power View での集計可能ではない階層")  
  
### <a name="implicit-measures"></a>暗黙のメジャー  
 表形式モデルでは、ユーザーはフィールドに COUNT、SUM、AVERAGE などの *暗黙の* メジャーを作成できます。 多次元モデルの場合、ディメンション属性データの格納先は異なるため、暗黙のメジャーに対してクエリを実行すると時間がかかることがあります。 このため、暗黙のメジャーは Power View では使用できません。  
  
## <a name="dimensions-attributes-and-hierarchies"></a>ディメンション、属性、および階層  
 キューブ ディメンションは、表形式のメタデータにテーブルとして公開されます。 Power View のフィールド リストでは、ディメンション属性が表示フォルダー内の列として表示されます。  AttributeHierarchyEnabled プロパティが false に設定されているディメンションの属性の一例を挙げてみると、Customer ディメンションの Birth Date 属性では、AttributeHierarchyVisible プロパティが false に設定されているので、Power View のフィールド リストで表示されません。 複数階層またはユーザー階層 (Customer ディメンションの Customer Geography など) は Power View のフィールド リストに階層として公開されます。 ディメンション属性の非表示の UnknownMember は DAX クエリおよび Power View では公開されます。  
  
 **SQL Server Data Tools (SSDT) と Power View のフィールド リストにおけるディメンション、属性、および階層**  
  
 ![SSDT と Power View のフィールド リストのディメンション](../media/daxmd-ssdt-dimensions.gif "SSDT と Power View のフィールド リストのディメンション")  
  
### <a name="dimension-attribute-type"></a>ディメンション属性の型  
 多次元モデルでは、ディメンション属性を特定のディメンション属性の型に関連付けることがサポートされています。 下の画像は、City、State-Province、Country、および Postal Code の各ディメンション属性に geography 型が関連付けられている Geography ディメンションを示しています。 これらの属性は表形式のメタデータで公開されます。 Power View では、ユーザーがマップの視覚エフェクトを作成できるようにするメタデータが認識されます。 これは、Power View のフィールド リストでは Geography テーブルの City、Country、Postal Code、および State-Province の各列の横にあるマップ アイコンによって示されています。  
  
 **SSDT と Power View のフィールド リストにおけるディメンション属性の geography 型**  
  
 ![ディメンション属性の geography 型](../media/daxmd-ssdt-attribute-geog-types.gif "ディメンション属性の geography 型")  
  
### <a name="dimension-calculated-members"></a>ディメンションの計算されるメンバー  
 多次元モデルでは、実際のメンバーを 1 つを含む All の子に対して計算されるメンバーがサポートされています。 このような計算されるメンバーを公開する際の追加の制約は次のとおりです。  
  
-   ディメンションに複数の属性がある場合は、実際の 1 つのメンバーである必要があります。  
  
-   計算されるメンバーが含まれる属性は、それが唯一の属性である場合を除いて、ディメンションのキー属性にすることはできません。  
  
-   計算されるメンバーが含まれる属性は、親子属性にすることができません。  
  
 ユーザー階層の計算されるメンバーは、Power View では公開されません。ただし、エンド ユーザーは、ユーザー階層に計算されるメンバーを含むキューブに引き続き接続できます。  
  
 次の図は、Date ディメンションのディメンション属性"Fiscal Date Calculations"にタイム インテリジェンス計算されるメンバーを含んでいるキューブの Power View レポートを示します。  
  
 **計算されるメンバーを含む Power View レポート**  
  
 ![計算されるメンバーは Power View で](../media/daxmd-calcmembersinpowerview.gif "計算されるメンバーは Power View")  
  
### <a name="default-members"></a>既定メンバー  
 多次元モデルでは、ディメンション属性の既定のメンバーがサポートされています。 既定のメンバーは、クエリのデータ集計時に Analysis Services によって使用されます。 ディメンション属性の既定のメンバーは、表形式のメタデータで対応する列の既定値または既定のフィルターとして公開されます。  
  
 Power View の動作は、属性が適用された Excel ピボットテーブルとほぼ同じです。 ユーザーが既定値を含む列を Power View の視覚エフェクト (テーブル、マトリックス、またはグラフ) に追加すると、既定値は適用されず、使用できるすべての値が表示されます。 ユーザーがフィルターに列を追加すると、既定値が適用されます。  
  
### <a name="dimension-security"></a>ディメンションのセキュリティ  
 多次元モデルでは、ロールを使用したディメンションおよびセル レベルのセキュリティがサポートされています。 Power View を使用してキューブに接続するユーザーは、認証され、適切な権限に対して評価されます。 ディメンションのセキュリティを適用した場合、Power View ではユーザーからそれぞれのディメンション メンバーは見えません。ただし、あるユーザーに定義されたセルのセキュリティ権限で、特定のセルが制限されている場合、そのユーザーは Power View を使用してキューブに接続することができません。 場合によっては、集計データは、一部がセキュリティで保護されたデータから計算されるときに参照できます。  
  
### <a name="non-aggregatable-attributeshierarchies"></a>集計可能ではない属性/階層  
 多次元モデルでは、ディメンションの属性の IsAggregatable プロパティを false に設定できます。 つまり、モデル作成者は、データに対してクエリを実行するときにクライアント アプリケーションが階層 (属性または複数レベル) 間でデータを集計しないように指定したことになります。 Power View では、このディメンション属性は小計が利用できない列として公開されます。 次の図では、集計可能ではない階層の例を確認できます。アカウント。 Accounts 親子階層の最上位レベルは、他のレベルが集計可能であるのに対して集計可能ではありません。 Accounts 階層 (最初の 2 レベル) のマトリックス視覚エフェクトでは、Account Level 02 の小計は確認できますが、最上位レベルである Account Level 01 の小計は確認できません。  
  
 **Power View での集計可能ではない階層**  
  
 ![Power View での集計可能ではない階層](../media/daxmd-nonaggrattrib.gif "Power View での集計可能ではない階層")  
  
## <a name="images"></a>画像  
 Power View には、画像を表示する機能が用意されています。 多次元モデルでは、Power View に画像を提供する方法の 1 つとして、画像の URL (Uniform Resource Locator) が含まれる列を公開します。 このリリースに含まれる Analysis Services では、ディメンション属性を ImageURL 型としてタグ付けできます。 タグ付けすると、このデータ型は表形式のメタデータで Power View に提供されます。 その後、Power View では、視覚エフェクト内の URL で指定された画像をダウンロードして表示できます。  
  
 **SSDT でのディメンション属性の ImageURL 型**  
  
 ![ディメンション属性プロパティ](../media/daxmd-dimattribute-properties.gif "ディメンション属性のプロパティ")  
  
## <a name="parent-child-hierarchies"></a>親子階層  
 多次元モデルでは、表形式のメタデータの階層として公開される親子階層がサポートされています。 親子階層の各レベルは、非表示の列として公開されます。 親子ディメンションのキー属性は、表形式のメタデータでは公開されません。  
  
 **Power View の親子階層**  
  
 ![親子階層](../media/daxmd-ssdt-hierarchies.gif "親子階層")  
  
## <a name="perspectives-and-translations"></a>パースペクティブと翻訳  
 パースペクティブとは、特定のディメンションまたはメジャー グループだけがクライアント ツールに表示されるキューブのビューです。 パースペクティブ名は、Cube 接続文字列プロパティに値として指定できます。 たとえば、次の接続文字列で ' Direct Sales' では、多次元モデルのパースペクティブには。  
  
 `Data Source=localost;Initial Catalog=AdventureWorksDW-MD;Cube='Direct Sales'`  
  
 キューブには、モデル内でさまざまな言語に指定されたメタデータとデータの翻訳を含めることができます。 翻訳 (データとメタデータ) を表示するには、省略可能な"Locale Identifier"プロパティを次に示すように、RSDS ファイル内の接続文字列に追加する必要があります。  
  
 `Data Source=localost;Initial Catalog=AdventureWorksDW-MD;Cube='Adventure Works'; Locale Identifier=3084`  
  
 ロケール識別子が指定された .rsds ファイルを使用して Power View から多次元モデルに接続する場合、および対応する翻訳がキューブに含まれている場合、Power View には翻訳が表示されます。  
  
 詳細については、「 [Create a Report Data Source](create-a-report-data-source.md)」を参照してください。  
  
## <a name="power-view-pinned-filters"></a>Power View の固定フィルター  
 Power View レポートには複数のビューを含めることができます。 このリリースでは、表形式モデルと多次元モデルの両方に使用できる *フィルターの固定* 機能によって、レポート内のすべてのビューで適用されるフィルターを作成できるようになります。 下の画像は、ビュー フィルターの [フィルターの固定] 切り替えボタンを示しています。 既定では、ビュー フィルターは固定されておらず、そのビューのみに適用されます。 ビュー フィルターを固定すると、そのフィルターがすべてのビューに適用されます。また、ビュー フィルターの固定を解除すると、他のビューからもビュー フィルターが削除されます。  
  
 **固定フィルター**  
  
 ![フィルターをピン留め](../media/daxmd-pinnedfilterinpowerview.gif "フィルターをピン留め")  
  
## <a name="unsupported-features"></a>サポートされていない機能  
 **Power View では、Excel 2013** -への接続および多次元モデルのレポートの作成はサポートされません。 多次元モデルの Power View では、ブラウザー ベースの Power View クライアントのみがサポートされています。  
  
 **アクション** - Power View レポート、または多次元モデルに対する DAX クエリではサポートされていません。  
  
 **名前付きセット** - 多次元モデルの場合、Power View、または多次元モデルに対する DAX クエリではサポートされていません。  
  
> [!NOTE]  
>  アクションと名前付きセットがサポートされていなくても、ユーザーは Power View を使用して多次元モデルに接続したり多次元モデルを探索したりできます。  
  
 **セル レベルのセキュリティ**-Power View レポートではサポートされていません。  
  
## <a name="csdlbi-annotations"></a>CSDLBI 注釈  
 多次元キューブ メタデータは、CSDLBI (Conceptual Schema Definition Language with Business Intelligence) 注釈によってエンティティ データ モデル (EDM) ベースの概念モデルとして公開されます。  
  
 多次元メタデータは、DISCOVER_CSDL_METADATA 要求が Analysis Services インスタンスに送信されるときに、CSDLBI ドキュメントまたは CSDL の出力で表形式モデルの名前空間として表されます。  
  
 **DISCOVER_CSDL_METADATA 要求のサンプル**  
  
```  
<Envelopexmlns="http://schemas.xmlsoap.org/soap/envelope/">  
   <Body>  
      <Discoverxmlns="urn:schemas-microsoft-com:xml-analysis">  
         <RequestType>DISCOVER_CSDL_METADATA</RequestType>  
         <Restrictions>  
            <RestrictionList>  
              <CATALOG_NAME>"catalogname"<CATALOG_NAME>  
            </RestrictionList>  
         </Restrictions>  
         <Properties>  
            <PropertyList>  
            </PropertyList>  
         </Properties>  
      </Discover>  
   </Body>  
</Envelope>  
  
```  
  
 DISCOVER_CSDL_METADATA 要求には、次の制限があります。  
  
|名前|必須|説明|  
|----------|--------------|-----------------|  
|CATALOG_NAME|はい|カタログ\データベース名。|  
|PERSPECTIVE_NAME|キューブに複数のパースペクティブが含まれている場合は必須。 キューブが 1 つしかない場合や既定のパースペクティブがある場合は省略可能。|多次元データベース内のキューブ名またはパースペクティブ名。|  
|VERSION|はい|クライアントによって要求される CSDL のバージョン。 多次元機能と多次元構造はバージョン 2.0 でサポートされています。|  
  
 返される CSDL 出力ドキュメントは、モデルを名前空間として表し、エンティティ、アソシエーション、およびプロパティを示しています。  
  
 詳細については表形式モデルの CSDLBI 注釈の詳細についてを参照してください[CSDL への BI 注釈のテクニカル リファレンス](https://docs.microsoft.com/bi-reference/csdl/technical-reference-for-bi-annotations-to-csdl)msdn、および[ \[MS-CSDLBI\]:。概念スキーマ定義ファイル形式のビジネス インテリジェンス注釈](https://msdn.microsoft.com/library/jj161299\(SQL.105\).aspx)します。  
  
## <a name="client-help-on-officecom"></a>Office.com のクライアント ヘルプ  
 Power View での多次元モデル オブジェクトの表示およびサンプル レポートの作成方法については、Office.com で提供されている次の記事を参照してください。  
  
 [Power View の多次元モデル オブジェクトについて](http://office.microsoft.com/excel-help/understanding-multidimensional-model-objects-in-power-view-HA104018589.aspx)  
  
 [Power View を使用した Adventure Works 多次元モデルの探索](http://office.microsoft.com/excel-help/explore-the-adventure-works-multidimensional-model-by-using-power-view-HA104046830.aspx)  
  
  
