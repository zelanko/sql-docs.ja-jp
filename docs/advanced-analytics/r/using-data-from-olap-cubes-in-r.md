---
title: "R での OLAP キューブからのデータの使用 | Microsoft Docs"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 8093599c-8307-4237-983b-0908d0f8ab77
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: bdd86896b43d79b5d7cd00383476700735accff4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="using-data-from-olap-cubes-in-r"></a>R での OLAP キューブからのデータの使用

**olapR** パッケージは、Microsoft R Server と SQL Server R サービスで提供されている新しい R パッケージです。R ソリューションで MDX クエリを実行し、OLAP キューブのデータを使用することができます。

このパッケージでは、リンクされたサーバーを作成したり、フラット化行セットをクリーンアップしたりする必要がありません。OLAP データを R で直接使用できます。

## <a name="overview"></a>概要

OLAP キューブは、 *メジャー*について事前に計算された集計を含む多次元データベースです。通常、売上高、売上数などの数値の重要なビジネス メトリックをキャプチャするために使用されます。 OLAP キューブは、長期間にわたって重要なビジネス データをキャプチャし、格納するために幅広く使用されています。 OLAP データは、多様なツール、ダッシュボード、視覚エフェクトでビジネス分析に使用されます。 詳細については、「 [Online analytical processing](https://en.wikipedia.org/wiki/Online_analytical_processing)」(オンライン分析処理) を参照してください。

**olapR** パッケージでは、MDX クエリを作成する方法が 2 つサポートされています。 

- 単純な MDX クエリを生成する場合は、R-style API を使用してキューブ、軸、スライサーを選択します。 この関数を使用すると、従来の OLAP ツールにアクセスできない場合や、MDX 言語を深く理解していない場合でも、有効な MDX クエリを構築できます。

  MDX は複雑な場合があるので、 **olapR** パッケージのこのメソッドを使用して作成できない MDX クエリもあります。 ただし、olapR パッケージは、N ディメンションのスライス、ダイス、ドリルダウン、ロールアップ、ピボットなど、最も一般的で便利な操作をすべてサポートしています。

+ 手動で作成し、任意の MDX クエリに貼り付けることができます。 このオプションは、再利用する既存の MDX クエリがある場合、または構築するクエリが複雑すぎて **olapR** で処理できない場合に便利です。 

  このアプローチでは、SSMS や Excel などのクライアント ユーティリティを使用して MDX を構築してから、このパッケージで提供されている *SSAS クエリ ハンドラー* に対する文字列引数として使用します。 **olapR** 関数から指定された Analysis Services サーバーに対してクエリが送信され、結果が R に戻されます。

MDX クエリを構築する方法や既存の MDX クエリを実行する方法例については、「 [How to Create MDX Queries using R](../../advanced-analytics/r-services/how-to-create-mdx-queries-using-olapr.md)」(R を使用して MDX クエリを作成する方法) を参照してください。


## <a name="mdx-basics"></a>MDX の基本

キューブのデータを取得するには、MDX (MultiDimensional Expression) クエリ言語を使用します。 OLAP キューブ (または Analysis Services データベース) のデータが表形式ではなく多次元の場合、MDX は、データのフィルターとスライスに使用できる複雑な構文と多様な操作をサポートしています。

+ *スライス* は、1 ディメンションの値を選択してキューブのサブセットを取り出すことです。結果としてキューブは 1 ディメンションだけ小さくなります。 

+ *ダイス* は、複数のディメンションに対して値の範囲を指定してサブキューブを作成することです。

+ *ドリルダウン* は、概要から詳細情報に移動することです。

+ *ドリルアップ* は、集計の詳細情報から概要に移動することです。

+ *ロールアップ* は、ディメンションに関するデータを要約することです。

+ *ピボット* は、キューブまたはデータの選択を回転させることです。

このトピックでは、キューブに対してクエリを実行するための基本的な構文例を紹介します。
[R を使って MDX クエリを作成する方法](../../advanced-analytics/r-services/how-to-create-mdx-queries-using-olapr.md)


## <a name="known-issues"></a>既知の問題

### <a name="tabular-models-not-supported-currently"></a>現在、表形式モデルはサポートされていません

Analysis Services の表形式インスタンスに接続することができて、 `explore` 関数から TRUE の戻り値で成功が報告されますが、表形式モデル オブジェクトは互換性のある種類ではないため、探索できません。 

表形式モデルは MDX クエリをサポートしていますが、表形式モデルに対する有効な MDX クエリからは NULL の結果が返され、エラーは報告されません。

## <a name="resources"></a>リソース

OLAP や MDX クエリの初心者の場合、Wikipedia の記事「 [OLAP Cubes](https://en.wikipedia.org/wiki/OLAP_cube)
[MDX queries](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)

### <a name="samples"></a>サンプル

キューブの詳細については、Analysis Services チュートリアル「 [多次元モデリング (Adventure Works チュートリアル)](../../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)」のレッスン 4 までに従って、これらの例で使用されているキューブを作成してみてください。

また、既存のキューブをバックアップとしてダウンロードし、Analysis Services のインスタンスに復元することもできます。 たとえば、 [Adventure Works Multidimensional Model SQL 2014](http://msftdbprodsamples.codeplex.com/downloads/get/882334)用の完全に処理されたキューブを zip 形式でダウンロードし、SSAS インスタンスに復元できます。 詳細については、「 [Analysis Services データベースのバックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)」または「 [Restore-ASDatabase コマンドレット](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)」を参照してください。

## <a name="see-also"></a>参照
[R を使って MDX クエリを作成する方法](../../advanced-analytics/r-services/how-to-create-mdx-queries-using-olapr.md)

[Analysis Services の MDX クエリ デザイナーのユーザー インターフェイス (レポート ビルダー)](http://msdn.microsoft.com/library/7e288eee-2d37-485e-a6a0-dbba5e041e26)



