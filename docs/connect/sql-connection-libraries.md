---
title: Microsoft SQL データベースの接続ライブラリ |Microsoft Docs
description: さまざまなプログラミング言語のクライアントから Microsoft SQL Server、Azure SQL Database への接続を有効にするモジュールのダウンロード リンクを提供します。
author: MightyPen
ms.prod: sql
ms.technology: ''
ms.custom: ''
ms.topic: article
ms.date: 06/18/2018
ms.author: genemi
ms.openlocfilehash: 7f759dbe9022cff557461d900a35b3ccc91d2c4b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62862425"
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Microsoft SQL データベースの接続モジュール

この記事では接続モジュールのダウンロード リンクまたは*ドライバー*と対話するために、クライアント プログラムが使用できる[Microsoft SQL Server](../relational-databases/database-features.md)、クラウド内のツインを使用して[AzureSQL Database](https://docs.microsoft.com/azure/sql-database/)します。 ドライバーは、次のオペレーティング システムで実行されているプログラミング言語のさまざまな利用できます。

- Linux
- MacOS
- Windows

#### <a name="oop-to-relational-mismatch"></a>OOP とリレーショナルの不一致

*リレーショナル*: 多くの場合、オブジェクト指向プログラミング (OOP) 言語で記述されたクライアント プログラムは、オブジェクト指向より以上のリレーショナル形式で照会されたデータを返す SQL ドライバーを使用します。 C# と ADO.NET を使用して、1 つの例です。 OOP リレーショナル形式が一致しない場合があります、OOP によりコードが記述も理解が困難になります。

*ORM*: 他のドライバーやフレームワークには、不一致を回避、OOP 形式で照会されたデータを返します。 これらのドライバーは、クラスを特定の SQL テーブルのデータ列に一致するように定義されていることを想定して動作します。 ドライバーを実行し、*オブジェクト リレーショナル マッピング*(ORM) クラスのインスタンスとして照会されたデータを返すにします。 C# の場合は、マイクロソフトの Entity Framework (EF) と java の場合、休止状態は、2 つの例を示します。

この記事では、個別のセクションを専用接続ドライバーのこれらの 2 種類にします。

<a name="anchor-20-drivers-relational-access" />

## <a name="drivers-for-relational-access"></a>リレーショナル アクセス用のドライバー


<!--
Each given Microsoft Download Center page should be enhanced
with a link to the next NEWER version page, on the day that the
original page is no longer the latest because the newer page is being added.
But this policy is not agreed on or observed,
putting the links in the following table at risk for being outdated.

PHP driver in Github.com also uses this FWLink:  https://go.microsoft.com/fwlink/?LinkID=518036 ,
although the FWLink is less precise than is https://github.com/Microsoft/msphpsql/tree/dev#install-unix .
-->

| [言語] | SQL driver をダウンロードします。 |
| :------- | :---------------------- |
| C# | [ADO.NET](https://www.microsoft.com/net/download/)<br /><br />[Linux-Ubuntu 用の .NET Core](https://www.microsoft.com/net/core#Ubuntu)<br />[MacOS 用の .NET core](https://www.microsoft.com/net/core#macos)<br />[Windows 用の .NET core](https://www.microsoft.com/net/core) |
| C++ | [ODBC](./odbc/download-odbc-driver-for-sql-server.md)<br /><br />[OLE DB](./oledb/download-oledb-driver-for-sql-server.md) |
| Java | [JDBC](./jdbc/download-microsoft-jdbc-driver-for-sql-server.md) |
| Node.js | [Node.js ドライバー、インストール手順](./node-js/step-1-configure-development-environment-for-node-js-development.md) |
| PHP (PHP) | [PHP](./php/download-drivers-php-sql-server.md) |
| Python | [pyodbc、インストール手順](./python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development.md)<br />[ODBC をダウンロードします。](./odbc/download-odbc-driver-for-sql-server.md) |
| Ruby | [インストール手順については、ruby ドライバー](./ruby/step-1-configure-development-environment-for-ruby-development.md)<br />[Ruby のダウンロード ページ](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |

<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>ORM へのアクセス用のドライバー


次の表では、Microsoft SQL データベースに接続するクライアント アプリケーションを使用するオブジェクト リレーショナル マッピング (ORM) フレームワークの例を示します。


| [言語] | ORM ドライバーのダウンロード |
| :------- | :------------------ |
| C# | [Entity Framework Core](https://docs.microsoft.com/ef/core/)<br />[Entity Framework (6.x 以降)](https://docs.microsoft.com/ef/) |
| Java | [ORM を休止状態します。](https://hibernate.org/orm)|
| PHP (PHP) | [連ねました ORM、Laravel のインストールに含まれる](https://laravel.com/docs/) |
| Node.js | [ORM を sequelize します。](https://docs.sequelizejs.com) |
| Python | [Django](https://www.djangoproject.com/) |
| Ruby | [Ruby on Rails](https://rubyonrails.org/) |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>ビルドのアプリ、web ページ
[https://aka.ms/sqldev](https://aka.ms/sqldev) セットに移動 *- アプリをビルド*web ページ。 Web ページは、プログラミング言語、オペレーティング システム、および SQL の接続用ドライバーのさまざまな組み合わせに関する情報を提供します。 などのビルドのアプリ、web ページによって提供される情報には、次の項目を示します。

- 言語 + オペレーティング システム、ドライバーの組み合わせごとに、最初から開始する方法の詳細。
    - SQL 接続の最新のドライバーをインストールするための手順です。
- 次の項目ごとのコード例:
    - オブジェクト リレーショナルのコード例です。
    - RDS のコード例です。
    - パフォーマンスを向上させる多くの列ストア インデックスのデモンストレーションします。

#### <a name="first-page-of-build-an-app-webpages"></a>ビルドのアプリ、web ページの最初のページ
![ビルドのアプリ、web ページ、最初のページのスクリーン ショット][image-ref-163-buildanapp-webpages-first-page]

#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Java - ビルド-アプリ、web ページの Ubuntu のメニュー
![ビルドのアプリ、web ページ、Java Ubuntu メニュー][image-ref-167-buildanapp-webpages-menu-java-ubuntu]

&nbsp;

## <a name="related-links"></a>関連リンク
- [コード例では、Java とその他の言語では、クラウドでの Azure SQL Database に接続するため](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java)します。

<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
