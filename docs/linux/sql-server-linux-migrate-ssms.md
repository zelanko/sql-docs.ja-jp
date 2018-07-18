---
title: エクスポートし、Linux 上のデータベースのインポート |Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: 2210cfc3-c23a-4025-a551-625890d6845f
ms.custom: sql-linux
ms.openlocfilehash: 7a7c1c73ca70e0d42104e74c868d6acd32cc01b1
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38020130"
---
# <a name="export-and-import-a-database-on-linux-with-ssms-or-sqlpackageexe-on-windows"></a>エクスポートし、SSMS または SqlPackage.exe で Windows を使った Linux 上のデータベースのインポート

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、使用する方法を示しています。 [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)と[SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx)をエクスポートし、SQL Server 2017 on Linux でのデータベースをインポートします。 SSMS および SqlPackage.exe は Windows アプリケーション、Linux 上のリモート SQL Server インスタンスに接続できる Windows コンピューターがある場合、そのためこの手法を使用します。

常にインストールし、」の説明に従って、最新バージョンの SQL Server Management Studio (SSMS) を使用する必要があります[SQL Server on Linux への接続に Windows 上の SSMS の使用](sql-server-linux-manage-ssms.md)

> [!NOTE]
> 別に 1 つの SQL Server インスタンスからデータベースを移行する場合、推奨事項は使用する[バックアップと復元](sql-server-linux-migrate-restore-database.md)します。

## <a name="export-a-database-with-ssms"></a>SSMS を使用したデータベースをエクスポートします。

1. 」と入力して SSMS を起動**Microsoft SQL Server Management Studio** Windows では、検索ボックス、およびデスクトップ アプリをクリックします。

    ![[SQL Server Management Studio]](./media/sql-server-linux-manage-ssms/ssms.png) 

2. オブジェクト エクスプ ローラーで、ソース データベースに接続します。 ソース データベースには、オンプレミスで実行されている Microsoft SQL server または Linux、Windows または Docker と Azure SQL Database または Azure SQL Data Warehouse では、クラウドでを指定できます。

3. オブジェクト エクスプ ローラーでソース データベースを右クリックし、[**タスク**、] をクリック**データ層アプリケーションのエクスポート.**

4. エクスポート ウィザードで、**次**、し、**設定** タブでいずれかのローカル ディスクの場所、または Azure blob には、BACPAC ファイルを保存するエクスポートを構成します。

5. 既定では、データベース内のすべてのオブジェクトがエクスポートされます。 をクリックして、**詳細設定 タブ**をエクスポートするデータベース オブジェクトを選択します。

6. **[次へ]** をクリックし、 **[完了]** をクリックします。

します *。BACPAC ファイルが選択した場所に正常に作成し、ターゲット データベースにインポートする準備が整いました。

## <a name="import-a-database-with-ssms"></a>SSMS でデータベースをインポートします。

1. 」と入力して SSMS を起動**Microsoft SQL Server Management Studio** Windows では、検索ボックス、およびデスクトップ アプリをクリックします。

    ![[SQL Server Management Studio]](./media/sql-server-linux-manage-ssms/ssms.png) 

2. オブジェクト エクスプ ローラーで、ターゲット サーバーに接続します。 ターゲット サーバーが Microsoft SQL Server をオンプレミスで実行できます。 または、Linux、Windows または Docker と Azure SQL Database または Azure SQL Data Warehouse では、クラウドで。

3. 右クリックし、**データベース**オブジェクト エクスプ ローラーでフォルダー**データ層アプリケーションのインポート.**

4. ターゲット サーバーでデータベースを作成するには、ローカル ディスクから BACPAC ファイルを指定または Azure ストレージ アカウントと BACPAC ファイルのアップロード先となるコンテナーを選択します。

5. データベースの新しいデータベース名を指定します。 Azure SQL Database でデータベースをインポートする場合は、Microsoft Azure SQL Database のエディション (サービス層)、データベースの最大サイズ、およびサービス目標 (パフォーマンス レベル) を設定します。

6. をクリックして **[次へ]** 順にクリックします**完了**ターゲット サーバーで新しいデータベースに BACPAC ファイルをインポートします。

します *。指定した対象サーバーで新しいデータベースを作成する BACPAC ファイルがインポートされます。

## <a id="sqlpackage"></a> SqlPackage コマンド ライン オプション

SQL Server Data Tools (SSDT) のコマンド ライン ツールを使用することも[SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx)をエクスポートして BACPAC ファイルをインポートします。

次のコマンドの例では、BACPAC ファイルをエクスポートします。

```bash
SqlPackage.exe /a:Export /ssn:tcp:<your_server> /sdn:<your_database> /su:<username> /sp:<password> /tf:<path_to_bacpac>
```

データベース スキーマとユーザー データをインポートする次のコマンドを使用します。BACPAC ファイル:

```bash
SqlPackage.exe /a:Import /tsn:tcp:<your_server> /tdn:<your_database> /tu:<username> /tp:<password> /sf:<path_to_bacpac>

```

## <a name="see-also"></a>参照
SSMS を使用する方法の詳細については、次を参照してください。 [SQL Server Management Studio を使用して](https://msdn.microsoft.com/library/ms174173.aspx)します。 SqlPackage.exe の詳細については、次を参照してください。、 [SqlPackage のリファレンス ドキュメント](https://msdn.microsoft.com/library/hh550080.aspx)します。
