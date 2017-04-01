---
title: "チュートリアル: Integration Services Scale Out をセットアップする | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cabb78a2-f234-46c3-842d-53aa2df8dfb3
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# チュートリアル: Integration Services Scale Out をセットアップする

以下のタスクを実行して、[!INCLUDE[ssISnoversion_md](../includes/ssisnoversion-md.md)] Scale Out をセットアップします。 

> [!NOTE] Scale Out を 1 台のコンピューターにインストールする場合は、Scale Out Master 機能と Scale Out Worker 機能を同時にインストールすることをお勧めします。 そうすると、Scale Out Master に接続するためのエンドポイントが自動的に生成されます。 

* [Scale Out Master をインストールする](#InstallMaster)

* [Scale Out Worker をインストールする](#InstallWorker)

* [Scale Out Worker クライアント証明書をインストールする](#InstallCert)

* [ファイアウォールのポートを開く](#Firewall)

* [SQL Server Scale Out Master および Worker サービスを開始する](#Start)

* [Scale Out Master を有効にする](#EnableMaster)

* [SQL Server 認証モードを有効にする](#EnableAuth)

* [Scale Out Worker を有効にする](#EnableWorker)

## <a name="a-nameinstallmastera-install-scale-out-master"></a><a name="InstallMaster"></a> Scale Out Master をインストールする

Scale Out Master の機能を有効にするには、[!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] をセットアップするときに、データベース エンジン サービス、[!INCLUDE[ssISnoversion_md](../includes/ssisnoversion-md.md)]、およびその Scale Out Master 機能をインストールする必要があります。 

データベース エンジン サービスと [!INCLUDE[ssISnoversion_md](../includes/ssisnoversion-md.md)] のセットアップについては、「[SQL Server データベース エンジンのインストール](../database-engine/install-windows/install-sql-server-database-engine.md)」および「[Integration Services のインストール](../integration-services/install-windows/install-integration-services.md)」をご覧ください。
> [!NOTE]
> データベース エンジンのインストールでは、[データベース エンジンの構成] ページの [認証モード] で [混合モード] を選びます。 

**Scale Out Master 機能をインストールするには、[!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] インストール ウィザードまたはコマンド プロンプト**を使います。

- [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] インストール ウィザードの手順
  1.  **[機能の選択]** ページで、[[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]] の下に表示される **[Scale Out Master]** (Scale Out Master) を選びます。   
  ![Master 機能の選択](../integration-services/media/feature-select-master.PNG)
  
  2.  **[サーバーの構成]** ページで、**[SQL Server Integration Services Scale Out Master service]** (SQL Server Integration Services Scale Out Master サービス) を実行するアカウントを選び、**[スタートアップの種類]** を選びます。  
  ![サーバーの構成](../integration-services/media/server-config.PNG)
  3.  **[Integration Services Scale Out Master Configuration]** (Integration Services Scale Out Master の構成) ページで、Scale Out Master が Scale Out Worker との通信に使うポート番号を指定します。 既定のポート番号は 8391 です。  
  ![Master Config](../integration-services/media/master-config.PNG "Master Config")
  4.  次のいずれかを行って、Scale Out Master と Scale Out Worker の間の通信の保護に使う SSL 証明書を指定します。
    * **[Create a new SSL certificate]** (新しい SSL 証明書を作成する) をクリックして、セットアップ プロセスで既定の自己署名 SSL 証明書を作成します。 既定の証明書は、ローカル コンピューターの信頼されたルート証明機関にインストールされます。
    * **[Use an existing SSL certificate]** (既存の SSL 証明書を使用する) をクリックして **[Browse]** (参照) をクリックし、ローカル コンピューターで既存の SSL 証明書を選びます。 証明書のサムプリントがテキスト ボックスに表示されます。 **[Browse]** (参照) をクリックすると、ローカル コンピューターの信頼されたルート証明機関に格納されている証明書が表示されます。 選択する証明書はここに格納されている必要があります。       
![Master Config 2](../integration-services/media/master-config-2.PNG "Master Config 2")
  5.  [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] インストール ウィザードを最後まで実行します。
- コマンド プロンプトの手順

    「[コマンド プロンプトからの SQL Server のインストール](../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」の手順に従います。 次のようにして、Scale Out Master 関連のパラメーターを設定します。
  1.  パラメーター /FEATURES に IS_Master を追加します。
  2.  パラメーター /ISMASTERSVCACCOUNT、/ISMASTERSVCPASSWORD、/ISMASTERSVCSTARTUPTYPE、/ISMASTERSVCPORT、/ISMASTERSVCTHUMBPRINT (省略可能) で Scale Out Master を構成します。
  
## <a name="a-nameinstallworkera-install-scale-out-worker"></a><a name="InstallWorker"></a> Scale Out Worker をインストールする
 
Scale Out Worker の機能を有効にするには、[!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] のセットアップで [!INCLUDE[ssISnoversion_md](../includes/ssisnoversion-md.md)] とその Scale Out Worker 機能をインストールする必要があります。

**Scale Out Worker 機能をインストールするには、[!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] インストール ウィザードまたはコマンド プロンプト**を使います。

- [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] インストール ウィザードの手順
  1.  **[機能の選択]** ページで、[[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]] の下に表示される **[Scale Out Worker]** (Scale Out Worker) を選びます。   
  ![Worker 機能の選択](../integration-services/media/feature-select-worker.PNG)
  2. **[サーバーの構成]** ページで、**[SQL Server Integration Services Scale Out Worker service]** (SQL Server Integration Services Scale Out Worker サービス) を実行するアカウントを選び、**[スタートアップの種類]** を選びます。    
  ![Server Config 2](../integration-services/media/server-config-2.PNG "Server Config 2")
  3. **[Integration Services Scale Out Worker Configuration]** (Integration Services Scale Out Worker の構成) ページで、Scale Out Master に接続するエンドポイントを指定します。 
    - **ワンボックス**環境では、Scale Out Master と Scale Out Worker を同時にインストールすると、エンドポイントが自動的に生成されます。 
    - **複数コンピューター**環境のエンドポイントは、Scale Out Master がインストールされているコンピューターの名前または IP と、Scale Out Master のインストール時に指定したポート番号で構成されます。    
   ![Worker Config 1](../integration-services/media/worker-config-1.PNG "Worker Config 1")
    
  4. **複数コンピューター**環境の場合は、Scale Out Master の検証に使われるクライアント SSL 証明書を指定します。 **ワンボックス**環境の場合は、クライアント SSL 証明書を指定する必要はありません。 
  
     > [!NOTE] Scale Out Master によって使われる SSL 証明書が自己署名されている場合は、Scale Out Worker のコンピューターに対応するクライアント SSL 証明書をインストールする必要があります。 **[Integration Services Scale Out Worker Configuration]** (Integration Services Scale Out Worker の構成) ページでクライアント SSL 証明書のファイル パスを指定した場合は、自動的にインストールされます。指定しなかった場合は、後で手動により証明書をインストールする必要があります。 
     
     **[Browse]** (参照) をクリックして、証明書ファイル (*.cer) を指定します。 既定の SSL 証明書を使う場合は、Scale Out Master をインストールしたコンピューターの \<ドライブ\>:\Program Files\Microsoft SQL Server\140\DTS\Binn にある SSISScaleOutMaster.cer ファイルを選びます。   
   ![Worker Config 2](../integration-services/media/worker-config-2.PNG "Worker Config 2")
  5. [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] インストール ウィザードを最後まで実行します。
- コマンド プロンプトの手順

    「[コマンド プロンプトからの SQL Server のインストール](../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」の手順に従います。 次のようにして、Scale Out Worker 関連のパラメーターを設定します。
    1.  パラメーター /FEATURES に IS_Worker を追加します。
    2. パラメーター /ISWORKERSVCACCOUNT、/ISWORKERSVCPASSWORD、/ISWORKERSVCSTARTUPTYPE、/ISWORKERSVCMASTER (省略可能)、/ISWORKERSVCCERT (省略可能) で、Scale Out Worker を構成します。

 
## <a name="a-nameinstallcerta-install-scale-out-worker-client-certificate"></a><a name="InstallCert"><a/> Scale Out Worker クライアント証明書をインストールする

Scale Out Worker のインストールの間に、ワーカー証明書が自動的に作成されて、コンピューターにインストールされます。 また、対応するクライアント証明書 SSISScaleOutWorker.cer が \<ドライブ\>:\Program Files\Microsoft SQL Server\140\DTS\Binn にインストールされます。 Scale Out Master が Scale Out Worker を認証するには、このクライアント証明書を Scale Out Master のローカル コンピューターのルート ストアに追加する必要があります。
  
ルート ストアにクライアント証明書を追加するには、.cer ファイルをダブルクリックし、[証明書] ダイアログ ボックスで **[証明書のインストール]** をクリックします。 **証明書のインポート ウィザード**が表示されます。  

## <a name="a-namefirewalla-open-firewall-port"></a><a name="Firewall"><a/> ファイアウォールのポートを開く

Scale Out Master コンピューターの Windows ファイアウォールを使って、Scale Out Master のインストールの間に指定したポートを開きます。
    
## <a name="a-namestarta-start-sql-server-scale-out-master-and-worker-services"></a><a name="Start"></a> SQL Server Scale Out Master および Worker サービスを開始する

前記のインストールの間にサービスのスタートアップの種類を自動に設定しなかった場合は、サービス SQL Server Integration Services Scale Out Master 14.0 (SSISScaleOutMaster140) と SQL Server Integration Services Scale Out Worker 14.0 (SSISScaleOutWorker140) を開始します。 

> [!NOTE]
>ファイアウォールのポートを開いた後は、Scale Out Worker サービスを開始し直す必要があります。
   
## <a name="a-nameenablemastera-enable-scale-out-master"></a><a name="EnableMaster"></a> Scale Out Master を有効にする

[!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio_md](../includes/ssmanstudio-md.md)] で SSISDB カタログを作成するときに、**[カタログの作成]** ダイアログ ボックスで **[Enable this server as SSIS scale out master]** (このサービスを SSIS Scale Out Master として有効にする) をクリックします。

## <a name="a-nameenableautha-enable-sql-server-authentication-mode"></a><a name="EnableAuth"></a> SQL Server 認証モードを有効にする
データベース エンジンをインストールするときに [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 認証を有効にしなかった場合は、SSISDB カタログをホストする [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] インスタンスで SQL Server 認証モードを有効にします。 

SQL Server 認証を無効にすると、パッケージの実行はブロックされません。 ただし、実行ログを SSISDB に書き込むことはできません。

## <a name="a-nameenableworkera-enable-scale-out-worker"></a><a name="EnableWorker"></a> Scale Out Worker を有効にする
Scale Out Worker を有効にするには、パラメーターとして **WorkerAgentId** を指定して *[catalog].[enable_worker_agent]* ストアド プロシージャを実行します。 

**WorkerAgentId** の値は、Scale Out Worker を Scale Out Master に登録した後で SSISDB の *[catalog].[worker_agents]* データベース ビューから取得します。 Scale Out Master および Worker サービスを開始した後、登録には数分かかります。

### <a name="example"></a>例
この例では、MachineA で Scale Out Worker を有効にします。
```tsql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    MachineA    --

EXEC [catalog].[enable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```
## <a name="next-steps"></a>次の手順
Scale Out 機能のセットアップが終わりました。 Scale Out のパッケージを実行できます。 詳しくは、「[Integration Services (SSIS) Scale Out でパッケージを実行する](../integration-services/run-packages-in-integration-services-ssis-scale-out.md)」をご覧ください。

