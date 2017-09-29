---
title: "SQL クライアントのプログラミングのホームページ |Microsoft ドキュメント"
description: "注釈付きへのリンクのダウンロードとドキュメントの言語と SQL Server または Azure SQL Database に接続するためのオペレーティング システムのさまざまな組み合わせをハブ ページ。"
author: MightyPen
ms.date: 09/13/2017
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.topic: article
ms.reviewer: meetb
ms.author: genemi
ms.translationtype: MT
ms.sourcegitcommit: 71ca2fac0a6b9f087f9d434c5a701f5656889b9e
ms.openlocfilehash: 000325a2e2c53e36f7a74a725962b8dd3be98988
ms.contentlocale: ja-jp
ms.lasthandoff: 09/13/2017

---
# <a name="homepage-for-client-programming-to-microsoft-sql-server"></a>クライアントの Microsoft SQL Server へのプログラミングのホームページ


クライアントの Microsoft SQL Server、およびクラウドで Azure SQL Database とのやり取りを行いますにプログラミングに関するマイクロソフトのホーム ページへようこそ。 この記事では、次の情報を示します。

- 使用可能な言語とドライバーの組み合わせを示しています。
    - Linux (Ubuntu など)、MacOS、および Windows オペレーティング システム用の情報が与えられます。
- 各組み合わせの詳細な説明へのリンクを提供します。
- 適切な場所、領域と特定の言語で階層的なドキュメントのサブエリアを表示します。


#### <a name="azure-sql-database"></a>Azure SQL データベース

、任意の言語では、SQL Server に接続するコードは Azure SQL Database に接続するためのコードとほぼ同じです。

詳細については、Azure SQL Database に接続するための接続文字列を参照してください。

- [.NET Core (c#) を使用して Azure SQL データベースのクエリを](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core)です。
- 他の言語は、内容の前の表に、アーティクルの近くにあるその他の Azure SQL Database には。 たとえばを参照してください[Azure SQL データベースに対してクエリを使用して PHP](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php)です。


#### <a name="build-an-app-webpages"></a>ビルドのアプリ、web ページ

当社*ビルドでアプリを*web ページが別の形式でのコード例については、構成情報と共にを提示します。 詳細については、この記事の後半を参照してください、[というラベルの付いたセクション*ビルドのアプリ、web サイト*](#an-204-aka-ms-sqldev)です。



<a name="an-050-languages-clients" />

## <a name="languages-and-drivers-for-client-programs"></a>言語およびクライアント プログラム用のドライバー


次の表では、各言語のイメージは、SQL Server での言語の使用に関する詳細な情報へのリンクがします。 各リンクは、この記事で、後のセクションにジャンプします。

| &nbsp; | &nbsp; | &nbsp; |
| :-- | :-- | :-- |
| &nbsp;[![C# のロゴ][イメージの ref-320-csharp]](#an-110-ado-net-docu) | &nbsp;[![ORM Entity Framework での .NET Framework][イメージの ref-333-ef]](#an-116-csharp-ef-orm) | &nbsp;[![Java ロゴ][イメージの ref-330-java]](#an-130-jdbc-docu) |
| &nbsp;[![Node.js のロゴ][イメージの ref-340-node]](#an-140-node-js-docu) | &nbsp; [**`ODBC for C++`**](#an-160-odbc-cpp-docu) | &nbsp;[![PHP のロゴ][イメージの ref-360-php]](#an-170-php-docu) |
| &nbsp;[![Python ロゴ][イメージの ref-370-python]](#an-180-python-docu) | &nbsp;[![Ruby ロゴ][イメージの ref-380-ruby]](#an-190-ruby-docu) | &nbsp; ... |
| &nbsp; | &nbsp; | <br />|


#### <a name="downloads-and-installs"></a>ダウンロードとインストール

次の記事では、ダウンロードに使用し、プログラミング言語で使用するためのさまざまな SQL 接続ドライバーをインストールします。

- [SQL Server ドライバー](sql-server-drivers.md)



<a name="an-110-ado-net-docu" />

## <a name="c-logoimage-ref-320-csharp-c-using-adonet"></a>![C# のロゴ][image-ref-320-csharp] ADO.NET を使用して、C#

C# および Visual Basic などの .NET マネージ言語とは、ADO.NET の最も一般的なユーザーです。 *ADO.NET* .NET Framework のクラスのサブセットの一般レベルの名前を指定します。

#### <a name="code-examples"></a>コード例

|||
| :-- | :-- |
| [ADO.NET を使用して SQL に接続する概念実証](./ado-net/step-3-proof-of-concept-connecting-to-sql-using-ado-net.md) | 接続して、SQL Server へのクエリに重点を置きます小さなコードの例です。 |
| [ADO.NET を使用した SQL に弾性的に接続します。](./ado-net/step-4-connect-resiliently-to-sql-with-ado-net.md) | 接続から接続が失われるの瞬間をときどき発生する可能性があるために、コード例では、ロジックを再試行してください。<br /><br />再試行ロジックを使用して管理、インターネット、どのクラウド データベースになど、Azure SQL Database への接続にも適用されます。 |
| [接続してクエリを Windows または Linux/macos .NET Core を使用して、c# プログラムを作成する方法の azure SQL データベース: デモ](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core) | Azure SQL データベースの例です。 |
| [C# の場合、ADO.NET、Windows アプリをビルドします。](http://www.microsoft.com/sql-server/developer-get-started/csharp/win/) | 構成については、コード例も紹介します。 |
| &nbsp; | <br /> |

#### <a name="documentation"></a>ドキュメント

|||
| :-- | :-- |
| [ADO.NET を使用して、C#](./ado-net/index.md)| こちらのドキュメントのルートです。 |
| [Namespace: System.Data](http://docs.microsoft.com/dotnet/api/system.data) | ADO.NET を使用するクラスのセット。 |
| [Namespace: System.Data.SqlClient](http://docs.microsoft.com/dotnet/api/system.data.SqlClient) | 最も直接的な ADO.NET のセンターではクラスのセット。 |
| &nbsp; | <br /> |



<a name="an-116-csharp-ef-orm" />

## <a name="entity-framework-logoimage-ref-333-ef-entity-framework-ef-with-cx23"></a>![Entity Framework のロゴ][image-ref-333-ef] C&#x23; entity Framework (EF)

Entity Framework (EF) は、オブジェクト リレーショナル マッピング (ORM) を提供します。 ORM では、SQL リレーショナル データベースから取得されたデータを操作するオブジェクト指向プログラミング (OOP) ソース コードを簡単にします。

EF には、次のテクノロジに直接的または間接的なリレーションシップがあります。

- .NET Framework
- [LINQ to SQL](http://docs.microsoft.com/dotnet/framework/data/adonet/sql/linq/)、または[LINQ to Entities](http://docs.microsoft.com/dotnet/framework/data/adonet/ef/language-reference/linq-to-entities)
- 言語の構文の機能強化など、 ** => ** (C#) 演算子。
- SQL データベースのテーブルにマップされるクラスのソース コードを生成する便利なプログラムです。 たとえば、 [EdmGen.exe](http://docs.microsoft.com/dotnet/framework/data/adonet/ef/edm-generator-edmgen-exe)です。


#### <a name="original-ef-and-new-ef"></a>元の EF と新しい EF

[Entity Framework 用のスタート ページ](http://docs.microsoft.com/ef/)には、次のような説明と EF が導入されています。

- Entity Framework は、.NET 開発者は .NET オブジェクトを使用してデータベースを使用するオブジェクト リレーショナル マッパー (O/RM) です。 これにより、開発者は、通常記述する必要のあるデータ アクセスのソース コードのほとんどの必要があります。

*Entity Framework* 2 つの別々 のソース コードの分岐で共有の名前を指定します。 EF の 1 つの分岐が古いと、そのソース コードは、パブリック管理ようになりましたことができます。 その他の EF は新しいです。 2 つの EFs は次のとおりです。

|     |     |
| :-- | :-- |
| [EF 6.x](http://docs.microsoft.com/ef/ef6/) | まず、Microsoft では、EF が 2008 年 8 月にリリースしました。 Microsoft では 2015 年 3 月に発表される EF 6.x が最終の Microsoft を開発します。 Microsoft では、パブリック ドメインにソース コードをリリースしました。<br /><br />最初に .NET Framework の一部であった EF です。 EF 6.x が .NET Framework から削除されました。<br /><br />[Github のリポジトリ内の EF 6.x ソース コード*aspnet/EntityFramework6*](http://github.com/aspnet/EntityFramework6) |
| [EF コア](http://docs.microsoft.com/ef/core/) | Microsoft では、2016 年 6 月で、新しく作成した EF コアをリリースしました。 EF コアは、柔軟性と移植性の向上のために設計されています。 EF コアは、Microsoft Windows 以外のオペレーティング システムで実行できます。 EF コアは、Microsoft SQL Server だけを超えるデータベースとその他のリレーショナル データベースと対話できます。<br /><br />**C&#x23;コードの例:**<br />[Entity Framework Core の概要](https://docs.microsoft.com/ef/core/get-started/index)<br />[EF Core 既存のデータベースでの .NET Framework の使用を開始します。](https://docs.microsoft.com/ef/core/get-started/full-dotnet/existing-db) |
| &nbsp; | <br /> |

EF と関連するテクノロジは強力ですが、なり領域全体を習得するには、開発者の学習に多くなります。

&nbsp;



<a name="an-130-jdbc-docu" />

## <a name="java-logoimage-ref-330-java-java-and-jdbc"></a>![Java ロゴ][image-ref-330-java] Java と JDBC

Microsoft は、SQL Server と (またはもちろん、Azure SQL データベース) を使用する Java Database Connectivity (JDBC) ドライバーを提供します。 Type 4 JDBC ドライバーであるし、標準の JDBC アプリケーション プログラム インターフェイス (Api) によって、データベース接続を提供します。

#### <a name="code-examples"></a>コード例

|||
| :-- | :-- |
| [コード例](./jdbc/code-samples/index.md) | データ型、結果セット、および大規模なデータについて説明するコード例です。 |
| [接続 URL のサンプル](./jdbc/connection-url-sample.md) | 接続 URL を使用して、SQL Server に接続する方法について説明します。 使用して、SQL ステートメントを使用してデータを取得します。 |
| [データ ソースのサンプル](./jdbc/data-source-sample.md) | データ ソースを使用して、SQL Server に接続する方法について説明します。 ストアド プロシージャを使用して、データを取得します。 |
| [Java を使用して Azure SQL データベースのクエリ](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java) | Azure SQL データベースの例です。 |
| [Ubuntu で SQL Server を使用して Java アプリケーションを作成します。](http://www.microsoft.com/sql-server/developer-get-started/java/ubuntu/) | 構成については、コード例も紹介します。 |
| &nbsp; | <br /> |

#### <a name="documentation"></a>ドキュメント

JDBC のドキュメントには、次の主要な領域が含まれています。

|||
| :-- | :-- |
| [Java Database Connectivity (JDBC)](./jdbc/index.md) | この JDBC ドキュメントのルートです。 |
| [リファレンス](./jdbc/reference/index.md) | インターフェイス、クラス、およびメンバー。 |
| [JDBC SQL ドライバーのガイドのプログラミング](./jdbc/programming-guide-for-jdbc-sql-driver.md) | 構成については、コード例も紹介します。 |
| &nbsp; | <br /> |



<a name="an-140-node-js-docu" />

## <a name="nodejs-logoimage-ref-340-node-nodejs"></a>![Node.js のロゴ][image-ref-340-node] Node.js

Windows、Linux、またはファルダから Node.js に SQL Server に接続できます。 Node.js ドキュメントのルートは[ここ](./node-js/index.md)です。

SQL Server 用の Node.js 接続ドライバーは、JavaScript で実装されます。 ドライバーは、すべての最新バージョンの SQL Server でサポートされている TDS プロトコルを使用します。 ドライバーは、オープン ソース プロジェクト[Github で利用可能](http://tediousjs.github.io/tedious/)です。

#### <a name="code-examples"></a>コード例

|||
| :-- | :-- |
| [Node.js を使用して SQL に接続する概念実証](./node-js/step-3-proof-of-concept-connecting-to-sql-using-node-js.md) | 骨は、SQL Server に接続し、クエリを実行するためのコードをソースです。 |
| [Azure SQL データベース: クエリに Node.js を使用します。](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | クラウド内の Azure SQL データベースの例です。 |
| [サーバーを使用する SQL macos Node.js アプリケーションを作成します。](http://www.microsoft.com/sql-server/developer-get-started/node/mac/) | 構成については、コード例も紹介します。 |
| &nbsp; | <br /> |



<a name="an-160-odbc-cpp-docu" />

## <a name="odbc-for-c"></a>C++ 用の ODBC 

![ODBC のロゴ][image-ref-350-odbc]

、1990 年代に開発されたオープン データベース コネクティビティ (ODBC) と .NET Framework が日付より前です。 ODBC は、任意の特定のデータベース システムから独立しており、別のオペレーティング システムに設計されています。

長年にわたって多数の ODBC ドライバーに作成およびグループ内で、Microsoft の外部でリリースします。 ドライバーの範囲には、いくつかのクライアントのプログラミング言語が含まれます。 データ ターゲットの一覧は、SQL Server 以外の操作も移動します。

その他の接続のドライバーによっては、ODBC を内部的に使用します。

#### <a name="code-example"></a>コード例

- [ODBC を使用して、C++ コードの例](../odbc/reference/sample-odbc-program.md)

#### <a name="documentation-outline"></a>ドキュメントのアウトライン

このセクションで、ODBC のコンテンツは、C++ から SQL Server または Azure SQL Database のいずれかへのアクセスについて説明します。 次の表には、ODBC 用の主要なドキュメントのおおよそのアウトラインが一覧表示します。


| 領域 | サブエリア | Description |
| :--- | :------ | :---------- |
| [C++ 用の ODBC](./odbc/index.md) | こちらのドキュメントのルートです。 |
| [Linux Mac](./odbc/linux-mac/index.md) | &nbsp; | Linux または MacOS オペレーティング システム上の ODBC の使用に関する情報。 |
| [Windows](./odbc/windows/index.md)     | &nbsp; | Windows オペレーティング システム上の ODBC の使用に関する情報。 |
| [管理](../odbc/admin/index.md) | &nbsp; | ODBC データ ソースの管理用の管理ツールです。 |
| [Microsoft](../odbc/microsoft/index.md)  | &nbsp; | 作成され、Microsoft によって提供されるさまざまな ODBC ドライバー。 |
| [概念とリファレンス](../odbc/reference/index.md) | &nbsp; | 従来の参照だけでなく、ODBC インターフェイスの概念に関する情報。 |
| &nbsp; " | [付録](../odbc/reference/appendixes/index.md)    | 移行テーブルや ODBC カーソル ライブラリを記述します。 |
| &nbsp; " | [アプリを開発します。](../odbc/reference/develop-app/index.md)  | 関数、ハンドル、および多くの場合は。 |
| &nbsp; " | [ドライバーを開発します。](../odbc/reference/develop-driver/index.md) | 特殊なデータ ソースがある場合は、ODBC ドライバーを開発する方法です。 |
| &nbsp; " | [インストール](../odbc/reference/install/index.md) | ODBC のインストール、サブキー、およびその他。 |
| &nbsp; " | [構文](../odbc/reference/syntax/index.md)   | セットアップ、インストーラー、翻訳、およびデータ アクセス Api。 |
| &nbsp; | &nbsp; | <br /> |



<a name="an-170-php-docu" />

## <a name="php-logoimage-ref-360-php-php"></a>![PHP のロゴ][image-ref-360-php] PHP (PHP)

PHP を使用して、SQL Server と対話することができます。 Node.js ドキュメントのルートは[ここ](./php/index.md)です。

#### <a name="code-examples"></a>コード例

|||
| :-- | :-- |
| [PHP を使用して SQL に接続する概念実証](./php/step-3-proof-of-concept-connecting-to-sql-using-php.md) | 接続して、SQL Server へのクエリに重点を置きます小さなコードの例です。 |
| [PHP で SQL に弾性的に接続します。](./php/step-4-connect-resiliently-to-sql-with-php.md) | インターネットとクラウド経由での接続から接続が失われるの瞬間をときどき発生する可能性があるために、コード例では、ロジックを再試行してください。 |
| [Azure SQL データベース: クエリに PHP を使用します。](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php) | Azure SQL データベースの例です。 |
| [RHEL で SQL Server を使用する PHP アプリケーションを作成します。](http://www.microsoft.com/sql-server/developer-get-started/php/rhel/) | 構成については、コード例も紹介します。 |
| &nbsp; | <br /> |



<a name="an-180-python-docu" />

## <a name="python-logoimage-ref-370-python-python"></a>![Python のロゴ][image-ref-370-python] Python


Python を使用して、SQL Server と対話することができます。

#### <a name="code-examples"></a>コード例

|||
| :-- | :-- |
| [Pyodbc を使用して Python の SQL に接続する概念実証](./python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc.md) | 接続して、SQL Server へのクエリに重点を置きます小さなコードの例です。 |
| [Azure SQL データベース: クエリに使用する Python](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-python) | Azure SQL データベースの例です。 |
| [SLES で SQL Server を使用する PHP アプリケーションを作成します。](http://www.microsoft.com/sql-server/developer-get-started/python/sles/) | 構成については、コード例も紹介します。 |
| &nbsp; | <br /> |

#### <a name="documentation"></a>ドキュメント

| 領域 | Description |
| :--- | :---------- |
| [SQL Server への Python](./python/index.md) | こちらのドキュメントのルートです。 |
| [pymssql ドライバー](./python/pymssql/index.md) | Microsoft の管理やしません pymssql ドライバーをテストします。<br /><br />Pymssql 接続ドライバーは、Python のプログラムで使用するための SQL データベースに単純なインターフェイスです。 Pymssql は、Microsoft SQL Server に Python DB API (PEP 249) インターフェイスを提供する、FreeTDS 上に構築します。 |
| [pyodbc ドライバー](./python/pyodbc/index.md)   | Pyodbc 接続ドライバーは、簡単にアクセスする ODBC データベースをオープン ソース Python モジュールです。 DB API 2.0 仕様を実装しているが、さらに多くの Pythonic 利便性が装備されています。 |
| &nbsp; | <br /> |


<a name="an-190-ruby-docu" />

## <a name="ruby-logoimage-ref-380-ruby-ruby"></a>![ルビのロゴ][image-ref-380-ruby] Ruby

Ruby を使用して、SQL Server と対話することができます。 Ruby、ドキュメントのルートは[ここ](./ruby/index.md)です。

#### <a name="code-examples"></a>コード例

|||
| :-- | :-- |
| [Ruby SQL に接続する概念実証](./ruby/step-3-proof-of-concept-connecting-to-sql-using-ruby.md) | 接続して、SQL Server へのクエリに重点を置きます小さなコードの例です。 |
| [Azure SQL データベース: クエリへのルビの使用](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ruby) | Azure SQL データベースの例です。 |
| [MacOS で SQL Server を使用するアプリは、ルビ作成します。](http://www.microsoft.com/sql-server/developer-get-started/ruby/mac/) | 構成については、コード例も紹介します。 |
| &nbsp; | <br /> |



<a name="an-204-aka-ms-sqldev" />

## <a name="build-an-app-website-for-sql-client-developmenthttpwwwmicrosoftcomsql-serverdeveloper-get-started"></a>[ビルドのアプリ、web サイトの SQL クライアントの開発用](http://www.microsoft.com/sql-server/developer-get-started/)


[*ビルドでアプリを*](https://www.microsoft.com/sql-server/developer-get-started/) web ページのプログラミング言語が SQL Server に接続するための長い一覧から選択できます。 クライアント プログラムは、さまざまなオペレーティング システムを実行できます。

*ビルドのアプリを*始めたばかり開発者簡潔さと完全性を強調します。 手順では、次のタスクについて説明します。

1. Microsoft SQL Server をインストールする方法
2. ダウンロードし、ツールとドライバーをインストールする方法。
3. 選択したオペレーティング システムに応じて、いずれの必要な構成を作成する方法です。
4. 指定されたソース コードをコンパイルする方法。
5. プログラムを実行する方法。

次に、web サイトで提供される詳細の概数、いくつかの輪郭は。

#### <a name="java-on-ubuntu"></a>Ubuntu で Java:

1. 環境を設定します
    - SQL Server のインストール手順 1.1
    - 手順 1.2 インストール Java
    - 手順 1.3 Java Development Kit (JDK) をインストールします。
    - 手順 1.4 インストール Maven
2. SQL Server と Java アプリケーションを作成します。
    - 手順 2.1 は、SQL Server に接続し、クエリを実行する Java アプリケーションを作成します。
    - 手順 2.2 が休止状態の一般的なフレームワークを使用して SQL Server に接続する Java アプリケーションを作成します。
3. 最大で 100 倍 Java アプリを高速化します。
    - 列ストア インデックスを示すために手順 3.1 作成 Java アプリ

#### <a name="python-on-windows"></a>Windows での Python:

1. 環境を設定します
    - SQL Server のインストール手順 1.1
    - 手順 1.2 インストール Python
    - 手順 1.3 SQL Server 用 ODBC ドライバーと SQL コマンド ライン ユーティリティをインストールします。
2. SQL Server での Python アプリケーションを作成します。
    - 手順 2.1 では、SQL Server 用 Python ドライバーをインストールします。
    - 手順 2.2、アプリケーションのデータベースを作成します。
    - 手順 2.3 SQL Server に接続し、クエリを実行する Python アプリケーションを作成します。
3. 最大で 100 倍 Python アプリを高速化します。
    - 手順 3.1 500万 sqlcmd を使用すると、新しいテーブルを作成します。
    - 3.2 の手順は、このテーブルのクエリを実行し、実行時間を測定する Python アプリを作成します。
    - 3.3 の手順は、クエリの実行にかかる時間を測定します。
    - 手順 3.4 追加、テーブルに列ストア インデックス
    - 列ストア インデックスを持つクエリを実行するのにかかる手順 3.5 の測定します。

次のスクリーン ショットでは、SQL、開発ドキュメントの web サイトの外観のアイデアを付けます。

#### <a name="choose-a-language"></a>言語を選択します。

![SQL デベロッパー web サイトを開始][image-ref-390-aka-ms-sqldev-choose-language]

&nbsp;

#### <a name="choose-an-operating-system"></a>オペレーティング システムを選択します。

![SQL デベロッパー web サイト、Java Ubuntu][image-ref-400-aka-ms-sqldev-java-ubuntu]

&nbsp;



## <a name="other-development"></a>その他の開発


このセクションでは、その他の開発オプションについてのリンクを示します。 これらは、Azure の開発のためこれら同じ言語を使用すると、一般に含まれます。 情報は、Azure SQL データベースと Microsoft SQL Server だけを対象とするをを越えてとします。

#### <a name="developer-hub-for-azure"></a>Azure の開発者のハブ

- [Azure の開発者のハブ](http://docs.microsoft.com/azure/)
- [.NET 開発者向けの azure](http://docs.microsoft.com/dotnet/azure/)
- [Java 開発者向けの azure](http://docs.microsoft.com/java/azure/)
- [Node.js 開発者用の azure](http://docs.microsoft.com/nodejs/azure/)
- [Python 開発者のための azure](http://docs.microsoft.com/python/azure/)
- [Azure で PHP web アプリケーションを作成します。](http://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-php)

#### <a name="other-languages"></a>その他の言語

- [Windows 上の SQL Server を使用して移動してアプリを作成します。](http://www.microsoft.com/sql-server/developer-get-started/go/windows/)



<!-- Image references. -->

[image-ref-310-ado-net]: ./media/homepage-sql-connection-drivers/gm-ado-net-an51.png
[image-ref-322-cpp]: ./media/homepage-sql-connection-drivers/gm-cpp-4point-p61f.png
[image-ref-320-csharp]: ./media/homepage-sql-connection-drivers/gm-csharp-c10c.png
[image-ref-333-ef]: ./media/homepage-sql-connection-drivers/gm-entity-framework-ef20d.png
[image-ref-330-java]: ./media/homepage-sql-connection-drivers/gm-java-j18c.png
[image-ref-340-node]: ./media/homepage-sql-connection-drivers/gm-node-n30.png
[image-ref-350-odbc]: ./media/homepage-sql-connection-drivers/gm-odbc-ic55826-o35.png
[image-ref-360-php]: ./media/homepage-sql-connection-drivers/gm-php-php60.png
[image-ref-370-python]: ./media/homepage-sql-connection-drivers/gm-python-py72.png
[image-ref-380-ruby]: ./media/homepage-sql-connection-drivers/gm-ruby-un-r82.png
[image-ref-390-aka-ms-sqldev-choose-language]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-400-aka-ms-sqldev-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png


