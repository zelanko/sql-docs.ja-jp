---
title: "Windows 認証でデータ ソースとファイル共有に接続する | Microsoft Docs"
ms.date: 11/27/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b84fdd15fa4a6393b2350aaf75985653b6273f31
ms.sourcegitcommit: 4aeedbb88c60a4b035a49754eff48128714ad290
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="connect-to-on-premises-data-sources-and-azure-file-shares-with-windows-authentication"></a>Windows 認証でオンプレミス データ ソースと Azure ファイル共有に接続する
この記事では、Azure SQL Database で SSIS カタログを構成して、Windows 認証を使用するパッケージを実行し、オンプレミスのデータ ソースと Azure ファイル共有に接続する方法について説明します。 Windows 認証を使用して、オンプレミスと Azure の仮想マシンの両方、さらに Azure Files で Azure SSIS Integration Runtime と同じ仮想ネットワーク内のデータ ソースに接続できます。

この記事の手順を実行する際に指定するドメインの資格情報は、資格情報を変更または削除するまで、SQL Database インスタンスのすべてのパッケージの実行に適用されます。

## <a name="provide-domain-credentials-for-windows-authentication"></a>Windows 認証のドメイン資格情報を提供する
パッケージが Windows 認証を使用して、オンプレミスのデータ ソースに接続できるようにするドメイン資格情報を提供するには、次のことを行います。

1.  SQL Server Management Studio (SSMS) または別のツールを使用して、SSIS カタログ データベース (SSISDB) をホストする SQL Database に接続します。 詳細については、「[Azure 上の SSISDB カタログ データベースへの接続](ssis-azure-connect-to-catalog-database.md)」を参照してください。

2.  SSISDB を現在のデータベースとして使用し、クエリ ウィンドウを開きます。

3.  次のストアド プロシージャを実行し、適切なドメイン資格情報を提供します。

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```

4.  SSIS パッケージを実行します。 パッケージは、指定した資格情報を使用して、Windows 認証でオンプレミス データ ソースに接続します。

### <a name="view-domain-credentials"></a>ドメイン資格情報の表示
アクティブなドメイン資格情報を表示するには、次のことを行います。

1.  SQL Server Management Studio (SSMS) または別のツールを使用して、SSIS カタログ データベース (SSISDB) をホストする SQL Database に接続します。

2.  SSISDB を現在のデータベースとして使用し、クエリ ウィンドウを開きます。

3.  次のストアド プロシージャを実行し、出力を調べます。

    ```sql
    SELECT * 
    FROM catalog.master_properties
    WHERE property_name = 'EXECUTION_DOMAIN' OR property_name = 'EXECUTION_USER'
    ```

### <a name="clear-domain-credentials"></a>ドメイン資格情報のクリア
この記事の説明に従って指定した資格情報を削除するには、次のことを行います。

1.  SQL Server Management Studio (SSMS) または別のツールを使用して、SSIS カタログ データベース (SSISDB) をホストする SQL Database に接続します。

2.  SSISDB を現在のデータベースとして使用し、クエリ ウィンドウを開きます。

3.  次のストアド プロシージャを実行します。

    ```sql
    catalog.set_execution_credential @user='', @domain='', @password=''
    ```

## <a name="connect-to-an-on-premises-sql-server"></a>オンプレミスの SQL Server への接続
オンプレミスの SQL Server に接続できるかどうかを確認するには、次のことを行います。

1.  このテストを実行するには、ドメインに参加していないコンピューターを見つけます。

2.  ドメインに参加していないコンピューターで、次のコマンドを実行し、使用したいドメイン資格情報を使用して SQL Server Management Studio (SSMS) を起動します。

    ```cmd
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
    ```

3.  SSMS から、使用するオンプレミスの SQL Server に接続できるかどうかを確認します。

### <a name="prerequisites"></a>Prerequisites
Azure で実行されるパッケージからオンプレミスの SQL Server に接続するには、次の前提条件を有効にする必要があります。

1.  SQL Server 構成マネージャーで、TCP/IP プロトコルを有効にします。
2.  Windows ファイアウォールからのアクセスを許可します。 詳細については、「[SQL Server のアクセスを許可するための Windows ファイアウォールの構成](https://docs.microsoft.com/sql/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access)」を参照してください。
3.  Windows 認証で接続するには、Azure-SSIS Integration Runtime がオンプレミスの SQL Server も含む仮想ネットワーク (VNet) に属していることを確認します。  詳しくは、「[Azure-SSIS 統合ランタイムを仮想ネットワークに参加させる](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network)」をご覧ください。 次に、この記事で説明されているように `catalog.set_execution_credential` を使用して資格情報を提供します。

## <a name="connect-to-an-on-premises-file-share"></a>オンプレミスのファイル共有への接続
オンプレミスのファイル共有に接続できるかどうかを確認するには、次のことを行います。

1.  このテストを実行するには、ドメインに参加していないコンピューターを見つけます。

2.  ドメインに参加していないコンピューターで、次のコマンドを実行します。 このコマンドは、使用したいドメイン資格情報を使用してコマンド プロンプト ウィンドウを開き、ディレクトリの一覧を取得することによって、ファイル共有への接続をテストします。

    ```cmd
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
    ```

3.  使用したいオンプレミスのファイルシェアに対して、ディレクトリの一覧が返されるかどうかを確認します。

## <a name="connect-to-a-file-share-on-an-azure-vm"></a>Azure VM のファイル共有への接続
Azure の仮想マシン上のファイル共有に接続するには、次のことを行います。

1.  SQL Server Management Studio (SSMS) または別のツールを使用して、SSIS カタログ データベース (SSISDB) をホストする SQL Database に接続します。

2.  SSISDB を現在のデータベースとして使用し、クエリ ウィンドウを開きます。

3.  次のオプションの説明に従って、`catalog.set_execution_credential` ストアド プロシージャを実行します。

    ```sql
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
    ```

## <a name="connect-to-a-file-share-in-azure-files"></a>Azure Files のファイル共有への接続
Azure Files に関する詳細については、「[Azure ファイル](https://azure.microsoft.com/services/storage/files/)」を参照してください。

Azure ファイル共有上のファイル共有に接続するには、次のことを行います。

1.  SQL Server Management Studio (SSMS) または別のツールを使用して、SSIS カタログ データベース (SSISDB) をホストする SQL Database に接続します。

2.  SSISDB を現在のデータベースとして使用し、クエリ ウィンドウを開きます。

3.  次のオプションの説明に従って、`catalog.set_execution_credential` ストアド プロシージャを実行します。

    ```sql
    catalog.set_execution_credential @domain = N'Azure', @user = N'<storage-account-name>', @password = N'<storage-account-key>'
    ```

## <a name="next-steps"></a>次の手順
- パッケージを配置します。 詳細については、「[SQL Server Management Studio (SSMS) を使用して SSIS プロジェクトを配置する](../ssis-quickstart-deploy-ssms.md)」を参照してください。
- パッケージを実行します。 詳細については、「[SQL Server Management Studio (SSMS) を使用して SSIS プロジェクトを配置する](../ssis-quickstart-run-ssms.md)」を参照してください。
- パッケージのスケジュールを設定します。 詳細については、「[Azure で SSIS パッケージの実行をスケジュールする](ssis-azure-schedule-packages.md)」を参照してください。
