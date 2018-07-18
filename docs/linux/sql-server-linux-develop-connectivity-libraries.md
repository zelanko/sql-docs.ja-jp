---
title: 接続ライブラリとフレームワーク |Microsoft Docs
description: クライアント アプリは、Linux、Windows、Docker と Azure SQL Database と Azure SQL Data Warehouse にも、クラウドまたはオンプレミスで実行されている Microsoft SQL Server に接続するさまざまな言語から使用できる接続ドライバーの一覧を表示します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.openlocfilehash: a10eb1c869af5268868f388197e3e160ad542d96
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982814"
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>Microsoft SQL Server の接続ライブラリとフレームワーク

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

チェック アウト、[チュートリアル入門](http://aka.ms/sqldev)を迅速に c#、Java、Node.js、PHP、Python などのプログラミング言語の使用開始し、macOS での Linux または Windows Docker で SQL Server を使用してアプリをビルドします。

次の表に、接続ライブラリまたは*ドライバー*または Linux、Windows、Docker、クラウドに接続し、オンプレミスで実行されている Microsoft SQL Server を使用する言語のさまざまなクライアント アプリケーションが使用できることとまたに Azure SQL Database と Azure SQL Data Warehouse。 

| [言語] | プラットフォーム | その他のリソース | ダウンロード | 開始するには |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows、Linux、macOS | [Microsoft ADO.NET for SQL Server](http://msdn.microsoft.com/library/mt657768.aspx) | [ダウンロード](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [はじめに](https://www.microsoft.com/en-us/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows、Linux、macOS | [Microsoft SQL Server 用 JDBC Driver](http://msdn.microsoft.com/library/mt484311.aspx) | [ダウンロード](http://go.microsoft.com/fwlink/?LinkId=245496) |  [はじめに](https://www.microsoft.com/en-us/sql-server/developer-get-started/java/ubuntu)
| PHP (PHP) | Windows、Linux、macOS| [SQL Server 用 PHP SQL ドライバー](http://msdn.microsoft.com/library/dn865013.aspx) | オペレーティング システム： <br/> \* [Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \* [Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \* [macOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [はじめに](https://www.microsoft.com/en-us/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows、Linux、macOS | [Node.js Driver for SQL Server](../connect/node-js/node-js-driver-for-sql-server.md) |  [はじめに](https://www.microsoft.com/en-us/sql-server/developer-get-started/node/ubuntu)
| Python | Windows、Linux、macOS | [Python SQL ドライバー](../connect/python/python-driver-for-sql-server.md) <br/> \* [pyodbc](http://msdn.microsoft.com/library/mt763257.aspx) |  [はじめに](https://www.microsoft.com/en-us/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows、Linux、macOS | [Ruby Driver for SQL Server](../connect/ruby/ruby-driver-for-sql-server.md) | [はじめに](https://www.microsoft.com/en-us/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows、Linux、macOS | [Microsoft ODBC Driver for SQL Server](https://msdn.microsoft.com/library/mt654048(v=sql.1).aspx) | [ダウンロード](https://msdn.microsoft.com/library/mt654048(v=sql.1).aspx) |  

次の表に、オブジェクト リレーショナル マッピング (ORM) フレームワークと web フレームワークで、オンプレミスで実行されている Microsoft SQL Server またはクライアント アプリケーションが使用する Linux、Windows、Docker と Azure SQL Database にも、クラウドでの例をいくつかとAzure SQL Data Warehouse。 

| [言語] | プラットフォーム | ORM(s) |
| :-- | :-- | :-- |
| C# | Windows、Linux、macOS | [Entity Framework](https://docs.microsoft.com/ef)<br>[Entity Framework Core](https://docs.microsoft.com/ef/core/index) |
| Java | Windows、Linux、macOS |[ORM を休止状態します。](http://hibernate.org/orm)|
| PHP (PHP) | Windows、Linux | [Laravel (連ねました)](https://laravel.com/docs/5.0/eloquent) |
| Node.js | Windows、Linux、macOS | [ORM を sequelize します。](http://docs.sequelizejs.com) |
| Python | Windows、Linux、macOS |[Django](https://www.djangoproject.com/) |
| Ruby | Windows、Linux、macOS | [レールを ruby](http://rubyonrails.org/) |

## <a name="related-links"></a>関連リンク
- [SQL Server ドライバー](http://msdn.microsoft.com/library/mt654049.aspx)クライアント アプリケーションからの接続用
