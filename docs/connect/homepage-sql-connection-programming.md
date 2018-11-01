---
title: SQL クライアントのプログラミングのホームページ |Microsoft Docs
description: ダウンロードし、言語および SQL Server または Azure SQL Database に接続するためのオペレーティング システムの組み合わせを多数のドキュメントへの注釈付きのリンクの [ハブ] ページ。
author: MightyPen
ms.date: 04/16/2018
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: meetb
ms.author: genemi
ms.openlocfilehash: e2c3da2ba71661602f69f85f5eb79ba6d550be9b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633800"
---
# <a name="homepage-for-client-programming-to-microsoft-sql-server"></a>クライアントの Microsoft SQL server プログラミングのホーム ページ


クライアントは、Microsoft SQL Server とクラウドでの Azure SQL Database を操作するプログラミングの詳細について、ホーム ページへようこそ。 この記事では、次の情報を提供します。

- 使用可能な言語とドライバーの組み合わせを示しています。
    - Linux (Ubuntu など)、MacOS、および Windows のオペレーティング システムの情報が提供されます。
- 各組み合わせの詳細なドキュメントへのリンクを提供します。
- 適切な場所は、領域と特定の言語の階層的なドキュメントのサブエリアを表示します。


#### <a name="azure-sql-database"></a>Azure SQL データベース

、任意の言語では、SQL Server に接続するコードは、Azure SQL Database に接続するためのコードとほぼ同じです。

詳細については、Azure SQL Database に接続するための接続文字列を参照してください。

- [.NET Core (c#) を使用して Azure SQL データベースに対してクエリを](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core)します。
- 他の言語についての内容のテーブルの前の記事の近くにあるその他の Azure SQL Database には。 たとえばを参照してください[PHP Azure SQL データベースに対してクエリを使用した](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php)します。


#### <a name="build-an-app-webpages"></a>ビルドのアプリ、web ページ

当社 *- アプリをビルド*web ページが別の形式でのコード例については、構成の情報と共にを提示します。 詳細については、この記事の後半を参照してください、[というラベルの付いたセクション*ビルド-アプリ、web サイト*](#an-204-aka-ms-sqldev)します。



<a name="an-050-languages-clients" />

## <a name="languages-and-drivers-for-client-programs"></a>言語およびクライアント プログラムのドライバー


次の表では、各言語のイメージは、SQL Server での言語の使用に関する詳細情報へのリンクは。 各リンクは、この記事では、後のセクションにジャンプします。

| &nbsp; | &nbsp; | &nbsp; |
| :-- | :-- | :-- |
| &nbsp; [![C# のロゴ][image-ref-320-csharp]](#an-110-ado-net-docu) | &nbsp; [![ORM の Entity Framework、.NET Framework の][image-ref-333-ef]](#an-116-csharp-ef-orm) | &nbsp; [![Java のロゴ][image-ref-330-java]](#an-130-jdbc-docu) |
| &nbsp; [![Node.js のロゴ][image-ref-340-node]](#an-140-node-js-docu) | &nbsp; [**`ODBC for C++`**](#an-160-odbc-cpp-docu)<br/>[![cpp ビッグ プラス][image-ref-322-cpp]](#an-160-odbc-cpp-docu) | &nbsp; [![PHP のロゴ][image-ref-360-php]](#an-170-php-docu) |
| &nbsp; [![Python のロゴ][image-ref-370-python]](#an-180-python-docu) | &nbsp; [![Ruby のロゴ][image-ref-380-ruby]](#an-190-ruby-docu) | &nbsp; ... |
| &nbsp; | &nbsp; | <br />|


#### <a name="downloads-and-installs"></a>ダウンロードおよびインストール

次の記事では、ダウンロードに使用して、プログラミング言語で使用するためのさまざまな SQL 接続ドライバーをインストールします。

- [SQL Server ドライバー](sql-server-drivers.md)



<a name="an-110-ado-net-docu" />

## <a name="c-logoimage-ref-320-csharp-c-using-adonet"></a>![C# のロゴ][image-ref-320-csharp] ADO.NET を使用して C#

C# および Visual Basic の場合など、.NET マネージ言語とは、ADO.NET の最も一般的なユーザーです。 *ADO.NET*は .NET Framework クラスのサブセットのカジュアル名です。

#### <a name="code-examples"></a>コード例

|||
| :-- | :-- |
| [ADO.NET を使用した SQL への接続を概念実証する](./ado-net/step-3-proof-of-concept-connecting-to-sql-using-ado-net.md) | 小規模なコード例は、接続して、SQL Server へのクエリに重点を置いています。 |
| [ADO.NET で SQL に弾性的に接続する](./ado-net/step-4-connect-resiliently-to-sql-with-ado-net.md) | 接続の接続が失われるまでに時間が発生することができますので、コード例では、ロジックを再試行してください。<br /><br />再試行ロジックは、Azure SQL Database になどに任意のクラウド データベースのインターネットを介して維持接続にも適用されます。 |
| [接続し、クエリに Windows/Linux と macOS で .NET Core を使用して c# プログラムを作成する方法のデモを azure SQL Database:](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core) | Azure SQL Database の例です。 |
| [C#、ADO.NET、Windows アプリをビルドします。](http://www.microsoft.com/sql-server/developer-get-started/csharp/win/) | コード例も構成情報。 |
| &nbsp; | <br /> |

#### <a name="documentation"></a>ドキュメント

|||
| :-- | :-- |
| [ADO.NET を使用して C#](./ado-net/index.md)| ドキュメントのルートです。 |
| [Namespace: System.Data](http://docs.microsoft.com/dotnet/api/system.data) | ADO.NET を使用するクラスのセット。 |
| [名前空間: System.Data.SqlClient](http://docs.microsoft.com/dotnet/api/system.data.SqlClient) | 最も直接的な ADO.NET のセンターではクラスのセット。 |
| &nbsp; | <br /> |



<a name="an-116-csharp-ef-orm" />

## <a name="entity-framework-logoimage-ref-333-ef-entity-framework-ef-with-cx23"></a>![Entity Framework のロゴ][image-ref-333-ef] C では、entity Framework (EF)&#x23;

Entity Framework (EF) は、オブジェクト リレーショナル マッピング (ORM) を提供します。 ORM によって、リレーショナル SQL database から取得されたデータを操作するオブジェクト指向プログラミング (OOP) ソース コードを簡単にできます。

EF では、次のテクノロジとの直接的または間接的なリレーションシップがあります。

- .NET Framework
- [LINQ to SQL](http://docs.microsoft.com/dotnet/framework/data/adonet/sql/linq/)、または[LINQ to Entities](http://docs.microsoft.com/dotnet/framework/data/adonet/ef/language-reference/linq-to-entities)
- 言語の構文の機能強化など、 **=>** (C#) 演算子。
- SQL データベースのテーブルにマップされるクラスのソース コードを生成する便利なプログラムです。 たとえば、 [EdmGen.exe](http://docs.microsoft.com/dotnet/framework/data/adonet/ef/edm-generator-edmgen-exe)します。


#### <a name="original-ef-and-new-ef"></a>元の EF と新しい EF

[Entity Framework 用のスタート ページ](http://docs.microsoft.com/ef/)次のような説明と EF が導入されています。

- Entity Framework は、.NET オブジェクトを使用してデータベースを使用する開発者は .NET オブジェクト リレーショナル マッパー (O/RM)。 ほとんどの開発者は通常、記述する必要があるデータ アクセスのソース コードの必要はありません。

*Entity Framework*別のソース コードの 2 つの分岐によって共有の名前を指定します。 EF の 1 つの分岐の方が古いと、そのソース コードは、パブリック管理ようになりましたことができます。 その他の EF は追加されました。 2 つの EFs は次のとおりです。

|     |     |
| :-- | :-- |
| [EF 6.x](http://docs.microsoft.com/ef/ef6/) | まず、Microsoft では、EF が 2008 年 8 月にリリースしました。 Microsoft では 2015 年 3 月に発表する EF 6.x は Microsoft が開発、最終バージョンでしたが。 Microsoft では、パブリック ドメインにソース コードをリリースしました。<br /><br />最初に EF には、.NET Framework の一部がでした。 EF 6.x は、.NET Framework から削除されました。<br /><br />[EF 6.x のソース コード リポジトリ、Github の*aspnet/EntityFramework6*](http://github.com/aspnet/EntityFramework6) |
| [EF Core](http://docs.microsoft.com/ef/core/) | Microsoft は、2016 年 6 月で、新しく作成した EF Core をリリースしました。 EF Core は、柔軟性と移植性の向上のために設計されています。 EF Core は、Microsoft Windows だけ以外のオペレーティング システムで実行できます。 EF Core は、Microsoft SQL Server だけを超えるデータベースおよびその他のリレーショナル データベースと対話できます。<br /><br />**C&#x23;のコード例。**<br />[Entity Framework Core の概要](https://docs.microsoft.com/ef/core/get-started/index)<br />[既存のデータベースでの .NET Framework での EF Core の概要](https://docs.microsoft.com/ef/core/get-started/full-dotnet/existing-db) |
| &nbsp; | <br /> |

EF と関連テクノロジは、強力であり、領域全体を習得する開発者の多くは。

&nbsp;



<a name="an-130-jdbc-docu" />

## <a name="java-logoimage-ref-330-java-java-and-jdbc"></a>![Java のロゴ][image-ref-330-java] Java と JDBC

Microsoft では、SQL Server (または Azure SQL database では、コースの) の使用の Java Database Connectivity (JDBC) ドライバーを提供します。 これは Type 4 JDBC ドライバーであり、標準の JDBC アプリケーション プログラム インターフェイス (API) によってデータベース接続を提供します。

#### <a name="code-examples"></a>コード例

|||
| :-- | :-- |
| [コード例](./jdbc/code-samples/index.md) | データ型、結果セット、および大規模なデータについて学習できるコード例です。 |
| [接続 URL のサンプル](./jdbc/connection-url-sample.md) | 接続 URL を使用して、SQL Server に接続する方法について説明します。 使用して、データを取得するのに SQL ステートメントを使用します。 |
| [データ ソースのサンプル](./jdbc/data-source-sample.md) | データ ソースを使用して、SQL Server に接続する方法について説明します。 ストアド プロシージャを使用して、データを取得します。 |
| [Java を使用して Azure SQL database のクエリ](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java) | Azure SQL Database の例です。 |
| [Ubuntu 上で SQL Server を使用して Java アプリを作成します。](http://www.microsoft.com/sql-server/developer-get-started/java/ubuntu/) | コード例も構成情報。 |
| &nbsp; | <br /> |

#### <a name="documentation"></a>ドキュメント

JDBC のドキュメントには、次の主要な領域が含まれています。

|||
| :-- | :-- |
| [Java Database Connectivity (JDBC)](./jdbc/index.md) | JDBC ドキュメントのルートです。 |
| [リファレンス](./jdbc/reference/index.md) | インターフェイス、クラス、およびメンバー。 |
| [JDBC SQL ドライバーのプログラミング ガイド](./jdbc/programming-guide-for-jdbc-sql-driver.md) | コード例も構成情報。 |
| &nbsp; | <br /> |



<a name="an-140-node-js-docu" />

## <a name="nodejs-logoimage-ref-340-node-nodejs"></a>![Node.js のロゴ][image-ref-340-node] Node.js

Windows、Linux、またはファルダから Node.js を使用した SQL Server に接続できます。 Node.js ドキュメントのルートは[ここ](./node-js/index.md)します。

SQL Server 用 Node.js 接続ドライバーは、JavaScript に実装されます。 ドライバーは、すべての最新バージョンの SQL Server でサポートされている TDS プロトコルを使用します。 ドライバーはオープン ソース プロジェクト、 [Github で入手できます](http://tediousjs.github.io/tedious/)します。

#### <a name="code-examples"></a>コード例

|||
| :-- | :-- |
| [Node.js を使用した SQL への接続を概念実証する](./node-js/step-3-proof-of-concept-connecting-to-sql-using-node-js.md) | ベア ボーンのソース コード、SQL Server への接続およびクエリを実行します。 |
| [Azure SQL database: Node.js クエリを使用して](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | クラウドでの Azure SQL Database の例です。 |
| [MacOS での SQL Server を使用する Node.js アプリを作成します。](http://www.microsoft.com/sql-server/developer-get-started/node/mac/) | コード例も構成情報。 |
| &nbsp; | <br /> |



<a name="an-160-odbc-cpp-docu" />

## <a name="odbc-for-c"></a>C++ 用の ODBC 

![ODBC のロゴ][image-ref-350-odbc] ![cpp ビッグ プラス][image-ref-322-cpp]

オープン データベース コネクティビティ (ODBC)、1990 年代に開発され、.NET Framework が復帰させる方します。 ODBC は、任意の特定のデータベース システムに依存しないオペレーティング システムから独立して設計されています。

長年にわたり多数の ODBC ドライバーに作成およびマイクロソフトの内外でのグループがリリースされます。 ドライバーの範囲には、いくつかのクライアント プログラミング言語が含まれます。 データ ターゲットの一覧は、SQL Server よりも移動します。

その他のいくつかの接続ドライバーは ODBC を内部的に使用します。

#### <a name="code-example"></a>コードの例

- [ODBC を使用して、C++ のコード例](../odbc/reference/sample-odbc-program.md)

#### <a name="documentation-outline"></a>ドキュメント アウトライン

このセクションでは、ODBC のコンテンツは、C から SQL Server または Azure SQL Database では、いずれかへのアクセスに焦点を当てています。 次の表では、ODBC 用の主要なドキュメントのおおよそのアウトラインを示します。


| 領域 | サブ区分 | [説明] |
| :--- | :------ | :---------- |
| [C++ 用の ODBC](./odbc/index.md) | ドキュメントのルートです。 |
| [Linux、Mac](./odbc/linux-mac/index.md) | &nbsp; | Linux または MacOS オペレーティング システムで ODBC を使用する方法の詳細についてはします。 |
| [Windows](./odbc/windows/index.md)     | &nbsp; | Windows オペレーティング システム上の ODBC の使用方法の詳細についてはします。 |
| [管理](../odbc/admin/index.md) | &nbsp; | ODBC データ ソースを管理するための管理ツールです。 |
| [Microsoft](../odbc/microsoft/index.md)  | &nbsp; | 作成され、Microsoft によって提供されるさまざまな ODBC ドライバー。 |
| [概念とリファレンス](../odbc/reference/index.md) | &nbsp; | 従来の参照だけでなく、ODBC インターフェイスに関する概念情報。 |
| &nbsp; " | [付録](../odbc/reference/appendixes/index.md)    | 状態遷移テーブル、ODBC カーソル ライブラリ、および詳細。 |
| &nbsp; " | [アプリを開発します。](../odbc/reference/develop-app/index.md)  | 関数、ハンドル、およびその他。 |
| &nbsp; " | [ドライバーを開発します。](../odbc/reference/develop-driver/index.md) | 特殊なデータ ソースがある場合は、ODBC ドライバーを開発する方法。 |
| &nbsp; " | [インストール](../odbc/reference/install/index.md) | ODBC のインストール、サブキー、および詳細。 |
| &nbsp; " | [構文](../odbc/reference/syntax/index.md)   | セットアップ、インストーラー、翻訳、およびデータ アクセス用の Api。 |
| &nbsp; | &nbsp; | <br /> |



<a name="an-170-php-docu" />

## <a name="php-logoimage-ref-360-php-php"></a>![PHP のロゴ][image-ref-360-php] PHP (PHP)

PHP を使用すると、SQL Server と対話します。 PHP ドキュメントのルートは[ここ](./php/index.md)します。

#### <a name="code-examples"></a>コード例

|||
| :-- | :-- |
| [PHP を使用した SQL への接続を概念実証する](./php/step-3-proof-of-concept-connecting-to-sql-using-php.md) | 小規模なコード例は、接続して、SQL Server へのクエリに重点を置いています。 |
| [PHP で SQL に弾性的に接続する](./php/step-4-connect-resiliently-to-sql-with-php.md) | インターネットと、クラウド経由で接続の接続が失われるまでに時間が発生することができますので、コード例では、ロジックを再試行してください。 |
| [Azure SQL database: PHP クエリを使って](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php) | Azure SQL Database の例です。 |
| [RHEL で SQL Server を使用する PHP アプリを作成します。](http://www.microsoft.com/sql-server/developer-get-started/php/rhel/) | コード例も構成情報。 |
| &nbsp; | <br /> |



<a name="an-180-python-docu" />

## <a name="python-logoimage-ref-370-python-python"></a>![Python のロゴ][image-ref-370-python] Python


Python を使用することで、SQL Server にやり取りすることができます。

#### <a name="code-examples"></a>コード例

|||
| :-- | :-- |
| [Pyodbc を使用して Python を使用した SQL 接続の概念実証](./python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc.md) | 小規模なコード例は、接続して、SQL Server へのクエリに重点を置いています。 |
| [Azure SQL database: Python クエリを使用](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-python) | Azure SQL Database の例です。 |
| [SLES での SQL Server を使用する PHP アプリを作成します。](http://www.microsoft.com/sql-server/developer-get-started/python/sles/) | コード例も構成情報。 |
| &nbsp; | <br /> |

#### <a name="documentation"></a>ドキュメント

| 領域 | [説明] |
| :--- | :---------- |
| [SQL Server への Python](./python/index.md) | ドキュメントのルートです。 |
| [pymssql ドライバー](./python/pymssql/index.md) | マイクロソフトは維持または pymssql ドライバーをテストできません。<br /><br />Pymssql 接続ドライバーは、Python プログラムで使用するための SQL データベースへの単純なインターフェイスです。 Pymssql は FreeTDS を Microsoft SQL Server Python DB API (PEP 249) インターフェイスを提供する上に構築します。 |
| [pyodbc ドライバー](./python/pyodbc/index.md)   | Pyodbc 接続ドライバーでは、簡単にアクセスする ODBC データベースをオープン ソース Python モジュールです。 DB API 2.0 の仕様を実装するが、さらに多くのらしい利便性が詰め込まれています。 |
| &nbsp; | <br /> |


<a name="an-190-ruby-docu" />

## <a name="ruby-logoimage-ref-380-ruby-ruby"></a>![Ruby のロゴ][image-ref-380-ruby] Ruby

Ruby を使用して、SQL Server にやり取りすることができます。 Ruby のドキュメントのルートは[ここ](./ruby/index.md)します。

#### <a name="code-examples"></a>コード例

|||
| :-- | :-- |
| [Ruby を使用した SQL への接続を概念実証する](./ruby/step-3-proof-of-concept-connecting-to-sql-using-ruby.md) | 小規模なコード例は、接続して、SQL Server へのクエリに重点を置いています。 |
| [Azure SQL database: Ruby クエリを使用](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ruby) | Azure SQL Database の例です。 |
| [MacOS での SQL Server を使用する Ruby アプリを作成します。](http://www.microsoft.com/sql-server/developer-get-started/ruby/mac/) | コード例も構成情報。 |
| &nbsp; | <br /> |



<a name="an-204-aka-ms-sqldev" />

## <a name="build-an-app-website-for-sql-client-developmenthttpwwwmicrosoftcomsql-serverdeveloper-get-started"></a>[ビルドのアプリを web サイト、SQL クライアント開発](http://www.microsoft.com/sql-server/developer-get-started/)


[ *- アプリをビルド*](https://www.microsoft.com/sql-server/developer-get-started/) web ページのプログラミング言語が SQL Server に接続するための長い一覧から選択できます。 また、クライアント プログラムのさまざまなオペレーティング システムを実行できます。

*アプリをビルド*始めたばかりの開発者のシンプルさと完全性を強調しています。 手順では、次のタスクについて説明します。

1. Microsoft SQL Server をインストールする方法
2. ダウンロードし、ツールやドライバーをインストールする方法。
3. 選択したオペレーティング システムに応じて、いずれのために必要な構成を作成する方法。
4. 指定されたソース コードをコンパイルする方法。
5. プログラムを実行する方法。

Web サイトで提供される詳細情報のおおよそのアウトラインをいくつかを次には。

#### <a name="java-on-ubuntu"></a>Ubuntu 上で Java:

1. 環境を設定します。
    - 手順 1.1 SQL Server をインストールする
    - 手順 1.2 インストール Java
    - 手順 1.3 Java Development Kit (JDK) をインストールします。
    - 手順 1.4 インストール Maven
2. SQL Server での Java アプリケーションを作成します。
    - 手順 2.1 は、SQL Server に接続し、クエリを実行する Java アプリを作成します。
    - 手順 2.2 休止状態の人気のフレームワークを使用して SQL Server に接続する Java アプリケーションを作成します。
3. 最大 100 倍 Java アプリを高速化します。
    - 列ストア インデックスを示すために手順 3.1 を作成する Java アプリ

#### <a name="python-on-windows"></a>Windows での Python:

1. 環境を設定します。
    - 手順 1.1 SQL Server をインストールする
    - 手順 1.2 Python をインストールします。
    - 手順 1.3 SQL Server 用 ODBC ドライバーと SQL コマンド ライン ユーティリティをインストールします。
2. SQL Server での Python アプリケーションを作成します。
    - 手順 2.1 では、SQL Server 用 Python ドライバーをインストールします。
    - 手順 2.2 アプリケーションのデータベースを作成します。
    - 手順 2.3 SQL Server に接続し、クエリを実行する Python アプリを作成します。
3. 最大 100 倍して Python アプリを高速化します。
    - 手順 3.1 で 500万 sqlcmd を使用して新しいテーブルを作成します。
    - 手順 3.2 は、このテーブルにクエリを実行し、実行時間を測定する Python アプリを作成します。
    - 手順 3.3、クエリの実行にかかる時間を測定します。
    - 手順 3.4 追加テーブルに列ストア インデックス
    - 列ストア インデックスを持つクエリを実行するのにかかる手順 3.5 の測定します。

次のスクリーン ショットでは、SQL、開発ドキュメントの web サイトがどのように見えるかが理解できます。

#### <a name="choose-a-language"></a>言語の選択:

![SQL デベロッパー web サイトを開始します。][image-ref-390-aka-ms-sqldev-choose-language]

&nbsp;

#### <a name="choose-an-operating-system"></a>オペレーティング システムを選択します。

![SQL デベロッパー web サイト、Java の Ubuntu][image-ref-400-aka-ms-sqldev-java-ubuntu]

&nbsp;



## <a name="other-development"></a>その他の開発


このセクションでは、その他の開発オプションについてのリンクを示します。 これらは、Azure 向け開発用これらと同じ言語を使用すると、一般に含まれます。 情報は、Azure SQL Database と Microsoft SQL Server だけを対象とするをを超えてとします。

#### <a name="developer-hub-for-azure"></a>Azure の開発者のハブ

- [Azure の開発者のハブ](http://docs.microsoft.com/azure/)
- [Azure for .NET 開発者](http://docs.microsoft.com/dotnet/azure/)
- [Java 開発者向けの azure](http://docs.microsoft.com/java/azure/)
- [Node.js 開発者向けの azure](http://docs.microsoft.com/nodejs/azure/)
- [Python 開発者向けの azure](http://docs.microsoft.com/python/azure/)
- [Azure での PHP web アプリを作成します。](http://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-php)

#### <a name="other-languages"></a>その他の言語

- [Windows 上の SQL Server を使用して、Go アプリを作成します。](http://www.microsoft.com/sql-server/developer-get-started/go/windows/)



<!-- Image references. -->

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

