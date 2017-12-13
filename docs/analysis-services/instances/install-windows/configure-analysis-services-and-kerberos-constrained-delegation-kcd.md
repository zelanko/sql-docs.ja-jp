---
title: "分析を構成するサービスと Kerberos の制約付き委任 (KCD) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/20/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0006e143-d3ba-4d10-a415-e42c45e2bb0a
caps.latest.revision: "20"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ae2cafe597e5540a58cc89e28cee87516942d021
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="configure-analysis-services-and-kerberos-constrained-delegation-kcd"></a>Analysis Services と Kerberos の制約付き委任 (KCD) の構成
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Kerberos の制約付き委任 (KCD) はクライアントの資格情報を委任するために Windows 認証で構成できる認証プロトコルは、環境内のサービスにサービスします。 KCD には、ドメイン コントローラーなどの追加のインフラストラクチャと環境の追加構成が必要です。 KCD は、SharePoint 2016 で [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] と [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] のデータが関係する一部のシナリオの要件となっています。 SharePoint 2016 では、Excel Services が SharePoint ファームの外部にある別の新しいサーバーである **Office Online Server**に移動しました。 Office Online Server は独立しているため、一般的な 2 つのホップ シナリオでクライアントの資格情報を委任する方法の必要性が高まります。  
  
||  
|-|  
|**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2016|  
  
## <a name="overview"></a>概要  
 KCD により、アカウントは、リソースにアクセスできるようにするために別のアカウントの権限を借用できます。 権限を借用する側のアカウントは、Web アプリケーションに割り当てられたサービス アカウントまたは Web サーバーのコンピューター アカウントであり、権限を借用される側のアカウントは、リソースへのアクセスを必要とするユーザー アカウントです。 KCD はサービス レベルで機能するため、権限を借用する側のアカウントによってサーバー上の選択されたサービスにアクセス権を付与できます。同じサーバー上の他のサービスや他のサーバー上のサービスはアクセスを拒否されます。  
  
 このトピックのセクションでは、KCD を必要とする [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] と [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] での一般的なシナリオを確認します。また、インストールおよび構成する必要があるものについて概要を説明しながら、サーバーの展開例を紹介します。 ドメイン コントローラーや KCD など、関連するテクノロジの詳細情報へのリンクについては、「 [詳細情報とコミュニティ コンテンツ](#bkmk_moreinfo) 」をご覧ください。  
  
## <a name="scenario-1-workbook-as-data-source-wds"></a>シナリオ 1: データ ソースとしてのブック (WDS)  
 ![1 を参照してください](../../../analysis-services/instances/install-windows/media/ssas-callout1.png "1 を参照してください")Office Online Server が Excel ブックを開くと![2 を参照してください](../../../analysis-services/instances/install-windows/media/ssas-callout2.png "2 を参照してください")別のブックへのデータ接続を検出します。 Office Online Server は要求を送信、[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]リダイレクター サービス![3 を参照してください](../../../analysis-services/instances/install-windows/media/ssas-callout3.png "3 を参照してください")を開くには 2 つ目のブックとデータ![4 参照](../../../analysis-services/instances/install-windows/media/ssas-callout4.png "4 を参照してください").  
  
 このシナリオでは、Office Online Server から SharePoint の SharePoint [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] リダイレクター サービスにユーザーの資格情報を委任する必要があります。  
  
 ![データ ソースとしてブック](../../../analysis-services/instances/install-windows/media/ssas-kcd-wtih-wds.png "データ ソースとしてブック")  
  
## <a name="scenario-2-an-analysis-services-tabular-model-links-to-an-excel-workbook"></a>シナリオ 2: Excel ブックにリンクする Analysis Services 表形式モデル  
 Analysis Services 表形式モデル![1 を参照してください](../../../analysis-services/instances/install-windows/media/ssas-callout1.png "1 を参照してください")Power Pivot モデルを含む Excel ブックにリンクします。 このシナリオでは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が表形式モデルを読み込んだときに、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はブックへのリンクを検出します。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は、モデルを処理するときに、クエリ要求を SharePoint に送信してブックを読み込みます。 このシナリオでは、Analysis Services から SharePoint にクライアントの資格情報を委任する必要は **ありません** が、クライアント アプリケーションがアウトオブライン バインドでデータ ソース情報を上書きする可能性があります。 アウトオブライン バインド要求で現在のユーザーの権限の借用が指定されている場合、ユーザーの資格情報を委任する必要があるため、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] と SharePoint 間で KCD を構成する必要があります。  
  
 ![office online server](../../../analysis-services/instances/install-windows/media/ssas-kcd-wtih-oos.png "office online server")  
  
## <a name="example-deployment-of-kcd-with-office-online-server-and-analysis-services"></a>Office Online Server と Analysis Services での KCD の展開例  
 ここでは、4 台のコンピューターを使用した展開例について説明します。 以下のセクションでは、各コンピューターの主なインストールおよび構成手順を概説します。 展開を開始する前に、オペレーティング システムの修正プログラムを適用して、コンピューターを最新の状態にしておくことをお勧めします。また、一部の構成手順でコンピューター名が必要となるため、各コンピューター名を把握しておいてください。  
  
-   ドメイン コントローラー  
  
-   SQL Server データベース エンジンと Power Pivot モードの Analysis Services。 データベース エンジンのインスタンスは、SharePoint コンテンツ データベースに使用されます。  
  
-   SharePoint Server 2016  
  
-   Office Online Server  
  
 ![domain controller](../../../analysis-services/instances/install-windows/media/ssas-kcd-domainserver-icon.png "domain controller")  
  
### <a name="domain-controller"></a>ドメイン コントローラー  
 ドメイン コントローラー (DC) 用にインストールするものは次のとおりです。  
  
-   **役割:** Active Directory ドメイン サービス。 概要については、「 [Configuring Active Directory (AD DS) in Windows Server 2012](http://sharepointgeorge.com/2012/configuring-active-directory-ad-ds-in-windows-server-2012/)」 (Windows Server 2012 での Active Directory (AD DS) の構成) をご覧ください。  
  
-   **役割:** DNS サーバー  
  
-   **機能:** .NET Framework 3.5 の機能/.NET Framework 3.5  
  
-   **機能:** リモート サーバー管理ツール/役割管理ツール  
  
-   Active Directory を構成して新しいフォレストを作成し、各コンピューターをドメインに参加させます。 他のコンピューターをプライベート ドメインに追加する前に、DC の IP アドレスに対してクライアント コンピューターの DNS を構成する必要があります。 DC コンピューターで `ipconfig /all` を実行して、次の手順で使用する IPv4 アドレスと IPv6 アドレスを取得します。  
  
-   IPv4 と IPv6 の両方のアドレスを構成することをお勧めします。 これは、Windows コントロール パネルで構成できます。  
  
    1.  **[ネットワークと共有センター]**をクリックします。  
  
    2.  イーサネット接続をクリックします。  
  
    3.  **[プロパティ]**をクリックします。  
  
    4.  **[インターネット プロトコル バージョン 6 (TCP/IPv6)]**をクリックします。  
  
    5.  **[プロパティ]**をクリックします。  
  
    6.  **[次の DNS サーバーのアドレスを使う]**をクリックします。  
  
    7.  ipconfig コマンドで取得した IP アドレスを入力します。  
  
    8.  **[詳細設定]** をクリックし、 **[DNS]** タブをクリックして DNS サフィックスが正しいことを確認します。  
  
    9. **[以下の DNS サフィックスを順に追加する]**をクリックします。  
  
    10. IPv4 でこれらの手順を繰り返します。  
  
-   **注:** Windows コントロール パネルの [システム設定] で、コンピューターをドメインに参加させることができます。 詳細については、「 [How To Join Windows Server 2012 to a Domain](http://social.technet.microsoft.com/wiki/contents/articles/20260.how-to-join-windows-server-2012-to-a-domain.aspx)」 (Windows Server 2012 をドメインに参加させる方法) を参照してください。  
  
 ![powerpivot モードでの ssas サーバー](../../../analysis-services/instances/install-windows/media/ssas-kcd-powerpivotserver-icon.png "powerpivot モードでの ssas サーバー")  
  
### <a name="2016-sql-server-database-engine-and-analysis-services-in-power-pivot-mode"></a>2016 SQL Server データベース エンジンと Power Pivot モードの Analysis Services  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コンピューターにインストールするものは次のとおりです。  
  
 ![注](../../../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "注")で、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]セットアップ ウィザードで、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Power pivot モードは、機能選択ワークフローの一部としてインストールします。  
  
1.  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] セットアップ ウィザードを実行し、機能選択ページで、データベース エンジン、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、管理ツールをクリックします。 セットアップ ウィザードの後の手順で、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] の [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]モードを指定できます。  
  
2.  インスタンスの構成では、"POWERPIVOT" という名前付きインスタンスを構成します。  
  
3.  [Analysis Services の構成] ページで、 **Power Pivot** モード用に Analysis Services サーバーを構成し、Office Online Server の **コンピューター名** を Analysis Services サーバー管理者の一覧に追加します。 詳細については、「 [Install Analysis Services in Power Pivot Mode](../../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)」を参照してください。  
  
4.  既定では、"コンピューター" オブジェクトは検索には含まれません。 をクリックして![コンピューター アカウントを追加するオブジェクト をクリックして](../../../analysis-services/instances/install-windows/media/ss-objects-button.png "コンピューター アカウントを追加するオブジェクト をクリックして")コンピューター オブジェクトを追加します。  
  
     ![ssas の管理者としてコンピューター アカウントを追加](../../../analysis-services/instances/media/ssas-in-ssms-computerobjects.png "ssas 管理者としてコンピューター アカウントを追加")  
  
5.  Analysis Services インスタンスのサービス プリンシパル名 (SPN) を作成します。  
  
     便利な SPN コマンドを次に示します。  
  
    -   目的のサービスを実行している特定のアカウント名の SPN を表示する: `SetSPN -l <account-name>`  
  
    -   目的のサービスを実行しているアカウント名の SPN を設定する: `SetSPN -a <SPN> <account-name>`  
  
    -   目的のサービスを実行している特定のアカウント名から SPN を削除する: `SetSPN -D <SPN> <account-name>`  
  
    -   重複する SPN を検索する: `SetSPN -X`  
  
     PowerPivot インスタンスの SPN は、次の形式になります。  
  
    ```  
    MSSQLSvc.3/\<Fully Qualified Domain Name (FQDN)>:POWERPIVOT  
    MSSQLSvc.3/<NetBIOS Name>:POWERPIVOT  
    ```  
  
     FQDN と NetBIOS 名は、インスタンスが存在するコンピューターの名前です。 これらの SPN は、サービス アカウントに使用されているドメイン アカウントに配置されます。  ネットワーク サービス、ローカル システム、またはサービス ID を使用している場合は、ドメイン コンピューター アカウントに SPN を配置できます。  ドメイン ユーザー アカウントを使用している場合は、そのアカウントに SPN を配置します。  
  
6.  Analysis Services コンピューターで SQL Browser サービスの SPN を作成します。  
  
     [詳細情報](https://support.microsoft.com/en-us/kb/950599)  
  
7.  SQL Server や Excel ファイルなど、更新元となる外部ソースに対して、Analysis Services サービス アカウントで**制約付き委任設定を構成** します。 Analysis Services サービス アカウントで、次のオプションが設定されていることを確認します。  
  
     **注:** Active Directory ユーザーとコンピューターでアカウントの委任タブが表示されていない場合、これはそのアカウントに SPN がないためです。  `my/spn`のような仮の SPN を追加することで、委任タブを表示できます。  
  
     **[指定されたサービスへの委任でのみこのユーザーを信頼する]** と **[任意の認証プロトコルを使う]**。  
  
     これは制約付き委任と呼ばれます。Windows トークンは、プロトコル遷移で制約付き委任を必要とする Claims to Windows Token Service (C2WTS) によって生成されるため、これが必要となります。  
  
     ![Analysis Services - 制約付き委任](../../../analysis-services/instances/install-windows/media/analysis-services-constrained-delegation.png "Analysis Services - 制約付き委任")  
  
     委任先のサービスも追加する必要があります。 これは環境によって異なります。  
  
### <a name="office-online-server"></a>Office Online Server  
  
1.  Office Online Server をインストールします。  
  
2.  **サーバーに接続するように** Office Online Server を構成 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] します。 Office Online Server コンピューター アカウントは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーの管理者である必要があります。 これは、このトピックの前のセクションで [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーをインストールしたときに完了しています。  
  
    1.  Office Online Server で、PowerShell ウィンドウを管理者特権で開き、次のコマンドを実行します。  
  
    2.  `New-OfficeWebAppsExcelBIServer –ServerId <AS instance name>`  
  
    3.  サンプル: `New-OfficeWebAppsExcelBIServer –ServerId "MTGQLSERVER-13\POWERPIVOT"`  
  
3.  Office Online Server コンピューター アカウントが SharePoint サービス アカウントに対してユーザーの権限を借用することを許可するように**Active Directory を構成** します。 そのために、Office Online Server で、SharePoint Web サービスのアプリケーション プールを実行するプリンシパルの委任プロパティを設定します。このセクションの PowerShell コマンドには、Active Directory (AD) PowerShell オブジェクトが必要です。  
  
    1.  Office Online Server の Active Directory ID を取得します。  
  
        ```  
        $computer1 = Get-ADComputer -Identity [ComputerName]  
        ```  
  
         このプリンシパル名を見つけるには、タスク マネージャーの [詳細] で w3wp.exe のユーザー名を調べます (例: svcSharePoint)。  
  
        ```  
        Set-ADUser svcSharePoint -PrincipalsAllowedToDelegateToAccount $computer1  
  
        ```  
  
    2.  プロパティが正しく設定されていることを確認します。  
  
    3.  ```  
        Get-ADUser svcSharePoint –Properties PrincipalsAllowedToDelegateToAccount  
        ```  
  
4.  Office Online Server アカウントで Analysis Services Power Pivot インスタンスに対する**制約付き委任設定を構成** します。 これは、Office Online Server が実行されているコンピューター アカウントです。 Office Online Service アカウントで、次のオプションが設定されていることを確認します。  
  
     **注:** Active Directory ユーザーとコンピューターでアカウントの委任タブが表示されていない場合、これはそのアカウントに SPN がないためです。  `my/spn`のような仮の SPN を追加することで、委任タブを表示できます。  
  
     **[指定されたサービスへの委任でのみこのユーザーを信頼する]** と **[任意の認証プロトコルを使う]**。  
  
     これは制約付き委任と呼ばれます。Windows トークンは、プロトコル遷移で制約付き委任を必要とする Claims to Windows Token Service (C2WTS) によって生成されるため、これが必要となります。  これで、以前に作成した SPN である MSOLAPSvc.3 と MSOLAPDisco.3 への委任が可能になります。  
  
5.  Claims to Windows Token Service (C2WTS) をセットアップします。 **これはシナリオ 1 で必要**です。 詳細については、「 [Claims to Windows Token Service (c2WTS) の概要](https://msdn.microsoft.com/library/ee517278.aspx)」をご覧ください。  
  
6.  C2WTS サービス アカウントで**制約付き委任設定を構成** します。  この設定は、手順 4. で行った設定と一致する必要があります。  
  
 ![sharepoint server](../../../analysis-services/instances/install-windows/media/ssas-kcd-sharepointserver-icon.png "sharepoint サーバー")  
  
### <a name="sharepoint-server-2016"></a>SharePoint Server 2016  
 SharePoint Server のインストールの概要を次に示します。  
  
1.  SharePoint 前提条件インストーラーを実行します。  
  
2.  SharePoint インストールを実行し、 **[単一サーバー ファーム]** セットアップ ロールを選択します。  
  
3.  PowerPivot for SharePoint アドイン (spPowerPivot16.msi) を実行します。 詳細については、次を参照してください[インストールまたは for SharePoint アドイン (SharePoint 2016) の Power Pivot のアンインストール。](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2016.md)  
  
4.  PowerPivot 構成ウィザードを実行します。 「 [Power Pivot の構成ツール](../../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)」をご覧ください。  
  
5.  SharePoint を Office Online Server に接続します。    ??Configure_xlwac_on_SPO.ps1 ??  
  
6.  Kerberos 用の SharePoint 認証プロバイダーを構成します。 **これはシナリオ 1 で必要**です。 詳細については、「 [SharePoint 2013 で Kerberos 認証を計画する](https://technet.microsoft.com/library/ee806870.aspx)」を参照してください。  
  
##  <a name="bkmk_moreinfo"></a> 詳細情報とコミュニティ コンテンツ  
 [Kerberos for the Busy Admin (多忙な管理者のための Kerberos)](http://blogs.technet.com/b/askds/archive/2008/03/06/kerberos-for-the-busy-admin.aspx)  
  
 [Understanding Kerberos Double Hop (Kerberos ダブル ホップについて)](http://blogs.technet.com/b/askds/archive/2008/06/13/understanding-kerberos-double-hop.aspx)  
  
 [ALL things .Net and SharePoint](http://sbrickey.com/Tech/Blog/Post/Kerberos_Primer)  
  
 [Resource Based Kerberos Constrained Delegation (リソース ベースの Kerberos の制約付き委任)](http://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)  
  
 [KERBEROS PRIMER (Kerberos の概要) - ビデオ](http://blog.martinlund.it/kerberos-primer/)  
  
 [SQL Server® の Microsoft® Kerberos Configuration Manager](http://www.microsoft.com/en-us/download/details.aspx?id=39046)  
  
  
