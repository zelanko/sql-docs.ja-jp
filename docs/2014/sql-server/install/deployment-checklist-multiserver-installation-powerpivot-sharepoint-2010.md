---
title: 配置のチェック リスト:PowerPivot for SharePoint 2010 のマルチ サーバーのインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 4380040a-1368-4a47-8930-47c65a192e59
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e738635465bf6e7af0b16913c4c1f91f719f6a35
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66095700"
---
# <a name="deployment-checklist-multi-server-installation-of-powerpivot-for-sharepoint-2010"></a>配置のチェック リスト:PowerPivot for SharePoint 2010 のマルチサーバー インストール
  このチェックリストを追加する手順の手順を説明します。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint をゼロから構築される 3 層 SharePoint 2010 ファームをします。 3 層ファームには、データベース層、アプリケーション層、および Web 層が含まれています。 追加[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]このトポロジをインストールする SQL Server セットアップを実行する必要があります[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]アプリケーション層にします。 PowerPivot プログラム ファイルは、web アプリケーション ソリューションでデプロイするときに、web 層には、インストール後のタスクとしてのみ追加されます。 配置手順は必要ですが、Web 層またはデータ層のいずれかで実行する必要のある個別のインストール手順はありません。 のみのインストール手順を実行する必要のあるをインストールする[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]アプリケーション サーバーにします。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010|  
  
  
  
## <a name="prerequisites"></a>前提条件  
 SQL Server および SharePoint 2010 をインストールするには、ローカル管理者である必要があります。  
  
 SharePoint のインストール担当者は、ファームも構成する必要があります。 ファームを構成するには、データベース サーバーに対する SQL Server ログイン権限が必要です。 ログインは、`dbcreator`、`securityadmin`、および `public` のロールに割り当てる必要があります。  
  
 Enterprise Edition または Enterprise Evaluation Edition の SharePoint Server 2010 が必要です。  
  
 コンピューターがドメインに参加する必要があります。  
  
 データベース エンジン、ファーム内のサービス、および SharePoint 統合モードの Analysis Services を実行するために使用するアカウントを把握している必要があります。 これらのアカウントは後で変更できますが、インストール時に最初に指定します。  
  
 インストール時に指定するサービス アカウントは、ドメイン ユーザー アカウントである必要があります。  
  
 インストールを開始する前に、インターネット接続が有効であるかどうかをブラウザーの設定で確認してください。 必須コンポーネントのインストーラーにより、必要なソフトウェアをダウンロードするためにインターネットに接続されます。 必要なソフトウェアをすべて取得するために、次の変更を行ってください。  
  
-   サーバー マネージャーで、Internet Explorer セキュリティ強化の構成を一時的に無効にし、サーバーへのダウンロードを許可します。 必要なソフトウェアをダウンロードする目的でのみ、[IE ESC の構成] の [管理者グループ用] をオフにできます。  
  
-   また、Internet Explorer で、プロキシ サーバーをバイパスしてインターネット URL へのローカルホストのアクセスを許可するようにブラウザーを構成することが必要になる場合もあります。  
  
    1.  Internet Explorer で、[ツール] メニューの [インターネット オプション] をクリックします。  
  
    2.  [接続] タブで、[ローカル エリア ネットワーク (LAN) の設定] 領域にある [LAN の設定] をクリックします。  
  
    3.  [自動構成] 領域で、[設定を自動的に検出する] チェック ボックスをオフにします。  
  
    4.  [プロキシ サーバー] 領域で、[LAN にプロキシ サーバーを使用する] チェック ボックスをオンにします。  
  
    5.  プロキシ サーバーのアドレスを [アドレス] ボックスに入力します。  
  
    6.  プロキシ サーバーのポート番号を [ポート] ボックスに入力します。  
  
    7.  [ローカル アドレスにはプロキシ サーバーを使用しない] チェック ボックスをオンにします。  
  
    8.  [OK] をクリックして [ローカル エリア ネットワーク (LAN) の設定] ダイアログ ボックスを閉じます。  
  
    9. [OK] をクリックして [インターネット オプション] ダイアログ ボックスを閉じます。  
  
##  <a name="installdb"></a> データベース サーバーをインストールします。  
 このトピックでは、ファーム トポロジは、情報の記事に記載されているものに基づいて前提としています。 [3 層ファーム用の複数サーバー](https://go.microsoft.com/fwlink/?LinkId=182771)します。 ファームが動作に既にある場合に進みます[PowerPivot for SharePoint インストール](#installppapp)します。  
  
 トポロジを初めて設定する場合は、SQL Server データベース エンジンのインストールから始めます。 以下の手順を実行すると、ファーム内の SharePoint サーバーがアクセスできるデータベース サーバーがインストールされます。  
  
1.  データベース サーバーを使用しているコンピューターで SQL Server データベース エンジンをインストールする SQL Server セットアップを実行します (を参照してください[インストール ウィザードからの SQL Server 2014 のインストール&#40;セットアップ&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md))。  
  
     インストールする機能として、以下を選択します。  
  
    -   データベース エンジン サービス  
  
    -   クライアント ツール接続  
  
    -   管理ツール - 完全 (基本機能は自動的に含まれます)  
  
2.  データベース エンジンをインストールした後、リモート接続用の TCP/IP を有効にし、サービスを再起動します。  
  
    1.  SQL Server 構成マネージャーを起動します。  
  
    2.  [SQL Server ネットワークの構成] を開きます。  
  
    3.  **[MSSQLSERVER のプロトコル]** を選択します。  
  
    4.  右クリック**TCP/IP**選択**を有効にする**します。  
  
    5.  クリックして**SQL Server サービス**します。  
  
    6.  右クリックして**SQL Server (MSSQLSERVER)**、 をクリック**再起動**します。  
  
3.  Windows ファイアウォールを経由したデータベース サーバーへの入力方向のアクセスを有効にします。 これにより、ファーム内の SharePoint サーバーが SharePoint データベースに接続できるようになります。 詳細については、「 [Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)」をご参照ください。  
  
    1.  Windows コントロール パネル] の [管理ツールで、**セキュリティが強化された Windows ファイアウォール**します。  
  
    2.  クリックして**受信規則**します。  
  
    3.  クリックして**新しいルール**します。  
  
    4.  規則の種類 をクリックして**カスタム**します。  
  
    5.  **[次へ]** をクリックします。  
  
    6.  サービス セクションで、プログラムで、**カスタマイズ**します。  
  
    7.  クリックして**このサービスに適用**します。  
  
    8.  選択**SQL Server (MSSQLSERVER)** かどうか、既定のインスタンスとして SQL Server をインストールし、クリックして**OK**します。  
  
    9. **[次へ]** をクリックします。  
  
    10. プロトコルおよびポートの場合は、既定の設定をそのまま使用し、をクリックして**次**します。  
  
    11. スコープで、既定の設定をそのまま使用し をクリックして**次**します。  
  
    12. アクションで、既定の設定をそのまま使用し、をクリックして**次**します。  
  
    13. [プロファイル] のチェック ボックスをオフに**プライベート**と**パブリック**、順にクリックします**次**します。  
  
    14. 名前、受信の規則のわかりやすい名前を入力します (たとえば、 **SQL Server**)。  
  
    15. **[完了]** をクリックします。  
  
##  <a name="installsp"></a> インストールして、3 層 SharePoint 2010 ファームの構成  
 SharePoint サーバーとして使用しているコンピューターで、SharePoint の必須コンポーネントのインストーラー プログラムを実行してから、SharePoint Server セットアップを実行します。  
  
 SharePoint 2010 ドキュメントに記載されている次の手順に従って、2 台の Web サーバーと 1 台のアプリケーション サーバーを含む SharePoint 2010 ファームをインストールし、構成します。  
  
 [3 層ファーム (SharePoint Server 2010) の複数のサーバー](https://go.microsoft.com/fwlink/?LinkId=182771)  
  
 データベース サーバーを指定するように求められたら、以前インストールしたデータベース サーバーを指定します。  
  
 以後の手順では、3 層ファームのセットアップ手順を使用してファームが構成されていることが前提となります。 ファームには次のサービスと機能が含まれている必要があります。  
  
-   Excel Services、Search Service、および Secure Store Service  
  
-   Web アプリケーションおよびサイト コレクション  
  
-   使用状況および正常性のデータ収集  
  
-   診断ログ  
  
##  <a name="installppapp"></a> アプリケーション サーバーで PowerPivot for SharePoint をインストールします。  
 SQL Server セットアップを実行して SharePoint ファームに PowerPivot for SharePoint を追加します。 ファームが複数の SharePoint サーバーで構成されている場合は、既にファームに参加しているアプリケーション サーバーで SQL Server セットアップを実行する必要があります。  
  
 アプリケーション サーバーには常に PowerPivot for SharePoint をインストールします。 PowerPivot for SharePoint サーバー コンポーネントは Web フロントエンド サーバーでも実行されますが、Web フロントエンドで実行されるコンポーネントは、PowerPivot for SharePoint の構成手順で、ファームにソリューションを配置するときにインストールされます。 セットアップの詳細については、次を参照してください。 [PowerPivot for SharePoint 2010 インストール](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)します。  
  
 配置トポロジに 2 つの PowerPivot for SharePoint インスタンスが必要な場合は、各アプリケーション サーバーで SQL Server セットアップを実行します。 1 台のコンピューターには PowerPivot for SharePoint のインスタンスを 1 つだけインストールできます。 複数のインスタンスが必要な場合は、追加のサーバーを使用する必要があります。 同じファームに複数の PowerPivot for SharePoint サーバーを追加する方法の詳細については、次を参照してください。[展開のチェックリスト。SharePoint 2010 ファームに PowerPivot サーバーの追加によるスケール アウト](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)します。  
  
##  <a name="installclientlib"></a> For SharePoint で PowerPivot のインストールを持たない SharePoint アプリケーション サーバー上の Analysis Services クライアント ライブラリをインストールします。  
 同じコンピューターに PowerPivot for SharePoint がインストールされておらず、次のアプリケーションを実行している Web フロントエンドまたはアプリケーション サーバーを含むファーム トポロジには、PowerPivot データ アクセスおよび機能をサポートするための追加ソフトウェアが必要になります。  
  
-   Excel Services または PerformancePoint Services  
  
-   自身のサーバーでスタンドアロン アプリケーションとして実行される、サーバーの全体管理  
  
 Excel Services と PerformancePoint Services には、PowerPivot データ アクセスをサポートするための新しいバージョンの Analysis Services OLE DB プロバイダーが必要です。 最新の OLE DB プロバイダーがインストールされていないコンピューターでいずれかのアプリケーションを実行する場合、プロバイダーを手動でインストールする必要があります。 詳細については、次を参照してください[SharePoint サーバーに、Analysis Services OLE DB プロバイダーをインストールする。](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
 同様に、サーバーの全体管理だけがインストールされていて、PowerPivot for SharePoint がインストールされていないコンピューターは、ADOMD.NET クライアント ライブラリが必要になります。 PowerPivot 管理ダッシュボードはこのライブラリを使用して内部データにアクセスし、このデータを使ってダッシュボードを設定します。 詳細については、「 [サーバーの全体管理を実行している Web フロントエンド サーバーに ADOMD.NET をインストールする方法](../../../2014/sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md)」を参照してください。  
  
##  <a name="configsrvr"></a> サーバーを構成します。  
 PowerPivot 構成ツールを使用して PowerPivot for SharePoint を構成します。 このツールは、ファームの既存の構成をスキャンし、インストールまたは SharePoint の PowerPivot で必要な SharePoint 機能をアクティブ化のオプションを提供します。 このステップで、Claims to Windows Token Service が開始されます。 さらに、その他の必要な SharePoint 機能がまだ有効になっていない場合は、構成ツールによってそれらが一覧に追加され、機能を有効にするためのアクションが組み込まれます。  
  
 詳細については、次を参照してください。[構成または修復の PowerPivot for SharePoint 2010 &#40;PowerPivot 構成ツール&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md)します。  
  
##  <a name="AAM"></a> Web フロント エンド サーバーの代替アクセス マッピングを構成します。  
 PowerPivot のデータ アクセスまたはデータ更新に対する要求を各 Web フロントエンド サーバーによって処理するには、各サーバーの異なる URL を同じ Web アプリケーションにマップする必要があります。  
  
1.  アプリケーションの管理でのサーバーの全体管理 をクリックして**代替アクセス マッピングを構成する**します。  
  
2.  [代替アクセス マッピング コレクション] で、Web アプリケーションを選択します。  
  
3.  クリックして**内部 URL を追加する**します。  
  
4.  最初の Web フロントエンド サーバーの URL を指定します。  
  
5.  前の手順を繰り返し、2 番目の Web フロントエンド サーバーの URL を追加します。  
  
##  <a name="activatePP"></a> サイト コレクションの PowerPivot 機能の統合をアクティブ化します。  
 サイト コレクション レベルで機能をアクティブ化すると、サイトでアプリケーション ページやテンプレートを使用できるようになります。これには、定期データを更新するための構成ページや、PowerPivot ギャラリーとデータ フィード ライブラリのアプリケーション ページなどが含まれます。  
  
 PowerPivot 構成ツールでは、指定したサイト コレクションに対して機能の統合がアクティブ化されます。 ツールを複数回実行すると追加のサイト コレクションを選択できます。 または、サイト管理者が SharePoint 内から機能のアクティブ化を構成することもできます。 詳細については、次を参照してください。 [PowerPivot 機能の統合サーバーの全体管理のサイト コレクション用にアクティブ化](../../analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca.md)します。  
  
##  <a name="verify"></a> 統合とサーバーの可用性を確認します。  
 ファームの PowerPivot クエリ処理は、ユーザーまたはアプリケーションが PowerPivot データを含む Excel ブックを開いたときに発生します。 PowerPivot 機能が使用可能になっているかどうかは、SharePoint サイトのページを調べれば確認できますが、 インストールを完全に確認するには、SharePoint にパブリッシュでき、ライブラリからアクセスできる PowerPivot ブックが必要になります。 テストの際には、既に PowerPivot データが含まれているサンプル ブックをパブリッシュし、それを使用して SharePoint 統合が正しく構成されているかどうかを確認できます。  
  
 PowerPivot の SharePoint サイトとの統合を確認するには、次の操作を行います。  
  
1.  ブラウザーで、作成した Web アプリケーションを開きます。 既定値を使用した場合は、 http:// を指定できます\<コンピューター名 >、URL アドレス。  
  
2.  PowerPivot データ アクセス機能と PowerPivot データ処理機能がアプリケーションで使用可能になっていることを確認します。 そのためには、PowerPivot によって提供されるライブラリ テンプレートがあるかどうかを確認します。  
  
    1.  サイトの操作をクリックします**オプション**。  
  
    2.  ライブラリでは、表示する必要があります**データ フィード ライブラリ**と**PowerPivot ギャラリー**します。 これらのライブラリ テンプレートは PowerPivot 機能によって提供されるものであり、PowerPivot 機能が正しく統合されている場合に [ライブラリ] に表示されます。  
  
 サーバーで PowerPivot データ アクセスを確認するには、次の操作を行います。  
  
1.  Reporting Services のチュートリアルにある Picnic のデータ サンプルを[ダウンロード](https://go.microsoft.com/fwlink/?LinkID=219108) します。 このダウンロードに含まれるサンプル ブックを使用して、PowerPivot データのアクセスを確認します。 ファイルを抽出します。  
  
2.  PowerPivot ブックを PowerPivot ギャラリーまたは任意の SharePoint ライブラリにアップロードします。  
  
3.  ドキュメントをクリックしてライブラリから開きます。  
  
4.  スライサーをクリックするかデータをフィルター処理して PowerPivot クエリを開始します。 サーバーは PowerPivot データをバックグラウンドで読み込んで結果を返します。 次の手順で、サーバーに接続して、データの読み込みとキャッシュが行われたことを確認します。  
  
5.  [スタート] メニューの Microsoft SQL Server 2008 R2 プログラム グループから SQL Server Management Studio を起動します。 サーバーでこのツールがインストールされていない場合は、手順を省略できます最後をキャッシュ ファイルの存在を確認します。  
  
6.  [サーバーの種類] で **[Analysis Services]** を選択します。  
  
7.  サーバー名 で次のように入力します。 **\<サーバー名 > \powerpivot**ここで、 **\<サーバー名 >** 、PowerPivot for SharePoint のインストールをしたコンピューターの名前を指定します。  
  
8.  **[接続]** をクリックします。  
  
9. オブジェクト エクスプ ローラーで次のようにクリックします。**データベース**読み込まれる PowerPivot データ ファイルの一覧を表示します。  
  
10. コンピューターのファイル システムのフォルダーで、ファイルがディスクにキャッシュされているかどうかを確認します。 キャッシュされたファイルが存在していれば、配置が機能していることの確認になります。 ファイル キャッシュを表示するには、\Program Files\Microsoft SQL Server\MSAS10_50.POWERPIVOT\OLAP\Backup フォルダーに移動します。  
  
##  <a name="nextsteps"></a> インストール後の手順  
 インストールの確認が完了したら、PowerPivot ギャラリーを作成するか個々の構成設定を調整してサービスの構成を終了します。 インストールしたサーバー コンポーネントを完全に利用するには、[!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] をダウンロードし、最初の PowerPivot ブックを作成してパブリッシュします。  
  
####  <a name="bkmk_disk"></a> ディスク領域使用量の上限値を設定します。  
 ディスクにキャッシュされる PowerPivot データ ファイルに使用されるディスク容量の最大制限を設定できます。 既定では、使用可能なすべてのディスク領域が使用されます。 ディスク使用量を制限する方法については、次を参照してください。[ディスク使用領域の構成&#40;PowerPivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-disk-space-usage-power-pivot-for-sharepoint.md)します。  
  
####  <a name="Upload"></a> SharePoint Web アプリケーションのファイルの最大アップロード サイズを増やす  
 PowerPivot ブックはサイズが大きくなる可能性があるため、ファイルの最大アップロード サイズを増やしたい場合があります。 構成する 2 つのファイル サイズの設定として、Web アプリケーションには [アップロードの最大サイズ]、Excel Services には [ブックの最大サイズ] があります。 最大ファイル サイズは、両方のアプリケーションで同じ値に設定してください。 手順については、次を参照してください。[構成ファイルの最大アップロード サイズ&#40;PowerPivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint.md)します。  
  
#### <a name="grant-sharepoint-permissions-to-workbook-users"></a>ブックのユーザーへの SharePoint 権限の付与  
 ユーザーがブックをパブリッシュまたは表示するには、SharePoint 権限が必要です。 付与してください**ビュー**パブリッシュ済みのブックを表示する必要があるユーザーへのアクセス許可と**投稿**パブリッシュまたはブックを管理するユーザーへのアクセス許可。 権限を付与するには、サイト コレクションの管理者である必要があります。  
  
1.  サイトで、次のようにクリックします。**サイトの操作**します。  
  
2.  クリックして**サイトの権限**します。  
  
3.  サイト コレクションのチェック ボックスをオン**メンバー**グループ。  
  
4.  リボンで、次のようにクリックします。**アクセス許可の付与**します。  
  
5.  ドキュメントを追加または削除する権限を必要とする Windows ドメインのユーザー アカウントまたはグループ アカウントを入力します。  
  
6.  **[OK]** をクリックします。  
  
7.  サイト コレクションのチェック ボックスをオン**訪問者**グループ。  
  
8.  リボンで、次のようにクリックします。**アクセス許可の付与**します。  
  
9. ドキュメントを表示する権限を必要とする Windows ドメインのユーザー アカウントまたはグループ アカウントを入力します。 上で説明した手順と同様に、アプリケーションで従来の認証が構成されている場合は、電子メール アドレスまたは配布グループを使用しないでください。  
  
10. **[OK]** をクリックします。  
  
#### <a name="install-adonet-data-services-35-sp1"></a>ADO.NET Data Services 3.5 SP1 のインストール  
 ADO.NET Data Services は、SharePoint リストのデータ フィードのエクスポートに必要です。 SharePoint 2010 では、このコンポーネントは PrerequisiteInstaller プログラムに含まれていないため、手動でインストールする必要があります。 ADO.NET Data Services をインストールする方法の詳細については、次を参照してください。[データをサポートする ADO.NET Data Services のインストールは、SharePoint リストのエクスポートをフィード](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md)します。  
  
#### <a name="install-data-providers-used-in-data-refresh-and-check-user-permissions"></a>データ更新で使用するデータ プロバイダーのインストールとユーザー権限の確認  
 サーバー側のデータ更新により、ユーザーは更新されたデータをブックに自動モードで再インポートできます。 データ更新を正常に行うためには、最初にデータをインポートするために使用したものと同じデータ プロバイダーがサーバーに必要になります。 さらに、通常は、データ更新を実行するユーザー アカウントに外部データ ソースに対する読み取り権限が必要です。 データ更新を正常に実行できるように、データ更新の有効化と構成の要件をご確認ください。 詳細については、次を参照してください。 [SharePoint 2010 で PowerPivot データ更新](../../../2014/analysis-services/powerpivot-data-refresh-with-sharepoint-2010.md)します。  
  
#### <a name="create-a-powerpivot-gallery"></a>PowerPivot ギャラリーを作成します。  
 PowerPivot ギャラリーは、SharePoint サイトの PowerPivot ブックを表示するためのプレビュー オプションや表示オプションを備えたライブラリです。 プレビュー機能があるため、PowerPivot ブックをパブリッシュしたり表示したりする際には PowerPivot ギャラリーを使用することをお勧めします。 同じ SharePoint サーバーに Reporting Services も配置されている場合は、 PowerPivot ギャラリーからレポート ビルダーを起動して、パブリッシュされた PowerPivot ブックを新しいレポートのベースとして使用することもできます。 作成して、ライブラリの使用の詳細については、次を参照してください。 [PowerPivot ギャラリーのカスタマイズの作成と](../../analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery.md)と[PowerPivot ギャラリーを使用して](../../analysis-services/power-pivot-sharepoint/use-power-pivot-gallery.md)します。  
  
#### <a name="tune-configuration-settings"></a>構成設定の調整  
 PowerPivot サービス アプリケーションは、既定のプロパティと値を使用して作成されますが、 個々のサービス アプリケーションの構成設定を変更して、要求の割り当て方法を変更したり、サーバー タイムアウトを設定したり、クエリ応答レポート イベントのしきい値を変更したり、使用状況データを保持する期間を指定したりすることもできます。 サーバーの全体管理の構成や SharePoint Web アプリケーションで PowerPivot 機能の使用に関する詳細については、次を参照してください。[サーバーの全体管理で PowerPivot サーバーの管理と構成](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)します。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2012 の各エディションでサポートされる機能](https://go.microsoft.com/fwlink/?linkid=232473)   
 [PowerPivot for SharePoint 2010 をインストールします。](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)   
 [配置のチェックリスト:SharePoint 2010 ファームに PowerPivot サーバーの追加によるスケール アウト](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)  
  
  
