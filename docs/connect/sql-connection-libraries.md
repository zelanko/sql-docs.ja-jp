---
title: Microsoft SQL データベースの接続ライブラリ | Microsoft Docs
description: 各種のクライアント プログラミング言語から Microsoft SQL Server および Azure SQL Database への接続を可能にするモジュールのダウンロード リンクを示します。
author: MightyPen
ms.prod: sql
ms.technology: ''
ms.custom: ''
ms.topic: article
ms.date: 06/18/2018
ms.author: genemi
ms.openlocfilehash: 71254b937c4c0173af9e1549efb98a0b42f65e02
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "73632815"
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Microsoft SQL データベースの接続モジュール

この記事では、クライアント プログラムが [Microsoft SQL Server](../relational-databases/database-features.md)、およびそれとよく似たクラウド版 [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/) との対話に使用できる接続モジュール (*ドライバー*) のダウンロード リンクを示します。 次のオペレーティング システムで実行されるさまざまなプログラミング言語用のドライバーが用意されています。

- Linux
- MacOS
- Windows

#### <a name="oop-to-relational-mismatch"></a>OOP とリレーショナルの不一致

*リレーショナル*:オブジェクト指向プログラミング (OOP) 言語で記述されたクライアント プログラムでは、多くの場合、オブジェクト指向よりもリレーショナルな形式でクエリ データを返す SQL ドライバーを使用します。 ADO.NET を使用する C# がその一例です。 OOP とリレーショナルの形式の不一致により、OOP コードの記述と理解が困難になることがあります。

*ORM*:ほかのドライバーまたはフレームワークは、OOP 形式のクエリ データを返すことで、不一致を回避します。 これらのドライバーは、特定の SQL テーブルのデータ列と一致するようにクラスが定義されていることを前提として機能します。 次に、ドライバーは*オブジェクト リレーショナル マッピング* (ORM) を実行して、クエリ データをクラスのインスタンスとして返します。 Microsoft の Entity Framework (EF) for C#、および Hibernate for Java の 2 つがその例です。

この記事では、この 2 種類の接続ドライバーに個別のセクションを割り当てています。

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

| Language | SQL ドライバーのダウンロード |
| :------- | :---------------------- |
| C# | [ADO.NET](https://www.microsoft.com/net/download/)<br />[Microsoft.Data.SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/)<br /><br />[Linux-Ubuntu 用の .NET Core](https://www.microsoft.com/net/core#Ubuntu)<br />[MacOS 用の .NET Core](https://www.microsoft.com/net/core#macos)<br />[Windows 用の .NET Core](https://www.microsoft.com/net/core) |
| C++ | [ODBC](./odbc/download-odbc-driver-for-sql-server.md)<br /><br />[OLE DB](./oledb/download-oledb-driver-for-sql-server.md) |
| Java | [JDBC](./jdbc/download-microsoft-jdbc-driver-for-sql-server.md) |
| Node.js | [Node.js ドライバー、インストール手順](./node-js/step-1-configure-development-environment-for-node-js-development.md) |
| PHP | [PHP](./php/download-drivers-php-sql-server.md) |
| Python | [pyodbc、インストール手順](./python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development.md)<br />[ODBC のダウンロード](./odbc/download-odbc-driver-for-sql-server.md) |
| Ruby | [Ruby ドライバー、インストール手順](./ruby/step-1-configure-development-environment-for-ruby-development.md)<br />[Ruby のダウンロード ページ](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |

<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>ORM アクセス用のドライバー


次の表は、クライアントアプリケーションが Microsoft SQL データベースに接続するために使用するオブジェクト リレーショナル マッピング (ORM) フレームワークの例を示しています。


| Language | ORM ドライバーのダウンロード |
| :------- | :------------------ |
| C# | [Entity Framework Core](https://docs.microsoft.com/ef/core/)<br />[Entity Framework (6.x 以降)](https://docs.microsoft.com/ef/) |
| Java | [Hibernate ORM](https://hibernate.org/orm)|
| PHP | [Eloquent ORM (Laravel のインストールに含まれています)](https://laravel.com/docs/) |
| Node.js | [Sequelize ORM](https://docs.sequelizejs.com) |
| Python | [Django](https://www.djangoproject.com/) |
| Ruby | [Ruby on Rails](https://rubyonrails.org/) |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Build-an-app の Web ページ
[https://aka.ms/sqldev](https://aka.ms/sqldev) により、*Build-an-app* の一連の Web ページが表示されます。 これらの Web ページには、プログラミング言語、オペレーティング システム、および SQL 接続ドライバーのさまざまな組み合わせに関する情報が記載されています。 Build-an-app の Web ページで提供される情報の中には、次の項目があります。

- 言語 + オペレーティングシステム + ドライバーの組み合わせごとに、作業を開始する方法についての詳細。
    - 最新の SQL 接続ドライバーをインストールするための手順。
- 次の各項目のコード例。
    - オブジェクト リレーショナル コードの例。
    - RDS のコード例です。
    - パフォーマンスの大幅な向上のための列ストア インデックスのデモ。

#### <a name="first-page-of-build-an-app-webpages"></a>Build-an-app の Web ページの最初のページ
![Build-an-app の Web ページの最初のページのスクリーンショット][image-ref-163-buildanapp-webpages-first-page]

#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Build-an-app の Web ページの [Java] メニューの [Ubuntu]
![Build-an-app の Web ページの [Java] メニューの [Ubuntu]][image-ref-167-buildanapp-webpages-menu-java-ubuntu]

&nbsp;

## <a name="related-links"></a>関連リンク
- [Java およびその他の言語を使用してクラウド内の Azure SQL Database に接続する方法のコード例](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java)

<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
