---
title: Windows 認証でデータ ソースとファイル共有に接続する | Microsoft Docs
description: この記事では、Azure SQL Database で SSIS カタログを構成し、Windows 認証を使用してデータ ソースとファイル共有に接続するパッケージを実行するように Azure-SSIS 統合ランタイムを構成する方法について説明します。
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: douglasl
manager: craigg
ms.openlocfilehash: 61d4d29b0dfc7fe67097c6cb61547c1c65dd79f1
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52411879"
---
# <a name="connect-to-data-sources-and-file-shares-with-windows-authentication-from-ssis-packages-in-azure"></a>Azure の SSIS パッケージから Windows 認証を使用してデータ ソースとファイル共有に接続する
Windows 認証を使用して、オンプレミスと Azure の仮想マシンの両方、さらに Azure Files で Azure SSIS 統合ランタイム (IR) と同じ仮想ネットワーク内のデータ ソースとファイル共有に接続できます。 Azure SSIS IR で実行されている SSIS パッケージから Windows 認証を使用してデータ ソースとファイル共有に接続する方法は次の 3 とおりです。

| 接続方法 | 有効な範囲 | セットアップ手順 | パッケージにおけるアクセス方法 | 資格情報のセットと接続されるリソースの数 | 接続されるリソースの種類 | 
|---|---|---|---|---|---|
| `cmdkey` コマンドを使用して資格情報を保持する | Azure SSIS IR 単位 | Azure SSIS IR のプロビジョニングまたは再構成の際にカスタム セットアップ スクリプト (`main.cmd`) の `cmdkey` コマンドを実行します。たとえば、次のように指定します。`cmdkey /add:fileshareserver /user:xxx /pass:yyy`<br/><br/> 詳細については、「[Azure-SSIS 統合ランタイムの設定のカスタマイズ](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup)」を参照してください。 | UNC パスを使用して、パッケージ内のリソースに直接アクセスします。たとえば、次のように指定します。`\\fileshareserver\folder` | 接続されるリソースごとに複数の資格情報のセットをサポート | - オンプレミスまたは Azure VM 上のファイル共有<br/><br/> - Azure Files ([Azure ファイル共有の使用](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows)に関する記事を参照) <br/><br/> - Windows 認証を使用する SQL Server<br/><br/> - Windows 認証を使用するその他のリソース |
| カタログ レベルの実行コンテキストを設定する | Azure SSIS IR 単位 | SSISDB `catalog.set_execution_credential` ストアド プロシージャを実行し、"として実行" コンテキストを設定します。<br/><br/> 詳細については、この記事の以降の内容を参照してください。 | パッケージ内のリソースに直接アクセスします。 | 接続されるすべてのリソースに対して資格情報のセットを 1 つだけサポート | - オンプレミスまたは Azure VM 上のファイル共有<br/><br/> - Azure Files ([Azure ファイル共有の使用](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows)に関する記事を参照) <br/><br/> - Windows 認証を使用する SQL Server<br/><br/> - Windows 認証を使用するその他のリソース | 
| パッケージの実行時にドライブをマウントする (非永続化) | パッケージ単位 | プロセス実行タスクの `net use` コマンドを実行します。このコマンドは、パッケージ内の制御フローの先頭に追加されます。たとえば、次のように指定します。`net use D: \\fileshareserver\sharename` | マップ済みドライブを使用してファイル共有にアクセスします。 | ファイル共有ごとに複数のドライブをサポート | - オンプレミスまたは Azure VM 上のファイル共有<br/><br/> - Azure Files ([Azure ファイル共有の使用](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows)に関する記事を参照) |
|||||||

> [!WARNING]
> 前述のいずれかの方法で Windows 認証を使用してデータ ソースまたはファイル共有に接続しない場合、Windows 認証に依存するパッケージはそのデータ ソースまたはファイル共有に接続できず、実行時に失敗します。 

この記事の以降の部分では、Azure SQL Database で SSIS カタログを構成して、Windows 認証を使用するパッケージを実行し、データ ソースとファイル共有に接続する方法について説明します。 

## <a name="you-can-only-use-one-set-of-credentials"></a>使用できる資格情報は 1 セットのみ
SSIS パッケージ内の Windows 認証を使用する場合は、パッケージ内の資格情報のセットを 1 つだけ使用できます。 この記事の手順を実行するときに指定したドメインの資格情報は、資格情報を変更または削除するまで、Azure-SSIS IR のすべてのパッケージの実行 (インタラクティブまたはスケジュール) に適用されます。 パッケージを資格情報のセットが異なる複数のデータ ソースおよびファイル共有に接続しなければならない場合は、前述の別の方法の検討が必要になる可能性があります。

## <a name="provide-domain-credentials-for-windows-authentication"></a>Windows 認証のドメイン資格情報を提供する
パッケージが Windows 認証を使用して、オンプレミスのデータ ソース/ファイル共有に接続できるようにするドメイン資格情報を提供するには、次のことを行います。

1.  SQL Server Management Studio (SSMS) または別のツールを使用して、SSIS カタログ データベース (SSISDB) をホストする SQL Database に接続します。 詳細については、「[Azure の SSIS カタログ (SSISDB) に接続する](ssis-azure-connect-to-catalog-database.md)」を参照してください。

2.  SSISDB を現在のデータベースとして使用し、クエリ ウィンドウを開きます。

3.  次のストアド プロシージャを実行し、適切なドメイン資格情報を提供します。

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```

4.  SSIS パッケージを実行します。 パッケージは、指定した資格情報を使用して、Windows 認証でオンプレミス データ ソース/ファイル共有に接続します。

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
3.  Windows 認証で接続するには、Azure-SSIS IR がオンプレミスの SQL Server も含む仮想ネットワークに属していることを確認します。  詳しくは、「[Azure-SSIS 統合ランタイムを仮想ネットワークに参加させる](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network)」をご覧ください。 次に、この記事で説明されているように `catalog.set_execution_credential` を使用して資格情報を提供します。

## <a name="connect-to-an-on-premises-file-share"></a>オンプレミスのファイル共有への接続
オンプレミスのファイル共有に接続できるかどうかをテストするには、次のことを行います。

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

Azure Files のファイル共有に接続するには、次のことを行います。

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
