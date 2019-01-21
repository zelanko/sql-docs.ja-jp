---
title: チュートリアル:SSMS を使用したセキュア エンクレーブを使用する Always Encrypted の概要 | Microsoft Docs
ms.custom: ''
ms.date: 10/04/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: jaszymas
ms.author: jaszymas
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: a4d833d132a0b4928d021beaa4cd9fcdd695d6c6
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046582"
---
# <a name="tutorial-getting-started-with-always-encrypted-with-secure-enclaves-using-ssms"></a>チュートリアル:SSMS を使用したセキュリティで保護されたエンクレーブを持つ Always Encrypted の概要
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このチュートリアルでは、[セキュア エンクレーブを使用する Always Encrypted](encryption/always-encrypted-enclaves.md) の開始方法について説明します。 次のことを示します。
- セキュア エンクレーブを使用する Always Encrypted をテストおよび評価する単純な環境を作成する方法。
- SQL Server Management Studio (SSMS) を使用して、データのインプレース暗号化を行い、暗号化された列に対して高度なクエリを実行する方法。

## <a name="prerequisites"></a>Prerequisites

セキュア エンクレーブを使用する Always Encrypted を開始するには、少なくとも 2 台のコンピューター (仮想マシンも可) が必要です。

- SQL Server と SSMS をホストする SQL Server コンピューター。
- エンクレーブの構成証明に必要なホスト ガーディアン サービスを実行する HGS コンピューター。

### <a name="sql-server-computer-requirements"></a>SQL Server コンピューターの要件

- [!INCLUDE [sssqlv15-md](../../includes/sssqlv15-md.md)] 以降
- Windows 10 Enterprise バージョン 1809、または Windows Server 2019 Datacenter
- [SQL Server Management Studio (SSMS) 18.0 以降](../../ssms/download-sql-server-management-studio-ssms.md)。

または、別のマシンに SSMS をインストールすることができます。

>[!WARNING] 
>運用環境では、SSMS またはその他のツールを使用して Always Encrypted キーを管理したり、SQL Server コンピューター上の暗号化されたデータに対してクエリを実行したりしないでください。これらの操作を行うと、Always Encrypted の使用目的が一部または完全に達成されなくなることがあります。

### <a name="hgs-computer-requirements"></a>HGS コンピューターの要件

- Windows Server 2019 Standard または Datacenter Edition
- 2 つの CPU
- 8 GB RAM
- 100 GB ストレージ

>[!NOTE]
>開始する前に、HGS コンピューターがドメインに参加していてはなりません。

## <a name="step-1-configure-the-hgs-computer"></a>手順 1:HGS コンピューターを構成する

この手順では、ホスト キーの構成証明をサポートしているホスト ガーディアン サービスを実行するように HGS コンピューターを構成します。

1. HGS コンピューターに管理者 (ローカル管理者) としてサインインし、管理者特権の Windows PowerShell コンソールを開き、次のコマンドを実行してホスト ガーディアン サービスの役割を追加します。

   ```powershell
   Install-WindowsFeature -Name HostGuardianServiceRole -IncludeManagementTools -Restart
   ```

2. HGS コンピューターが再起動した後、管理者アカウントでもう一度サインインし、管理者特権の Windows PowerShell コンソールを開きます。次のコマンドを実行してホスト ガーディアン サービスをインストールし、そのドメインを構成します。 ここで指定したパスワードは、Active Directory のディレクトリ サービスの修復モード パスワードに対してのみ適用されます、管理者アカウントのログイン パスワードは変更されません。 -HgsDomainName に対して任意のドメイン名を指定できます。

   ```powershell
   $adminPassword = ConvertTo-SecureString -AsPlainText '<password>' -Force
   Install-HgsServer -HgsDomainName 'bastion.local' -SafeModeAdministratorPassword $adminPassword -Restart
   ```

3. コンピューターが再起動したら、管理者アカウント (今回もドメイン管理者) でサインインし、管理者特権の Windows PowerShell コンソールを開いて、HGS インスタンスのホスト キーの構成証明を構成します。 

   ```powershell
   Initialize-HgsAttestation -HgsServiceName 'hgs' -TrustHostKey  
   ```

4. 次のコマンドを実行して、HGS コンピューターの IP アドレスを検索します。 後の手順で使用するために、この IP アドレスを保存します。

   ```powershell
   Get-NetIPAddress  
   ```

>[!NOTE]
>または、HGS コンピューターを DNS 名によって参照する場合は、企業の DNS サーバーから新しい HGS ドメイン コントローラーにフォワーダーを設定できます。  

## <a name="step-2-configure-the-sql-server-computer-as-a-guarded-host"></a>手順 2:SQL Server コンピューターを保護されたホストとして構成する
この手順では、ホスト キーの構成証明を使用して、HGS に登録されている保護されたホストとして SQL Server コンピューターを構成します。
>[!NOTE]
>ホスト キーの構成証明はテスト環境でのみ使用することをお勧めします。 運用環境では、TPM 構成証明を使用してください。

1. 管理者として SQL Server コンピューターにサインインし、管理者特権の Windows PowerShell コンソールを開いて、保護されたホスト機能をインストールします。これにより、Hyper-V もインストールされます (まだインストールされていない場合)。

   ```powershell
   Enable-WindowsOptionalFeature -Online -FeatureName HostGuardian -All
   ```

2. Hyper-V のインストールを完了するように求められたら、SQL Server コンピューターを再起動します。
3. 以下の変数の値を取得して、SQL Server コンピューターの名前を確認します。

   ```powershell
   $env:computername 
   ```

4. もう一度 SQL Server コンピューターに管理者としてサインインし、管理者特権の Windows PowerShell コンソールを開きます。一意のホスト キーを生成し、結果の公開キーをファイルにエクスポートします。

   ```powershell
   Set-HgsClientHostKey 
   Get-HgsClientHostKey -Path $HOME\Desktop\hostkey.cer
   ```

5. 前の手順で生成されたホスト キー ファイルを HGS マシンにコピーします。 次の手順では、ファイル名が hostkey.cer で、これを HGS マシン上のデスクトップにコピーすることを想定しています。
6. HGS コンピューター上で、管理者特権の Windows PowerShell コンソールを開き、SQL Server コンピューターのホスト キーを HGS に登録します。

   ```powershell
   Add-HgsAttestationHostKey -Name <your SQL Server computer name> -Path $HOME\Desktop\hostkey.cer
   ```

7. SQL Server コンピューター上で、管理者特権の Windows PowerShell コンソール内で次のコマンドを実行して、SQL Server コンピューターに証明する場所を指示します。 HGS コンピューターの IP アドレスまたは DNS 名を必ず指定します。 

   ```powershell
   # use http, and not https
   Set-HgsClientConfiguration -AttestationServerUrl http://<IP address or DNS name>/Attestation -KeyProtectionServerUrl http://<IP address or DNS name>/KeyProtection/  
   ```

上記のコマンドの結果として、AttestationStatus = Passed と表示されます。

HostUnreachable エラーが発生する場合、SQL Server コンピューターが HGS と通信できないことを意味します。 HGS コンピューターに対して ping を実行できることを確認します。

UnauthorizedHost エラーは、公開キーが HGS サーバーに登録されていないことを示します。手順 5. と 6. を繰り返してエラーを解決します。

他のすべてに失敗した場合は、Clear-HgsClientHostKey を実行し、手順 4. から 7. を繰り返します。

## <a name="step-3-enable-always-encrypted-with-secure-enclaves-in-sql-server"></a>手順 3:SQL Server 上でセキュア エンクレーブを使用する Always Encrypted を有効にする

この手順では、SQL Server インスタンス上でエンクレーブを使用する Always Encrypted の機能を有効にします。

1. SSMS を開き、sysadmin として SQL Server インスタンスに接続し、新しいクエリ ウィンドウを開きます。
2. セキュア エンクレーブの型を VBS に構成します。

   ```sql
   EXEC sys.sp_configure 'column encryption enclave type', 1
   RECONFIGURE
   ```

3. SQL Server インスタンスを再起動して、前の変更を反映します。 SSMS でインスタンスを再起動するには、オブジェクト エクスプローラー上でそのインスタンスを右クリックし、[再起動] を選択します。 インスタンスの再起動後に、再接続します。

4. 次のクエリを実行して、セキュア エンクレーブが読み込まれていることを確認します。

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type'
   ```

    クエリによって、次のような行が返されます。  

    | NAME                           | value | value_in_use |
    | ------------------------------ | ----- | -------------- |
    | 列暗号化エンクレーブの型 | 1     | 1              |

5. 暗号化された列に対して高度な計算を有効にするには、次のクエリを実行します。

   ```sql
   DBCC traceon(127,-1)
   ```

    > [!NOTE]
    > [!INCLUDE [sssqlv15-md](../../includes/sssqlv15-md.md)] では、高度な計算が既定で無効になります。 これらは、SQL Server インスタンスを再起動するたびに、上記のステートメントを使用して有効にする必要があります。

## <a name="step-4-create-a-sample-database"></a>手順 4:サンプル データベースの作成
この手順では、いくつかのサンプル データを含むデータベースを作成し、その後暗号化します。

1. SSMS を使用して SQL Server インスタンスに接続します。
2. ContosoHR という名前の新しいデータベースを作成します。

    ```sql
    CREATE DATABASE [ContosoHR] COLLATE Latin1_General_BIN2
    ```

3. 新規に作成したデータベースに接続していることを確認します。 Employees という名前の新しいテーブルを作成します。

    ```sql
    CREATE TABLE [dbo].[Employees]
    (
        [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
        [SSN] [char](11) NOT NULL,
        [FirstName] [nvarchar](50) NOT NULL,
        [LastName] [nvarchar](50) NOT NULL,
        [Salary] [money] NOT NULL
    ) ON [PRIMARY]
    GO
    ```

4. いくつかの従業員レコードを Employees テーブルに追加します。

    ```sql
    INSERT INTO [dbo].[Employees]
            ([SSN]
            ,[FirstName]
            ,[LastName]
            ,[Salary])
        VALUES
            ('795-73-9838'
            , N'Catherine'
            , N'Abel'
            , $31692)
    GO

    INSERT INTO [dbo].[Employees]
            ([SSN]
            ,[FirstName]
            ,[LastName]
            ,[Salary])
        VALUES
            ('990-00-6818'
            , N'Kim'
            , N'Abercrombie'
            , $55415)
    GO
    ```

## <a name="step-5-provision-enclave-enabled-keys"></a>手順 5:エンクレーブ対応キーをプロビジョニングする

この手順では、エンクレーブ計算を許可する列マスター キーと列暗号化キーを作成します。

1. SSMS を使用してデータベースに接続します。
2. **[オブジェクト エクスプローラー]** で、データベースを展開し、**[セキュリティ]** > **[Always Encrypted キー]** に移動します。
3. エンクレーブ対応の列マスター キーをプロビジョニングします。
    1. **[Always Encrypted キー]** を右クリックし、**[新しい列マスター キー...]** を選択します。
    2. 列マスター キー名CMK1 を選択します。
    3. **[Windows 証明書ストア -現在のユーザー] または [Windows 証明書ストア - ローカル コンピューター]** か、**[Azure Key Vault]** を選択します。
    4. **[エンクレーブ計算を許可する]** を選択します。
    5. [Azure Key Vault] を選択した場合は、Azure にサインインし、キー コンテナーを選択します。 Always Encrypted のキー コンテナーを作成する方法について詳しくは、「[Manage your key vaults from Azure portal](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/)」(Azure portal からキー コンテナーを管理する) を参照してください。
    6. 既にキーが存在する場合はそれを選択します。または、フォームの指示に従って新しいキーを作成します。
    7. **[OK]** を選択します。

        ![エンクレーブ計算を許可する](encryption/media/always-encrypted-enclaves/allow-enclave-computations.png)

4. 新しいエンクレーブ対応の列暗号化キーを作成します。

    1. **[Always Encrypted キー]** を右クリックし、**[新しい列の暗号化キー]** を選択します。
    2. 新しい列暗号化キーの名前CEK1 を入力します。
    3. **[列マスター キー]** ドロップダウンで、前の手順で作成した列マスター キーを選択します。
    4. **[OK]** を選択します。

## <a name="step-6-encrypt-some-columns-in-place"></a>手順 6:一部の列のインプレース暗号化を行う

この手順では、サーバー側エンクレーブ内の SSN および給与列に格納されたデータを暗号化し、データの SELECT クエリをテストします。

1. SSMS で、データベース接続に対して Always Encrypted が有効になっている新しいクエリ ウィンドウを構成します。
    1. SSM で、新しいクエリ ウィンドウを開きます。
    2. 新しいクエリ ウィンドウ内の任意の場所を右クリックします。
    3. [接続] \> [接続の変更] の順に選択します。
    4. **[オプション]** を選択します。 **[Always Encrypted]** タブに移動し、**[Always Encrypted を有効にする]** を選択し、エンクレーブ構成証明 URL を指定します。
    5. **[接続]** を選択します。
2. SSMS 上で、データベース接続に対して Always Encrypted が無効になっている別のクエリ ウィンドウを構成します。
    1. SSM で、新しいクエリ ウィンドウを開きます。
    2. 新しいクエリ ウィンドウ内の任意の場所を右クリックします。
    3. [接続] \> [接続の変更] の順に選択します。
    4. **[オプション]** を選択します。 **[Always Encrypted]** タブに移動し、**[Always Encrypted を有効にする]** が選択されていないことを確認します。
    5. **[接続]** を選択します。
3. SSN と給与の列を暗号化します。 Always Encrypted を有効にしたクエリ ウィンドウで、次のステートメントを貼り付けて実行します。

    ```sql
    ALTER TABLE [dbo].[Employees]
    ALTER COLUMN [SSN] [char] (11)
    ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
    WITH
    (ONLINE = ON)
    GO
    DBCC FREEPROCCACHE
    GO

    ALTER TABLE [dbo].[Employees]
    ALTER COLUMN [Salary] [money]
    ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
    WITH
    (ONLINE = ON)
    GO
    DBCC FREEPROCCACHE
    GO
    ```

4. SSN と給与の列が暗号化されていることを確認するには、Always Encrypted を無効にしたクエリ ウィンドウで、次のステートメントを貼り付け、実行します。 クエリ ウィンドウで、SSN と給与の列に暗号化された値が返されます。 Always Encrypted が有効なクエリ ウィンドウで、同じクエリを試して復号化されたデータを確認します。

    ```sql
    SELECT * FROM [dbo].[Employees]
    ```

## <a name="step-7-run-rich-queries-against-encrypted-columns"></a>手順 7:暗号化された列に対して高度なクエリを実行する

ここで、暗号化された列に対して高度なクエリを実行できます。 いくつかのクエリ処理は、サーバー側エンクレーブ内で実行されます。 

1. Always Encrypted のパラメーター化を有効にします。
    1. SSMS のメイン メニューから **[クエリ]** を選択します。
    2. **[クエリ オプション...]** を選択します。
    3. **[実行]** > **[詳細]** の順に移動します。
    4. [Always Encrypted のパラメーター化を有効にする]をオンまたはオフにします。
    5. [OK] を選択します。
2. Always Encrypted を有効にしたクエリ ウィンドウで、次のクエリを貼り付けて実行します。 クエリでは、指定した検索条件を満たすプレーンテキスト値と行が返されます。

    ```sql
    DECLARE @SSNPattern [char](11) = '%6818'
    DECLARE @MinSalary [money] = $1000
    SELECT * FROM [dbo].[Employees]
    WHERE SSN LIKE @SSNPattern AND [Salary] >= @MinSalary;
    ```

## <a name="next-steps"></a>Next Steps
その他のユース ケースについては、「[Configure Always Encrypted with secure enclaves](encryption/configure-always-encrypted-enclaves.md)」(セキュア エンクレーブを使用する Always Encrypted の構成) をご覧ください。 次のことを試すこともできます。

- [TPM 構成証明を構成する。](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode)
- [HGS インスタンスに対して HTTPS を構成する。](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-https)
- 暗号化された列に対して高度なクエリを発行するアプリケーションを開発する。
