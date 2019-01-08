---
title: 初期構成 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: dc6ab85f562aa4a2149e6471b13422e97d7fc7c5
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53353424"
---
# <a name="initial-configuration-powerpivot-for-sharepoint"></a>初期構成 (PowerPivot for SharePoint)
  このトピックの手順を使用して、PowerPivot for SharePoint の最初のインストールを構成します。 最初のインストールを構成する最も簡単な方法は、PowerPivot 構成ツールを使用することです。 これによって、以下に説明したすべての構成手順が自動で行われます。  
  
 また、サーバーの構成方法を制御する場合には、サーバーの全体管理とこのトピックの情報を使用して各手順を個別に実行できます。  
  
 
  
## <a name="prerequisites"></a>前提条件  
 SharePoint サーバーは、SharePoint セットアップでサーバー ファーム インストール オプションを使用してインストールされたものである必要があります。 組み込みのデータベースを使用するスタンドアロン SharePoint サーバーはサポートされません。 詳細については、次を参照してください。 [、SharePoint 2010 ファームで SQL Server BI 機能を使用するためのガイダンス](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] データベース サーバーを使用する PowerPivot for SharePoint または SharePoint ファームを構成する前に、SharePoint 2010 SP1 をインストールする必要があります。 サービス パックをインストールしていない場合は、サーバーの構成を始める前にここでインストールしてください。  
  
 PowerPivot for SharePoint をインストールする必要があります。 少なくともファーム ソリューションを配置する必要があります。 PowerPivot 構成ツールまたは PowerShell スクリプトを使用してファーム ソリューションを配置します。 この手順はこのトピックで説明します。  
  
 コンピューターがドメインに参加する必要があります。 サービスに指定するアカウントは、ドメイン ユーザー アカウントである必要があります。 PowerPivot サービス アプリケーションには、少なくとも 1 つのドメイン アカウントが必要になります。 Excel Services などの他のサービスを構成している場合は、提供する各サービスに個別のアカウントを指定する必要があります。  
  
 PowerPivot for SharePoint をファームに追加するには、ファームの管理者である必要があります。 サーバーおよびアプリケーションをファームに追加するためのパスフレーズを把握しておく必要があります。  
  
##  <a name="deploywsp"></a> 手順 1:PowerPivot ソリューションの配置  
 ファーム ソリューションおよび Web アプリケーション ソリューションという 2 つのソリューションをインストールして配置する必要があります。  
  
 **インストールし、ファーム ソリューションの配置**  
  
 以前のリリースでは、SQL Server セットアップによってファーム ソリューションがインストールされ、配置されました。 このリリースでは、PowerPivot 構成ツールまたは PowerShell スクリプトを使用してファーム ソリューションを配置する必要があります。 サーバーの全体管理をファーム ソリューションの配置に使用することはできません。 これは、サーバーの全体管理で実行できない PowerPivot for SharePoint 構成の唯一の手順です。 ファーム ソリューションの配置後は、サーバーの全体管理とこのトピックの手順を使用して PowerPivot for SharePoint のインストールを構成できます。  
  
 この手順では、PowerShell を実行してファーム ソリューションをインストールおよび配置します。 詳細については、次を参照してください。 [Windows PowerShell を使用して、PowerPivot 構成](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)します。  
  
1.  **[管理者として実行]** オプションを使用して SharePoint 2010 管理シェルを開きます。  
  
2.  最初のコマンドレットを実行します。  
  
    ```  
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     コマンドレットにより、ソリューション名、ソリューション ID、および Deployed=False が返されます。 次の手順では、ソリューションを配置します。  
  
3.  2 番目のコマンドレットを実行してソリューションを配置します。  
  
    ```  
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
 **Web アプリケーション ソリューションを配置します。**  
  
1.  スタート ボタンをクリックし、選択**すべてのプログラム**、 **Microsoft SharePoint Products 2010**、し、 **SharePoint 2010 サーバーの全体管理**。  
  
2.  SharePoint 2010 サーバーの全体管理で、[システム設定] の **[ファーム ソリューションの管理]** をクリックします。  
  
     owerpivotfarm.wsp および powerpivotwebapp.wsp の 2 つの個別のソリューション パッケージが表示されます。 最初のソリューション (powerpivotfarm.wsp) は既に配置されています。 これを配置した後は、再度配置する必要はありません。 2 つ目のソリューション (powerpivotwebapp.wsp) は、サーバーの全体管理に配置されるソリューションですが、PowerPivot データ アクセスをサポートする各 SharePoint Web アプリケーションに手動で配置する必要があります。  
  
3.  **[powerpivotwebapp.wsp]** をクリックします。  
  
4.  クリックして**ソリューションをデプロイします。**  
  
5.  **をデプロイしますか?**、PowerPivot 機能のサポートを追加する SharePoint web アプリケーションを選択します。  
  
6.  **[OK]** をクリックします。  
  
7.  PowerPivot データ アクセスをサポートする他の SharePoint Web アプリケーションに対して、この手順を繰り返します。  
  
##  <a name="Geneva"></a> 手順 2:サーバーでのサービスの開始  
 PowerPivot for SharePoint の配置では、Excel Calculation Services、Secure Store Service、および Claims to Windows Token Service の各サービスがファームに含まれている必要があります。  
  
 Excel Services および PowerPivot for SharePoint には、Windows トークン サービスに対するクレームが必要です。 これは、現在の SharePoint ユーザーの Windows ID を使用して外部データ ソースとの接続を確立するために使用されるサービスです。 このサービスは、Excel Services または PowerPivot for SharePoint が有効になっている各 SharePoint サーバーで実行する必要があります。 このサービスが開始されていない場合は、Excel Services から PowerPivot System サービスに認証済みの要求を転送できるようにするために、ここで開始する必要があります。  
  
1.  サーバーの全体管理で、[システム設定] の **[サーバーのサービスの管理]** をクリックします。  
  
2.  Windows トークン サービスに対するクレームを開始します。  
  
3.  Excel Calculation Services を開始します。  
  
4.  Secure Store Service を開始します。  
  
5.  SQL Server Analysis Services と SQL Server PowerPivot System サービスの両方が開始されていることを確認します。  
  
##  <a name="createapp"></a> 手順 3:PowerPivot サービス アプリケーションを作成します。  
 次に、PowerPivot サービス アプリケーションを作成します。  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  **[サービス アプリケーション]** リボンで、 **[新規作成]** をクリックします。  
  
3.  選択**SQL Server PowerPivot サービス アプリケーション**します。 この項目が一覧に表示されない場合は、PowerPivot for SharePoint がインストールされていないか、ソリューションが配置されていません。  
  
4.  **新しい PowerPivot サービス アプリケーションの作成**ページで、アプリケーションの名前を入力します。 既定値は PowerPivotServiceApplication\<数 >。 複数の PowerPivot サービス アプリケーションを作成する場合は、それぞれの用途を明確に示す名前を付けると他の管理者にわかりやすくなります。  
  
5.  [アプリケーション プール] で、新しいアプリケーション プールを作成して、そのアプリケーション プールのセキュリティ アカウントを選択します。 ドメイン ユーザー アカウントが必要となります。  
  
6.  **データベース サーバー**、サービス アプリケーション データベースを作成するデータベース サーバーを選択します。 既定値は、ファーム構成データベースをホストする SQL Server データベース エンジン インスタンスです。  
  
7.  **データベース名**、既定値は PowerPivotServiceApplication1_\<guid >。 既定のデータベース名は、既定のサービス アプリケーション名に対応しています。 独自のサービス アプリケーション名を入力した場合は、サービス アプリケーションとデータベースを一緒に管理できるように、データベース名に対しても同様の命名規則を使用してください。  
  
8.  **[データベース認証]** の既定値は、"Windows 認証" です。 **[SQL 認証]** を選択する場合は、SharePoint 管理者ガイドを参照して、SharePoint 配置でその認証の種類を使用するためのベスト プラクティスを確認してください。  
  
9. チェック ボックスをオン**プロキシを既定のプロキシ グループにこの PowerPivot サービス アプリケーションを追加します。** のチェック ボックスをオンにします。これにより、このサービス アプリケーション接続が既定のサービス接続のグループに追加されます。 既定の接続グループに少なくとも 1 つの PowerPivot サービス アプリケーションを追加する必要があります。  
  
     既定の接続グループの一覧に既に PowerPivot サービス アプリケーションが表示されている場合は、そのグループにサービス アプリケーションをそれ以上追加しないでください。 既定の接続グループに同じ型のサービス アプリケーションを 2 つ追加する構成はサポートされていません。 接続グループの追加のサービス アプリケーションを使用する方法の詳細については、次を参照してください。[サーバーの全体管理で SharePoint Web アプリケーションへの PowerPivot サービス アプリケーションの接続](../../analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md)します。  
  
10. **[OK]** をクリックします。 作成したサービスが、他のマネージド サービスと共にファームのサービス アプリケーションの一覧に表示されます。  
  
##  <a name="ExcelServ"></a> 手順 4:Excel Services を有効にします。  
 PowerPivot for SharePoint でファーム内の PowerPivot データ アクセスをサポートするには、Excel Services が必要です。 Excel Services が既に有効になっているかどうかを確認するには、サーバーの全体管理のサービス アプリケーションの一覧に Excel Services アプリケーションが表示されているかどうかを確認します。 Excel Services が一覧に表示されていない場合は、次の手順に従ってここで有効にしてください。  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  サービス アプリケーション リボンの作成、**新規**します。  
  
3.  選択**Excel Services アプリケーション**します。  
  
4.  [新しい Excel Services アプリケーションの作成] で、名前を指定します ("Excel Services アプリケーション" など)。  
  
5.  [アプリケーション プール] で、[新しいアプリケーション プールの作成] をクリックして、わかりやすい名前を指定します ("Excel Services アプリケーション プール" など)。  
  
6.  [構成可能] で、このアプリケーション プール ID の Windows ドメイン ユーザー アカウントを選択します。  
  
7.  チェック ボックスをオンのままにして、このサービス アプリケーション プロキシを既定のサービス接続リストに追加します。  
  
8.  **[OK]** をクリックします。  
  
9. 作成した Excel Services アプリケーションをクリックします。  
  
10. クリックして**信頼できるファイルの場所**このページで、信頼できる場所を選択します。 (通常、として登録されます**http://** アドレス 列です)。Excel Services と PowerPivot サービスの両方がブックにアクセスできるようにするには、SharePoint を Excel Services の信頼できる場所として含める必要があります。 PowerPivot System サービスは、SharePoint ファーム外に格納されたブックにはアクセスできません。  
  
11. ブックのプロパティ 領域で、次のように設定します。**ブックの最大サイズ**を 50。  
  
12. 外部データは、次のように設定します。**外部データの許可**に**データ接続ライブラリを信頼されていると、埋め込み**します。 この設定は、ブックでの PowerPivot データ アクセスに必要です。  
  
13. クリア、**データ更新に関する警告を表示**PowerPivot ギャラリー内の個々 のワークシートのプレビュー イメージを許可するチェック ボックスをオンします。 警告とブックの設定で、ファイルを開くときに更新する動作が指定されていると、ブックのページではなく警告の単一のプレビュー イメージが表示されることがあります。  
  
14. **[OK]** をクリックします。  
  
##  <a name="SSS"></a> 手順 5:Secure Store Service の有効化とデータ更新の構成  
 PowerPivot for SharePoint で資格情報とデータ更新用の自動実行アカウントを格納するには、Secure Store Service が必要です。 Secure Store Service が既に有効になっているかどうかを確認するには、サービス アプリケーションの一覧に表示されているかどうかを確認します。  
  
> [!IMPORTANT]  
>  Secure Store Service が有効になっている場合でも、マスター キーが生成されていることを確認するようにしてください。 手順については、第 2 部を参照してください。マスター キーの生成」を参照してください。  
  
 Secure Store Service が一覧に表示されていない場合は、次の手順に従ってここで有効にしてください。 Secure Store を有効にすると、ブックの作成者やドキュメントの所有者が、パブリッシュしたブックのデータ更新をスケジュールする際に、より多くのデータ ソース接続オプションを必要に応じて使用できるようになります。  
  
##### <a name="part-1-enable-secure-store-service"></a>作業 1:Secure Store Service の有効化  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  サービス アプリケーション リボンの作成、**新規**します。  
  
3.  選択**Secure Store Service**します。  
  
4.  **Secure Store アプリケーション作成**ページで、アプリケーションの名前を入力します。  
  
5.  **データベース**、このサービス アプリケーション データベースをホストする SQL Server インスタンスを指定します。 既定値は、ファーム構成データベースをホストする SQL Server データベース エンジン インスタンスです。  
  
6.  **データベース名**、サービス アプリケーション データベースの名前を入力します。 既定値は、secure_store_service_db _\<guid >。 既定の名前は、既定のサービス アプリケーション名に対応しています。 独自のサービス アプリケーション名を入力した場合は、サービス アプリケーションとデータベースを一緒に管理できるように、データベース名に対しても同様の命名規則を使用してください。  
  
7.  **[データベース認証]** の既定値は、"Windows 認証" です。 "SQL 認証" を選択する場合は、SharePoint 管理者ガイドを参照して、ファームでその認証の種類を使用する方法を確認してください。  
  
8.  アプリケーション プールでは、次のように選択します。**新しいアプリケーション プールを作成します。** 他のサーバー管理者がアプリケーション プールの使用方法を理解できるように、わかりやすい名前を指定します。  
  
9. アプリケーション プールのセキュリティ アカウントを選択します。 ドメイン ユーザー アカウントを使用するマネージド アカウントを指定します。  
  
10. 残りの既定値をそのまま使用し、 **ok をクリックします。** 作成したサービス アプリケーションが、他のマネージド サービスと共にファームのサービス アプリケーションの一覧に表示されます。  
  
##### <a name="part-2-generate-the-master-key"></a>パート 2:マスター_キーを生成します。  
  
1.  一覧で、Secure Store Service アプリケーションをクリックします。  
  
2.  サービス アプリケーション リボン**管理**します。  
  
3.  キーの管理 でクリックして**新しいキーの生成**します。  
  
4.  パス フレーズを入力し、そのパス フレーズを確認します。 パス フレーズは、Secure Store 共有サービス アプリケーションを追加するために使用されます。  
  
5.  **[OK]** をクリックします。  
  
##### <a name="part-3-configure-the-unattended-powerpivot-data-refresh-account"></a>パート 3:PowerPivot 自動データ更新アカウントの構成  
 データ更新時の外部データ アクセスのために、PowerPivot データ アクセスに対する自動データ更新アカウントの作成が必要になることがよくあります。 たとえば、Kerberos が有効になっていない場合、外部データ ソースに接続するには、PowerPivot サービスで使用できる自動アカウントを作成する必要があります。  
  
 データ更新を参照してくださいアカウントまたはその他で使用されている保存された資格情報を更新する自動 PowerPivot データを作成する方法について[PowerPivot 自動データ更新アカウントを構成する&#40;PowerPivot for SharePoint&#41;](../../analysis-services/configure-unattended-data-refresh-account-powerpivot-sharepoint.md)と[PowerPivot データ更新用の保存された資格情報の構成&#40;PowerPivot for SharePoint&#41;](../../../2014/analysis-services/configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)します。  
  
##  <a name="Usage"></a> 手順 6:使用状況データ収集の有効化  
 PowerPivot for SharePoint は、SharePoint の使用状況データ収集インフラストラクチャを使用して、PowerPivot の使用状況に関する情報をファーム全体で収集します。 使用状況データは常に SharePoint のインストールに含まれますが、使用する前に有効にする必要がある場合があります。 手順については、次を参照してください。[の使用状況データ収集を構成する&#40;PowerPivot for SharePoint](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md)します。  
  
##  <a name="Upload"></a> 手順 7:SharePoint Web アプリケーションと Excel Services の最大アップロード サイズの増加  
 PowerPivot ブックはサイズが大きくなる可能性があるため、最大ファイル サイズを増やしたい場合があります。 構成する 2 つのファイル サイズの設定として、Web アプリケーションには [アップロードの最大サイズ]、Excel Services には [ブックの最大サイズ] があります。 最大ファイル サイズは、両方のアプリケーションで同じ値に設定してください。 手順については、次を参照してください。[構成ファイルの最大アップロード サイズ&#40;PowerPivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint.md)します。  
  
##  <a name="activatePP"></a> 手順 8:サイト コレクションを対象とした PowerPivot 機能の統合のアクティブ化  
 サイト コレクション レベルで機能をアクティブ化すると、サイトでアプリケーション ページやテンプレートを使用できるようになります。これには、定期データを更新するための構成ページや、PowerPivot ギャラリーとデータ フィード ライブラリのアプリケーション ページなどが含まれます。  
  
1.  SharePoint サイトで、 **[サイトの操作]** をクリックします。  
  
     既定では、SharePoint Web アプリケーションへのアクセスにはポート 80 が使用されます。 つまり http:// を入力して、SharePoint サイトを多くの場合、アクセスできる\<コンピューター名 > をルート サイト コレクションを開きます。  
  
2.  **[サイトの設定]** をクリックします。  
  
3.  [サイト コレクションの管理] で **[サイト コレクションの機能]** をクリックします。  
  
4.  ページが表示されるまで下へスクロール**PowerPivot 統合サイト コレクション機能**します。  
  
5.  **[アクティブ化]** をクリックします。  
  
6.  他のサイト コレクションについても、各サイトを開き、 **[サイトの操作]** をクリックして手順を繰り返します。  
  
 詳細については、次を参照してください。 [PowerPivot 機能の統合サーバーの全体管理のサイト コレクション用にアクティブ化](../../analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca.md)します。  
  
##  <a name="bkmk_redist"></a> 手順 9:SQL Server 2012 PowerPivot for SharePoint インスタンスへの SQL Server 2008 R2 バージョンの OLE DB プロバイダーのインストール  
 同じサーバーで古いバージョンと新しいバージョンの PowerPivot ブックを平行して実行するには、SQL Server 2008 R2 に付属の Analysis Services OLE DB プロバイダーを [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot for SharePoint サーバーにインストールする必要があります。  
  
 このプロバイダーをインストールすると、データ接続文字列の MSOLAP.4 を参照するブックが [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot サーバーで正常に機能するようになります。 Excel 用 PowerPivot の以前のバージョンで作成されたブックをアップグレードする方法は、SQL Server 2008 R2 OLE DB プロバイダーをインストールします。  
  
 プロバイダーをダウンロードする[SQL Server 2008 R2 Feature Pack ページ](https://go.microsoft.com/fwlink/?LinkId=159570)します。 探して**Microsoft® Analysis Services OLE DB Provider for Microsoft® SQL Server® 2008 R2**、x64 をダウンロードしのパッケージ、`SQLServer2008_ASOLEDB10.msi`インストール プログラム。  
  
 検証の手順を含め、プロバイダーのインストールの詳細については、次を参照してください。 [SharePoint サーバーに、Analysis Services OLE DB プロバイダーをインストール](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)します。  
  
##  <a name="verifyinstall"></a> 手順 10:インストールを確認します。  
 ファームの PowerPivot クエリ処理は、ユーザーまたはアプリケーションが PowerPivot データを含む Excel ブックを開いたときに発生します。 PowerPivot 機能が使用可能になっているかどうかは、SharePoint サイトのページを調べれば確認できますが、 インストールを完全に確認するには、SharePoint にパブリッシュでき、ライブラリからアクセスできる PowerPivot ブックが必要になります。 テストの際には、既に PowerPivot データが含まれているサンプル ブックをパブリッシュし、それを使用して SharePoint 統合が正しく構成されているかどうかを確認できます。  
  
 PowerPivot の SharePoint サイトとの統合を確認するには、次の操作を行います。  
  
1.  ブラウザーで、作成した Web アプリケーションを開きます。 既定値を使用した場合は、 http:// を指定できます\<コンピューター名 >、URL アドレス。  
  
2.  PowerPivot データ アクセス機能と PowerPivot データ処理機能がアプリケーションで使用可能になっていることを確認します。 そのためには、PowerPivot によって提供されるライブラリ テンプレートがあるかどうかを確認します。  
  
    1.  サイトの操作をクリックします**オプション**。  
  
    2.  ライブラリでは、表示する必要があります**データ フィード ライブラリ**と**PowerPivot ギャラリー**します。 これらのライブラリ テンプレートは PowerPivot 機能によって提供されるものであり、PowerPivot 機能が正しく統合されている場合に [ライブラリ] に表示されます。  
  
 サーバーで PowerPivot データ アクセスを確認するには、次の操作を行います。  
  
1.  PowerPivot ブックを PowerPivot ギャラリーまたは任意の SharePoint ライブラリにアップロードします。  
  
2.  ドキュメントをクリックしてライブラリから開きます。  
  
3.  スライサーをクリックするかデータをフィルター処理して PowerPivot クエリを開始します。 サーバーは PowerPivot データをバックグラウンドで読み込んで結果を返します。 次の手順で、サーバーに接続して、データの読み込みとキャッシュが行われたことを確認します。  
  
4.  [スタート] メニューの Microsoft SQL Server 2008 R2 プログラム グループから SQL Server Management Studio を起動します。 サーバーでこのツールがインストールされていない場合は、手順を省略できます最後をキャッシュ ファイルの存在を確認します。  
  
5.  [サーバーの種類] で **[Analysis Services]** を選択します。  
  
6.  サーバー名 で次のように入力します。 **\<サーバー名 > \powerpivot**ここで、 **\<サーバー名 >** 、PowerPivot for SharePoint のインストールをしたコンピューターの名前を指定します。  
  
7.  **[接続]** をクリックします。  
  
8.  オブジェクト エクスプ ローラーで次のようにクリックします。**データベース**読み込まれる PowerPivot データ ファイルの一覧を表示します。  
  
9. コンピューターのファイル システムのフォルダーで、ファイルがディスクにキャッシュされているかどうかを確認します。 キャッシュされたファイルが存在していれば、配置が機能していることの確認になります。 ファイル キャッシュを表示するには、\Program Files\Microsoft SQL Server\MSAS10_50.POWERPIVOT\OLAP\Backup フォルダーに移動します。  
  
##  <a name="nextsteps"></a> インストール後の手順  
 インストールの確認が完了したら、PowerPivot ギャラリーを作成するか個々の構成設定を調整してサービスの構成を終了します。 インストールしたサーバー コンポーネントを完全に利用するには、[!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] をダウンロードし、最初の PowerPivot ブックを作成してパブリッシュします。  
  
### <a name="install-data-providers-used-for-data-refresh"></a>データの更新に使用されるデータ プロバイダーのインストール  
 データの更新を有効にしている場合、サーバーでは、PowerPivot クライアント アプリケーションで元のデータをインポートするときに使用したのと同じデータ プロバイダーが、外部データ アクセス用に必要となります (たとえば、最初にデータが 32 ビット プロバイダーを使用してインポートされていた場合は、サーバー側のデータ更新で同じ外部データ ソースにアクセスするときに、32 ビット プロバイダーが必要です)。 詳細については、次を参照してください。 [SharePoint 2010 で PowerPivot データ更新](../../../2014/analysis-services/powerpivot-data-refresh-with-sharepoint-2010.md)します。  
  
### <a name="install-adonet-data-services"></a>ADO.NET Data Services のインストール  
 SharePoint リストをデータ フィードとしてエクスポートする場合は、ADO.NET Data Services 3.5 SP1 をインストールする必要があります。 手順については、次を参照してください。[データをサポートする ADO.NET Data Services のインストールは、SharePoint リストのエクスポートをフィード](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md)します。  
  
### <a name="create-a-powerpivot-gallery"></a>PowerPivot ギャラリーを作成します。  
 PowerPivot ギャラリーは、SharePoint サイトの PowerPivot ブックを表示するためのプレビュー オプションや表示オプションを備えたライブラリです。 プレビュー機能があるため、PowerPivot ブックをパブリッシュしたり表示したりする際には PowerPivot ギャラリーを使用することをお勧めします。 同じ SharePoint サーバーに Reporting Services も配置されている場合は、 PowerPivot ギャラリーからレポート ビルダーを起動して、パブリッシュされた PowerPivot ブックを新しいレポートのベースとして使用することもできます。 作成して、ライブラリの使用の詳細については、次を参照してください。 [PowerPivot ギャラリーのカスタマイズの作成と](../../analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery.md)と[PowerPivot ギャラリーを使用して](../../analysis-services/power-pivot-sharepoint/use-power-pivot-gallery.md)します。  
  
### <a name="create-additional-trusted-sites-in-excel-services"></a>Excel Services に追加の信頼できるサイトの作成  
 Excel Services に信頼できるサイトを追加して、Excel ブックおよび PowerPivot のデータを提供するサイトの権限および構成設定を変更できます。 詳細については、「 [サーバーの全体管理での PowerPivot サイト用の信頼できる場所の作成](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)」を参照してください。  
  
### <a name="tune-configuration-settings"></a>構成設定の調整  
 PowerPivot サービス アプリケーションは、既定のプロパティと値を使用して作成されますが、 個々のサービス アプリケーションの構成設定を変更して、要求の割り当て方法を変更したり、サーバー タイムアウトを設定したり、クエリ応答レポート イベントのしきい値を変更したり、使用状況データを保持する期間を指定したりすることもできます。 サーバーの全体管理の構成や SharePoint Web アプリケーションで PowerPivot 機能の使用に関する詳細については、次を参照してください。[サーバーの全体管理で PowerPivot サーバーの管理と構成](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)します。  
  
### <a name="install-powerpivot-for-excel-and-build-a-powerpivot-workbook"></a>PowerPivot for Excel のインストールと PowerPivot ブックの作成  
 ファームにサーバー コンポーネントをインストールしたら、PowerPivot データが埋め込まれた最初の Excel 2010 ブックを作成して、Web アプリケーションの SharePoint ライブラリにパブリッシュすることができます。 PowerPivot データを含む Excel ブックを作成するには、まず Excel 2010 をインストールし、次に PowerPivot for Excel アドインをインストールする必要があります。このアドインは、PowerPivot データのインポートと高度な利用をサポートするように Excel を拡張します。  
  
### <a name="add-servers-or-applications"></a>サーバーまたはアプリケーションの追加  
 PowerPivot ソリューションを展開するときに、web アプリケーション内のすべてのサイト コレクションのサイト コレクション レベルで機能の統合がアクティブ化します。 後で新しい Web アプリケーションを作成した場合は、そのそれぞれに対して powerpivotwebapp ソリューションを配置する必要があります。 手順については、次を参照してください。 [SharePoint に PowerPivot ソリューションの配置](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)します。  
  
 PowerPivot サービス アプリケーションの構成方法によっては、PowerPivot System サービスが既定の接続グループに追加され、既定の接続を使用するすべての Web アプリケーションで使用できるようになります。 ただし、カスタム サービス アプリケーション接続リストを使用するように Web アプリケーションを構成した場合は、PowerPivot データ処理を有効にする各 SharePoint Web アプリケーションに PowerPivot サービス アプリケーションを追加する必要があります。 詳細については、次を参照してください。[サーバーの全体管理で SharePoint Web アプリケーションへの PowerPivot サービス アプリケーションの接続](../../analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md)します。  
  
 後でデータ ストレージや処理能力を追加する必要が生じた場合は、ファームに 2 つ目の PowerPivot for SharePoint サーバー インスタンスを追加することができます。 インストールの手順は、最初のサーバーを追加したときの手順とほとんど同じですが、インスタンス名とサービス アカウント情報の指定についての要件が異なります。 手順については、次を参照してください。[展開のチェックリスト。SharePoint 2010 ファームに PowerPivot サーバーの追加によるスケール アウト](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)します。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 のエディションでサポートされる機能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [PowerPivot サービス アカウントを構成します。](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)   
 [作成し、サーバーの全体管理で PowerPivot サービス アプリケーションを構成します。](../../analysis-services/power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)   
 [SharePoint に PowerPivot ソリューションを配置します。](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)   
 [サーバーの全体管理のサイト コレクションの PowerPivot 機能の統合をアクティブ化します。](../../analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca.md)   
 [PowerPivot for SharePoint 2010 のインストール](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
