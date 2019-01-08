---
title: データ処理タスクのコードを生成します。
titleSuffix: Azure Data Studio
description: この記事では、Azure Data Studio で自動的に共通のデータ処理タスクのコードを生成する、PROSE コード アクセラレータを使用する方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: a42820199c2a481e490b510e3fd00f9dc765cb27
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030523"
---
# <a name="data-wrangling-using-prose-code-accelerator"></a>PROSE コード アクセラレータを使用してデータ Wrangling

PROSE コード アクセラレータは、データ処理タスクの読み取り可能な Python コードを生成します。 Azure Data Studio 内で、notebook での作業中に、シームレスな方法で手作業で記述されたコードで生成されたコードを複数使用できます。 この記事では、コードのアクセラレータを使用する方法の概要を示します。

 > [!NOTE]
 > プログラム Synthesis using Examples、PROSE とも呼ばれる、AI を使用して、人間が判読できるコードを生成する Microsoft テクノロジです。 これは、ユーザーの意図だけでなくデータの分析、いくつかの候補プログラムを生成および順位付けアルゴリズムを使用して最適なプログラムを選択します。 PROSE テクノロジについて詳しく知るには、次を参照してください。、 [PROSE ホームページ](https://microsoft.github.io/prose/)します。

コードのアクセラレータは、Azure Data Studio プレインストールされています。 ノートブックの他の Python パッケージと同様にインポートできます。 慣例により、インポートします略して cx として。

```python
import prose.codeaccelerator as cx
```

現在のリリースでコード アクセラレータは、次のタスクの Python コードをインテリジェントに生成できます。

- Pandas をデータ ファイルの読み取りまたは Pyspark データ フレーム。
- データ フレームには、データ型を修正します。
- 文字列のリスト内のパターンを表す正規表現を検索します。

メソッドのコードのアクセラレータの概要を取得するを参照してください。、[ドキュメント](https://aka.ms/prose-codeaccelerator-overview)します。

## <a name="reading-data-from-a-file-to-a-dataframe"></a>ファイルからデータ フレームにデータの読み取り

多くの場合、データ フレームにファイルの読み取りは、ファイルの内容を見ると、適切なデータ読み込みのライブラリに渡すパラメーターを決定する必要があります。 ファイルの複雑さに応じて、適切なパラメーターを識別するいくつかのイテレーションが必要があります。

PROSE コード アクセラレータは、データ ファイルの構造を分析し、ファイルを読み込むためのコードを自動的に生成するこの問題を解決します。 ほとんどの場合、生成されたコードでは、データが正しく解析します。 いくつかの場合は、ニーズに合わせてコードを調整する必要があります。

次に例を示します。

 ```python
import prose.codeaccelerator as cx

# Call the ReadCsvBuilder builder to analyze the file content and generate code to load it
builder = cx.ReadCsvBuilder(r'C:/911.txt')

#Set target to pyspark if generating code to use pyspark library
#builder.Target = "pyspark"

#Get the code generated to fix the data types
builder.learn().code()
 ```

前のコード ブロックは、区切られたファイルの読み取りには、次の python コードを出力します。 どの PROSE を自動的に判別ヘッダー、quotechars、区切り記号をスキップする行の数に注意してください。

 ```python
import pandas as pd

def read_file(file):
    names = ["lat",
             "lng",
             "desc",
             "zip",
             "title"]

    df = pd.read_csv(file,
        skiprows = 11,
        header = None,
        names = names,
        quotechar = "\"",
        delimiter = "|",
        index_col = False,
        dtype = str,
        na_values = [],
        keep_default_na = False,
        skipinitialspace = True)
    return df
 ```

コードのアクセラレータには、負荷の区切られた、JSON、およびデータ フレームに固定長ファイルにコードを生成できます。 固定長のファイルを読み取るため、`ReadFwfBuilder`必要に応じて列の位置を取得することを解析できる人間が判読できるスキーマ ファイルを受け取る。 詳細についてを参照してください、[ドキュメント](https://aka.ms/prose-codeaccelerator-docs)します。

## <a name="fixing-data-types-in-a-dataframe"></a>データ フレームのデータ型を解決します。

Pandas を使用して一般的なまたは正しくないデータ型を持つ pyspark データ フレーム。 いくつか非準拠のための多くの場合、この動作の列の値。 その結果、整数は float 型または文字列として読み取られ、日付が文字列として読み取られます。 データ型を手動で修正するための労力では、列の数に比例します。

使用することができます、`DetectTypesBuilder`このような場合。 データを分析し、ブラック ボックス的にデータ型を修正してではなく、データ型を修正するためのコードを生成します。 コードは、開始点として機能します。 確認し、使用、または必要に応じて変更できます。

```python
import prose.codeaccelerator as cx

builder = cx.DetectTypesBuilder(df)

#Set target to pyspark if working with pyspark
#builder.Target = "pyspark"

#Get the code generated to fix the data types
builder.learn().code()
```

詳細についてを参照してください、[ドキュメント](https://aka.ms/prose-codeaccelerator-fixtypes)します。

## <a name="identifying-patterns-in-strings"></a>文字列内のパターンを識別します。

もう 1 つの一般的なシナリオは、クリーニングまたはグループ化するために文字列型の列のパターンを検出します。 たとえば、複数の異なる形式で日付を含む日付列があります。 値を標準化するために正規表現を使用して条件付きステートメントを記述する場合があります。


|   |名前                      |BirthDate      |
|---|:-------------------------|:--------------|
| 0 |Bertram du Plessis        |1995           |
| 1 |Naiara Moravcikova        |Unknown        |
| 2 |Jihoo Spel                |2014           |
| 3 |Viachaslau Gordan Hilario |67-22-年 4 月      |
| 4 |Maya de Villiers          |19 ~ 3 月 3 日-60      |

、、のボリュームとデータでの多様性によっては、列のさまざまなパターンの正規表現を記述すると非常に時間がかかるタスクがあります。 `FindPatternsBuilder`は文字列の一覧については正規表現を生成することによって、上記の問題を解決する強力なコードの高速化ツールです。

```python
import prose.codeaccelerator as cx

builder = cx.FindPatternsBuilder(df['BirthDate'])

#Set target to pyspark if working with pyspark
#builder.Target = "pyspark"

builder.learn().regexes
```

によって生成された正規表現をここでは、`FindPatternsBuilder`上のデータ。

```
^[0-9]{2}-[A-Z][a-z]+-[0-9]{2}$
^[0-9]{2}[\s][A-Z][a-z]+[\s][0-9]{4}$
^[0-9]{4}$
^Unknown$
```

正規表現を生成するとは別に`FindPatternsBuilder`生成された正規表現に基づく値をクラスター化するためのコードを生成することもできます。 列内のすべての値が生成された正規表現に準拠していることをアサートことできますも。 詳細およびその他の有用なシナリオを参照してください、次を参照してください。、[ドキュメント](https://aka.ms/prose-codeaccelerator-findpatterns)します。
