---
title: "R Services で使用するための R コードの変換 | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 06/29/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 0b11ab52-b2f9-4a4f-b1ab-68ba09c8adcc
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d403b716d6be6c571f4de76a25ba3f6f7f5c4e8d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="converting-r-code-for-use-in-r-services"></a>R Services で使用するための R コードの変換

SQL Server に R Studio や他の環境から R コードを移動するときに多くの場合、コードの動作に追加するとさらに変更せず、  *@script* のパラメーター [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。 使用してソリューションを開発している場合は特に、 **RevoScaleR**関数、比較的簡単に実行コンテキストを変更します。

ただし、通常は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との緊密な統合を活用することとデータの高コストの転送を避けることの両方を目的として、SQL Server で実行する R コードを変更します。

SQL Server での R コードの実行方法の例を確認するには、次のチュートリアルを参照してください。

+ [データベース内の分析、SQL 開発者の](../tutorials/sqldev-in-database-r-for-sql-developers.md)ように方法について説明することができます、R コード モジュール化が進んでストアド プロシージャ内にラップして、

+ [エンド ツー エンドのデータ サイエンス ソリューション](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)R と T-SQL で特徴エンジニア リングの比較が含まれています

## <a name="how-the-data-science-process-changes-in-sql-server"></a>SQL Server で、データ サイエンス プロセスの変更

している専用の R 開発環境でなど[!INCLUDE[rsql_rtvs_md](../../includes/rsql-rtvs-md.md)]RStudio、一般的なワークフローは、コンピューターにデータをプル、繰り返し、データの分析、書き込むまたは結果を表示するか。 ただし、スタンドアロン R コードを SQL Server に移行すると、このプロセスの多くする簡略化したり、他の SQL Server のツールに委任できます。 さらに、そのためパフォーマンスが向上多くの場合。

| 外部コード | SQL Server での R |
|-------|-------|
| データを取り込む| SQL クエリとして、入力データを定義します。 データ移動を回避します。 |
| データを集計して視覚化する| プロットのイメージとしてエクスポートまたはリモート ワークステーションに送信されることができます。|
|機能エンジニアリング| コードの変更が、クエリの最適化を見てしたくない場合は、データベース内に R を使用します。 T-SQL 関数またはカスタムの Udf の呼び出しにより効率的に可能性があるかどうかを調査します。|
|分析プロセスのデータ クレンジング部分| 特徴エンジニア リング、特徴を抽出、およびデータのワークフローの一部としてデータ クレンジングを事前に実行します。|
|ファイルへの出力予測| データ移動を回避するテーブルの予測を出力します。 Wrap では、アプリケーションで直接アクセスするためのストアド プロシージャ内の関数を予測します。|

## <a name="best-practices"></a>ベスト プラクティス

+ 必要なパッケージなどの依存関係のメモを事前に作成します。 開発/テスト環境では、パッケージをコードの一部としてインストールしても問題はないかもしれませんが、これは運用環境では不適切な行為です。 管理者に通知して、コードを展開する前にパッケージをインストールして事前にテストできるようにしてください。

+ 起こり得るデータ型の問題のチェックリストを作成します。 コードの各セクションで予想される結果のスキーマを文書化します。

+ モデルのトレーニング データや予測用の入力データなどのプライマリ データ ソースと、要因や追加のグループ化変数などのセカンダリ ソースを識別します。 最も大きなデータセットを、[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) の入力パラメーターにマップします。

+ 入力データのステートメントを、データベース内で直接動作するように変更します。 なく、ローカルの CSV ファイルにデータを移動または作成は、ODBC 呼び出しを繰り返し、することができますパフォーマンスを向上させる SQL クエリまたは、データベースに対して直接実行できるビューを使用してデータの移動を回避します。

+ SQL Server クエリ プランを使用して、並列で実行できるタスクを識別します。 入力クエリが並列化できる場合は、設定`@parallel=1`に渡す引数の一部として[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。 このフラグによる並列処理は、SQL Server がパーティション分割されたテーブルを操作できるか、クエリを複数のプロセスに分散して最後に結果を集計できるときは、通常はいつでも実行できます。

  このフラグによる並列処理は、すべてのデータを読み取る必要があるアルゴリズムを使用するモデルをトレーニングする場合、または集計を作成する必要がある場合は、通常は実行できません。

+ 可能であれば、従来の R 関数を、分散実行をサポートする **ScaleR** 関数に置き換えます。 詳細については、次を参照してください。[ベース R の比較と R 関数の小数点以下桁数](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler-compared-to-base-r)です。

+ R コードを見直して、別のストアド プロシージャの呼び出しを使用して単独で実行できる手順またはより効率的に実行できる手順があるかどうかを判断します。 たとえば、機能エンジニアリングや機能抽出を別々に実行し、値を新しい列に追加することができます。 

  セットベースの計算用の R コードではなく、T-SQL を使用します。 機能のエンジニア リング タスク Udf と R を比較する R ソリューションの例は、次を参照してください。[データ サイエンスのエンド ツー エンド チュートリアル](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)です。

+ R パッケージを使用して**sqlrutils**コードを明確に定義された入力と出力で、ストアド プロシージャのパラメーターに簡単にマップできる 1 つの関数に変換します。 詳細と例については、次を参照してください。 [SqlRUtils](../r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)です。


## <a name="restrictions"></a>制限

 R コードを変換するときは、次の制限事項に留意してください。

### <a name="data-types"></a>データ型

-   すべての R データ型がサポートされます。 ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は R よりも多くの種類のデータ型をサポートするため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータを R に送信するときに (逆の場合も)、暗黙的なデータ型変換が実行されます。 明示的にキャストまたは一部のデータを変換する必要もあります。

- NULL 値がサポートされます。 R の使用、`na`は null 値に似ていますが、不足している値を表すデータ構造です。

詳細については、次を参照してください。 [R ライブラリとデータ型](../r/r-libraries-and-data-types.md)です。

### <a name="inputs-and-outputs"></a>[スクリプト変換エディター]

+ ストアド プロシージャのパラメーターの一部として、入力データセットを 1 つだけ定義できます。 ストアド プロシージャに対するこの入力クエリには、有効な 1つの SELECT ステートメントを指定できます。 最大のデータセットでは、この入力を使用し、RODBC への呼び出しを使用して、必要に応じて、小規模なデータセットの取得することをお勧めします。

+ 入力として前に実行するストアド プロシージャ呼び出しを使用することはできません[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。

+ 入力データセット内のすべての列は、R スクリプトの変数にマップする必要があります。 変数は、名前によって自動的にマップされます。 たとえば、R スクリプトには、次のような数式が含まれています。
    
    ```R
    formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek
    ```
    
     入力データセットに一致する名前 ArrDelay、CRSDepTime、DayOfWeek、CRSDepHour、および曜日の列が含まれていない場合、エラーが発生します。

+ 入力として複数のスカラー パラメーターを指定することもできます。 ただし、ストアド プロシージャ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) のパラメーターとして渡す変数は、R コードの変数にマップされる必要があります。 既定では、変数は、名前によってマップされます。

+ スカラー入力変数を R コードの出力に含めるには、変数を定義するときに **OUTPUT** キーワードを追加するだけです。

+ [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では、R コードの動作は、単一のデータセットを data.frame オブジェクトとして出力することに制限されてます。 ただし、バイナリ形式のプロットと varbinary 形式のモデル化を含む複数のスカラー出力も出力できます。

+ 通常、R スクリプトによって返されるデータセットは、WITH RESULT SETS UNDEFINED オプションを使用することで、出力列の名前を指定せずに出力できます。 ただし、出力する R スクリプトのすべての変数は、SQL の出力パラメーターにマップされる必要があります。

+ R スクリプトで `@parallel=1` 引数を使用する場合は、出力スキーマを定義する必要があります。 理由は、クエリを並列で実行するために SQL Server が複数のプロセスを作成し、最後に結果を収集する可能性があるためです。 したがって、並列処理を作成する前に、出力スキーマを定義しなければなりません。

### <a name="dependencies"></a>依存関係

 + R コードからパッケージをインストールすることは避けてください。 SQL Server にパッケージを事前にインストールしてください。
 
  Machine Learning サービスによって使用される既定のパッケージのライブラリにパッケージをインストールすることを確認します。 詳細については、次を参照してください[for SQL Server の R パッケージの管理。](../r/r-package-management-for-sql-server-r-services.md)
