---
title: Windows 認証でデータとファイル共有に接続する | Microsoft Docs
description: この記事では、Azure SQL Database で SSIS カタログを構成して、Windows 認証を使用するパッケージを実行し、データ ソースとファイル共有に接続する方法について説明します。
ms.date: 02/05/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.suite: sql
ms.custom: ''
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cca5deecf90fbbe28399d33ac2038bc2264b1ae6
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35332686"
---
# <a name="connect-to-data-sources-and-file-shares-with-windows-authentication-in-ssis-packages-in-azure"></a>Azure の SSIS パッケージで Windows 認証を使用し、データ ソースとファイル共有に接続する

この記事では、Azure SQL Database で SSIS カタログを構成して、Windows 認証を使用するパッケージを実行し、データ ソースとファイル共有に接続する方法について説明します。 Windows 認証を使用して、オンプレミスと Azure の仮想マシンの両方、さらに Azure Files で Azure SSIS Integration Runtime と同じ仮想ネットワーク内のデータ ソースに接続できます。

> [!WARNING]
> この記事で説明されているように、`catalog`.`set_execution_credential` を実行して、Windows 認証に有効なドメイン資格情報を指定しない場合、 Windows 認証に依存するパッケージはデータ ソースに接続することができず、実行時に失敗します。

## <a name="you-can-only-use-one-set-of-credentials"></a>使用できる資格情報は 1 セットのみ

現在、パッケージで使用できる資格情報は 1 セットだけです。 この記事の手順を実行するときに指定したドメインの資格情報は、資格情報を変更または削除するまで、SQL Database インスタンスのすべてのパッケージの実行 (インタラクティブまたはスケジュール) に適用されます。 パッケージを資格情報のセットが異なる複数のデータ ソースに接続する必要がある場合は、パッケージを複数のパッケージに分割することが必要な場合があります。

データ ソースの 1 つが Azure Files の場合、プロセス実行タスクで `net use` またはそれと同等のものを使って、パッケージの実行時に Azure ファイル共有をマウントすることにより、この制限を回避できます。 詳しくは、「[Windows で Azure ファイル共有をマウントして共有にアクセスする](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows)」をご覧ください。

## <a name="provide-domain-credentials-for-windows-authentication"></a>Windows 認証のドメイン資格情報を提供する
パッケージが Windows 認証を使用して、オンプレミスのデータ ソースに接続できるようにするドメイン資格情報を提供するには、次のことを行います。

1.  SQL Server Management Studio (SSMS) または別のツールを使用して、SSIS カタログ データベース (SSISDB) をホストする SQL Database に接続します。 詳細については、「[Azure の SSIS カタログ (SSISDB) に接続する](ssis-azure-connect-to-catalog-database.md)」を参照してください。

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
3.  Windows 認証で接続するには、Azure-SSIS Integration Runtime がオンプレミスの SQL Server も含む仮想ネットワークに属していることを確認します。  詳しくは、「[Azure-SSIS 統合ランタイムを仮想ネットワークに参加させる](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network)」をご覧ください。 次に、この記事で説明されているように `catalog.set_execution_credential` を使用して資格情報を提供します。

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
- パッケージのスケジュールを設定します。 詳細については、「[Azure で SSIS パッケージのスケジュールを設定する](ssis-azure-schedule-packages.md)」を参照してください。
