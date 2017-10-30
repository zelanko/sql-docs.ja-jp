---
title: "Windows 認証でオンプレミス データ ソースへの接続 |Microsoft ドキュメント"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1e3d9736612211038991489a4bd858d1ff89d333
ms.openlocfilehash: 1b60d877c6c75a77dd16fa8cb1704e10baf36bdb
ms.contentlocale: ja-jp
ms.lasthandoff: 10/19/2017

---
# <a name="connect-to-on-premises-data-sources-with-windows-authentication"></a>Windows 認証でオンプレミス データ ソースへの接続します。
この記事では、内部設置型のデータ ソースへの接続に Windows 認証を使用してパッケージを実行する Azure SQL データベースで、SSIS カタログを構成する方法について説明します。

この記事の手順を実行した場合に指定したドメインの資格情報は、変更するか、資格情報を削除するまで、SQL データベース インスタンスのすべてのパッケージの実行に適用されます。

## <a name="prerequisite"></a>前提条件
Windows 認証のドメインの資格情報を設定する前に確認するかどうか、ドメインに参加しているコンピューターに接続できる、内部設置型のデータ ソースで`runas`モード。

### <a name="connecting-to-sql-server"></a>SQL Server に接続します。
内部設置型 SQL Server に接続することができるかどうかを確認するには、次の作業を行います。

1.  このテストを実行するには、ドメインに参加しているコンピューターを検索します。

2.  ドメインに参加しているコンピューターで、SQL Server Management Studio (SSMS) を使用する場合、ドメイン資格情報で開始するには、次のコマンドを実行します。

    ```cmd
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
    ```

3.  Ssms で使用する内部設置型 SQL Server に接続することができるかどうかを確認します。

### <a name="connecting-to-a-file-share"></a>ファイル共有への接続
内部設置型ファイル共有に接続できるかどうかを確認するには、次の作業を行います。

1.  このテストを実行するには、ドメインに参加しているコンピューターを検索します。

2.  ドメインに参加しているコンピューターで、次のコマンドを実行します。 このコマンドは、ディレクトリの一覧を取得することによって、ドメインの資格情報を使用すると、ファイル共有への接続をテスト コマンド prommpt を開きます。

    ```cmd
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
    ```

3.  ディレクトリの一覧が返されるかどうかを確認して、内部設置型ファイルを使用する共有します。

## <a name="provide-domain-credentials"></a>ドメインの資格情報を提供します。
パッケージが Windows 認証を使用して、内部設置型のデータ ソースに接続するのに便利なドメイン資格情報を提供するには、次の作業を行います。

1.  SQL Server Management Studio (SSMS) または別のツールでは、接続 SQL データベースをホストする、SSIS カタログ データベース (SSISDB)。 詳細については、次を参照してください。 [Azure 上の SSISDB カタログ データベースへの接続](ssis-azure-connect-to-catalog-database.md)です。

2.  現在のデータベースとして SSISDB とには、クエリ ウィンドウを開きます。

3.  次のストアド プロシージャを実行し、適切なドメイン資格情報を提供します。

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```
4.  SSIS パッケージを実行します。 パッケージは、Windows 認証でオンプレミス データ ソースへの接続に指定した資格情報を使用します。

## <a name="view-domain-credentials"></a>ドメインの資格情報の表示
アクティブなドメイン資格情報を表示するには、次の作業を行います。

1.  SQL Server Management Studio (SSMS) または別のツールでは、接続 SQL データベースをホストする、SSIS カタログ データベース (SSISDB)。

2.  現在のデータベースとして SSISDB とには、クエリ ウィンドウを開きます。

3.  次のストアド プロシージャを実行し、出力を調べます。

    ```sql
    SELECT * 
    FROM catalog.master_properties
    WHERE property_name = 'EXECUTION_DOMAIN' OR property_name = 'EXECUTION_USER'
    ```

## <a name="clear-domain-credentials"></a>クリア ドメインの資格情報
オフにし、この記事で説明したように指定した資格情報を削除するには、次の作業を行います。

1.  SQL Server Management Studio (SSMS) または別のツールでは、接続 SQL データベースをホストする、SSIS カタログ データベース (SSISDB)。

2.  現在のデータベースとして SSISDB とには、クエリ ウィンドウを開きます。

3.  次のストアド プロシージャを実行します。

    ```sql
    catalog.set_execution_credential @user='', @domain='', @password=''
    ```

## <a name="connect-to-file-shares"></a>ファイル共有に接続します。
オンプレミスと Azure の仮想マシンの両方に、Azure SSIS 統合ランタイムと同じ仮想ネットワーク内のファイル共有への接続に Windows 認証を使用することができます。

Azure の仮想マシン上のファイル共有に接続するには、次の作業を行います。

1.  SQL Server Management Studio (SSMS) または別のツールでは、接続 SQL データベースをホストする、SSIS カタログ データベース (SSISDB)。

2.  現在のデータベースとして SSISDB とには、クエリ ウィンドウを開きます。

3.  次のストアド プロシージャを実行します。

    ```sql
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
    ```

## <a name="next-steps"></a>次の手順
- パッケージを展開します。 詳細については、次を参照してください。 [SSIS プロジェクトを SQL Server Management Studio (SSMS) を配置](../ssis-quickstart-deploy-ssms.md)です。
- パッケージを実行します。 詳細については、次を参照してください。 [、SSIS パッケージを SQL Server Management Studio (SSMS) で実行](../ssis-quickstart-run-ssms.md)です。
- パッケージのスケジュールを設定します。 詳細については、次を参照してください[スケジュール SSIS パッケージを Azure での実行。](ssis-azure-schedule-packages.md)

