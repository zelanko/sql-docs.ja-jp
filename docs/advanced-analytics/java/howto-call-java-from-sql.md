---
title: SQL - SQL Server Machine Learning サービスから Java を呼び出す方法
description: Java のクラスを Java プログラミング言語の拡張機能で SQL Server 2019 を使用して SQL Server のストアド プロシージャから呼び出す方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a75878ccc4f14d03f84102dd48bfd43a6e04daea
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473553"
---
# <a name="how-to-call-java-from-sql-server-2019-preview"></a>SQL Server 2019 プレビューから Java を呼び出す方法

使用する場合、 [Java 言語の拡張機能](extension-java.md)、 [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)システム ストアド プロシージャは、Java ランタイムを呼び出すために使用するインターフェイス。 Java でコードが実行に、データベースに対するアクセス許可が適用されます。

この記事では、Java のクラスと SQL Server で実行されるメソッドの実装の詳細について説明します。 これらの詳細について理解したら後でレビュー、 [Java サンプル](java-first-sample.md)として次の手順。

SQL Server での Java クラスを呼び出すための 2 つの方法はあります。

1. .Class または .jar ファイルを配置、 [Java classpath](#classpath)します。 これは、Windows と Linux の両方を使用できます。

2. .Jar ファイルおよびその他の依存関係を使用して、データベースにコンパイル済みのクラスをアップロード、[外部ライブラリ](#external-library)DDL。 このオプションは、Windows および Linux CTP 2.4 から使用できます。

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

### <a name="call-java-class"></a>Java クラスを呼び出します。

Windows と Linux の両方に適用可能な[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)システム ストアド プロシージャは、Java ランタイムを呼び出すために使用するインターフェイス。 次の例では、パス、スクリプト、およびカスタム コードを指定するための Java の拡張機能、およびパラメーターを使用して、sp_execute_external_script を示します。

> [!NOTE]
> 呼び出すメソッドを定義する必要があることに注意してください。 既定では、メソッドが呼び出される**実行**が呼び出されます。 つまり、次の SDK と Java クラスでは execute メソッドを実装する必要があります。

```sql
DECLARE @param1 int
SET @param1 = 3

EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'<packageName>.<ClassName>'
, @input_data_1 = N'<Input Query>'
, @param1 = @param1
```

<a name="set-classpath"></a>

### <a name="set-classpath"></a>クラスパスを設定します。

1 回または複数の Java クラスをコンパイルして jar ファイルを作成するには、Java classpath を使用して SQL Server の Java の機能拡張するためのクラスパスに提供するための 2 つのオプション。

**オプション 1:外部ライブラリを使用して**最も簡単なオプションは SQL Server の外部ライブラリを作成し、jar をライブラリをポイントして、クラスを自動的に検出します。 [Java 用の外部ライブラリを使用します。](howto-call-java-from-sql.md#external-library)

**オプション 2:システム環境変数を登録します。**

Java ランタイムのシステム環境変数を作成したのと同様は、システム環境変数を作成し、クラスを含む jar ファイルのパスを指定します。 これを行うには、「クラスパス」と呼ばれるシステム環境変数を作成する必要があります。

<a name="external-library"></a>

## <a name="external-library"></a>外部ライブラリ

SQL Server 2019 CTP 2.4 では、Windows および Linux で Java 言語の外部ライブラリを使用できます。 .Jar ファイルに、クラスをコンパイルして、.jar ファイルとその他の依存関係を使用して、データベースにアップロード、 [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) DDL。

外部ライブラリを使用した .jar ファイルをアップロードする方法の例:

```sql 
CREATE EXTERNAL LIBRARY myJar
FROM (CONTENT = '<local path to .jar file>') 
WITH (LANGUAGE = 'Java'); 
GO
```

外部ライブラリを作成すると、SQL Server がアクセスする Java クラスには自動的にし、クラスパスに特殊なアクセス許可を設定する必要はありません。

パッケージからのクラスでメソッドを呼び出す例については、外部ライブラリとしてアップロード。

```sql
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'MyPackage.MyCLass'
, @input_data_1 = N'SELECT * FROM MYTABLE'
with result sets ((column1 int))
```

詳細については、次を参照してください。 [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)します。

## <a name="next-steps"></a>次のステップ

+ [SQL Server での Java サンプル](java-first-sample.md)
+ [Java および SQL Server データ型](java-sql-datatypes.md)
+ [SQL Server での Java 言語の拡張機能](extension-java.md)
