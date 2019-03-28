---
title: R - SQL Server Machine Learning Services での OLAP キューブからのデータの使用
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e55093c83e9a306a06235d6bb613dac78d4677ce
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58512969"
---
# <a name="using-data-from-olap-cubes-in-r"></a>R での OLAP キューブからのデータの使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**OlapR**により OLAP キューブからデータを取得する MDX クエリを実行する Machine Learning Server および SQL Server で使用できる Microsoft が提供される、パッケージは、R パッケージ。 このパッケージによってリンク サーバーを作成または平面化された行セットをクリーンアップする必要はありません。R. から直接 OLAP データを取得することができます。

この記事では、多次元キューブ データベースに新しい可能性がある R ユーザーの OLAP と MDX の概要と共に、API について説明します。

> [!IMPORTANT]
> Analysis Services のインスタンスは、従来の多次元キューブまたは表形式モデルでは、いずれかをサポートできますが、インスタンスが両方の種類のモデルをサポートできません。 そのため、キューブに対して MDX クエリを作成する前に、Analysis Services インスタンスに多次元モデルが含まれていることを確認します。

## <a name="what-is-an-olap-cube"></a>OLAP キューブとは何ですか。

OLAP は省略形でオンライン分析処理です。 キャプチャおよび重要なビジネス データを格納する時間の経過と共に広くの OLAP ソリューションが使用されます。 OLAP データは、多様なツール、ダッシュボード、視覚エフェクトでビジネス分析に使用されます。 詳細については、次を参照してください。[オンライン分析処理](https://en.wikipedia.org/wiki/Online_analytical_processing)します。

Microsoft が提供[Analysis Services](https://docs.microsoft.com/sql/analysis-services/analysis-services)、設計、展開、および OLAP データの形式でクエリを実行することができます_キューブ_または_表形式モデル_します。 キューブは、多次元データベースです。 _ディメンション_ディメンションを使用して、集計または分析するデータの特定のサブセットを識別するためには、データ、または r の要因のファセットに似ています。 たとえば、時間は、します多くの OLAP ソリューションがスライス、データの集計時に使用する、既定で定義されている複数の予定表が含まれるようにほど重要なディメンション。 

パフォーマンス上の理由から、OLAP データベースの多くの場合、集計を計算 (または_集計_)、事前にし高速な検索を保存します。 概要に基づく*メジャー*、数値データに適用できる式を表します。 ディメンションを使用して、データのサブセットを定義して、そのデータに対するメジャーを計算します。 たとえば、税金、特定の仕入先、年度累計の累積的な賃金、有料などの平均送料を報告するのに-複数の四半期経由で特定の製品ラインの売上合計を計算するのにメジャーを使用と。

MDX では、省略形での多次元式は、キューブを照会するために使用される言語です。 通常、MDX クエリには、MDX クエリがよりかなり複雑、およびローリング windows、累積平均、合計、ランク、または百分位が含まれますが、1 つまたは複数のディメンション、および少なくとも 1 つのメジャーを含むデータの定義が含まれています。 

MDX クエリの構築を開始するときに立つ場合があるその他のいくつかの用語を次に示します。

+ *スライス*1 つのディメンションから値を使用して、キューブのサブセットを受け取る。

+ *ダイス* は、複数のディメンションに対して値の範囲を指定してサブキューブを作成することです。

+ *ドリルダウン* は、概要から詳細情報に移動することです。

+ *ドリルアップ* は、集計の詳細情報から概要に移動することです。

+ *ロールアップ* は、ディメンションに関するデータを要約することです。

+ *ピボット* は、キューブまたはデータの選択を回転させることです。

## <a name="how-to-use-olapr-to-create-mdx-queries"></a>OlapR を使用して MDX クエリを作成する方法

次の記事では、作成またはキューブに対してクエリを実行するための構文の詳細な例を示します。

+ [R を使用して MDX クエリを作成する方法](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md)

## <a name="olapr-api"></a>olapR API

**olapR** パッケージでは、MDX クエリを作成する方法が 2 つサポートされています。

- **MDX ビルダーを使用します。** パッケージの R 関数を使用すると、キューブを選択して、軸とスライサーを設定し、単純な MDX クエリを生成できます。 これは、従来の OLAP ツールへのアクセスはありません。 または、MDX 言語を深く理解する場合は、有効な MDX クエリを構築する簡単な方法です。

    MDX は複雑になるために、このメソッドを使用してすべての MDX クエリを作成できます。 ただし、この API では、N ディメンションでスライス、ダイス、ドリルダウン、ロールアップ、およびピボットを含めた、最も一般的で便利な操作のほとんどをサポートしています。

+ **適切な形式で MDX をコピーして貼り付けます。** 手動で作成し、任意の MDX クエリを貼り付けます。 ビルドするクエリが複雑すぎる場合や、再利用する既存の MDX クエリがある場合、このオプションは最適な**olapR**を処理します。

    SSMS や Excel などの任意のクライアント ユーティリティを使用して、MDX をビルドした後に、クエリ文字列を保存します。 この MDX 文字列への引数として指定、 *SSAS クエリ ハンドラー*で、 **olapR**パッケージ。 プロバイダーは、指定された Analysis Services サーバーにクエリを送信し、R. に結果を渡します 

MDX を構築する方法の例では、クエリまたは既存の MDX クエリの実行を参照してください。 [R を使用して MDX クエリを作成する方法](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md)します。

## <a name="known-issues"></a>既知の問題

このセクションに関するいくつかの既知の問題と一般的な質問を表示、 **olapR**パッケージ。

### <a name="tabular-model-support"></a>表形式モデルのサポート

表形式モデルを含む Analysis Services のインスタンスに接続する場合、`explore`関数が TRUE の戻り値で成功を報告します。 ただし、表形式モデル オブジェクトは、多次元オブジェクトと異なると、多次元データベースの構造は表形式モデルの異なる。

DAX (データ分析式) には、通常、表形式モデルで使用する言語が、MDX に慣れている場合、表形式モデルに対する有効な MDX クエリをデザインできます。 OlapR コンス トラクターを使用して、表形式モデルに対する有効な MDX クエリを作成することはできません。

ただし、MDX クエリは、表形式モデルからデータを取得する非効率的な方法です。 R で使用するため、表形式モデルからデータを取得する必要がある場合は、代わりにこれらのメソッドを検討します。

+ モデルで DirectQuery を有効にし、SQL Server のリンク サーバーとして、サーバーを追加します。 
+ 表形式モデルがリレーショナル データ マートでビルドされている場合は、ソースから直接データを取得します。

### <a name="how-to-determine-whether-an-instance-contains-tabular-or-multidimensional-models"></a>インスタンスが表形式または多次元モデルに含まれるかどうかを確認する方法

複数のモデルを含めることができますが、1 つの Analysis Services インスタンスは、モデルの種類を 1 つだけを含めることができます。 理由は、表形式モデルとデータを格納および処理する方法を制御する多次元モデルの基本的な違いがあることです。 たとえば、表形式モデルでは、メモリに格納され、非常に高速計算を実行する列ストア インデックスを活用します。 多次元モデルは、データがディスクに格納されていると集計が事前に定義されているし、MDX クエリを使用して取得します。

SQL Server Management Studio などのクライアントを使用して Analysis Services に接続する場合ことがわかりますを一目でデータベースのアイコンを見れば、どのモデルの種類がサポートされています。

表示し、モデルの種類のインスタンスをサポートしているサーバーのプロパティを照会できます。 **サーバー モード**プロパティは、2 つの値をサポートしています:_多次元_または_テーブル_します。

2 つの種類のモデルの詳細については、次の記事を参照してください。

+ [多次元および表形式モデルの比較](https://docs.microsoft.com/sql/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas)

サーバーのプロパティのクエリを実行する方法については、次の記事を参照してください。

+ [OLE DB for OLAP Schema 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets)

### <a name="writeback-is-not-supported"></a>書き戻しはサポートされていません

キューブにカスタムの R 計算の結果を書き戻すことはできません。

一般に、キューブの書き戻しを有効にしている場合でも、限られた操作のみがサポートされていると追加の構成が必要になります。 このような操作には、MDX を使用することをお勧めします。

+ [書き込み許可ディメンション](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions)
+ [書き込み許可パーティション](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions)
+ [セル データへのカスタム アクセス権を設定します。](https://docs.microsoft.com/sql/analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services)

### <a name="long-running-mdx-queries-block-cube-processing"></a>MDX クエリの実行時間の長いキューブの処理をブロックします。

ただし、 **olapR**パッケージのみ読み取り操作を実行、実行時間の長いの MDX クエリは、キューブが処理されていることを防ぐロックを作成できます。 データの量を返す必要があることがわかるように、MDX クエリを事前にテスト常にします。

ロックされているキューブに接続しようとすると、SQL Server データ ウェアハウスに到達できないエラーが発生する可能性があります。 推奨される解決策は、サーバーまたはインスタンス名、およびなどのチェック、リモート接続を有効化ただし、前回の開いている接続の可能性を検討してください。

SSAS 管理者により、問題の原因を特定し、開いているセッションを終了してロックします。 Timeout プロパティは、すべての実行時間の長いクエリの終了を強制するサーバー レベルの MDX クエリにも適用できます。

## <a name="resources"></a>リソース

OLAP や MDX クエリは、新しい場合は、Wikipedia の記事を参照してください。 

+ [OLAP キューブ](https://en.wikipedia.org/wiki/OLAP_cube)
+ [MDX クエリ](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)
