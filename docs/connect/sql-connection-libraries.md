---
title: "Microsoft SQL データベースに対する接続ライブラリ |Microsoft ドキュメント"
description: "さまざまなプログラミング言語のクライアントから Microsoft SQL Server と Azure SQL データベースへの接続を有効にするモジュールのダウンロードのリンクを提供します。"
author: MightyPen
ms.service: 
ms.component: connect
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.technology: dbe-data-tier-apps
ms.custom: 
ms.workload: data-management
ms.topic: article
ms.date: 08/09/2017
ms.author: genemi
ms.openlocfilehash: fceff06b2a35fbcc5621f08883ece0a126723f6b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Microsoft SQL データベースを接続するモジュール

この記事は、接続モジュールのダウンロード リンクを提供または*ドライバー*と対話するために使用するクライアント プログラムを[Microsoft SQL Server](../index.md)、その対となるクラウドを使用して[AzureSQL データベース](http://docs.microsoft.com/azure/sql-database/)です。 ドライバーは、次のオペレーティング システムで実行されているプログラミング言語のさまざまな利用できます。

- Linux (Ubuntu)
- MacOS
- Windows


#### <a name="oop-to-relational-mismatch"></a>OOP リレーショナルが一致しません

*リレーショナル*: 多くの場合、オブジェクト指向プログラミング (OOP) 言語で記述されたクライアント プログラムは、オブジェクト指向より以上のリレーショナル形式でクエリ データを返すことが SQL ドライバーを使用します。 ADO.NET を使用して、c#、1 つの例です。 OOP リレーショナル形式が一致しない場合がありますにより OOP コードが困難を記述して理解します。

*ORM*: 他のドライバーやフレームワークには、不一致を回避する、OOP 形式でクエリ データを返します。 これらのドライバーは、特定の SQL テーブルのデータ列と一致するクラスが定義されていることを指定してくださいによって機能します。 ドライバーを実行し、*オブジェクト リレーショナル マッピング*(ORM) クラスのインスタンスにクエリ データを返すにします。 C# の場合は、Microsoft の Entity Framework (EF) と java の場合、休止状態は、次の 2 つの例です。

この記事では、個別のセクションをリビルドこれら 2 つのドライバーの接続にします。


<a name="anchor-20-drivers-relational-access" />

## <a name="drivers-for-relational-access"></a>リレーショナル アクセス用のドライバー


<!--
Each given Microsoft Download Center page should be enhanced
with a link to the next NEWER version page, on the day that the
original page is no longer the latest because the newer page is being added.
But this policy is not agreed on or observed,
putting the links in the following table at risk for being outdated.

PHP driver in Github.com also uses this FWLink:  http://go.microsoft.com/fwlink/?LinkID=518036 ,
although the FWLink is less precise than is http://github.com/Microsoft/msphpsql/tree/dev#install-unix .
-->


| 言語 | SQL driver をダウンロードします。 |
| :------- | :---------------------- |
| C#       | [ADO.NET](http://www.microsoft.com/net/download/)<br /><br />[Ubuntu Linux 用の .NET core](https://www.microsoft.com/net/core#Ubuntu)<br />[.NET core、MacOS 用](https://www.microsoft.com/net/core#macos)<br />[Windows 用の .NET core](https://www.microsoft.com/net/core) |
| C++      | [ODBC 13.1](http://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server) |
| Java     | [JDBC](http://go.microsoft.com/fwlink/?LinkId=245496)<br />[6.2 をダウンロードします。](http://www.microsoft.com/download/details.aspx?id=55539) |
| Node.js  | [Node.js ドライバー、インストール手順](http://docs.microsoft.com/sql/connect/node-js/step-1-configure-development-environment-for-node-js-development) |
| PHP (PHP)      | *オペレーティング システム：*<br /><br />[Windows の PHP driver](http://www.microsoft.com/download/details.aspx?id=20098)<br />[Github から、Ubuntu または MacOS PHP のドライバー](http://github.com/Microsoft/msphpsql/tree/dev#install-unix) |
| Python   | [pyodbc、インストール手順](http://docs.microsoft.com/sql/connect/python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development)<br />[ODBC 13.1 をダウンロードします。](http://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server) |
| Ruby     | [Ruby ドライバー、インストール手順](https://docs.microsoft.com/sql/connect/ruby/step-1-configure-development-environment-for-ruby-development)<br />[ルビのダウンロード ページ](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |


<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>ORM アクセス用のドライバー


次の表は、Microsoft SQL データベースに接続するクライアント アプリケーションを使用するオブジェクト リレーショナル マッピング (ORM) フレームワークの例を示します。


| 言語 | ORM ドライバーのダウンロード |
| :------- | :------------------ |
| C# | [Entity Framework Core](http://docs.microsoft.com/ef/core/)<br />[Entity Framework (6.x またはそれ以降)](http://docs.microsoft.com/ef/) |
| Java | [ORM を休止状態します。](http://hibernate.org/orm)|
| PHP (PHP) | [やすい ORM、Laravel インストールに含まれる](http://laravel.com/docs/) |
| Node.js | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | [Django](http://www.djangoproject.com/) |
| Ruby | [レールを ruby](http://rubyonrails.org/) |
| &nbsp; | <br /> |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>ビルドのアプリ、web ページ


[http://aka.ms/sqldev](http://aka.ms/sqldev)のセットに移動、*ビルドでアプリを*web ページ。 Web ページは、プログラミング言語、オペレーティング システム、および SQL 接続のドライバーのさまざまな組み合わせに関する情報を提供します。 ビルドのアプリ、web ページによって提供される情報は、次の項目です。

- 言語 + 工程 sys ドライバーの組み合わせごとに、最初から開始する方法についての詳細。
    - 最新の SQL 接続ドライバーをインストールする手順です。
- 次の項目の各用のコード例:
    - オブジェクト リレーショナル コードの例です。
    - ORM コードの例です。
    - パフォーマンスを向上させる多くの列ストア インデックス デモンストレーションします。


#### <a name="first-page-of-build-an-app-webpages"></a>ビルドのアプリ、web ページの最初のページ

![ビルドのアプリ、web ページ、最初のページのスクリーン ショット][image-ref-163-buildanapp-webpages-first-page]


#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Java のビルドのアプリ、web ページの Ubuntu のメニュー

![ビルドのアプリ、web ページ、Java Ubuntu メニュー][image-ref-167-buildanapp-webpages-menu-java-ubuntu]


&nbsp;


## <a name="related-links"></a>関連リンク

- [Java およびその他の言語で、クラウド内の Azure SQL データベースに接続するための例のコード](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java)です。


<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
