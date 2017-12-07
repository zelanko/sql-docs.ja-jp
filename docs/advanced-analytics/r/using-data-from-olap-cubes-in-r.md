---
title: "R で OLAP キューブからデータを使用して |Microsoft ドキュメント"
ms.custom: 
ms.prod: sql-non-specified
ms.date: 11/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: r-services
ms.assetid: 8093599c-8307-4237-983b-0908d0f8ab77
caps.latest.revision: "12"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 60e95f4c101a4afe2a8161ba40df7b27bd85f602
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="using-data-from-olap-cubes-in-r"></a>R での OLAP キューブからデータの使用

**OlapR**パッケージは、R パッケージ、Microsoft Machine Learning のサーバーと SQL Server を使用するため、によってを可能にする OLAP キューブからデータを取得する MDX クエリを実行します。 このパッケージにリンク サーバーを作成またはフラット化された行セットをクリーンアップする必要はありません。直接 R. で OLAP データを使用することができます。

この記事では、OLAP および MDX の概要を持つ可能性がある多次元キューブ データベースに新しい R ユーザーと共に、API について説明します。

> [!IMPORTANT]
> Analysis Services のインスタンスは、従来の多次元キューブまたは表形式モデルでは、いずれかをサポートできますが、インスタンスが両方の種類のモデルをサポートできません。 そのため、Analysis Services データベースに対してクエリを作成する前に、多次元モデルが含まれていることを確認します。
> 
> 表形式モデルは、MDX を使用して照会できますが、 **olapR**パッケージが表形式モデルのインスタンスへの接続をサポートしていません。 良いオプションが有効にするのには表形式モードからデータを取得する必要がある場合[DirectQuery](https://docs.microsoft.com/sql/analysis-services/tabular-models/directquery-mode-ssas-tabular)モデル、および SQL Server でリンク サーバーとして使用できますのインスタンスを作成します。 

## <a name="what-is-an-olap-cube"></a>OLAP キューブとは何ですか。

OLAP はの短縮形オンライン分析処理です。 OLAP ソリューションは広くをキャプチャして、重要なビジネス データを格納する時間の経過と共に使用されます。 OLAP データは、多様なツール、ダッシュボード、視覚エフェクトでビジネス分析に使用されます。 詳細については、次を参照してください。[オンライン分析処理](https://en.wikipedia.org/wiki/Online_analytical_processing)です。

マイクロソフトが提供[Analysis Services](https://docs.microsoft.com/sql/analysis-services/analysis-services)、設計、展開、および OLAP データの形式でクエリを実行することができます_キューブ_または_表形式モデル_です。 キューブは、多次元データベースです。 _ディメンション_ディメンションを使用して、集計または分析するデータの特定のサブセットを特定するデータ、または r: の要因のファセットと似ています。 たとえば、時間は、重要なディメンション、あまり多くの OLAP ソリューションにスライスし、データの概要を作成するときに使用する、既定で定義されている複数の予定表が含まれるようにです。 

パフォーマンス上の理由から、OLAP データベースの多くの場合、集計を計算 (または_集計_) 事前、しに高速な検索を保存します。 概要がに基づいて*メジャー*、数値データに適用できる数式として表示されています。 ディメンションを使用して、データのサブセットを定義し、そのデータに対するメジャーを計算します。 たとえば、税金、特定の仕入先、年度累計の累積的な給与支払い済みの場合などの平均の輸送費を報告するのに-複数の四半期を特定の製品ラインの売上合計を計算するのにメジャーを使用するは。

MDX では、短縮形の多次元式は、キューブを照会するために使用される言語です。 通常、MDX クエリには、MDX クエリはかなり複雑、取得され、ローリング windows、累積平均、合計、ランク、または百分位が含まれていて、1 つまたは複数のディメンション、および少なくとも 1 つのメジャーを含むデータの定義が含まれています。 

MDX クエリの構築を開始するときに役に立つ場合がありますの他のいくつかの用語を次に示します。

+ *スライス*1 つのディメンションからの値を使用して、キューブのサブセットを取得します。

+ *ダイス* は、複数のディメンションに対して値の範囲を指定してサブキューブを作成することです。

+ *ドリルダウン* は、概要から詳細情報に移動することです。

+ *ドリルアップ* は、集計の詳細情報から概要に移動することです。

+ *ロールアップ* は、ディメンションに関するデータを要約することです。

+ *ピボット* は、キューブまたはデータの選択を回転させることです。

## <a name="how-to-use-olapr-to-create-mdx-queries"></a>OlapR を使用して MDX クエリを作成する方法

次の記事では、作成またはキューブに対するクエリの実行のため構文の詳細な例を示します。

+ [R を使用する MDX クエリを作成する方法](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md)

## <a name="olapr-api"></a>olapR API

**olapR** パッケージでは、MDX クエリを作成する方法が 2 つサポートされています。

- **MDX ビルダーを使用します。** パッケージで R 関数を使用すると、キューブを選択し、軸とスライサーを設定して簡単な MDX クエリを生成できます。 これは、従来の OLAP ツールにアクセスできないか、MDX 言語の知識がない場合は、有効な MDX クエリを構築する簡単な方法です。

    MDX は複雑になることができますので、このメソッドを使用してすべての MDX クエリを作成できます。 ただし、この API は、N ディメンションでスライス、ダイス、ドリルダウン、rollup、およびピボットを含む、最も一般的で便利な操作の大半をサポートします。

+ **整形式の MDX をコピー アンド ペーストします。** 手動で作成し、任意の MDX クエリに貼り付けます。 このオプションは、再利用する既存の MDX クエリがある場合、またはビルドするクエリが複雑すぎるため、最適な**olapR**を処理します。 

    SSMS や Excel などの任意のクライアント ユーティリティを使用して、MDX をビルドし、MDX クエリを定義する文字列を保存します。 この MDX 文字列に渡す引数として指定する、 *SSAS クエリ ハンドラー*で、 **olapR**パッケージです。 この関数は、指定した Analysis Services サーバーにクエリを送信し、r、もちろん、キューブをクエリする権限があると仮定した場合の結果を渡します。

MDX をビルドする方法の例では、クエリまたは既存の MDX クエリの実行を参照してください[R を使用する MDX クエリを作成する方法](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md)です。

## <a name="known-issues"></a>既知の問題

このセクションの内容に関するいくつかの既知の問題およびよく寄せられる質問を表示、 **olapR**パッケージです。

### <a name="tabular-models-are-not-supported"></a>表形式モデルがサポートされていません

表形式モデルを含む Analysis Services のインスタンスに接続する場合、`explore`関数の戻り値の TRUE の場合の成功をレポートします。 ただし、表形式モデル オブジェクトは、互換性のある型ではありません、ため、探索できません。

さらに、(を外部ツールを使用)、表形式モデルに対する有効な MDX クエリをデザインし、この API に貼り付けて、クエリ、クエリは、NULL の結果を返し、エラーを報告しません。

R で使用するためのテーブル モデルからデータを抽出する必要がある場合は、これらのオプションを考慮してください。

+ モデルで DirectQuery を有効にして、SQL Server でリンク サーバーとして、サーバーを追加します。 
+ 表形式モデルがリレーショナル データ マートでビルドされていた場合は、ソースから直接データを取得します。

### <a name="how-to-determine-whether-an-instance-contains-tabular-or-multidimensional-models"></a>インスタンスが表形式または多次元のモデルを含むかどうかを確認する方法

表形式モデルの基本的な違いがあると、多次元モデルに影響を与える方法データを保管および処理します。 など、テーブル モデルでは、メモリに格納され、非常に高速計算を実行する列ストア インデックスを活用します。 多次元モデルでデータがディスクに格納されていると集計を事前に定義し MDX クエリを使用して取得します。

このため、1 つの Analysis Services インスタンスは、モデルの種類を 1 つだけを含めることができます。 2 つの種類のモデルを識別する方法の詳細については、次の記事を参照してください。

+ [多次元と表形式モデルの比較](https://docs.microsoft.com/sql/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas)

SQL Server Management Studio などのクライアントを使用して Analysis Services に接続する場合がわかりますがひとめでデータベースのアイコンを見れば、どのモデルの種類がサポートされています。

また、サーバーのプロパティを表示することができます。 **サーバー モード**プロパティは、2 つの値をサポートしています:_多次元_または_テーブル_です。

サーバー プロパティを使用してサーバーの種類を確認する方法の詳細については、次を参照してください[OLE DB for OLAP スキーマ行セット。](https://docs.microsoft.com/sql/analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets)

### <a name="writeback-is-not-supported"></a>書き戻しはサポートされていません

キューブにカスタムの R 演算の結果を書き戻すことはできません。

一般に、キューブが書き戻しの有効な場合でも、限られた操作のみがサポートされてし、追加の構成が必要な可能性があります。 これらの操作には、MDX を使用することをお勧めします。

+ [書き込み許可ディメンション](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions)
+ [書き込み許可パーティション](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions)
+ [セル データへのカスタム アクセス権を設定します。](https://docs.microsoft.com/sql/analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services)

## <a name="resources"></a>リソース

OLAP や MDX クエリを初めて使用する場合は、次の Wikipedia 記事を参照してください。 

+ [OLAP キューブ](https://en.wikipedia.org/wiki/OLAP_cube)
+ [MDX クエリ](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)
