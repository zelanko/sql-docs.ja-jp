---
title: Java サンプルとチュートリアルを SQL Server 2019 - SQL Server Machine Learning サービス
description: SQL Server のデータを Java 言語の拡張機能を使用するための手順については、SQL Server 2019 の Java サンプル コードを実行します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 000318716b07f58e94bd5c482d9c349e5d4e5481
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473768"
---
# <a name="sql-server-regex-java-sample"></a>SQL Server の正規表現の Java サンプル

この例は、SQL Server から 2 つの列 (ID および文字列) を受け取り、入力パラメーターとしての正規表現ではも Java クラスを示します。 クラスは、SQL Server (ID および文字列) に 2 つの列を返します。

指定された正規表現が満たされ、元の ID と共に、そのテキストが返されますかどうかの Java クラスに送信されるテキストの列で指定したテキスト、コードを確認します 

このサンプルでは、テキストには、"Java"または"java"という語が含まれている場合にチェックする正規表現を使用します。

## <a name="microsoft-extensibility-sdk-for-java-for-microsoft-sql-server"></a>Microsoft 拡張機能の Microsoft SQL Server 用の Java SDK

 CTP 2.5 では、SQL Server と通信するために、Java 言語の拡張機能を使用する Java コードを実装する方法を変更しています。 Java から SQL Server にやり取りするときは、開発者エクスペリエンスの向上に送りします。

SQL Server に対して実行されている Java コードを実装しやすく、構成するためのヘルパー インターフェイスとして SDK を考慮する必要があります。

> [!NOTE]
> SDK の概要は、以前の Ctp から大きな変更です。 前のサンプルが作業する必要があるが、SDK を使用して更新する必要があります。

詳細については、次を参照してください。、 [SDK ドキュメント](java-sdk.md)します。

## <a name="prerequisites"></a>前提条件

+ Java 拡張機能のプログラミングと拡張性フレームワークでの SQL Server 2019 データベース エンジン インスタンス[Windows で](../install/sql-machine-learning-services-windows-install.md)または[on Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup)します。 システム構成の詳細については、次を参照してください。 [Java 言語の拡張機能で SQL Server 2019](extension-java.md)します。 コーディングの要件の詳細については、次を参照してください。 [SQL Server で Java を呼び出す方法](howto-call-java-from-sql.md)します。

+ SQL Server Management Studio または T-SQL を実行するための Azure Data Studio。

+ Java SE Development Kit (JDK) 8 または JRE 8 on Windows または Linux。

+ [Microsoft SQL Server 用 Microsoft Java 拡張機能 SDK](http://aka.ms/mssql-java-lang-extension) mssql java lang extension.jar します。

コマンド ライン コンパイルを使用して**javac**でこのチュートリアルでは十分です。

## <a name="1---create-sample-data-in-a-sql-server-table"></a>1-SQL Server テーブルにサンプル データを作成します。

最初に、作成し、設定、 *testdata*を持つテーブル**ID**と**テキスト**列。 SQL Server に接続し、テーブルを作成する次のスクリプトを実行します。

```sql
CREATE DATABASE javatest
GO
USE javatest
GO

-- Create table for test data
DROP TABLE IF exists testdata;
GO

CREATE TABLE testdata(
id int NOT NULL,
"text" nvarchar(100) NOT NULL)
GO

TRUNCATE TABLE testdata
GO

-- Insert data into test table
INSERT INTO testdata(id, "text") VALUES (1, 'This sentence contains java')
INSERT INTO testdata(id, "text") VALUES (2, 'This sentence does not')
INSERT INTO testdata(id, "text") VALUES (3, 'I love Java!')
GO
Select * FROM testdata
```

## <a name="2---class-regexsamplejava"></a>2 - Class RegexSample.java

まず、メイン クラスを作成します。

この手順で作成と呼ばれるクラス**RegexSample.java**し、そのファイルに次の Java コードをコピーします。

この主なクラスは、SDK は、手順 1 で jar ファイルがダウンロードしたことを意味をこのクラスから検出可能にする必要がありますをインポートしています。

> [!NOTE]
> このクラスが、Java の拡張機能 SDK パッケージをインポートすることに注意してください。
に関する記事を参照してください、 [Java for Microsoft SQL Server 用の Microsoft 拡張機能 SDK](java-sdk.md)の詳細。

```java
package pkg;

import com.microsoft.sqlserver.javalangextension.PrimitiveDataset;
import com.microsoft.sqlserver.javalangextension.AbstractSqlServerExtensionExecutor;
import java.util.LinkedHashMap;
import java.util.LinkedList;
import java.util.ListIterator;
import java.util.regex.*;

public class RegexSample extends AbstractSqlServerExtensionExecutor {
    private Pattern expr;

    public RegexSample() {
        // Setup the expected extension version, and class to use for input and output dataset
        executorExtensionVersion = SQLSERVER_JAVA_LANG_EXTENSION_V1;
        executorInputDatasetClassName = PrimitiveDataset.class.getName();
        executorOutputDatasetClassName = PrimitiveDataset.class.getName();
    }
    
    public PrimitiveDataset execute(PrimitiveDataset input, LinkedHashMap<String, Object> params) {
        // Validate the input parameters and input column schema
        validateInput(input, params);

        int[] inIds = input.getIntColumn(0);
        String[] inValues = input.getStringColumn(1);
        int rowCount = inValues.length;

        String regexExpr = (String)params.get("regexExpr");
        expr = Pattern.compile(regexExpr);

        System.out.println("regex expression: " + regexExpr);

        // Lists to store the output data
        LinkedList<Integer> outIds = new LinkedList<Integer>();
        LinkedList<String> outValues = new LinkedList<String>();

        // Evaluate each row
        for(int i = 0; i < rowCount; i++) {
            if (check(inValues[i])) {
                outIds.add(inIds[i]);
                outValues.add(inValues[i]);
            }
        }

        int outputRowCount = outValues.size();

        int[] idOutputCol = new int[outputRowCount];
        String[] valueOutputCol = new String[outputRowCount];

        // Convert the list of output columns to arrays
        outValues.toArray(valueOutputCol);

        ListIterator<Integer> it = outIds.listIterator(0);
        int rowId = 0;

        System.out.println("Output data:");
        while (it.hasNext()) {
            idOutputCol[rowId] = it.next().intValue();

            System.out.println("ID: " + idOutputCol[rowId] + " Value: " + valueOutputCol[rowId]);
            rowId++;
        }

        // Construct the output dataset
        PrimitiveDataset output = new PrimitiveDataset();

        output.addColumnMetadata(0, "ID", java.sql.Types.INTEGER, 0, 0);
        output.addColumnMetadata(1, "Text", java.sql.Types.NVARCHAR, 0, 0);

        output.addIntColumn(0, idOutputCol, null);
        output.addStringColumn(1, valueOutputCol);

        return output;
    }

    private void validateInput(PrimitiveDataset input, LinkedHashMap<String, Object> params) {
        // Check for the regex expression input parameter
        if (params.get("regexExpr") == null) {
            throw new IllegalArgumentException("Input parameter 'regexExpr' is not found");
        }

        // The expected input schema should be at least 2 columns, (INTEGER, STRING)
        if (input.getColumnCount() < 2) {
            throw new IllegalArgumentException("Unexpected input schema, schema should be an (INTEGER, NVARCHAR or VARCHAR)");
        }

        // Check that the input column types are expected
        if (input.getColumnType(0) != java.sql.Types.INTEGER &&
                (input.getColumnType(1) != java.sql.Types.VARCHAR && input.getColumnType(1) == java.sql.Types.NVARCHAR )) {
            throw new IllegalArgumentException("Unexpected input schema, schema should be an (INTEGER, NVARCHAR or VARCHAR)");
        }
    }

    private boolean check(String text) {
        Matcher m = expr.matcher(text);

        return m.find();
    }
}
```

## <a name="3-compile-and-create-jar-file"></a>3 は、コンパイルし、.jar ファイルを作成

クラスと依存関係 jar ファイルにパッケージ化することをお勧めします。 Eclipse または IntelliJ のサポートを生成するように、ほとんどの Java Ide は jar とフォルダーをビルド/コンパイルなプロジェクト ファイルです。 このサンプルで、jar ファイルがあるという**regex.jar**します。

.Jar ファイルを手動で作成する場合は、次の手順を参照してください[jar ファイルを作成する方法](extension-java.md#create-jar)します。

> [!NOTE]
> つまり、クラスの上にあるパッケージ「パッケージ」により、コンパイルされたコードが「パッケージ」と呼ばれる、サブ フォルダーに保存されることを確認しているこのサンプルで、パッケージが使用されています。 これは自動的に行われますの IDE を使用する場合は、クラスを使用して手動でコンパイルする場合**javac**、pkg サブ フォルダーに手動でコンパイルされたコードを配置する必要があります。

## <a name="4---create-external-libraries"></a>4 - 外部ライブラリを作成します。

外部ライブラリを作成すると、SQL Server は jar ファイルへのアクセスが自動的にし、クラスパスに特殊なアクセス許可を設定する必要はありません。

このサンプルでは、2 つの外部ライブラリを作成する必要があります。 SDK のいずれかと、正規表現の Java サンプルの 1 つ。

1.  ダウンロード[Java for Microsoft SQL Server 用の Microsoft 拡張機能 SDK](http://aka.ms/mssql-java-lang-extension) mssql java lang extension.jar します。

1. Sdk の外部ライブラリを作成します。

```sql
-- Create external library for the SDK
CREATE EXTERNAL LIBRARY sdk
FROM (CONTENT = '<path>/mssql-java-lang-extension.jar')
WITH (LANGUAGE = 'Java');
GO
```

3. 正規表現の例の外部ライブラリを作成します。

```sql
-- Create external library for the regex sample
CREATE EXTERNAL LIBRARY regex
FROM (CONTENT = '<path>/regex.jar')
WITH (LANGUAGE = 'Java');
GO
```

## <a name="5---set-permissions-skip-if-you-performed-step-4"></a>5-アクセス許可 (スキップ手順 4 を実行した場合) を設定します。

外部ライブラリを使用する場合は、この手順は必要ありません。 推奨作業の方法では、jar をから外部ライブラリを作成します。

外部ライブラリを使用しない場合は、必要なアクセス許可を設定する必要があります。 スクリプトの実行は、プロセス id が、コードにアクセスしている場合にのみ成功します。 アクセス許可を設定する方法について詳細を検索できます[ここ](extension-java.md)します。

### <a name="on-linux"></a>On Linux

クラスパスをに対する読み取り/実行の権限の付与、 **mssql_satellite**ユーザー。

### <a name="on-windows"></a>Windows で

'読み取りと実行' アクセス許可を付与**SQLRUserGroup**と**すべてのアプリケーション パッケージ**コンパイル済みの Java コードを含むフォルダーの SID。 

ツリー全体がルートから親の最後のサブ フォルダー、アクセス許可が必要があります。 
 
1. フォルダー (たとえば、' C:\myJavaCode') を右クリックし、選択**プロパティ** > **セキュリティ**します。
2. **[編集]** をクリックします。
3. **[追加]** をクリックします。
4. **ユーザー、コンピューター、サービス アカウント、またはグループを選択します**:。
   + をクリックして**オブジェクトの種類**を確認して*組み込みのセキュリティ原則*と*グループ*が選択されています。
   + クリックして**場所**一覧の上部にあるローカル コンピューター名を選択します。
5. 入力**SQLRUserGroup**名前を確認およびグループを追加するには、[ok] をクリックします。
6. 入力**ALL APPLICATION PACKAGES**名前を確認および追加するには、[ok] をクリックします。 名前が解決しない場合は、ロケーション ステップを見直します。 SID は、マシンに対してローカルです。

両方のセキュリティ id が「パッケージ」サブ フォルダーとフォルダーに '読み取りと実行' の権限を持っていることを確認します。

<a name="call-method"></a>

## <a name="2---call-the-java-class"></a>2 - Java クラスを呼び出す

SQL Server からの Java コードを呼び出すストアド プロシージャ sp_execute_external_script の呼び出しを作成します。 「スクリプト」パラメーターでは、[パッケージ] を定義します。[クラス] を呼び出します。 このサンプルでのクラスが属している、という名前のパッケージに**pkg**というクラス ファイルと**RegexSample.java**します。

> [!NOTE]
>どのメソッドを呼び出すしない定義しています。 既定で、**実行**メソッドが呼び出されます。 つまり、次の SDK インターフェイスと、Java クラスの execute メソッドを実装する必要があることを SQL Server からクラスを呼び出せるようにする場合。

```sql
/*
This stored procedure takes an input query (input dataset) and a regular expression and returns the rows that fulfilled the given regular expression. This sample uses a regular expression that checks if a text contains the word "Java" or "java" ([Jj]ava) 
*/

CREATE OR ALTER PROCEDURE [dbo].[java_regex] @expr nvarchar(200), @query nvarchar(400)
AS
BEGIN
--Call the Java program by giving the package.className in @script
--The method invoked in the Java code is always the "execute" method
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'pkg.RegexSample'
, @input_data_1 = @query
, @params = N'@regexExpr nvarchar(200)'
, @regexExpr = @expr
with result sets ((ID int, text nvarchar(100)));
END
GO

--Now execute the above stored procedure and provide the regular expression and an input query
EXECUTE [dbo].[java_regex] N'[Jj]ava', N'SELECT id, text FROM testdata'
GO
```

### <a name="results"></a>[結果]

呼び出しを実行した後の 2 つの行を含む結果セットを取得する必要があります。

![Java サンプルの結果](../media/java/java-sample-results.png "サンプルの結果")

### <a name="if-you-get-an-error"></a>エラーが発生する場合

+ クラスをコンパイルするときに「パッケージ」のサブ フォルダーでは、コンパイルされたコードの 3 つすべてのクラスを含める必要があります。

+ 最後に、外部ライブラリを使用していない場合、このアクセス許可でチェック*各*ルートから外部のプロセスを実行するセキュリティ id の読み取りし、コードを実行するアクセス許可でいることを確認する、「パッケージ」サブ フォルダーへのフォルダー。

## <a name="next-steps"></a>次のステップ

+ [Microsoft 拡張機能の Microsoft SQL Server 用の Java SDK](java-sdk.md)
+ [SQL Server で Java を呼び出す方法](howto-call-java-from-sql.md)
+ [SQL Server での Java 拡張機能](extension-java.md)
+ [Java および SQL Server データ型](java-sql-datatypes.md)
