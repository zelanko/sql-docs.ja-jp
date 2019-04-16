---
title: Java サンプルとチュートリアルを SQL Server 2019 - SQL Server Machine Learning サービス
description: SQL Server のデータを Java 言語の拡張機能を使用するための手順については、SQL Server 2019 の Java サンプル コードを実行します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/27/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 25deba880827cc7396082dac9a2c86cc4dd66cd8
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582575"
---
# <a name="sql-server-java-sample-walkthrough"></a>SQL Server の Java サンプルのチュートリアル

この例では、SQL Server から 2 つの列 (ID および文字列) を受け取り、SQL Server (ID と ngram) に 2 つの列を返す Java クラスを示します。 指定した ID と文字列の組み合わせでは、コードには、元の ID と共にそれらの順列を返す ngrams (部分文字列) の順列が生成されます。 Ngram の長さは、Java クラスに送信されるパラメーターによって定義されます。

## <a name="prerequisites"></a>前提条件

+ Java 拡張機能のプログラミングと拡張性フレームワークでの SQL Server 2019 データベース エンジン インスタンス[Windows で](../install/sql-machine-learning-services-windows-install.md)または[on Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup)します。 システム構成の詳細については、次を参照してください。 [Java 言語の拡張機能で SQL Server 2019](extension-java.md)します。 コーディングの要件の詳細については、次を参照してください。 [SQL Server で Java を呼び出す方法](howto-call-java-from-sql.md)します。

+ SQL Server Management Studio または T-SQL を実行するための別のツール。

+ Java SE Development Kit (JDK) 8 on Windows または Linux。

コマンド ライン コンパイルを使用して**javac**でこのチュートリアルでは十分です。 

## <a name="1---load-sample-data"></a>1 - サンプル データを読み込む

最初に、作成し、設定、*レビュー*を持つテーブル**ID**と**テキスト**列。 SQL Server に接続し、テーブルを作成する次のスクリプトを実行します。

```sql
DROP TABLE IF exists reviews;
GO
CREATE TABLE reviews(
    id int NOT NULL,
    "text" nvarchar(30) NOT NULL)

INSERT INTO reviews(id, "text") VALUES (1, 'AAA BBB CCC DDD EEE FFF')
INSERT INTO reviews(id, "text") VALUES (2, 'GGG HHH III JJJ KKK LLL')
INSERT INTO reviews(id, "text") VALUES (3, 'MMM NNN OOO PPP QQQ RRR')
GO
```

## <a name="2---class-ngramjava"></a>2 - Class Ngram.java

まず、メイン クラスを作成します。 これは、最初の 3 つのクラスです。

この手順で作成と呼ばれるクラス**Ngram.java**し、そのファイルに次の Java コードをコピーします。 


```java
//We will package our classes in a package called pkg
//Packages are option in Java-SQL, but required for this sample.
package pkg;

import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.IntStream;

public class Ngram {

    //Required: This is only required if you are passing data in @input_data_1
    //from SQL Server in sp_execute_external_script
    public static int[] inputDataCol1 = new int[1];
    public static String[] inputDataCol2 = new String[1];

    //Required: Input null map. Size just needs to be set to "1"
    public static boolean[][] inputNullMap = new boolean[1][1];

    //Required: Output data columns returned back to SQL Server
    public static int[] outputDataCol1;
    public static String[] outputDataCol2;

    //Required: Output null map. Is populated with true or false values 
    //to indicate nulls
    public static boolean[][] outputNullMap;

    //Optional: This is only required if parameters are passed with @params
    // from SQL Server in sp_execute_external_script
    // n is giving us the size of ngram substrings
    public static int param1;

    //Optional: The number of rows we will be returning
    public static int numberOfRows;

    //Required: Number of output columns returned
    public static short numberOfOutputCols;

    /*Java main method - Only for testing purposes outside of SQL Server
    public static void main(String... args) {
        //getNGrams();
    }*/

    //This is the method we will be calling from SQL Server
    public static void getNGrams() {

        System.out.println("inputDataCol1.length= "+ inputDataCol1.length);
        if (inputDataCol1.length == 0 ) {
            // TODO: Set empty return
            return;
        }
        //Using a stream to "loop" over the input data inputDataCol1.length. You can also use a for loop for this.
        final List<InputRow> inputDataSet = IntStream.range(0, inputDataCol1.length)
                .mapToObj(i -> new InputRow(inputDataCol1[i], inputDataCol2[i]))
                .collect(Collectors.toList());


        //Again, we are using a stream to loop over data
        final List<OutputRow> outputDataSet = inputDataSet.stream()
                // Generate ngrams of size n for each incoming string
                // Each invocation of ngrams returns a list. flatMap flattens
                // the resulting list-of-lists to a flat list.
                .flatMap(inputRow -> ngrams(param1, inputRow.text).stream().map(s -> new OutputRow(inputRow.id, s)))
                .collect(Collectors.toList());

        //Print the outputDataSet
        System.out.println(outputDataSet);

        //Set the number of rows and columns we will be returning
        numberOfOutputCols = 2;
        numberOfRows = outputDataSet.size();
        outputDataCol1 = new int[numberOfRows]; // ID column
        outputDataCol2 = new String[numberOfRows]; //The ngram column
        outputNullMap = new boolean[2][numberOfRows];// output null map

        //Since we don't have any null values, we will populate all values in the outputNullMap to false
        IntStream.range(0, numberOfRows).forEach(i -> {
            final OutputRow outputRow = outputDataSet.get(i);
            outputDataCol1[i] = outputRow.id;
            outputDataCol2[i] = outputRow.ngram;
            outputNullMap[0][i] = false;
            outputNullMap[1][i] = false;
        });
    }

    // Example: ngrams(3, "abcde") = ["abc", "bcd", "cde"].
    private static List<String> ngrams(int n, String text) {
        return IntStream.range(0, text.length() - n + 1)
                .mapToObj(i -> text.substring(i, i + n))
                .collect(Collectors.toList());
    }
}
```

## <a name="3---class-inputrowjava"></a>3-クラス InputRow.java

呼ばれる 2 番目のクラスを作成する**InputRow.java**、次のコードから成るおよびと同じ場所に保存**Ngram.java**します。

```java
package pkg;

//This object represents one input row
public class InputRow {
    public final int id;
    public final String text;

    public InputRow(final int id, final String text) {
        this.id = id;
        this.text = text;
    }
}
```

## <a name="4---class-outputrowjava"></a>4-クラス OutputRow.java

3 番目と最後のクラスと呼びます**OutputRow.java**します。 コードをコピーし、他の場合と同じ場所に OutputRow.java として保存します。

```java
package pkg;

//This object represents one output row
public class OutputRow {
    public final int id;
    public final String ngram;

    public OutputRow(final int id, final String ngram) {
        this.id = id;
        this.ngram = ngram;
    }

    @Override
    public String toString() { return id + ":" + ngram; }
}
```

## <a name="5---compile"></a>5-コンパイル

Javac".class"ファイルにコンパイルを実行する準備ができて、クラスを用意したら (`javac Ngram.java InputRow.java OutputRow.java`)。 (Ngram.class、InputRow.class、および OutputRow.class) は、このサンプルの 3 つのクラス ファイルを取得する必要があります。

Classpath の場所に「パッケージ」をという名前のサブフォルダーには、コンパイル済みコードを配置します。 開発用ワークステーションで作業している場合、この手順は、SQL Server コンピューターにファイルをコピーするには。

クラスパスは、コンパイル済みコードの場所です。 たとえば、Linux では、クラスパスは、する場合 '/ホーム/myclasspath/' の '/ホーム/myclasspath/pkg'.class ファイルである必要があります。 スクリプトの例では、手順 7. で、sp_execute_external_script で提供される CLASSPATH が '/ホーム/myclasspath ' (Linux の場合)。 

Windows での使用をお勧め比較的浅いフォルダー構造、1 つまたは 2 階のアクセス許可を簡略化します。 たとえば、クラスパスようになります 'C:\myJavaCode' コンパイル済みのクラスを含む ' \pkg' という名前のサブフォルダーにします。 

Classpath の詳細については、次を参照してください。[クラスパスの設定](howto-call-java-from-sql.md#set-classpath)します。 

### <a name="using-jar-files"></a>.Jar ファイルを使用します。

クラスと依存関係に .jar ファイルをパッケージ化する場合は、sp_execute_external_script のクラスパス パラメーター内の .jar ファイルへの完全パスを提供します。 たとえば、jar ファイルには、'ngram.jar' を呼び出すと、クラスパスなります '/home/myclasspath/ngram.jar' on Linux。

## <a name="6---create-external-library"></a>6 - 外部ライブラリを作成します。

外部ライブラリを作成すると、SQL Server は自動的に、jar にやアクセスのクラスパスに特殊なアクセス許可を設定する必要はありません。

```sql 
CREATE EXTERNAL LIBRARY ngram
FROM (CONTENT = '<path>/ngram.jar') 
WITH (LANGUAGE = 'Java'); 
GO
```

## <a name="7---set-permissions-skip-if-you-performed-step-6"></a>7-アクセス許可 (スキップ手順 6 を実行した場合) を設定します。

外部ライブラリを使用する場合は、この手順は必要ありません。 推奨作業の方法では、jar をから外部ライブラリを作成します。 

外部ライブラリを使用しない場合は、必要なアクセス許可を設定する必要があります。 スクリプトの実行は、プロセス id が、コードにアクセスしている場合にのみ成功します。 

### <a name="on-linux"></a>On Linux

クラスパスをに対する読み取り/実行の権限の付与、 **mssql_satellite**ユーザー。

### <a name="on-windows"></a>Windows で

'読み取りと実行' アクセス許可を付与**SQLRUserGroup**と**すべてのアプリケーション パッケージ**コンパイル済みの Java コードを含むフォルダーの SID。 

ツリー全体は、アクセス許可がある、ルートからを利用するサブフォルダー親、最後にする必要があります。 
 
1. フォルダー (たとえば、' C:\myJavaCode') を右クリックし、選択**プロパティ** > **セキュリティ**します。
2. **[編集]** をクリックします。
3. **[追加]** をクリックします。
4. **ユーザー、コンピューター、サービス アカウント、またはグループを選択します**:。
   + をクリックして**オブジェクトの種類**を確認して*組み込みのセキュリティ原則*と*グループ*が選択されています。
   + クリックして**場所**一覧の上部にあるローカル コンピューター名を選択します。
5. 入力**SQLRUserGroup**名前を確認およびグループを追加するには、[ok] をクリックします。
6. 入力**ALL APPLICATION PACKAGES**名前を確認および追加するには、[ok] をクリックします。 名前が解決しない場合は、ロケーション ステップを見直します。 SID は、マシンに対してローカルです。

両方のセキュリティ id は、フォルダーとサブフォルダーの「パッケージ」の '読み取りと実行' の権限を持っていることを確認します。

<a name="call-method"></a>

## <a name="8---call-getngrams"></a>8 - Call *getNgrams()*

SQL Server からコードを呼び出す Java メソッドを指定**getNgrams()** sp_execute_external_script の「スクリプト」パラメーターにします。 このメソッドは、「パッケージ」と"という名前のクラス ファイル"というパッケージに属する**Ngram.java**します。

この例では、Java ファイルへのパスを提供するクラスパス パラメーターを渡します。 また、Java クラスにパラメーターを渡す"params"も使用します。 そのクラスパスは 30 文字を超えていないことを確認します。 その場合は、以下のスクリプトの値を増やします。

+ Linux では、SQL Server Management Studio または TRANSACT-SQL を実行するために使用されるもう 1 つのツールで次のコードを実行します。 

+ Windows では、変更@myClassPathN'C:\myJavaCode に\'(\pkg の親フォルダーがあると仮定) SQL Server Management Studio または他のツールでクエリを実行する前にします。

```sql
DECLARE @myClassPath nvarchar(50)
DECLARE @n int 
--This is where you store your classes or jars.
--This is the size of the ngram
SET @n = 3
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'pkg.Ngram.getNGrams'
, @input_data_1 = N'SELECT id, text FROM reviews'
, @parallel = 0
, @params = N'@param1 INT'
, @param1 = @n
with result sets ((ID int, ngram varchar(20)))
GO
```

### <a name="results"></a>[結果]

呼び出しを実行した後、2 つの列を示す結果セットが表示されます。

![Java サンプルの結果](../media/java/java-sample-results.png "サンプルの結果")

### <a name="if-you-get-an-error"></a>エラーが発生する場合

+ クラスをコンパイルするときに、「パッケージ」サブフォルダーは、コンパイルされたコードの 3 つすべてのクラスを含める必要があります。

+ Classpath の長さは、宣言された値を超えることはできません (`DECLARE @myClassPath nvarchar(50)`)。 場合は、パスは、最初の 50 文字に切り捨てられ、コンパイル済みのコードは読み込まれません。 行うことができます、`SELECT @myClassPath`値をチェックします。 50 文字が十分でない場合は、長さを拡張します。 

+ 最後に、アクセス許可を確認*各*ルートから外部のプロセスを実行するセキュリティ id の読み取りし、コードを実行するアクセス許可でいることを確認する、「パッケージ」のサブフォルダーへのフォルダー。

## <a name="see-also"></a>関連項目

+ [SQL Server で Java を呼び出す方法](howto-call-java-from-sql.md)
+ [SQL Server での Java 拡張機能](extension-java.md)
+ [Java および SQL Server データ型](java-sql-datatypes.md)
