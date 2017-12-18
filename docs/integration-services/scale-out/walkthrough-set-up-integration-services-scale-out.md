---
title: "チュートリアル: SQL Server Integration Services Scale Out をセットアップする | Microsoft Docs"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ec9744a1efb0e78aca55e85e7f9f3eca007de5a2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="walkthrough-set-up-integration-services-scale-out"></a>チュートリアル: Integration Services Scale Out をセットアップする
以下のタスクを実行して、[!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] Scale Out をセットアップします。 

> [!NOTE]
> Scale Out を 1 台のコンピューターにインストールする場合は、Scale Out Master 機能と Scale Out Worker 機能を同時にインストールします。 そうすると、Scale Out Master に接続するためのエンドポイントが自動的に生成されます。 

* [Scale Out Master をインストールする](#InstallMaster)

* [Scale Out Worker をインストールする](#InstallWorker)

* [Scale Out Worker クライアント証明書をインストールする](#InstallCert)

* [ファイアウォールのポートを開く](#Firewall)

* [SQL Server Scale Out Master および Worker サービスを開始する](#Start)

* [Scale Out Master を有効にする](#EnableMaster)

* [SQL Server 認証モードを有効にする](#EnableAuth)

* [Scale Out Worker を有効にする](#EnableWorker)

## <a name="InstallMaster"></a> Scale Out Master をインストールする

Scale Out Master の機能を有効にするには、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] をセットアップするときに、データベース エンジン サービス、[!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)]、およびその Scale Out Master 機能をインストールする必要があります。 

データベース エンジン サービスと [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] のセットアップについては、「[SQL Server データベース エンジンのインストール](../../database-engine/install-windows/install-sql-server-database-engine.md)」および「[Integration Services のインストール](../install-windows/install-integration-services.md)」をご覧ください。
> [!NOTE]
> Scale Out ログの既定の SQL 認証アカウントを使用するには、データベース エンジンのインストール時に [データベース エンジンの構成] ページの [認証モード] で [混合モード] を選択します。 詳細については、「[Scale Out ログのアカウントの変更](change-logdb-account.md)」を参照してください。

**Scale Out Master 機能をインストールするには、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インストール ウィザードまたはコマンド プロンプト**を使います。

- [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インストール ウィザードの手順
  1.  **[機能の選択]** ページで、[[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]] の下に一覧表示される **[Scale Out Master]** を選択します。   
  ![Master 機能の選択](media/feature-select-master.PNG)
  
  2.  **[サーバーの構成]** ページで、 **[SQL Server Integration Services Scale Out Master service]** (SQL Server Integration Services Scale Out Master サービス) を実行するアカウントを選び、 **[スタートアップの種類]**を選びます。  
  ![サーバーの構成](media/server-config.PNG)
  3.  **[Integration Services Scale Out Master Configuration]** (Integration Services Scale Out Master の構成) ページで、Scale Out Master が Scale Out Worker との通信に使うポート番号を指定します。 既定のポート番号は 8391 です。  
  ![マスターの構成](media/master-config.PNG "マスターの構成")
  4.  次のいずれかを行って、Scale Out Master と Scale Out Worker の間の通信の保護に使用する SSL 証明書を指定します。
    * **[新しい SSL 証明書の作成]** をクリックして、セットアップ プロセスで既定の自己署名 SSL 証明書を作成します。  既定の証明書は、ローカル コンピューターの信頼されたルート証明機関にインストールされます。 この証明書で CN を指定できます。 マスター エンドポイントのホスト名は、CN に含める必要があります。 既定では、マスター ノードのコンピューター名と IP が含まれます。
    * **[既存の SSL 証明書を使用する]** をクリックしてから **[参照]** をクリックして証明書を選択し、ローカル コンピューターで既存の SSL 証明書を選択します。 証明書のサムプリントがテキスト ボックスに表示されます。 **[Browse]** (参照) をクリックすると、ローカル コンピューターの信頼されたルート証明機関に格納されている証明書が表示されます。 選択する証明書はここに格納されている必要があります。       
![マスターの構成 2](media/master-config-2.PNG "マスターの構成 2")
  5.  [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インストール ウィザードを最後まで実行します。
- コマンド プロンプトの手順

    「[コマンド プロンプトからの SQL Server のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」の手順に従います。 次のようにして、Scale Out Master 関連のパラメーターを設定します。
  1.  パラメーター /FEATURES に IS_Master を追加します。
  2.  パラメーター /ISMASTERSVCACCOUNT, /ISMASTERSVCPASSWORD, /ISMASTERSVCSTARTUPTYPE, /ISMASTERSVCPORT, /ISMasterSVCSSLCertCN (省略可能), /ISMASTERSVCTHUMBPRINT (省略可能) とその値を指定して、Scale Out Master を構成します。

> [!Note]
> Scale Out Master が Microsoft SQL Server データベース エンジンと共にインストールされず、そのデータベース エンジンが名前付きインスタンスである場合は、インストール後に Scale Out Master サービス構成ファイルで SqlServerName を構成する必要があります。 詳細については、「[Scale Out Master](integration-services-ssis-scale-out-master.md)」を参照してください。

## <a name="InstallWorker"></a> Scale Out Worker をインストールする
 
Scale Out Worker の機能を有効にするには、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] のセットアップで [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] とその Scale Out Worker 機能をインストールする必要があります。

**Scale Out Worker 機能をインストールするには、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インストール ウィザードまたはコマンド プロンプト**を使います。

- [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インストール ウィザードの手順
  1.  **[機能の選択]** ページで、[[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]] の下に一覧表示される **[Scale Out Worker]** を選択します。   
  ![Worker 機能の選択](media/feature-select-worker.PNG)
  2. **[サーバーの構成]** ページで、 **[SQL Server Integration Services Scale Out Worker service]** (SQL Server Integration Services Scale Out Worker サービス) を実行するアカウントを選び、 **[スタートアップの種類]**を選びます。    
  ![サーバーの構成 2](media/server-config-2.PNG "サーバーの構成 2")
  3. **[Integration Services Scale Out Worker Configuration]** (Integration Services Scale Out Worker の構成) ページで、Scale Out Master に接続するエンドポイントを指定します。 
      > [!Note]
      > ここでワーカー ノードの構成 (手順 3 と 4) を省略し、インストール後に [Scale Out Manager](integration-services-ssis-scale-out-manager.md) を使用して Scale Out Worker を Scale Out Master に関連付けることができます。

    - **1 台のコンピューター**環境では、Scale Out Master と Scale Out Worker を同時にインストールすると、エンドポイントが自動的に生成されます。 
    - **複数コンピューター**環境では、エンドポイントは、Scale Out Master がインストールされているコンピューターの名前または IP と、Scale Out Master のインストール時に指定したポート番号で構成されます。    
   ![ワーカーの構成 1](media/worker-config.PNG "ワーカーの構成 1")    

  4. **複数コンピューター**環境の場合は、Scale Out Master の検証に使用されるクライアント SSL 証明書を指定します。 **1 台のコンピューター**環境の場合は、クライアント SSL 証明書を指定する必要はありません。 
  
     > [!NOTE]
     > Scale Out Master で使用される SSL 証明書が自己署名されている場合は、Scale Out Worker のコンピューターに対応するクライアント SSL 証明書をインストールする必要があります。 **[Integration Services スケール アウト ワーカーの構成]** ページでクライアント SSL 証明書のファイル パスを指定した場合、証明書は自動的にインストールされます。それ以外の場合は、後で証明書を手動でインストールする必要があります。 
     
     **[Browse]** (参照) をクリックして、証明書ファイル (*.cer) を指定します。 既定の SSL 証明書を使用する場合は、Scale Out Master がインストールされているコンピューターの \<ドライブ\>:\Program Files\Microsoft SQL Server\140\DTS\Binn にある SSISScaleOutMaster.cer ファイルを選択します。   
   ![ワーカーの構成 2](media/worker-config-2.PNG "ワーカーの構成 2")
  5. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インストール ウィザードを最後まで実行します。
- コマンド プロンプトの手順

    「[コマンド プロンプトからの SQL Server のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」の手順に従います。 次のようにして、Scale Out Worker 関連のパラメーターを設定します。
    1.  パラメーター /FEATURES に IS_Worker を追加します。
    2. パラメーター /ISWORKERSVCACCOUNT、/ISWORKERSVCPASSWORD、/ISWORKERSVCSTARTUPTYPE、/ISWORKERSVCMASTER (省略可能)、/ISWORKERSVCCERT (省略可能) とその値を指定して、Scale Out Worker を構成します。

 
## <a name="InstallCert"></a> Scale Out Worker クライアント証明書をインストールする

Scale Out Worker のインストール時に、ワーカー証明書が自動的に作成され、コンピューターにインストールされます。 また、対応するクライアント証明書 SSISScaleOutWorker.cer が \<ドライブ\>:\Program Files\Microsoft SQL Server\140\DTS\Binn にインストールされます。 Scale Out Master で Scale Out Worker を認証するには、このクライアント証明書を Scale Out Master のローカル コンピューターのルート ストアに追加する必要があります。
  
ルート ストアにクライアント証明書を追加するには、.cer ファイルをダブルクリックし、[証明書] ダイアログ ボックスで **[証明書のインストール]** をクリックします。 **証明書のインポート ウィザード** が表示されます。  

## <a name="Firewall"></a> ファイアウォールのポートを開く

Scale Out Master コンピューターの Windows ファイアウォールを使用して、Scale Out Master のインストール時に指定したポートと SQL Server のポート (既定では 1433) を開きます。
    
## <a name="Start"></a> SQL Server Scale Out Master および Worker サービスを開始する

インストール時にサービスのスタートアップの種類を自動に設定しなかった場合は、サービス SQL Server Integration Services Scale Out Master 14.0 (SSISScaleOutMaster140) と SQL Server Integration Services Scale Out Worker 14.0 (SSISScaleOutWorker140) を開始します。 

> [!Note]
> ファイアウォールのポートを開いた後に、Scale Out Worker サービスを再開する必要もあります。
   
## <a name="EnableMaster"></a> Scale Out Master を有効にする

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio_md](../../includes/ssmanstudio-md.md)] で SSISDB カタログを作成するときに、**[カタログの作成]** ダイアログ ボックスで **[Enable this server as SSIS scale out master]** (このサービスを SSIS Scale Out Master として有効にする) をクリックします。 カタログが作成されてから、[Scale Out Manager](integration-services-ssis-scale-out-manager.md) を使用して Scale Out Master を有効にすることもできます。

## <a name="EnableAuth"></a> SQL Server 認証モードを有効にする
データベース エンジンをインストールするときに [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 認証を有効にしなかった場合は、SSISDB カタログをホストする [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスで SQL Server 認証モードを有効にします。 

SQL Server 認証を無効にすると、パッケージの実行はブロックされません。 ただし、実行ログを SSISDB に書き込むことはできません。

## <a name="EnableWorker"></a> Scale Out Worker を有効にする

GUI を提供する [Scale Out Manager](integration-services-ssis-scale-out-manager.md) を使用して Scale Out Worker を有効にすることができます。また、次のようにストアド プロシージャを使用して有効にすることもできます。

Scale Out Worker を有効にするには、パラメーターとして *WorkerAgentId* を指定して **[catalog].[enable_worker_agent]** ストアド プロシージャを実行します。 

**WorkerAgentId** の値は、Scale Out Worker を Scale Out Master に登録した後で SSISDB の *[catalog].[worker_agents]* データベース ビューから取得します。 Scale Out Master および Worker サービスを開始した後、登録には数分かかります。

#### <a name="example"></a>例
この例では、computerA で Scale Out Worker を有効にします。
```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName  --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    computerA    --

EXEC [catalog].[enable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```
## <a name="next-steps"></a>次の手順
Scale Out 機能のセットアップが終わりました。 これで、Scale Out のパッケージを実行できます。詳しくは、「[Integration Services (SSIS) Scale Out でパッケージを実行する](run-packages-in-integration-services-ssis-scale-out.md)」をご覧ください。
