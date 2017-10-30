---
title: "チュートリアル: 設定 SQL Server Integration Services のスケール アウト |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 685286966599c4dcd3dc2f7029413c77f3ff2689
ms.openlocfilehash: c386b01043764405872365af379cfdedb036b65f
ms.contentlocale: ja-jp
ms.lasthandoff: 10/20/2017

---
# <a name="walkthrough-set-up-integration-services-scale-out"></a>チュートリアル: Integration Services Scale Out をセットアップする
セットアップ[!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)]スケール アウトを次のタスクを完了します。 

> [!NOTE]
> スケール アウト 1 台のコンピューターにインストールする場合は、同時にスケール アウト マスターとスケール アウト ワーカー機能をインストールします。 そうすると、Scale Out Master に接続するためのエンドポイントが自動的に生成されます。 

* [Scale Out Master をインストールする](#InstallMaster)

* [Scale Out Worker をインストールする](#InstallWorker)

* [Scale Out Worker クライアント証明書をインストールする](#InstallCert)

* [ファイアウォールのポートを開く](#Firewall)

* [SQL Server Scale Out Master および Worker サービスを開始する](#Start)

* [Scale Out Master を有効にする](#EnableMaster)

* [SQL Server 認証モードを有効にする](#EnableAuth)

* [Scale Out Worker を有効にする](#EnableWorker)

## <a name="InstallMaster"></a> Scale Out Master をインストールする

スケール アウト master データベースの機能を有効にするには、データベース エンジン サービスをインストールする必要があります[!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)]、およびセットアップするときに、スケール アウト マスター機能[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]します。 

データベース エンジン サービスと [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] のセットアップについては、「[SQL Server データベース エンジンのインストール](../../database-engine/install-windows/install-sql-server-database-engine.md)」および「[Integration Services のインストール](../install-windows/install-integration-services.md)」をご覧ください。
> [!NOTE]
> をスケール アウト ログの既定の SQL 認証アカウントを使用するには、データベース エンジンのインストール中にデータベース エンジンの構成 ページでの認証モードを混在モードを選択します。 参照してください[スケール アウト ログのアカウントの変更](change-logdb-account.md)詳細についてはします。

**Scale Out Master 機能をインストールするには、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インストール ウィザードまたはコマンド プロンプト**を使います。

- [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インストール ウィザードの手順
  1.  **機能の選択**] ページで、[**スケール アウト マスター**の下に表示される[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]です。   
  ![Master 機能の選択](media/feature-select-master.PNG)
  
  2.  **[サーバーの構成]** ページで、 **[SQL Server Integration Services Scale Out Master service]** (SQL Server Integration Services Scale Out Master サービス) を実行するアカウントを選び、 **[スタートアップの種類]**を選びます。  
  ![サーバーの構成](media/server-config.PNG)
  3.  **[Integration Services Scale Out Master Configuration]** (Integration Services Scale Out Master の構成) ページで、Scale Out Master が Scale Out Worker との通信に使うポート番号を指定します。 既定のポート番号は 8391 です。  
  ![マスター Config](media/master-config.PNG "マスター構成")
  4.  次のいずれかの方法でスケール アウト マスターとスケール アウト ワーカー間の通信を保護するために使用する SSL 証明書を指定します。
    * 既定で自己署名 SSL 証明書を作成する をクリックして、セットアップ プロセス**新しい SSL 証明書を作成**です。  既定の証明書は、ローカル コンピューターの信頼されたルート証明機関にインストールされます。 この証明書の Cn を指定できます。 マスターのエンドポイントのホスト名は、Cn に含める必要があります。 既定では、コンピューター名と ip アドレスのマスター ノードが含まれます。
    * クリックして、ローカル コンピューター上の既存の SSL 証明書を選択**既存の SSL 証明書を使用して**クリックし、**参照**証明書を選択します。 証明書のサムプリントがテキスト ボックスに表示されます。 **[Browse]** (参照) をクリックすると、ローカル コンピューターの信頼されたルート証明機関に格納されている証明書が表示されます。 選択する証明書はここに格納されている必要があります。       
![マスター Config 2](media/master-config-2.PNG "マスター Config 2")
  5.  [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インストール ウィザードを最後まで実行します。
- コマンド プロンプトの手順

    「[コマンド プロンプトからの SQL Server のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」の手順に従います。 次のようにして、Scale Out Master 関連のパラメーターを設定します。
  1.  パラメーター /FEATURES に IS_Master を追加します。
  2.  次のパラメーターとその値を指定してスケール アウト マスターを構成する:/ISMASTERSVCACCOUNT、/ISMASTERSVCPASSWORD、/ISMASTERSVCSTARTUPTYPE、/ISMASTERSVCPORT、/ISMasterSVCSSLCertCN(optional)、/ISMASTERSVCTHUMBPRINT(optional) です。

> [!Note]
> スケール アウト マスターがデータベース エンジンと共にインストールされていない場合、データベース エンジンは、名前付きインスタンスは、インストール後にスケール アウト マスター サービス構成ファイルで SqlServerName を構成する必要があります。 参照してください[スケール アウト マスター](integration-services-ssis-scale-out-master.md)詳細についてはします。

## <a name="InstallWorker"></a> Scale Out Worker をインストールする
 
Scale Out Worker の機能を有効にするには、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] のセットアップで [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] とその Scale Out Worker 機能をインストールする必要があります。

**Scale Out Worker 機能をインストールするには、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インストール ウィザードまたはコマンド プロンプト**を使います。

- [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インストール ウィザードの手順
  1.  **機能の選択**] ページで、[**スケール アウト ワーカー**の下に表示される[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]です。   
  ![Worker 機能の選択](media/feature-select-worker.PNG)
  2. **[サーバーの構成]** ページで、 **[SQL Server Integration Services Scale Out Worker service]** (SQL Server Integration Services Scale Out Worker サービス) を実行するアカウントを選び、 **[スタートアップの種類]**を選びます。    
  ![サーバーの構成 2](media/server-config-2.PNG "サーバー Config 2")
  3. **[Integration Services Scale Out Worker Configuration]** (Integration Services Scale Out Worker の構成) ページで、Scale Out Master に接続するエンドポイントを指定します。 
      > [!Note]
      > ここでワーカー ノードの構成 (手順 3 & 4) は省略して、スケール アウト ワーカーを使用してスケール アウト マスターを関連付ける[スケール アウト Manager](integration-services-ssis-scale-out-manager.md)インストール後にします。

    - **1 台のコンピューター**スケール アウト マスターとスケール アウト ワーカーが、同時にインストールされている環境では、エンドポイントが自動的に生成します。 
    - **複数のコンピューター**環境では、エンドポイントの名前またはコンピューターの ip アドレスのスケール アウト マスター インストールされていると、スケール アウト マスター インストール時に指定されたポート番号で構成します。    
   ![ワーカー Config 1](media/worker-config.PNG "ワーカー構成 1")    

  4. **複数のコンピューター**環境では、スケール アウト マスターの検証に使用されるクライアント SSL 証明書を指定します。 **1 台のコンピューター**環境では、クライアント SSL 証明書を指定する必要はありません。 
  
     > [!NOTE]
     > スケール アウト マスターによって使用される SSL 証明書は、自己署名が、対応するクライアント SSL 証明書はスケール アウト ワーカーを使用してコンピューターにインストールされている必要があります。 クライアント SSL 証明書のファイルのパスを指定したかどうか、 **Integration Services スケール アウト ワーカーの構成** ページで、証明書が自動的にインストールする以外の場合は、証明書を後で手動でインストールする必要がそれ以外の場合。 
     
     **[Browse]** (参照) をクリックして、証明書ファイル (*.cer) を指定します。 既定の SSL 証明書を使用するファイルを選択、SSISScaleOutMaster.cer の下にある\<ドライブ\>: \Program Files\Microsoft SQL Server\140\DTS\Binn スケール アウト マスターがインストールされているコンピューターにします。   
   ![ワーカーの構成 2](media/worker-config-2.PNG "ワーカー Config 2")
  5. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インストール ウィザードを最後まで実行します。
- コマンド プロンプトの手順

    「[コマンド プロンプトからの SQL Server のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」の手順に従います。 次のようにして、Scale Out Worker 関連のパラメーターを設定します。
    1.  パラメーター /FEATURES に IS_Worker を追加します。
    2. スケール アウト Worker は、次のパラメーターとその値を指定する構成:/ISWORKERSVCACCOUNT、/ISWORKERSVCPASSWORD、/ISWORKERSVCSTARTUPTYPE、/ISWORKERSVCMASTER(optional)、/ISWORKERSVCCERT(optional) です。

 
## <a name="InstallCert"></a> Scale Out Worker クライアント証明書をインストールする

スケール アウト Worker のインストール時にワーカーの証明書が自動的に作成され、コンピューターにインストールします。 また、対応するクライアント証明書 SSISScaleOutWorker.cer が \<ドライブ\>:\Program Files\Microsoft SQL Server\140\DTS\Binn にインストールされます。 スケール アウト マスター、スケール アウト ワーカーを認証するためには、スケール アウト マスターでローカル コンピューターのルート ストアにこのクライアント証明書を追加する必要があります。
  
ルート ストアにクライアント証明書を追加するには、.cer ファイルをダブルクリックし、[証明書] ダイアログ ボックスで **[証明書のインストール]** をクリックします。 **証明書のインポート ウィザード** が表示されます。  

## <a name="Firewall"></a> ファイアウォールのポートを開く

スケール アウト マスター インストールとポートの SQL Server (1433、既定では)、中に指定されたポートを開いてでは、Windows ファイアウォールを使用してスケール アウト マスター コンピューターにします。
    
## <a name="Start"></a> SQL Server Scale Out Master および Worker サービスを開始する

サービスのスタートアップの種類が設定されていない場合を 自動インストール中に、サービスを開始: SQL Server Integration Services スケール アウト マスター 14.0 (SSISScaleOutMaster140) と SQL Server Integration Services スケール アウト ワーカー 14.0 (SSISScaleOutWorker140)。 

> [!Note]
> ファイアウォール ポートを開くと後も、スケール アウト ワーカー サービスを再起動する必要があります。
   
## <a name="EnableMaster"></a> Scale Out Master を有効にする

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio_md](../../includes/ssmanstudio-md.md)] で SSISDB カタログを作成するときに、**[カタログの作成]** ダイアログ ボックスで **[Enable this server as SSIS scale out master]** (このサービスを SSIS Scale Out Master として有効にする) をクリックします。 スケール アウト マスターを有効にする代わりに、[スケール アウト Manager](integration-services-ssis-scale-out-manager.md)カタログの作成後にします。

## <a name="EnableAuth"></a> SQL Server 認証モードを有効にする
場合[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]データベース エンジンのインストール中に認証が有効になっていません、SQL Server 認証モードを有効にする、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] SSISDB カタログをホストするインスタンス。 

SQL Server 認証を無効にすると、パッケージの実行はブロックされません。 ただし、実行ログを SSISDB に書き込むことはできません。

## <a name="EnableWorker"></a> Scale Out Worker を有効にする

スケール アウト ワーカーを有効にすることができます[スケール アウト Manager](integration-services-ssis-scale-out-manager.md)GUI を提供する、またはストアド プロシージャを介して有効になっている、次を参照してください。

Scale Out Worker を有効にするには、パラメーターとして *WorkerAgentId* を指定して **[catalog].[enable_worker_agent]** ストアド プロシージャを実行します。 

**WorkerAgentId** の値は、Scale Out Worker を Scale Out Master に登録した後で SSISDB の *[catalog].[worker_agents]* データベース ビューから取得します。 Scale Out Master および Worker サービスを開始した後、登録には数分かかります。

#### <a name="example"></a>例
この例では、スケール アウト Worker コンピューター a を有効にします。
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
Scale Out 機能のセットアップが終わりました。 スケール アウトでパッケージを実行できます。詳しくは、「[Integration Services (SSIS) Scale Out でパッケージを実行する](run-packages-in-integration-services-ssis-scale-out.md)」をご覧ください。

