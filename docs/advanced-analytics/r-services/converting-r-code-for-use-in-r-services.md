---
title: "R のサービスで使用するための R コードに変換します。 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 0b11ab52-b2f9-4a4f-b1ab-68ba09c8adcc
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# R のサービスで使用するための R コードに変換します。
R コードを R Studio や他の環境から SQL Server に移動すると多くの場合、コードが動作に追加されたときにそれ以上変更せず、 *@script* のパラメーター [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。 これは、実行コンテキストを変更するのには比較的単純なので、スケーラ関数を使用して、ソリューションを開発した場合に特に当てはまります。    
    
ただし、通常は変更する、R コードを両方との緊密な統合を活用するために SQL Server で実行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 、データの転送のコストを回避することです。   
   
   
## リソース  
  
SQL Server での R コードの実行方法の例については、これらのチュートリアルを参照してください。   
+ [SQL Developer を使用したデータベースの分析](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)    
  方法について説明できる R コード モジュール性の高いストアド プロシージャをラップして、  
+ [エンド ツー エンドのデータ サイエンスのソリューション](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md)    
  R と T-SQL で特徴エンジニア リングの比較が含まれています

## SQL Server のデータ サイエンス プロセスへの変更  
  
作業しているときに [!INCLUDE[rsql_rtvs_md](../../includes/rsql-rtvs-md.md)], 、RStudio では、またはその他の環境では、一般的なワークフローをコンピューターにデータを取得、データを繰り返し、分析、書き出すまたは結果を表示します。 ただし、スタンドアロン R コードを SQL Server に移行すると、このプロセスの多く簡素化したりその他の SQL Server ツールに委任します。

| 外部コード | SQL Server での R |
|-------|-------|
| データを取り込む| 入力データをデータベース内の SQL クエリとして定義します。 | 
| 集計し、データを視覚化する.| 変更はありません。プロットをイメージとしてエクスポートしたり、リモート ワークステーションに送信されます。|
|特徴エンジニア リング| R でのデータベースを使用することができます。 が、T-SQL 関数またはカスタムのユーザー定義関数を呼び出すことがより効率的であることができます。|
|データの分析プロセスの一部の消去| データ クレンジングの ETL プロセスに委任して事前に実行|
|ファイルへ出力予測| テーブルまたはラップするための予測を出力 `predict` アプリケーションによって直接アクセスするためのストアド プロシージャで|
  

  
## ベスト プラクティス  
  
+ 必要なパッケージなどの依存関係のメモを事前にください。 な開発・ テスト環境では、パッケージ、コードの一部としてインストール問題がない場合がありますが、これは、実稼働環境で不適切な手法です。 管理者に通知できるように、パッケージがインストールされ、コードを展開する前にテストすることができます。  
+ 懸案事項を入力できるデータのチェックリストを確認します。 コードの各セクションで想定される結果のスキーマを文書化します。  
+ モデルのトレーニング データ、またはセカンダリ ソースなどの要因、追加のグループ変数と予測の入力データなどのプライマリ データ ソースを識別します。 入力パラメーターに最も大きなデータセットをマップ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。  
+ データベースで直接作業する、入力データのステートメントを変更します。 ローカルの CSV ファイルにデータを移動または作成は、ODBC 呼び出しを繰り返しではなくが得られますパフォーマンスを向上させる SQL のクエリや、データベースに対して直接実行できるビューを使用してデータの移動を回避します。  
+ 並列で実行できるタスクを識別するには、SQL Server クエリ プランを使用します。 入力クエリを並列化できる場合は、設定 `@parallel=1` sp_execute_external_script に渡す引数の一部として。 並列処理のこのフラグでは通常考えられるいつでも SQL Server できますパーティション分割されたテーブルを操作するまたは複数プロセス間でクエリを配布、最後に結果を集計します。 
   並列処理のこのフラグでは通常できませんを読み取り、すべてのデータを必要とするアルゴリズムを使用してモデルを学習する場合、または集計を作成する必要があります。 
+ 可能であればと従来の R 関数を置き換える **スケーラ** 分散の実行をサポートする関数。 詳細については、次を参照してください。 [スケール R、および CRAN R 関数の比較](Summary%20of%20rx%20Functions.md)します。
+ 単独で実行または別のストアド プロシージャの呼び出しを使用してより効率的に実行できる手順があるかどうかを決定する R コードを確認します。 たとえば、特徴エンジニア リングや特徴の抽出を個別に実行し、新しい列に値を追加することができます。 セットベースの計算用 R コードではなく、T-SQL を使用します。 機能のエンジニア リング タスク用の Udf と R のパフォーマンスを比較する R ソリューションの一例は、このチュートリアルを参照してください: [データ サイエンスのエンド ツー エンド チュートリアル](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md)します。  
  
    
## 制限    
 R コードを変換するときに、次の制限事項に留意してください。    
   
**データ型**    
-   すべての R のデータ型がサポートされます。 ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は R キーを押しを送信するときにいくつかの暗黙的なデータ型変換が実行されるためよりも大きい各種のデータ型をサポートしている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と R のデータです。 明示的にキャストまたは変換は、いくつかのデータを必要する可能性があります。    
    
- NULL 値がサポートされています。 R の使用方法、 `na` null 値に似ている不足値を表すデータを作成します。    
    
- 詳細については、次を参照してください。 [R のデータ型を扱う](../../advanced-analytics/r-services/working-with-r-data-types.md)します。    
 
 **[入力および出力]**   
+ ストアド プロシージャのパラメーターの一部として、1 つだけの入力データセットを定義できます。 ストアド プロシージャの入力このクエリは、任意の有効な単一の SELECT ステートメントを指定できます。 最大のデータセットでは、この入力を使用し、RODBC への呼び出しを使用して、必要な場合は小規模なデータセットの取得をお勧めします。 

+ ストアド プロシージャの呼び出しの実行前に付けたは sp_execute_external_script の入力として使用できません。    
    
+ 入力データセットのすべての列は、R スクリプトの変数にマップする必要があります。 変数は、名前によって自動的にマップされます。 たとえば、R スクリプトには、次のような数式が含まれています。    
    
    ```    
    formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek    
    ```    
    
     入力データセットは、ArrDelay、CRSDepTime、DayOfWeek、CRSDepHour、および DayOfWeek に一致する名前の列を含まない場合、エラーが発生します。    

+ 入力として複数のスカラー パラメーターを指定することもできます。 ただし、ストアド プロシージャのパラメーターとして渡す変数 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) R コードで変数をマップする必要があります。 既定では、変数は、名前によってマップされます。
+ スカラーの入力変数は、R コードの出力で、追加、 **出力** キーワード、変数を定義するとします。             
+  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], 、R コードは、data.frame オブジェクトとして 1 つのデータセットを出力することに制限します。 ただし、複数のスカラーをバイナリ形式でプロットを含むを出力し、varbinary 形式でモデル化をも出力できます。    
    
+ 通常で RESULT SETS UNDEFINED オプションを使用して出力列の名前を指定せずに、R スクリプトによって返されるデータセットを出力することができます。 ただし、SQL の出力パラメーターに出力する R スクリプト内のどの変数をマップする必要があります。
    
+ R スクリプトの引数を使用している場合 `@parallel=1`, 、出力スキーマを定義する必要があります。 理由は、最後に、収集された結果と同時にクエリを実行する SQL Server で複数のプロセスを作成する可能性があります。 したがって、並列処理を作成する前に、出力スキーマを定義する必要があります。

 **依存関係**
 + R コードからパッケージをインストールしないようにします。 SQL Server にパッケージを事前にインストールする必要があります。  
  
  
  

