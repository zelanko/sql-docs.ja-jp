---
title: OLAP キューブからデータを使用して r (SQL Server の機械学習) |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 0753fc84ea6516da63e1e49dc68063780b99361b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="using-data-from-olap-cubes-in-r"></a>R での OLAP キューブからデータの使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**OlapR**パッケージは、R パッケージ、Microsoft Machine Learning のサーバーと SQL Server を使用するため、によってを可能にする OLAP キューブからデータを取得する MDX クエリを実行します。 このパッケージにリンク サーバーを作成またはフラット化された行セットをクリーンアップする必要はありません。R. から直接 OLAP データを取得することができます。

この記事では、OLAP および MDX の概要を持つ可能性がある多次元キューブ データベースに新しい R ユーザーと共に、API について説明します。

> [!IMPORTANT]
> Analysis Services のインスタンスは、従来の多次元キューブまたは表形式モデルでは、いずれかをサポートできますが、インスタンスが両方の種類のモデルをサポートできません。 そのため、キューブに対して MDX クエリを構築しようとすると、前に、Analysis Services インスタンスに多次元モデルが含まれていることを確認します。

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

    SSMS や Excel などの任意のクライアント ユーティリティを使用して、MDX のビルド後に、クエリ文字列を保存します。 この MDX 文字列に渡す引数として指定、 *SSAS クエリ ハンドラー*で、 **olapR**パッケージです。 プロバイダーは、指定した Analysis Services サーバーにクエリを送信し、R. に戻る、結果を渡します 

MDX をビルドする方法の例では、クエリまたは既存の MDX クエリの実行を参照してください[R を使用する MDX クエリを作成する方法](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md)です。

## <a name="known-issues"></a>既知の問題

このセクションの内容に関するいくつかの既知の問題およびよく寄せられる質問を表示、 **olapR**パッケージです。

### <a name="tabular-model-support"></a>表形式モデルのサポート

表形式モデルを含む Analysis Services のインスタンスに接続する場合、`explore`関数の戻り値の TRUE の場合の成功をレポートします。 ただし、表形式モデル オブジェクトは、多次元オブジェクトと異なると、多次元データベースの構造は、表形式モデルの場合と異なります。

DAX (データ分析式) には、通常、表形式モデルで使用する言語が、既に MDX に慣れている場合、表形式モデルに対する有効な MDX クエリをデザインできます。 OlapR コンス トラクターを使用して、表形式モデルに対する有効な MDX クエリを作成することはできません。

ただし、MDX クエリは、表形式モデルからデータを取得する非効率的な方法です。 R で使用するため、表形式モデルからデータを取得する必要がある場合は、これらのメソッドを検討します。

+ モデルで DirectQuery を有効にして、SQL Server でリンク サーバーとして、サーバーを追加します。 
+ 表形式モデルがリレーショナル データ マートでビルドされていた場合は、ソースから直接データを取得します。

### <a name="how-to-determine-whether-an-instance-contains-tabular-or-multidimensional-models"></a>インスタンスが表形式または多次元のモデルを含むかどうかを確認する方法

複数のモデルを含めることができますが、1 つの Analysis Services インスタンスは、モデルの 1 つだけの型を含めることができます。 表形式モデルとデータを保管および処理する方法を制御する多次元モデルの基本的な違いがあることです。 など、テーブル モデルでは、メモリに格納され、非常に高速計算を実行する列ストア インデックスを活用します。 多次元モデルでデータがディスクに格納されていると集計を事前に定義し MDX クエリを使用して取得します。

SQL Server Management Studio などのクライアントを使用して Analysis Services に接続する場合がわかりますがひとめでデータベースのアイコンを見れば、どのモデルの種類がサポートされています。

表示し、モデルの種類のインスタンスをサポートしているサーバーのプロパティを照会できます。 **サーバー モード**プロパティは、2 つの値をサポートしています:_多次元_または_テーブル_です。

概要について、次の 2 つの種類のモデルは、次の記事を参照してください。

+ [多次元と表形式モデルの比較](https://docs.microsoft.com/sql/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas)

サーバーのプロパティを照会する方法については、次の記事を参照してください。

+ [OLE DB for OLAP スキーマ行セット](https://docs.microsoft.com/sql/analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets)

### <a name="writeback-is-not-supported"></a>書き戻しはサポートされていません

キューブにカスタムの R 演算の結果を書き戻すことはできません。

一般に、キューブが書き戻しの有効な場合でも、限られた操作のみがサポートされてし、追加の構成が必要な可能性があります。 このような操作には、MDX を使用することをお勧めします。

+ [書き込み許可ディメンション](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions)
+ [書き込み許可パーティション](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions)
+ [セル データへのカスタム アクセス権を設定します。](https://docs.microsoft.com/sql/analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services)

### <a name="long-running-mdx-queries-block-cube-processing"></a>MDX クエリの実行時間の長いブロック キューブの処理

ただし、 **olapR**パッケージのみ読み取り操作を実行、実行時間の長いの MDX クエリは、キューブが処理されていることを防ぐロックを作成できます。 データの量を返す必要があるとわかるように、MDX クエリを事前にテスト常にします。

ロックされているキューブに接続しようとする場合、SQL Server データ ウェアハウスに到達できないエラーが表示する可能性があります。 推奨される解決策は、サーバーまたはインスタンス名、およびなどの確認、リモート接続を有効化ただし、前回の開いている接続の可能性を考慮します。

SSAS の管理者を防ぐことができますロックの問題を特定することによって、開いているセッションを終了します。 Timeout プロパティは、すべての実行時間の長いクエリの終了を強制するサーバー レベルの MDX クエリにも適用できます。

## <a name="resources"></a>リソース

OLAP や MDX クエリを初めて使用する場合は、次の Wikipedia 記事を参照してください。 

+ [OLAP キューブ](https://en.wikipedia.org/wiki/OLAP_cube)
+ [MDX クエリ](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)
