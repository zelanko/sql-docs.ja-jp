---
title: "リモートの Integration Services サーバーに接続する (SSIS サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サービス [Integration Services], リモート インスタンス"
  - "Integration Services サービス, 接続"
  - "Integration Services サービス, リモート インスタンス"
  - "サービス [Integration Services], 接続"
ms.assetid: 9487aff1-44d8-42c1-8176-bb9891d4632d
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# リモートの Integration Services サーバーに接続する (SSIS サービス)
    
> [!IMPORTANT] このトピックでは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスについて説明します。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、以前のリリースの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] との互換性を維持するために、このサービスをサポートしています。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または他の管理アプリケーションからリモート サーバー上の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のインスタンスに接続するには、アプリケーションのユーザーがそのサーバーに対して特定の権限を持っている必要があります。  
  
> [!IMPORTANT] レガシ Integration Services サービスに直接接続するには、Integration Services サービスが実行されている SQL Server のバージョンと合わせたバージョンの SQL Server Management Studio (SSMS) を使用する必要があります。 たとえば、SQL Server 2016 のインスタンスで実行されているレガシ Integration Services サービスに接続するには、SQL Server 2016 用にリリースされたバージョンの SSMS を使用する必要があります。 [SQL Server Management Studio (SSMS) をダウンロードしてください](https://msdn.microsoft.com/library/mt238290.aspx)。
>
>  リモート サーバーに格納されるパッケージを管理するために、そのリモート サーバー上の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスのインスタンスに接続する必要はありません。 代わりに、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスの構成ファイルを編集し、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でリモート サーバーに格納されているパッケージが表示されるようにします。 詳細については、「[Integration Services サービスの構成 &#40;SSIS サービス&#41;](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md)」を参照してください。  
  
## リモート サーバー上の Integration Services への接続  
  
#### リモート サーバー上の Integration Services に接続するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開きます。  
  
2.  **[ファイル]** メニューの **[オブジェクト エクスプローラーを接続]** をクリックして、**[サーバーへの接続]** ダイアログ ボックスを表示します。  
  
3.  **[サーバーの種類]** ボックスの一覧で **[Integration Services]** を選択します。  
  
4.  **[サーバー名]** ボックスに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーの名前を入力します。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは、そのインスタンスに固有のものではありません。 このサービスに接続するには、Integration Services サービスが実行されているコンピューターの名前を使用します。  
  
5.  **[接続]**をクリックします。  
  
> [!NOTE]  
>  **[サーバーの参照]** ダイアログ ボックスには、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のリモート インスタンスは表示されません。 また、**[サーバーへの接続]** ダイアログ ボックスで **[オプション]** ボタンをクリックしたときに表示される **[接続プロパティ]** タブのオプションは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] への接続時には適用されません。  
  
## "アクセスが拒否されました" エラーの回避  
 十分な権限を持っていないユーザーがリモート サーバー上の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] インスタンスに接続しようとすると、サーバーから "アクセスは拒否されました" というエラー メッセージが返されます。 必要な権限がユーザーに与えられていることを確認すれば、このエラー メッセージを回避できます。  
  
#### Windows Server 2003 または Windows XP でリモート ユーザーの権限を構成するには  
  
1.  ユーザーがローカルの Administrators グループのメンバーでない場合、そのユーザーを Distributed COM Users グループに追加します。 この操作は、**[管理ツール]** メニューからアクセスできるコンピューターの管理 MMC スナップインで実行できます。  
  
2.  コントロール パネルを開き、**[管理ツール]**、**[コンポーネント サービス]** の順にダブルクリックして、コンポーネント サービス MMC スナップインを起動します。  
  
3.  コンソールの左ペインで **[コンポーネント サービス]** ノードを展開します。 **[コンピューター]** ノード、**[マイ コンピューター]** の順に展開し、**[DCOM の構成]** ノードをクリックします。  
  
4.  **[DCOM の構成]** ノードを選択し、構成できるアプリケーションの一覧から [SQL Server Integration Services 11.0] を選択します。  
  
5.  [SQL Server Integration Services 11.0] を右クリックし、**[プロパティ]** を選択します。  
  
6.  **[SQL Server Integration Services 11.0 のプロパティ]** ダイアログ ボックスで、**[セキュリティ]** タブをクリックします。  
  
7.  **[起動とアクティブ化のアクセス許可]** で **[カスタマイズ]** を選択し、**[編集]** をクリックして **[起動許可]** ダイアログ ボックスを開きます。  
  
8.  **[起動許可]** ダイアログ ボックスで、ユーザーを追加または削除し、適切なアクセス許可を適切なユーザーとグループに割り当てます。 使用可能なアクセス許可は、[ローカルからの起動]、[リモートからの起動]、[ローカルからのアクティブ化]、[リモートからのアクティブ化] です。 起動権限ではサービスを開始および停止するアクセス許可を許可または拒否し、アクティブ化権限ではサービスに接続するアクセス許可を許可または拒否します。  
  
9. [OK] をクリックして、ダイアログ ボックスを閉じます。  
  
10. **[アクセス許可]** で手順 7. ～ 8. を繰り返し、適切なユーザーとグループに適切なアクセス許可を割り当てます。  
  
11. MMC スナップインを閉じます。  
  
12. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスを再開します。  
  
#### 最新の Service Pack が適用されている Windows 2000 でリモート ユーザーの権限を構成するには  
  
1.  コマンド プロンプトで **dcomcnfg.exe** を実行します。  
  
2.  **[分散 COM の構成のプロパティ]** ダイアログ ボックスの **[アプリケーション]** ページで、[SQL Server Integration Services 11.0] をクリックして **[プロパティ]** をクリックします。  
  
3.  **[セキュリティ]** ページをクリックします。  
  
4.  2 つのダイアログ ボックスを使用して、**[アクセスの許可]** と **[起動の許可]** を構成します。 リモートとローカルのアクセスは区別できません。アクセスの許可にはローカルとリモートのアクセス権が含まれており、起動の権限にはローカルとリモートの起動権限が含まれています。  
  
5.  ダイアログ ボックスを閉じ、**dcomcnfg.exe** を閉じます。  
  
6.  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスを再開します。  
  
## ローカル アカウントを使用した接続  
 クライアント コンピューターのローカル Windows アカウントで作業している場合、リモート コンピューターの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスに接続できるのは、同じ名前、同じパスワード、および十分な権限が設定されたローカル アカウントがリモート コンピューター上に存在する場合だけです。  
  
## 既定では SSIS サービスは委任をサポートしない  
既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは資格情報を委任できません。資格情報の委任はダブル ホップとも呼ばれます。 たとえば、ユーザーがクライアント コンピューターで作業しており、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] が別のコンピューターで実行されているとします。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はさらに別のコンピューターで実行されています。 まず、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] がクライアント コンピューターから [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスが実行されている 2 番目のコンピューターに資格情報を渡します。 ただし、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスは 2 番目のコンピューターから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行されている 3 番目のコンピューターに資格情報を委任できません。

資格情報の委任は、**[任意のサービスへの委任でこのユーザーを信頼する (Kerberos のみ)]** の権限を SQL Server のサービス アカウントで有効にできます。これにより、子プロセスとして Integration Services サービス (ISServerExec.exe) が起動します。 この権限を付与する前に、組織のセキュリティ要件を満たしているかどうかを検討してください。

詳細については、「[Getting Cross Domain Kerberos and Delegation working with SSIS Package](https://blogs.msdn.microsoft.com/psssql/2014/06/26/getting-cross-domain-kerberos-and-delegation-working-with-ssis-package/)」(SSIS パッケージで機能するクロス ドメイン Kerberos の取得) を参照してください。
  
## 参照  
 [SSIS サービスにアクセスするように Windows ファイアウォールを構成する](../../integration-services/service/configure-a-windows-firewall-for-access-to-the-ssis-service.md)  
  
  