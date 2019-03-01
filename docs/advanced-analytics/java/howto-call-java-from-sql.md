---
title: SQL - SQL Server Machine Learning サービスから Java を呼び出す方法
description: Java のクラスを Java プログラミング言語の拡張機能で SQL Server 2019 を使用して SQL Server のストアド プロシージャから呼び出す方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/28/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 801ffe50ca83fbeda69a3172b5914d39373d643f
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017758"
---
# <a name="how-to-call-java-from-sql-server-2019-preview"></a>SQL Server 2019 プレビューから Java を呼び出す方法

使用する場合、 [Java 言語の拡張機能](extension-java.md)、 [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)システム ストアド プロシージャは、Java ランタイムを呼び出すために使用するインターフェイス。 Java でコードが実行に、データベースに対するアクセス許可が適用されます。

この記事では、Java のクラスと SQL Server で実行されるメソッドの実装の詳細について説明します。 これらの詳細について理解したら後でレビュー、 [Java サンプル](java-first-sample.md)として次の手順。

SQL Server での Java クラスを呼び出すための 2 つの方法はあります。

1. .Class または .jar ファイルを配置、 [Java classpath](#classpath)します。 これは、Windows と Linux の両方を使用できます。

2. .Jar ファイルおよびその他の依存関係を使用して、データベースにコンパイル済みのクラスをアップロード、[外部ライブラリ](#external-library)DDL。 このオプションは、Windows CTP 2.3 でのみ使用できます。 Linux サポートは、以降の CTP で追加されます。

> [!NOTE]
> 一般的な推奨事項、として、.jar ファイルおよび .class を単独ではないファイルを使用します。 これは Java での一般的な方法であり、簡単に全体的なエクスペリエンスが実現されます。 関連項目:[クラス ファイルから jar ファイルを作成する方法](extension-java.md#create-jar)します。

<a name="classpath"></a>

## <a name="classpath"></a>Classpath

### <a name="basic-principles"></a>基本原則

* コンパイル済みのカスタム Java クラスは、.class ファイルまたは、Java classpath の .jar ファイルに存在する必要があります。 [クラスパス パラメーター](#set-classpath)コンパイル済みの Java ファイルへのパスを提供します。 

* 呼び出している Java メソッドは、ストアド プロシージャの「スクリプト」パラメーターを指定する必要があります。

* クラスに属する場合、パッケージ、"packageName"を指定する必要があります。

* Java クラスにパラメーターを渡す"params"が使用されます。 引数を必要とするメソッドを呼び出すことはサポートされていません、パラメーター、メソッドに引数の値を渡す唯一の方法を使用します。 

> [!Note]
> この注の CTP では Java に固有の操作をサポートされているとサポートされていないように換言 2.x。
> * ストアド プロシージャでは、入力パラメーターがサポートされます。 出力パラメーターはありません。
> * Sp_execute_external_script パラメーターを使用してストリーミング@r_rowsPerReadはサポートされていません。
> * 使用してパーティション分割@input_data_1_partition_by_columnsはサポートされていません。
> * 並列処理を使用して@parallel= 1 はサポートされています。

### <a name="call-class"></a>クラスを呼び出します。

Windows と Linux の両方に適用可能な[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)システム ストアド プロシージャは、Java ランタイムを呼び出すために使用するインターフェイス。 次の例では、パス、スクリプト、およびカスタム コードを指定するための Java の拡張機能、およびパラメーターを使用して、sp_execute_external_script を示します。

```sql
DECLARE @myClassPath nvarchar(30)
DECLARE @param1 int

SET @myClassPath = N'/<my path>/program.jar'
SET @param1 = 3

EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'<packageName>.<ClassName>.<methodName>'
, @input_data_1 = N'<Input Query>'
, @params = N'@CLASSPATH nvarchar(30), @param1 INT'
, @CLASSPATH = @myClassPath
, @param1 = @param1
```

<a name="set-classpath"></a>

### <a name="set-classpath"></a>クラスパスを設定します。

Java クラスまたはクラスをコンパイルし、.class ファイルまたは .jar ファイルを Java classpath に配置されますが、SQL Server の Java の機能拡張するためのクラスパスに提供するための 2 つのオプションがあります。

**オプション 1:パラメーターとして渡す**

コンパイル済みコードへのパスを指定する方法の 1 つは、sp_execute_external_script プロシージャへの入力パラメーターとしてクラスパスを設定することです。 [Java サンプル](java-first-sample.md#call-method)この手法を実証します。 場合は、この方法を選択し、パスが複数ある、基になるオペレーティング システムに対して有効なパスの区切り文字を使用することを確認します。

* Linux では、コロン、クラスパス内のパスを区切ります。":"です。
* Windows、セミコロンでクラスパス内のパスを区切ります";"。

**オプション 2:システム変数を登録します。**

JDK の実行可能ファイルのシステム変数を作成したのと同様に、コード パスのシステム変数を作成できます。 "CLASSPATH"と呼ばれるシステム環境変数を作成してこれを行う

<a name="external-library"></a>

## <a name="external-library"></a>外部ライブラリ

SQL Server 2019 の CTP 2.3 では、Windows 上の Java 言語の外部ライブラリを使用できます。 同じ機能は今後の CTP での Linux で利用可能になります。 .Jar ファイルに、クラスをコンパイルして、.jar ファイルとその他の依存関係を使用して、データベースにアップロード、 [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) DDL。

外部ライブラリを使用した .jar ファイルをアップロードする方法の例:

```sql 
CREATE EXTERNAL LIBRARY myJar
FROM (CONTENT = '<local path to .jar file>') 
WITH (LANGUAGE = 'Java'); 
GO
```

外部ライブラリを作成すると、提供する必要はありません、[クラスパス](#classpath)sp_execute_external_script の呼び出しで。 SQL Server がアクセスする Java クラスには自動的にし、クラスパスに特殊なアクセス許可を設定する必要はありません。

パッケージからのクラスでメソッドを呼び出す例については、外部ライブラリとしてアップロード。

```sql
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'MyPackage.MyCLass.myMethod'
, @input_data_1 = N'SELECT * FROM MYTABLE'
with result sets ((column1 int))
```

詳細については、次を参照してください。 [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)します。

## <a name="class-requirements"></a>クラスの要件

SQL Server、Java ランタイムと通信するためには、特定の静的変数をクラスで実装する必要があります。 SQL Server は、Java 言語の拡張機能を使用して Java クラスと exchange のデータでメソッドを実行できます。

> [!Note]
> 実装の詳細を開発者のエクスペリエンスを向上させる努力を今後の Ctp で変更される予定です。

## <a name="method-requirements"></a>メソッドの要件
引数を渡すには使用、 @param sp_execute_external_script のパラメーター。 メソッド自体は、任意の引数を持つことはできません。 戻り値の型は void である必要があります。  

```java
public static void test()  {}
```

## <a name="data-inputs"></a>データ入力 

このセクションは、java を使用して SQL Server クエリからデータをプッシュする方法を説明します**InputDataSet** sp_execute_external_script でします。

入力列が、SQL クエリは、Java にプッシュごと、配列を宣言する必要があります。

### <a name="inputdatacol"></a>inputDataCol

Java 拡張機能の現在のバージョンで、 **inputDataColN**変数は、必要な*N*列番号です。 

```java
public static <type>[] inputDataColN = new <type>[1]
```

初期化する必要はこれらの配列 (配列のサイズ、0 より大きい値を指定する必要があるし、列の実際の長さを反映する必要はありません)。

例: `public static int[] inputDataCol1 = new int[1];`

呼び出している Java プログラムを実行する前に SQL server クエリからの入力データでは、これらの配列変数が表示されます。

### <a name="inputnullmap"></a>inputNullMap

Null のマップは、null 値を認識する、拡張機能によって使用されます。 SQL Server では、ユーザー関数の実行前にこの変数を null 値に関する情報が作成されます。

ユーザーは、この変数を初期化するためにのみ必要があります (および配列のサイズが 0 より大きい値を指定する必要があります)。

```java
public static boolean[][] inputNullMap = new boolean[1][1];
```

## <a name="data-outputs"></a>データ出力

このセクションについて説明します**OutputDataSet**を送信し、SQL Server で永続化できる Java から、出力データ セットが返されます。

> [!Note]
> 出力パラメーターで[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)は、このバージョンではサポートされていません。

### <a name="outputdatacoln"></a>outputDataColN

ような**inputDataSet**、Java プログラムは、SQL サーバーに送信すべての出力列の配列変数を宣言する必要があります。 すべて**outputDataCol**配列は同じ長さである必要があります。 クラスの実行の終了時刻によってこれが初期化されるかどうかを確認する必要があります。

```java
public static <type>[] outputDataColN = new <type>[]
```

### <a name="numberofoutputcols"></a>numberofOutputCols

ユーザー関数の実行の終了時に、予想される出力データ列の数には、この変数を設定します。

```java
public static short numberofOutputCols = <expected number of output columns>;
```

### <a name="outputnullmap"></a>outputNullMap

Null のマップは、null 値を示すために、拡張機能によって使用されます。 プリミティブ型を null にサポートしないためこれが必要です。 現時点では、私たちも map が必要です、null、文字列型の場合でも、文字列を null にすることができます。 Null 値は"true"で示されます。

この NullMap は、列と SQL Server に返す行の数で入力する必要があります。

```java
public static boolean[][] outputNullMap
```

## <a name="next-steps"></a>次のステップ

+ [SQL Server での Java サンプル](java-first-sample.md)
+ [Java および SQL Server データ型](java-sql-datatypes.md)
+ [SQL Server での Java 言語の拡張機能](extension-java.md)
