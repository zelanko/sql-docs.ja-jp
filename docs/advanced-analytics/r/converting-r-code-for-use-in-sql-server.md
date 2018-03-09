---
title: "R Services で使用するための R コードの変換 | Microsoft Docs"
ms.date: 12/20/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 0b11ab52-b2f9-4a4f-b1ab-68ba09c8adcc
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 802ad1ee49920db65eadccfb29650c649c339d48
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="converting-r-code-for-execution-in-database"></a>データベース内の実行の R コードの変換
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server で R コードを変更する方法の大まかなガイダンスを提供します。 

R Studio や他の環境から SQL Server への R コードを移動するときに最も多くの場合、コードが動作せず、さらに変更します。 たとえば、コードが単純な場合は、などいくつかを取得する関数が入力され値を返します。 使用するポート ソリューションを簡単にも、 **RevoScaleR**または**MicrosoftML**パッケージで、最小限の変更で異なる実行コンテキストで実行をサポートします。

ただし、コードでは、次のいずれかに大幅な変更が必要です可能性があります。

+ ネットワークにアクセスするか、SQL Server にインストールされていることはできません、R ライブラリを使用するとします。
+ コードでは、Excel ワークシート、共有のファイルおよびその他のデータベースなどの SQL Server の外部データ ソースに別の呼び出しを行います。 
+ コードを実行する、  *@script* のパラメーター [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)も、ストアド プロシージャのパラメーター化とします。
+ 元のソリューションには、データ準備とトレーニング、スコア付け、またはレポート モデルと特徴エンジニア リングなど個別に、実行される場合は、実稼働環境でより効率的になる可能性がある複数のステップが含まれます。
+ 向上させるために必要なライブラリを変更する、並列実行を使用して、または SQL Server にいくつかの処理をオフロードすることによってパフォーマンスを最適化します。 

## <a name="step-1-plan-requirements-and-resources"></a>手順 1. 要件とリソースを計画します。

**パッケージ**

+ どのパッケージが必要かを判断して、SQL Server で作業することを確認してください。
 
+ Machine Learning サービスによって使用される既定のパッケージのライブラリに事前にパッケージをインストールします。 ユーザーのライブラリがサポートされていません。

**[データ ソース]** 

+ R コードを埋め込む場合[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)、プライマリとセカンダリのデータ ソースを特定します。 

    + **プライマリ**データ ソースは、モデルのトレーニング データ、または予測の入力データなど、大きなデータセット。 入力パラメーターに最も大きなデータセットをマップする[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。

    + **セカンダリ**データ ソースは通常より小さいデータ セットは、要因、またはその他のグループ変数のリストなどです。 
    
    現時点では、sp_execute_external_script では、ストアド プロシージャへの入力として 1 つのデータセットのみをサポートしています。 ただし、スカラーまたはバイナリの複数の入力を追加することができます。

    入力として前に実行するストアド プロシージャ呼び出しを使用することはできません[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。 クエリ、ビュー、または有効な SELECT ステートメントを使用することができます。

+ 必要がある出力を決定します。 Sp_execute_external_script を使用して R コードを実行する場合、ストアド プロシージャでは、結果として 1 つのデータ フレームを出力できます。 ただし、プロットを含め、複数のスカラー出力を出力することもでき、パラメーターの R コード、または SQL から派生したその他のスカラー値と同様にバイナリ形式のモデル。

**データ型**

+ 起こり得るデータ型の問題のチェックリストを作成します。

    すべての R データ型は、SQL Server の machine Learning サービスによってサポートされます。 ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]大きいのさまざまなデータ型は、R をサポートしています送信するときにそのため、一部の暗黙的なデータ型変換が実行される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データから R、およびその逆です。 明示的にキャストまたは一部のデータを変換する必要があります。 

    NULL 値がサポートされます。 ただし、R を使用して、`na`は null 値に似ていますが、不足している値を表すデータ構造です。

+ R: たとえば、rowid が使用できないデータへの依存関係を排除することを考慮し、SQL Server からのデータ型の GUID が R では使用できないし、エラーを生成します。

    詳細については、次を参照してください。 [R ライブラリとデータ型](../r/r-libraries-and-data-types.md)です。

## <a name="step-2-convert-or-repackage-code"></a>手順 2. 変換するか、コードを再パッケージ化

コードを変更する量は、SQL Server のコンピューティング コンテキストで実行するリモート クライアントから R コードを送信するか、パフォーマンスが向上し、データのセキュリティを提供できる、ストアド プロシージャの一部として、コードをデプロイする予定かによって異なります。 ストアド プロシージャでコードを折り返すには、いくつかの追加要件が適用されます。 

+ 可能な限り、データ移動を回避する、SQL クエリとして、主な入力データを定義します。

+ 複数を通過できるストアド プロシージャで R を実行している、**スカラー**入力します。 出力に使用するパラメーターを追加、**出力**キーワード。 

    たとえば、次のスカラー入力`@model_name`も独自の列に、結果の出力は、モデルの名前が含まれています。

    ```SQL
    EXEC sp_execute_external_script @model_name="DefaultModel" OUTPUT, @language=N'R', @script=N'R code here'
    ``` 

+ ストアド プロシージャのパラメーターとして渡したされる変数[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) R コードでの変数にマップする必要があります。 既定では、変数は、名前によってマップされます。

    入力データセットのすべての列は、R スクリプト内の変数にもマップする必要があります。  たとえば、R スクリプトには、次のような数式が含まれています。

    ```R
    formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek
    ```
    
    入力データセットに一致する名前 ArrDelay、CRSDepTime、DayOfWeek、CRSDepHour、および曜日の列が含まれていない場合、エラーが発生します。

+ 場合によっては、出力スキーマは、結果を得るのために事前に定義する必要があります。

    たとえば、テーブルにデータを挿入するにする必要がありますを使用して、**結果のセット**句をスキーマを指定します。

    出力スキーマは、R スクリプトは、引数を使用している場合にも必要`@parallel=1`です。 理由は、クエリを並列で実行するために SQL Server が複数のプロセスを作成し、最後に結果を収集する可能性があるためです。 したがって、並列処理を作成するには、出力スキーマを準備する必要があります。
    
    オプションを使用して結果のスキーマを省略した場合に、**で RESULT SETS UNDEFINED**です。 このステートメントは、列の名前付けや SQL データ型を指定することがなく、R スクリプトからデータセットを返します。

+ R. ではなく、T-SQL を使用するタイミングまたは追跡のデータの生成を検討してください。

    たとえば、システム時刻または R スクリプトで類似データを生成するのではなく、結果にを通じて渡される T-SQL 呼び出しを追加することによって監査と記憶域に使用されるその他の情報を渡す可能性があります。 

**パフォーマンスとセキュリティを向上します。**

+ 予測またはファイルへの中間結果を記述しないでください。 データ移動を回避する代わりに、テーブルに予測を作成します。

+ 事前にすべてのクエリを実行し、並列で実行できるタスクを識別する SQL Server クエリ プランを確認します。

    入力クエリが並列化できる場合は、設定`@parallel=1`に渡す引数の一部として[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。 

    このフラグによる並列処理は、SQL Server がパーティション分割されたテーブルを操作できるか、クエリを複数のプロセスに分散して最後に結果を集計できるときは、通常はいつでも実行できます。 このフラグによる並列処理は、すべてのデータを読み取る必要があるアルゴリズムを使用するモデルをトレーニングする場合、または集計を作成する必要がある場合は、通常は実行できません。

+ R コードを見直して、別のストアド プロシージャの呼び出しを使用して単独で実行できる手順またはより効率的に実行できる手順があるかどうかを判断します。 たとえばとは別に、特徴エンジニア リングまたは特徴抽出を行うと、テーブルに値を保存してパフォーマンスを向上させるを取得する可能性があります。

+ セットベースの計算用の R コードではなく、T-SQL を使用する方法を模索します。

    たとえば、この R ソリューションの T-SQL で関数のユーザー定義方法を示しています、R が同じ機能のエンジニア リング タスクを実行できます:[データ サイエンスのエンド ツー エンド チュートリアル](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)です。

+ 可能であればを持つ従来の R 関数を置き換える**ScaleR**分散実行をサポートする関数。 詳細については、次を参照してください。[ベース R の比較と R 関数の小数点以下桁数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler-compared-to-base-r)です。

+ SQL Server の機能を使用して、パフォーマンスを向上させる方法を決定する、データベース開発者に相談[メモリ最適化テーブル](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables)、または Enterprise Edition を使用していれば[リソース ガバナー](https://docs.microsoft.com/sql/relational-databases/resource-governor/resource-governor))。

    詳細については、次を参照してください[分析サービスの SQL Server の最適化ヒントとテクニック。](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

### <a name="step-3-prepare-for-deployment"></a>手順 3. 展開を準備します。

+ 管理者に通知して、コードを展開する前にパッケージをインストールして事前にテストできるようにしてください。 

    開発環境で、コードの一部としてパッケージをインストールするよい場合がありますが、実稼働環境では、不適切なプラクティスです。 

    ユーザーのライブラリはサポートされていません、ストアド プロシージャを使用するか、SQL Server のコンピューティング コンテキストで R コードを実行するかに関係なく。

**ストアド プロシージャで R コードをパッケージ化します。**

+ コードが比較的単純な場合に埋め込んだりできます、改変の有無 T-SQL は、ユーザー定義関数でこれらのサンプル」の説明に従って。

    + [RxExec で実行されている R 関数を作成します。](..\tutorials\deepdive-create-a-simple-simulation.md)
    + [T-SQL と R を使用して特徴エンジニア リング](..\tutorials\sqldev-create-data-features-using-t-sql.md)

+ コードがより複雑な場合は、R パッケージを使用して**sqlrutils**コードに変換します。 経験豊富な R ユーザーの適切なストアド プロシージャのコードの記述には、このパッケージは設計されています。 

    最初の手順では、明確に定義された入力と出力と 1 つの関数として、R コードを書き直してください。

    次に、使用、 **sqlrutils**正しい形式で入力と出力を生成するパッケージ。 **Sqlrutils**パッケージは、ストアド プロシージャの完全なコードを生成し、データベースでストアド プロシージャを登録することもできます。 

    詳細と例については、次を参照してください。 [SqlRUtils](../r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)です。

**他のワークフローとの統合します。**

+ ETL プロセスの T-SQL でツールを活用できます。 特徴エンジニア リング、特徴を抽出、およびデータのワークフローの一部としてデータ クレンジングを事前に実行します。

    している専用の R 開発環境でなど[!INCLUDE[rsql_rtvs_md](../../includes/rsql-rtvs-md.md)]または RStudio、する可能性がありますをコンピューターにデータをプル、データの分析を繰り返し、書き込むしたり結果を表示します。 
    
    ただし、スタンドアロン R コードを SQL Server に移行すると、このプロセスの多くする簡略化したり、他の SQL Server のツールに委任できます。 

+ セキュリティで保護された、非同期の視覚エフェクトの戦略を使用します。

    多くの場合、SQL Server のユーザーは、サーバー上のファイルにアクセスできないし、SQL クライアント ツールは通常、R のグラフィックス デバイスをサポートしています。 ソリューションの一部としてプロットやその他のグラフィックスを生成する場合は、バイナリ データとして、プロットをエクスポートして、テーブルへの保存または書き込みを検討してください。

+ アプリケーションで直接アクセスするためのストアド プロシージャで予測およびスコアリングの関数をラップします。

### <a name="other-resources"></a>その他のリソース

SQL Server で R ソリューションを展開する方法の例については、これらのサンプルを参照してください。

+ [R と SQL Server を使用して ski レンタル ビジネスの予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [データベース内の分析、SQL 開発者の](../tutorials/sqldev-in-database-r-for-sql-developers.md)ように方法について説明することができます、R コード モジュール化が進んでストアド プロシージャ内にラップして、

+ [エンド ツー エンドのデータ サイエンス ソリューション](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)R と T-SQL で特徴エンジニア リングの比較が含まれています
