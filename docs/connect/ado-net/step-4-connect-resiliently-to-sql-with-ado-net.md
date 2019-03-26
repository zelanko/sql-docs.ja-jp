---
title: '手順 4: は、ADO.NET を使用して SQL に弾性的接続 |Microsoft Docs'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9b608b0b-6b38-42da-bb83-79df8c170cd7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fceeefd7c9dd0d3bd7df761273f69355c4e6024a
ms.sourcegitcommit: 1a182443e4f70f4632617cfef4efa56d898e64e9
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2019
ms.locfileid: "58342869"
---
# <a name="step-4-connect-resiliently-to-sql-with-adonet"></a>ステップ 4: ADO.NET で SQL に弾性的に接続する

- 前の記事:&nbsp;&nbsp;&nbsp;[手順 3: ADO.NET を使用した SQL への接続を概念実証する](step-3-proof-of-concept-connecting-to-sql-using-ado-net.md)  

  
このトピックでは、カスタムの再試行ロジックを示す C# コード サンプルを提供します。 再試行ロジックは、信頼性を提供します。 再試行ロジックが適切に一時的なエラーを処理するように設計または*一過性の障害*消える場合は、プログラムがいくつかの秒、再試行を待機する傾向があります。  
  
一時的な障害の発生源は次のとおりです。  
  
- インターネットをサポートするネットワークの簡単なエラーです。  
- クラウドのシステムには、負荷、クエリが送信された時点でそのリソースを分散する可能性があります。  
  
  
ローカル Microsoft SQL Server に接続するための ADO.NET クラスは、Azure SQL Database に接続できます。 ただし、ADO.NET 単独でクラスを提供できません、すべての堅牢性と運用環境で必要な信頼性。 クライアント プログラムには、元にする必要がありますサイレント モードで、適切に回復して続行、独自の一時的な障害が発生する可能性が。  
  
## <a name="step-1-identify-transient-errors"></a>手順 1: 一時的なエラーを特定します。  
  
プログラムは、永続的なエラーと一時的なエラーを区別する必要があります。 一時的なエラーは、短時間、一時的なネットワークの問題などの解消がエラー状態です。  永続的なエラーの例はありますが、プログラムがターゲット データベース名のスペルミスがある - この場合は、「このようなデータベースが見つかりません」エラーは保持は、および、短時間で消去する可能性がない場合。  
  
一時的な障害に分類されるエラー番号の一覧は[SQL Database クライアント アプリケーションのエラー メッセージ](https://docs.microsoft.com/azure/sql-database/sql-database-develop-error-messages/)  
  
## <a name="step-2-create-and-run-sample-application"></a>手順 2: を作成し、サンプル アプリケーションを実行  
  
このサンプルでは、.NET Framework 4.5.1 を前提としています。 または以降がインストールされています。  C# コード サンプルは、Program.cs という名前の 1 つのファイルで構成されます。 次のセクションでは、そのコードを示します。  
  
### <a name="step-2a-capture-and-compile-the-code-sample"></a>手順 2.a: キャプチャし、コード サンプルをコンパイル  
  
次の手順でサンプルをコンパイルすることができます。  
  
1. [無料の Visual Studio Community edition](https://www.visualstudio.com/products/visual-studio-community-vs)、C# コンソール アプリケーション テンプレートから新しいプロジェクトを作成します。  
    - ファイル > 新規 > プロジェクト > インストール > テンプレート > Visual c# > Windows > クラシック デスクトップ > コンソール アプリケーション  
    - プロジェクトに名前を**RetryAdo2**します。  
2. ソリューション エクスプ ローラー ウィンドウを開きます。  
    - プロジェクトの名前を参照してください。  
    - Program.cs ファイルの名前を参照してください。  
3. Program.cs ファイルを開きます。  
4. 完全では、次のコード ブロックのコードで Program.cs ファイルの内容を置き換えます。  
5. [ビルド] メニューをクリックします。 > ソリューションのビルド。  
  
### <a name="step-2b-copy-and-paste-sample-code"></a>手順 2. b: コピーと貼り付けのサンプル コード  
  
次のコードを貼り付け、 **Program.cs**ファイル。  
  
サーバー名やパスワードの文字列を編集する必要があります。 という名前のメソッドでこれらの文字列を検索する**GetSqlConnectionStringBuilder**します。  
  
注: サーバー名の接続文字列を対象とした Azure SQL Database では、4 つの文字のプレフィックスが含まれているため**tcp:** します。 Microsoft SQL Server に接続するサーバーの文字列を調整することができます。  
  
  
```csharp
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
  
###  <a name="step-2c-run-the-program"></a>手順 2. c: プログラムの実行  
  
  
**RetryAdo2.exe**実行可能ファイルがパラメーターを入力しません。 .Exe を実行します。  
  
1. RetryAdo2.exe バイナリをコンパイルした場所にコンソール ウィンドウを開きます。  
2. 入力パラメーターなしで RetryAdo2.exe を実行します。  
  
  
  
```  
    database_firewall_rules_table   245575913  
    filestream_tombstone_2073058421 2073058421  
    filetable_updates_2105058535    2105058535  
```  
  
  
  
## <a name="step-3-ways-to-test-your-retry-logic"></a>再試行ロジックをテストする方法は手順 3:  
  
いくつかの方法の再試行ロジックをテストする一時的なエラーをシミュレートすることができます。  
  
  
###  <a name="step-3a-throw-a-test-exception"></a>手順 3.a: テスト例外をスローします。  
  
コード サンプルは次のとおりです。  
  
- という名前の 2 番目の小さなクラス**TestSqlException**、という名前のプロパティで**数**します。  
- `//throw new TestSqlException(4060);` 、コメントを解除できます。  
  
Throw ステートメント、および再コンパイルのコメントを解除する場合、次回の実行の**RetryAdo2.exe**次のようなものを出力します。  
  
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
  
###  <a name="step-3b-retest-with-a-persistent-error"></a>手順の 3.b: 永続的なエラーで再テストします。  
  
コードを証明するために、ハンドルは永続的なエラーを除く上記のテストを正常に再実行は 4060 などの実際の一時的なエラーの数を使用しないでください。 代わりに意味がない数 7654321 を使用します。 プログラムでは、これを永続的なエラーとして扱う必要があり、すべての再試行をバイパスする必要があります。  
  
###  <a name="step-3c-disconnect-from-the-network"></a>ステップ 3.c: ネットワークから切断  
  
1. クライアント コンピューターをネットワークから切断します。  
    - デスクトップ、ネットワーク ケーブルを外します。  
    - ラップトップの場合は、ネットワーク アダプターを無効にするキーの関数の組み合わせを押します。  
2. RetryAdo2.exe を起動し、コンソールにおそらく 11001 最初一時的なエラーを表示するまで待ちます。  
3. RetryAdo2.exe が実行を続けながら、ネットワークに再接続します。  
4. 後続の再試行時にコンソールのレポートの成功をご覧ください。  
  
  
###  <a name="step-2d-temporarily-misspell-the-server-name"></a>手順 2. d: サーバー名のスペルが一時的に  
  
1. 一時的に 40615 を別のエラー番号として追加**TransientErrorNumbers**、し、再コンパイルします。  
2. 行にブレークポイントを設定します。`new QC.SqlConnectionStringBuilder()`します。  
3. 使用して、*エディット コンティニュ*数行下、サーバー名のスペルが意図的に機能します。  
    - プログラムを実行し、ブレークポイントに戻ることができます。  
    - 40615 エラーが発生します。  
4. スペルミスを修正します。  
5. プログラムを実行し、正常に終了することができます。  
6. 40615 を削除し、再コンパイルします。  
  
## <a name="next-steps"></a>Next Steps  
  
その他のベスト practicies と設計のガイドラインを参照する、次を参照してください[SQL Database への接続: リンク、ベスト プラクティスと設計のガイドライン。](https://azure.microsoft.com/documentation/articles/sql-database-connect-central-recommendations/)  
