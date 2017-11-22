---
title: "R で OLAP キューブからデータを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/03/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 8093599c-8307-4237-983b-0908d0f8ab77
caps.latest.revision: "12"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 1c55a5b834cd91478a87ded7ebb86884117c7bfb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="using-data-from-olap-cubes-in-r"></a>R での OLAP キューブからデータの使用

**OlapR**パッケージは、R パッケージ、Microsoft Machine Learning サーバーおよび SQL Server R Services で使用するでを可能にする OLAP キューブからデータを取得する MDX クエリを実行します。 このパッケージにリンク サーバーを作成またはフラット化された行セットをクリーンアップする必要はありません。直接 R. で OLAP データを使用することができます。

この記事 API について説明します、概要と共に fo OLAP と持つ可能性がある多次元キューブ データベースに新しい R ユーザーの MDX です。

## <a name="what-is-an-olap-cube"></a>OLAP キューブとは何ですか。

OLAP はの短縮形オンライン分析処理です。 OLAP ソリューションは広くをキャプチャして、重要なビジネス データを格納する時間の経過と共に使用されます。 OLAP データは、多様なツール、ダッシュボード、視覚エフェクトでビジネス分析に使用されます。 詳細については、次を参照してください。[オンライン分析処理](https://en.wikipedia.org/wiki/Online_analytical_processing)です。

マイクロソフトが提供[Analysis Services](https://docs.microsoft.com/sql/analysis-services/analysis-services)、設計、展開、および OLAP データの形式でクエリを実行することができます_キューブ_または_表形式モデル_です。 キューブは、多次元データベースです。 _ディメンション_ディメンションを使用して、集計または分析するデータの特定のサブセットを特定するデータ、または r: の要因のファセットと似ています。 たとえば、時間は、重要なディメンション、あまり多くの OLAP ソリューションにスライスし、データの概要を作成するときに使用する、既定で定義されている複数の予定表が含まれるようにです。 

パフォーマンス上の理由から、OLAP データベースの多くの場合、集計を計算 (または_集計_) 事前、しに高速な検索を保存します。 概要がに基づいて*メジャー*、数値データに適用できる数式として表示されています。 ディメンションを使用して、データのサブセットを定義し、そのデータに対するメジャーを計算します。 たとえば、税金、特定の仕入先、年度累計の累積的な給与支払い済みの場合などの平均の輸送費を報告するのに-複数の四半期を特定の製品ラインの売上合計を計算するのにメジャーを使用するは。

MDX では、短縮形の多次元式は、キューブを照会するために使用される言語です。 MDX クエリを通常のデータが定義されている 1 つまたは複数のディメンション、および少なくとも 1 つのメジャーが含まれています、thogh MDX クエリがかなり複雑、取得しローリング ウィンドウ、累積平均または合計、百分位が含まれます。 

MDX クエリの構築を開始するときに役に立つ場合がありますの他のいくつかの用語を次に示します。

+ *スライス*1 つのディメンションからの値を使用して、キューブのサブセットを取得します。

+ *ダイス* は、複数のディメンションに対して値の範囲を指定してサブキューブを作成することです。

+ *ドリルダウン* は、概要から詳細情報に移動することです。

+ *ドリルアップ* は、集計の詳細情報から概要に移動することです。

+ *ロールアップ* は、ディメンションに関するデータを要約することです。

+ *ピボット* は、キューブまたはデータの選択を回転させることです。

このトピックでは、キューブに対するクエリの基本的な構文の例を示します。 

+ [R を使用する MDX クエリを作成する方法](../../advanced-analytics/r-services/how-to-create-mdx-queries-using-olapr.md)

## <a name="olapr-api"></a>olapR API

**olapR** パッケージでは、MDX クエリを作成する方法が 2 つサポートされています。

- **MDX ビルダーを使用します。** パッケージで R 関数を使用すると、キューブ、および設定軸とスライサーを選択して簡単な MDX クエリを生成できます。 これは、従来の OLAP ツールにアクセスできないか、MDX 言語の知識がない場合は、有効な MDX クエリを構築する簡単な方法です。

    MDX は複雑になることができますので、このメソッドを使用していないすべての MDX クエリを作成できます。 ただし、この API は、N ディメンションでスライス、ダイス、ドリルダウン、rollup、およびピボットを含む、最も一般的で便利な操作の大半をサポートします。

+ **整形式の MDX をコピー アンド ペーストします。** 手動で作成し、任意の MDX クエリに貼り付けます。 このオプションは、再利用する既存の MDX クエリがある場合、またはビルドするクエリが複雑すぎるため、最適な**olapR**を処理します。 

    SSMS や Excel などの任意のクライアント ユーティリティを使用して、MDX をビルドし、MDX クエリを定義する文字列を保存します。 この MDX 文字列に渡す引数として指定する、 *SSAS クエリ ハンドラー*で、 **olapR**パッケージです。 この関数は、指定した Analysis Services サーバーにクエリを送信し、r、もちろん、キューブをクエリする権限があると仮定した場合の結果を渡します。

MDX をビルドする方法の例では、クエリまたは既存の MDX クエリの実行を参照してください[R を使用する MDX クエリを作成する方法](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md)です。

## <a name="known-issues"></a>既知の問題

### <a name="tabular-models-not-supported"></a>表形式モデルがサポートされていません

+ Analysis Services の表形式インスタンスに接続する場合、`explore`関数の戻り値の TRUE の場合の成功をレポートします。 ただし、表形式モデル オブジェクトは、互換性のある型ではありません、ため、探索できません。

+ 表形式モデルは、DAX または MDX を使用して照会できます。 した場合、外部ツールを使用して表形式モデルに対して有効な MDX クエリをデザインし、この API にクエリを貼り付けます、クエリは、NULL の結果を返し、エラーを報告しません。

## <a name="resources"></a>リソース

OLAP や MDX クエリの初心者の場合、Wikipedia の記事「 [OLAP Cubes](https://en.wikipedia.org/wiki/OLAP_cube)
[MDX queries](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)

### <a name="samples"></a>サンプル

キューブの詳細については、Analysis Services チュートリアル「 [多次元モデリング (Adventure Works チュートリアル)](../../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)」のレッスン 4 までに従って、これらの例で使用されているキューブを作成してみてください。

また、既存のキューブをバックアップとしてダウンロードし、Analysis Services のインスタンスに復元することもできます。 たとえば、 [Adventure Works Multidimensional Model SQL 2014](http://msftdbprodsamples.codeplex.com/downloads/get/882334)用の完全に処理されたキューブを zip 形式でダウンロードし、SSAS インスタンスに復元できます。 詳細については、「 [Analysis Services データベースのバックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)」または「 [Restore-ASDatabase コマンドレット](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)」を参照してください。
