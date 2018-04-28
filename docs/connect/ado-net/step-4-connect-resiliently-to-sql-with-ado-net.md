---
title: '手順 4: は、ADO.NET を使用した SQL に弾性的接続 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado-net
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 9b608b0b-6b38-42da-bb83-79df8c170cd7
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f7ccf61c8c1e440ed8ae9533e61cbbf74d156eb8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="step-4-connect-resiliently-to-sql-with-adonet"></a>手順 4: は ADO.NET を使用した SQL に弾性的に接続します。

- 前の記事:&nbsp;&nbsp;&nbsp;[手順 3: ADO.NET を使用して SQL に接続する概念実証](step-3-proof-of-concept-connecting-to-sql-using-ado-net.md)  

  
このトピックでは、カスタムの再試行ロジックを示しています (C#) コード サンプルを提供します。 再試行ロジックは、信頼性を提供します。 一時的なエラーを適切に処理する再試行ロジックを設計または*一時的なエラー*プログラムは、いくつかの秒および再試行が待機する場合を解消する傾向があります。  
  
一時的なエラーの原因は次のとおりです。  
  
- インターネットをサポートするネットワークの簡単なエラーです。  
- クラウド システムでは、送信されるクエリを実行する時点でそのリソースを分散負荷をする可能性があります。  
  
  
ローカル Microsoft SQL Server に接続するための ADO.NET クラスは、Azure SQL データベースにも接続できます。 ただし、ADO.NET 単独でクラスを提供できませんすべての堅牢性と信頼性を実稼働環境で必要です。 クライアント プログラムには、元となるする必要がありますサイレント モードで正常に回復して、独自のまま続行する一時的なエラーが発生することができます。  
  
## <a name="step-1-identify-transient-errors"></a>手順 1: 一時的なエラーを特定します。  
  
プログラムは、一時的なエラー永続的なエラーとを区別する必要があります。 一時的なエラーは、エラー状態を短時間、ネットワークの一時的な問題などオフに可能性があります。  永続的なエラーの例は、プログラムがターゲット データベース名のスペル ミスがある - この場合、「データベースがありませんが見つかりません」エラーし維持され、短時間でを消去する可能性がない場合にされます。  
  
一時的なエラーとして分類されるエラー番号の一覧は時に使用可能な[SQL データベース クライアント アプリケーションのエラー メッセージ](http://docs.microsoft.com/azure/sql-database/sql-database-develop-error-messages/)  
  
## <a name="step-2-create-and-run-sample-application"></a>手順 2: を作成し、サンプル アプリケーションを実行  
  
このサンプルでは、.NET Framework 4.5.1 を前提としていますか、以降がインストールされています。  C# コード サンプルは、Program.cs」という名前の 1 つのファイルで構成されます。 そのコードは、次のセクションで提供されます。  
  
### <a name="step-2a-capture-and-compile-the-code-sample"></a>ステップ 2.a: キャプチャし、コード サンプルをコンパイル  
  
次の手順でサンプルをコンパイルすることができます。  
  
1. [無料の Visual Studio Community エディション](https://www.visualstudio.com/products/visual-studio-community-vs)、c# コンソール アプリケーション テンプレートから新しいプロジェクトを作成します。  
    - ファイル > 新しい > プロジェクト > インストールされている > テンプレート > Visual c# > Windows > クラシック デスクトップ > コンソール アプリケーション  
    - プロジェクトに名前を**RetryAdo2**です。  
2. ソリューション エクスプ ローラー ウィンドウを開きます。  
    - プロジェクトの名前を参照してください。  
    - Program.cs ファイルの名前を参照してください。  
3. Program.cs ファイルを開きます。  
4. 完全次のコード ブロック内のコードで、Program.cs ファイルの内容を置き換えます。  
5. [ビルド] メニューをクリックして > ソリューションのビルドします。  
  
### <a name="step-2b-copy-and-paste-sample-code"></a>ステップ 2.b: コピーと貼り付けのサンプル コード  
  
このコードに貼り付けて、 **Program.cs**ファイル。  
  
サーバー名、パスワード、およびなどの文字列を編集する必要があります。 という名前のメソッドでこれらの文字列を検索できます**GetSqlConnectionStringBuilder**です。  
  
注: サーバー名の接続文字列が対象としています、Azure SQL データベースの 4 つの文字のプレフィックスが含まれているため**tcp:** です。 Microsoft SQL Server に接続するサーバーの文字列を調整することができます。  
  
  
```CSharp  
    using System;  // C#  
    using CG = System.Collections.Generic;  
    using QC = System.Data.SqlClient;  
    using TD = System.Threading;  
        
    namespace RetryAdo2  
    {  
      public class Program  
      {  
        static public int Main(string[] args)  
        {  
          bool succeeded = false;  
          int totalNumberOfTimesToTry = 4;  
          int retryIntervalSeconds = 10;  
        
          for (int tries = 1;  
            tries <= totalNumberOfTimesToTry;  
            tries++)  
          {  
            try  
            {  
              if (tries > 1)  
              {  
                Console.WriteLine  
                  ("Transient error encountered. Will begin attempt number {0} of {1} max...",  
                  tries, totalNumberOfTimesToTry  
                  );  
                TD.Thread.Sleep(1000 * retryIntervalSeconds);  
                retryIntervalSeconds = Convert.ToInt32  
                  (retryIntervalSeconds * 1.5);  
              }  
              AccessDatabase();  
              succeeded = true;  
              break;  
            }  
        
            catch (QC.SqlException sqlExc)  
            {  
              if (TransientErrorNumbers.Contains  
                (sqlExc.Number) == true)  
              {  
                Console.WriteLine("{0}: transient occurred.", sqlExc.Number);  
                continue;  
              }  
              else  
              {  
                Console.WriteLine(sqlExc);  
                succeeded = false;  
                break;  
              }  
            }  
        
            catch (TestSqlException sqlExc)  
            {  
              if (TransientErrorNumbers.Contains  
                (sqlExc.Number) == true)  
              {  
                Console.WriteLine("{0}: transient occurred. (TESTING.)", sqlExc.Number);  
                continue;  
              }  
              else  
              {  
                Console.WriteLine(sqlExc);  
                succeeded = false;  
                break;  
              }  
            }  
        
            catch (Exception Exc)  
            {  
              Console.WriteLine(Exc);  
              succeeded = false;  
              break;  
            }  
          }  
        
          if (succeeded == true)  
          {  
            return 0;  
          }  
          else  
          {  
            Console.WriteLine("ERROR: Unable to access the database!");  
            return 1;  
          }  
        }  
        
        /// <summary>  
        /// Connects to the database, reads,  
        /// prints results to the console.  
        /// </summary>  
        static public void AccessDatabase()  
        {  
          //throw new TestSqlException(4060); //(7654321);  // Uncomment for testing.  
        
          using (var sqlConnection = new QC.SqlConnection  
              (GetSqlConnectionString()))  
          {  
            using (var dbCommand = sqlConnection.CreateCommand())  
            {  
              dbCommand.CommandText = @"  
    SELECT TOP 3  
        ob.name,  
        CAST(ob.object_id as nvarchar(32)) as [object_id]  
      FROM sys.objects as ob  
      WHERE ob.type='IT'  
      ORDER BY ob.name;";  
        
              sqlConnection.Open();  
              var dataReader = dbCommand.ExecuteReader();  
        
              while (dataReader.Read())  
              {  
                Console.WriteLine("{0}\t{1}",  
                  dataReader.GetString(0),  
                  dataReader.GetString(1));  
              }  
            }  
          }  
        }  
        
        /// <summary>  
        /// You must edit the four 'my' string values.  
        /// </summary>  
        /// <returns>An ADO.NET connection string.</returns>  
        static private string GetSqlConnectionString()  
        {  
          // Prepare the connection string to Azure SQL Database.  
          var sqlConnectionSB = new QC.SqlConnectionStringBuilder();  
        
          // Change these values to your values.  
          sqlConnectionSB.DataSource = "tcp:myazuresqldbserver.database.windows.net,1433"; //["Server"]  
          sqlConnectionSB.InitialCatalog = "MyDatabase"; //["Database"]  
        
          sqlConnectionSB.UserID = "MyLogin";  // "@yourservername"  as suffix sometimes.  
          sqlConnectionSB.Password = "MyPassword";  
          sqlConnectionSB.IntegratedSecurity = false;  
        
          // Adjust these values if you like. (ADO.NET 4.5.1 or later.)  
          sqlConnectionSB.ConnectRetryCount = 3;  
          sqlConnectionSB.ConnectRetryInterval = 10;  // Seconds.  
        
          // Leave these values as they are.  
          sqlConnectionSB.IntegratedSecurity = false;  
          sqlConnectionSB.Encrypt = true;  
          sqlConnectionSB.ConnectTimeout = 30;  
        
          return sqlConnectionSB.ToString();  
        }  
        
        static public CG.List<int> TransientErrorNumbers =  
          new CG.List<int> { 4060, 40197, 40501, 40613,  
          49918, 49919, 49920, 11001 };  
      }  
        
      /// <summary>  
      /// For testing retry logic, you can have method  
      /// AccessDatabase start by throwing a new  
      /// TestSqlException with a Number that does  
      /// or does not match a transient error number  
      /// present in TransientErrorNumbers.  
      /// </summary>  
      internal class TestSqlException : ApplicationException  
      {  
        internal TestSqlException(int testErrorNumber)  
        { this.Number = testErrorNumber; }  
        
        internal int Number  
        { get; set; }  
      }  
    }  
```  
  
###  <a name="step-2c-run-the-program"></a>ステップ 2.c: プログラムの実行  
  
  
**RetryAdo2.exe**実行可能ファイルのパラメーター入力されません。 .Exe を実行します。  
  
1. RetryAdo2.exe バイナリがコンパイルされる場所をコンソール ウィンドウを開きます。  
2. 入力パラメーターのない RetryAdo2.exe を実行します。  
  
  
  
```  
    database_firewall_rules_table   245575913  
    filestream_tombstone_2073058421 2073058421  
    filetable_updates_2105058535    2105058535  
```  
  
  
  
## <a name="step-3-ways-to-test-your-retry-logic"></a>再試行ロジックをテストする方法を手順 3:  
  
いくつかの方法の再試行ロジックをテストすると、一時的なエラーをシミュレートすることができます。  
  
  
###  <a name="step-3a-throw-a-test-exception"></a>3.a のステップ: テストの例外をスローします。  
  
コード サンプルは次のとおりです。  
  
- という名前の小さな秒クラス**TestSqlException**、という名前のプロパティを**数**です。  
- `//throw new TestSqlException(4060);` 、コメントを解除することができます。  
  
Throw ステートメントを再コンパイルをコメントを解除する場合、次回の実行の**RetryAdo2.exe**には、次のように出力します。  
  
```  
    [C:\VS15\RetryAdo2\RetryAdo2\bin\Debug\]  
    >> RetryAdo2.exe  
    4060: transient occurred. (TESTING.)  
    Transient error encountered. Will begin attempt number 2 of 4 max...  
    4060: transient occurred. (TESTING.)  
    Transient error encountered. Will begin attempt number 3 of 4 max...  
    4060: transient occurred. (TESTING.)  
    Transient error encountered. Will begin attempt number 4 of 4 max...  
    4060: transient occurred. (TESTING.)  
    ERROR: Unable to access the database!  
      
    [C:\VS15\RetryAdo2\RetryAdo2\bin\Debug\]  
    >>  
```  
  
###  <a name="step-3b-retest-with-a-persistent-error"></a>ステップ 3.b: 持続的なエラーで再テスト  
  
コードを証明するために永続的なエラーが正しく、以外、前のテストを再実行のハンドルは 4060 のように実際に一時的なエラーの数を使用しないでください。 代わりに意味がない数 7654321 を使用します。 プログラムでは、これを永続的なエラーとして扱う必要があり、任意の再試行をバイパスする必要があります。  
  
###  <a name="step-3c-disconnect-from-the-network"></a>ステップ 3.c: ネットワークから切断  
  
1. クライアント コンピューターをネットワークから切断します。  
    - デスクトップのネットワーク ケーブルを外します。  
    - ラップトップ コンピューター、ネットワーク アダプターをオフにするためのキーを関数の組み合わせをキーを押します。  
2. RetryAdo2.exe を起動し、おそらく 11001 最初一時的なエラーを表示するコンソールを待ちます。  
3. RetryAdo2.exe を実行し続けながら、ネットワークに再接続します。  
4. 以降の再試行時にコンソールのレポートの成功を確認します。  
  
  
###  <a name="step-2d-temporarily-misspell-the-server-name"></a>ステップ 2.d: サーバー名のスペルが一時的に  
  
1. 別のエラー番号として 40615 を一時的に追加**TransientErrorNumbers**、再コンパイルしてください。  
2. 行にブレークポイントを設定します。`new QC.SqlConnectionStringBuilder()`です。  
3. 使用して、*エディット コンティニュ*意図的にスペルを間違えて入力サーバー名では、以下の 2 つの行に機能します。  
    - プログラムを実行し、ブレークポイントに戻ることができます。  
    - 40615 エラーが発生します。  
4. スペル ミスを修正します。  
5. プログラムを実行し、正常に完了できるようにします。  
6. 40615 を削除し、再コンパイルします。  
  
## <a name="next-steps"></a>次の手順  
  
調べるために他の最適な practicies とデザイン ガイドラインには、次を参照してください[SQL データベースへの接続: リンク、ベスト プラクティスとデザイン ガイドライン。](http://azure.microsoft.com/documentation/articles/sql-database-connect-central-recommendations/)  
