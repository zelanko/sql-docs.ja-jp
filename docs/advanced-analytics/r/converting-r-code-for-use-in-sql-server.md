---
title: ストアド プロシージャ - SQL Server Machine Learning Services の R コードを変換します。
description: SQL Server のリレーショナル データへのソリューションの配置とデータ アクセス用の SQL Server ストアド プロシージャに R コードを移行します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: a3348058b03ff1441256cc8298ddc1b5b2216b0d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642785"
---
# <a name="convert-r-code-for-execution-in-sql-server-in-database-instances"></a>SQL Server (In-database) のインスタンスで実行される R コードを変換します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server で R コードを変更する方法の大まかなガイダンスを提供します。 

R Studio または別の環境から SQL Server に R コードを移動するときに最も多くの場合、コードの動作変更なし: など、コードが単純な場合などいくつかを受け取る関数の入力し、値を返します。 使用するポートのソリューションを簡単にも、 **RevoScaleR**または**MicrosoftML**パッケージで、最小限の変更で異なる実行コンテキストで実行をサポートします。

ただし、次のいずれかの場合、コードは大幅な変更を必要があります。

+ ネットワークにアクセスするか、SQL Server をインストールすることはできません、R ライブラリを使用するとします。
+ コードは、Excel ワークシート、共有のファイルおよびその他のデータベースなど、SQL Server の外部データ ソースに個別の呼び出しです。 
+ コードを実行する、 *@script*パラメーターの[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)もストアド プロシージャをパラメーター化します。
+ 元のソリューションには、データの準備やトレーニング、スコア付け、またはレポート モデルと特徴エンジニア リングなど、独立して実行する場合は、運用環境でより効率的になる可能性がある複数のステップが含まれています。
+ 強化するライブラリを変更する、並列実行を使用して、または SQL Server にいくつかの処理をオフロードしてパフォーマンスを最適化します。 

## <a name="step-1-plan-requirements-and-resources"></a>手順 1. 要件とリソースを計画します。

**パッケージ**

+ どのパッケージが必要です。 を決定し、SQL Server で動作することを確認します。
 
+ Machine Learning サービスで使用される既定のパッケージ ライブラリ、事前にパッケージをインストールします。 ユーザー ライブラリがサポートされていません。

**[データ ソース]** 

+ R コードを埋め込む場合[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)、プライマリとセカンダリのデータ ソースを特定します。 

    + **プライマリ**データ ソースは、モデルのトレーニング データや予測の入力データなどの大規模なデータセット。 入力パラメーターに、最も大きなデータセットをマップする[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。

    + **セカンダリ**データ ソースは、要因や追加のグループ化変数のリストなどの小規模な通常のデータ セット。 
    
    現時点では、sp_execute_external_script では、ストアド プロシージャへの入力として 1 つのデータセットのみをサポートしています。 ただし、スカラーまたはバイナリの複数の入力を追加することができます。

    EXECUTE に先行するストアド プロシージャ呼び出しへの入力として使用することはできません[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。 クエリ、ビュー、または有効な SELECT ステートメントを使用することができます。

+ 必要な出力を決定します。 Sp_execute_external_script を使用して R コードを実行する場合、ストアド プロシージャでは、結果として 1 つだけのデータ フレームを出力できます。 ただし、プロットを含む複数のスカラー出力を出力することもでき、パラメーターの R コード、または SQL から派生したその他のスカラー値と同様に、バイナリ形式でのモデル。

**データ型**

+ 起こり得るデータ型の問題のチェックリストを作成します。

    すべての R データ型は、SQL Server machine Learning Services でサポートされます。 ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] R. よりも大きい各種のデータ型をサポートしています送信するときにそのため、一部の暗黙的なデータ型変換が実行される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データから R、およびその逆です。 明示的にキャストまたは一部のデータを変換する必要があります。 

    NULL 値がサポートされます。 ただし、R を使用して、`na`を null に似ていますが、欠損値を表すデータ構造。

+ R: たとえば、rowid が使用できないデータへの依存関係を排除することを検討し、SQL Server からのデータ型の GUID は、R で使用されることはできませんし、エラーが発生します。

    詳細については、次を参照してください。 [R ライブラリとデータ型](../r/r-libraries-and-data-types.md)します。

## <a name="step-2-convert-or-repackage-code"></a>手順 2. 変換するか、コードを再パッケージ化

コードを変更する量は、SQL Server 計算コンテキストで実行するリモート クライアントから R コードを送信するか、パフォーマンスが向上し、データのセキュリティを提供するストアド プロシージャの一部として、コードをデプロイするかどうかによって異なります。 いくつか追加の要件は、ストアド プロシージャにコードをラップします。 

+ 可能な限り、データの移動を回避するためには、SQL クエリとして、プライマリの入力データを定義します。

+ 複数を通過できるストアド プロシージャで R を実行するときに**スカラー**入力します。 出力で使用するパラメーターを追加、**出力**キーワード。 

    たとえば、次のスカラー入力`@model_name`も出力結果に独自の列では、モデルの名前が含まれています。

    ```sql
    EXEC sp_execute_external_script @model_name="DefaultModel" OUTPUT, @language=N'R', @script=N'R code here'
    ``` 

+ ストアド プロシージャのパラメーターとして渡す変数[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) R コードの変数にマップする必要があります。 既定では、変数は、名前によってマップされます。

    入力データセットのすべての列は、R スクリプトの変数にもマップする必要があります。  たとえば、R スクリプトには、次のような数式が含まれています。

    ```R
    formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek
    ```
    
    入力データセットに一致する名前 ArrDelay、CRSDepTime、DayOfWeek、CRSDepHour、および DayOfWeek の列が含まれていない場合は、エラーが発生します。

+ 場合によっては、出力スキーマは、結果を得るのために事前に定義する必要があります。

    たとえば、テーブルにデータを挿入するにする必要がありますを使用して、**結果のセット**スキーマを指定する句。

    出力のスキーマは、R スクリプトの引数を使用している場合にも必要`@parallel=1`します。 理由は、クエリを並列で実行するために SQL Server が複数のプロセスを作成し、最後に結果を収集する可能性があるためです。 そのため、並列処理を作成するには、出力スキーマを準備する必要があります。
    
    それ以外の場合、オプションを使用して、結果のスキーマを省略できます**で RESULT SETS UNDEFINED**します。 このステートメントは、列の名前を付け、または SQL データ型を指定することがなく、R スクリプトからデータセットを返します。

+ R. ではなく T-SQL を使用してタイミングまたは追跡データの生成を検討してください。

    たとえば、システム時刻など、R スクリプトのようなデータを生成するのではなく、結果に渡される T-SQL の呼び出しを追加で監査とストレージの使用の情報を渡すこともできます。 

**パフォーマンスとセキュリティを向上します。**

+ 予測またはファイルへの中間結果を記述しないでください。 テーブルにデータの移動を回避する代わりに、予測を書き込みます。

+ 事前に、すべてのクエリを実行し、並列で実行できるタスクを識別するために SQL Server クエリ プランを確認します。

    入力クエリを並列に処理できる場合は、設定`@parallel=1`に渡す引数の一部として[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。 

    このフラグによる並列処理は、SQL Server がパーティション分割されたテーブルを操作できるか、クエリを複数のプロセスに分散して最後に結果を集計できるときは、通常はいつでも実行できます。 このフラグによる並列処理は、すべてのデータを読み取る必要があるアルゴリズムを使用するモデルをトレーニングする場合、または集計を作成する必要がある場合は、通常は実行できません。

+ R コードを見直して、別のストアド プロシージャの呼び出しを使用して単独で実行できる手順またはより効率的に実行できる手順があるかどうかを判断します。 たとえばとは別に、特徴エンジニア リングや特徴の抽出を行うと、テーブルに値を保存してパフォーマンスを向上させるを取得可能性があります。

+ セットベースの計算用 R コードではなく T-SQL を使用する方法を探します。

    この R ソリューションは、T-SQL 関数のユーザー定義方法を示しています。 して、R は、同じ機能エンジニア リング タスクを実行できます。[データ サイエンスのエンド ツー エンド チュートリアル](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)します。

+ 可能であれば、従来の R 関数を置き換える**ScaleR**分散的実行をサポートする関数。 詳細については、次を参照してください。[比較の基本 R と R の機能をスケール](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler-compared-to-base-r)します。

+ SQL Server の機能を使用して、パフォーマンスを向上させる方法を決定する、データベース開発者にご相談[メモリ最適化テーブルで](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables)、または Enterprise Edition がある場合[リソース ガバナー](https://docs.microsoft.com/sql/relational-databases/resource-governor/resource-governor))。

    詳細については、次を参照してください[分析サービスの SQL Server の最適化のヒントとテクニック。](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

### <a name="step-3-prepare-for-deployment"></a>手順 3. 展開を準備します。

+ 管理者に通知して、コードを展開する前にパッケージをインストールして事前にテストできるようにしてください。 

    開発環境で、コードの一部としてパッケージをインストールできることが考えられますが、これは、運用環境での不適切な手法。 

    ストアド プロシージャを使用するか、SQL Server 計算コンテキストで R コードを実行するかに関係なく、このユーザー ライブラリがサポートされているいません。

**ストアド プロシージャで R コードをパッケージ化します。**

+ コードが比較的単純な場合は、埋め込むことができます、変更を加えなければ、T-SQL ユーザー定義関数でこれらのサンプル」の説明に従って。

    + [RxExec で実行されている R 関数を作成します。](../tutorials/deepdive-create-a-simple-simulation.md)
    + [T-SQL と R を使用して特徴エンジニア リング](../tutorials/sqldev-create-data-features-using-t-sql.md)

+ コードがより複雑な場合は、R パッケージを使用して、 **sqlrutils**コードを変換します。 このパッケージは、経験豊富な R ユーザーが適切なストアド プロシージャのコードを記述するように設計されています。 

    最初の手順では、明確に定義された入力と出力の 1 つの関数として、R コードを書き直してください。

    次に、使用、 **sqlrutils**正しい形式で入力と出力を生成するパッケージ。 **Sqlrutils**パッケージは、ストアド プロシージャの完全なコードを生成し、データベースでストアド プロシージャを登録することもできます。 

    詳細と例については、次を参照してください。 [sqlrutils (SQL)](ref-r-sqlrutils.md)します。

**他のワークフローとの統合します。**

+ T-SQL のツールと ETL プロセスを活用します。 特徴エンジニア リング、特徴の抽出、およびデータのワークフローの一部として事前にデータのクレンジングを実行します。

    で作業している専用の R 開発環境など[!INCLUDE[rsql_rtvs_md](../../includes/rsql-rtvs-md.md)]または RStudio、する可能性がありますをコンピューターにデータをプル、繰り返し、データを分析し、書き出すまたは結果が表示されます。 
    
    ただし、スタンドアロン R コードが SQL Server に移行されると、このプロセスの多くが簡素化したり、他の SQL Server ツールに委任します。 

+ セキュリティで保護された、非同期の視覚エフェクトの戦略を使用します。

    多くの場合、SQL Server のユーザーは、サーバー上のファイルにアクセスできないし、SQL クライアント ツールは通常、R グラフィックス デバイスをサポートしています。 ソリューションの一部としてプロットやその他のグラフィックスを生成する場合は、バイナリ データとして、プロットをエクスポートして、テーブルへの保存または書き込みを検討してください。

+ アプリケーションで直接アクセスするためのストアド プロシージャで予測およびスコアリング関数をラップします。

### <a name="other-resources"></a>その他のリソース

SQL Server で R ソリューションを展開する方法の例については、これらのサンプルを参照してください。

+ [R と SQL Server を使用して、スキー レンタル業の予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [SQL 開発者向けのデータベース内分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)利用方法を示しますが、R コード モジュール性の高いストアド プロシージャにラップします。

+ [エンド ツー エンドのデータ サイエンス ソリューション](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)R と T-SQL での特徴エンジニア リングの比較が含まれています
