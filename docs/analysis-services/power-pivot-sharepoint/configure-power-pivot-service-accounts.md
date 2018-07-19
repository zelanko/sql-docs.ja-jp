---
title: Power Pivot サービス アカウントの構成 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 54dc66e30356f3896d7ce509bf83e56a1973c5b2
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38984844"
---
# <a name="configure-power-pivot-service-accounts"></a>Power Pivot サービス アカウントの構成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]のインストールには、サーバー処理をサポートする 2 つのサービスが含まれます。 **SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)])** サービスは、アプリケーション サーバー上での [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データの処理およびクエリのサポートを提供する Windows サービスです。 このサービスのログイン アカウントは、SharePoint 統合モードで Analysis Services をインストールするときに、SQL Server セットアップで必ず指定します。  
  
 SharePoint ファームのアプリケーション プール ID で実行される共有 Web サービスである [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション用に、アカウントをもう 1 つ指定する必要があります。 このアカウントは、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]構成ツールまたは PowerShell を使用して [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] インストールを構成するときに指定します。  
  
 接続を監査したり、ファームで Kerberos 認証プロトコルを有効にしたりできるように、それぞれのサービスは、専用のアカウントで実行する必要があります。  
  
 サービス アカウントを設定した後で、いずれかのアカウントに変更を加える場合は、SharePoint サーバーの全体管理を使用する必要があります。 別のツール (Services コンソール アプリケーション、IIS マネージャー、SQL Server 構成マネージャーなど) を使用すると、ファーム内でのデータベース アクセス、または物理サーバー上でのファイル アクセスに必要な権限が更新されません。  
  
 このトピックには、次のセクションが含まれます。  
  
 [SQL Server Analysis Services (Power Pivot) インスタンスの期限切れパスワードの更新](#bkmk_passwordssas)  
  
 [Power Pivot サービス アプリケーションの期限切れパスワードの更新](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md#bkmk_passwordapp)  
  
 [各サービスの実行に使用するアカウントの変更](#bkmk_newacct)  
  
 [Power Pivot サービス アプリケーションのアプリケーション プールの作成または変更](#bkmk_appPool)  
  
 [アカウント要件と権限](#requirements)  
  
 [トラブルシューティング: 管理権限の手動による付与](#updatemanually)  
  
 [トラブルシューティング: サーバーの全体管理または SharePoint Foundation Web アプリケーション サービスのパスワードの期限切れによる HTTP 503 エラーの解決](#expired)  
  
##  <a name="bkmk_passwordssas"></a> SQL Server Analysis Services (Power Pivot) インスタンスの期限切れパスワードの更新  
  
1.  [スタート] ボタンをクリックし、 **[管理ツール]**、 **[サービス]** の順にクリックします。 **[SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)])]** をダブルクリックします。 **[ログオン]** をクリックし、アカウントの新しいパスワードを入力します。  
  
2.  サーバーの全体管理で、[セキュリティ] セクションの **[管理アカウントの構成]** をクリックします。  
  
3.  **[編集]** をクリックして指定のアカウントを変更します。  
  
4.  **[今すぐパスワードを変更]** をクリックします。  
  
5.  **[アカウント パスワードを新しい値に設定する]** をクリックします。 管理アカウントで実行されるすべてのサービスで、更新された資格情報が使用されます。  
  
##  <a name="bkmk_passwordapp"></a> Power Pivot サービス アプリケーションの期限切れパスワードの更新  
  
1.  サーバーの全体管理で、[セキュリティ] セクションの **[管理アカウントの構成]** をクリックします。  
  
2.  **[編集]** をクリックして指定のアカウントを変更します。  
  
3.  **[今すぐパスワードを変更]** をクリックします。  
  
4.  **[アカウント パスワードを新しい値に設定する]** をクリックします。 管理アカウントで実行されるすべてのサービスで、更新された資格情報が使用されます。  
  
##  <a name="bkmk_newacct"></a> 各サービスの実行に使用するアカウントの変更  
  
1.  サーバーの全体管理で、[セキュリティ] セクションの **[サービス アカウントの構成]** をクリックします。  
  
2.  **[Windows サービス - SQL Server Analysis Services]** を選択して、Analysis Services サービス アカウントを変更します。  
  
3.  
  **[このサービスのアカウントを選択する]** で、既存の管理アカウントを選択するか、新規に作成します。 このアカウントは、ドメイン ユーザー アカウントであることが必要です。  
  
4.  **[サービス アプリケーション プール - SharePoint Web サービスのシステム]** を選択して、既定の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションのアプリケーション プール ID を変更します。 インストールの構成によっては、SharePoint サービス用に作成された既存のサービス アプリケーション プールでサービスが実行されている場合があります。 既定では、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツールによって、サービスが**既定の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション)** として登録されます。  
  
     サービスが SharePoint 管理者によって手動で構成された場合、サービスにはほとんどの場合に自身のサービス アプリケーション プールがあります。  
  
5.  
  **[このサービスのアカウントを選択する]** で、既存の管理アカウントを選択するか、新規に作成します。 このアカウントは、ドメイン ユーザー アカウントであることが必要です。  
  
6.  **[OK]** をクリックします。  
  
##  <a name="bkmk_appPool"></a> Power Pivot サービス アプリケーションのアプリケーション プールの作成または変更  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを選択します。ただし、クリックはしないでください。 アプリケーション名をクリックすると、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードが開きます。このダッシュボードには、アプリケーション プールを指定するプロパティ ページへのリンクはありません。  行の空白部分をクリックするか、種類名をクリックすると、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを選択できます。  
  
3.  リボンの **[プロパティ]** をクリックします。  
  
4.  **[新しいアプリケーション プールの作成]** をクリックします。 アプリケーション プールの名前を指定し、その ID の管理アカウントを指定します。  
  
##  <a name="requirements"></a> アカウント要件と権限  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint の配置を計画するときには、次のサービス アカウントについて計画する必要があります。  
  
-   Analysis Services サービス アカウント。 Analysis Services は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] のクエリおよびデータ更新のジョブをファームで処理します。 このアカウントは、SQL Server のセットアップ中に、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint をインストールするときに必ず指定します。  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション プール [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスに関連付けられ、ファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] クエリ処理に SharePoint 統合と SharePoint インフラストラクチャを提供します。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションに対して指定するアプリケーション プールは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスのサービス ID です。 1 つのファームに複数の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを作成できますが、 それぞれのサービス アプリケーションを、固有のアプリケーション プールで実行する必要があります。  
  
#### <a name="analysis-services-service-account"></a>Analysis Services サービス アカウント  
  
|要件|説明|  
|-----------------|-----------------|  
|プロビジョニングの要件|このアカウントは、SQL Server セットアップ中にインストール ウィザードの **[Analysis Services - 構成]** ページ (またはコマンド ライン セットアップの **ASSVCACCOUNT** インストール パラメーター) を使用して指定する必要があります。<br /><br /> ユーザー名やパスワードは、サーバーの全体管理、PowerShell、または [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツールを使用して変更できます。 その他のツールでのアカウントやパスワードの変更はサポートされていません。|  
|ドメイン ユーザー アカウントの要件|このアカウントは Windows ドメイン ユーザー アカウントであることが必要です。 ビルトイン コンピューター アカウント (Network Service や Local Service など) は禁止されています。 SQL Server セットアップは、コンピューター アカウントが指定された場合にインストールをブロックすることで、ドメイン ユーザー アカウント要件を適用します。|  
|権限の要件|このアカウントは SQLServerMSASUser$ のメンバーである必要があります\<server > $PowerPivot セキュリティ グループとローカル コンピューターの WSS_WPG セキュリティ グループ。 これらの権限は自動的に付与されます。 権限の確認や付与を行う方法の詳細については、このトピックの「 [PowerPivot サービス アカウントの管理権限を手動で付与する](#updatemanually) 」および「 [初期構成 (Power Pivot for SharePoint)](http://msdn.microsoft.com/3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146)」を参照してください。|  
|スケールアウトの要件|ファームに複数の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint サーバー インスタンスをインストールする場合は、すべての Analysis Services サーバー インスタンスが同じドメイン ユーザー アカウントで実行されている必要があります。 たとえば、最初の [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] インスタンスが Contoso\ssas-srv01 として実行されるように構成した場合は、それ以降に同じファームに配置したその他のすべての [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] インスタンスも Contoso\ssas-srv01 (または現在の任意のアカウント) として実行される必要があります。<br /><br /> すべてのサービス インスタンスが同じアカウントで実行されるように構成すると、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスで、クエリ処理やデータ更新のジョブをファーム内の任意の Analysis Services サービス インスタンスに割り当てられるようになります。 また、Analysis Services サーバー インスタンスに対してサーバーの全体管理の管理アカウント機能を使用できるようになります。 すべての [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] インスタンスに同じアカウントを使用すると、アカウントまたはパスワードを 1 回変更するだけで、これらの資格情報を使用するすべてのサービス インスタンスを自動的に更新できます。<br /><br /> SQL Server セットアップでは、同一アカウント要件が適用されます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint インスタンスが既に SharePoint ファームにインストールされているスケールアウト配置では、指定した [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] アカウントとファーム内で既に使用されているアカウントが異なる場合、セットアップによって新規インストールがブロックされます。|  
  
#### <a name="power-pivot-service-application-pool"></a>Power Pivot サービス アプリケーション プール  
  
|要件|説明|  
|-----------------|-----------------|  
|プロビジョニングの要件|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスは、ファーム上の共有リソースで、サービス アプリケーションを作成すると使用できるようになります。 サービス アプリケーション プールは、サービス アプリケーションの作成時に指定する必要があります。 サービス アプリケーション プールを指定する方法には、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツールを使用する方法と PowerShell コマンドを使用する方法の 2 つがあります。<br /><br /> アプリケーション プール ID を一意のアカウントで実行されるように構成 していない場合は、別のアカウントで実行するように変更することを検討してください。|  
|ドメイン ユーザー アカウントの要件|アプリケーション プール ID は Windows ドメイン ユーザー アカウントであることが必要です。 ビルトイン コンピューター アカウント (Network Service や Local Service など) は禁止されています。|  
|権限の要件|このアカウントには、コンピューターのローカルのシステム管理者権限は必要ありません。 ただし、同じコンピューターにインストールされているローカル [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] に対する Analysis Services のシステム管理者権限が必要です。 これらの権限は、SQL Server セットアップを実行したり、サーバーの全体管理でアプリケーション プール ID を設定または変更したりすると、自動的に付与されます。<br /><br /> 管理権限は、 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]にクエリを転送する場合に必要です。 また、状態の監視、非アクティブなセッションの終了、およびトレース イベントのリッスンにも必要です。<br /><br /> このアカウントには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション データベースに対する接続、読み取り、および書き込みの権限が必要です。 これらの権限は、アプリケーションの作成時に自動的に付与され、サーバーの全体管理でアカウントやパスワードを変更した場合にも自動的に更新されます。<br /><br /> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションでは、ファイルの取得前に、データを表示する権限が SharePoint ユーザーにあるかどうかを確認しますが、ユーザーの権限の借用は行いません。 そのため、権限の借用に関する権限の要件はありません。|  
|スケールアウトの要件|[なし] :|  
  
##  <a name="updatemanually"></a> トラブルシューティング: 管理権限の手動による付与  
 資格情報を更新するユーザーがコンピューターのロカール管理者でない場合、管理者権限は更新されません。 この場合は、管理者権限を手動で付与できます。 最も簡単な方法でこの操作を行うには、サーバーの全体管理で [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] の構成タイマー ジョブを実行します。 この方法を使用すると、ファーム内のすべての [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバーの権限をリセットできます。 この方法は、SharePoint タイマー ジョブがファームの管理者およびコンピューターのローカル管理者の両方として実行されている場合にのみ使用できる点に注意してください。  
  
1.  [監視] で、 **[ジョブ定義の確認]** をクリックします。  
  
2.  **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] の構成タイマー ジョブ**をクリックします。  
  
3.  **[今すぐ実行]** をクリックします。  
  
 Analysis Services システム管理権限を付与することで適切なアクセス許可を確認する最後の手段として、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サービス アプリケーション、および具体的には、サービスのアプリケーション id を SQLServerMSASUser$を追加\<servername > $PowerPivot Windows セキュリティ グループ。 SharePoint ファームに統合された各 Analysis Services インスタンスに対してこれらの手順を繰り返す必要があります。  
  
 Windows セキュリティ グループを更新するには、ローカル管理者である必要があります。  
  
1.  SQL Server Management studio で、Analysis Services インスタンスに接続します。\<サーバー名 > \POWERPIVOT します。  
  
2.  サーバー名を右クリックし、 **[プロパティ]** をクリックします。  
  
3.  **[セキュリティ]** をクリックします。  
  
4.  **[追加]** をクリックします。  
  
5.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション プールに使用するアカウントの名前を入力し、 **[OK]** をクリックします。  
  
6.  [管理ツール] で、 **[コンピューターの管理]** をクリックします。  
  
7.  **[ローカル ユーザーとグループ]** を開きます。  
  
8.  **[グループ]** を開きます。  
  
9. SQLServerMSASUser$ をダブルクリックして\<servername > $PowerPivot します。  
  
10. **[追加]** をクリックします。  
  
11. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション プールに使用するアカウントの名前を入力し、 **[OK]** をクリックします。  
  
##  <a name="expired"></a> トラブルシューティング: サーバーの全体管理または SharePoint Foundation Web アプリケーション サービスのパスワードの期限切れによる HTTP 503 エラーの解決  
 アカウントのリセットまたはパスワードの期限切れが原因で、サーバーの全体管理サービスまたは SharePoint Foundation Web アプリケーション サービスが停止する場合は、SharePoint サーバーの全体管理あるいは SharePoint サイトを開こうとすると、"サービスを利用できません" という HTTP 503 エラー メッセージが表示されます。 サーバーをオンラインに戻すには、次の手順を実行します。 サーバーの全体管理を使用できる場合は、続行して期限切れのアカウント情報を更新できます。  
  
1.  [管理ツール] で、 **[インターネット インフォメーション サービス マネージャー]** をクリックします。  
  
2.  サイトまたはサーバーの全体管理アプリケーション プールの ID が、期限切れのパスワードを持つドメイン ユーザー アカウントである場合は、次の手順を実行します。  
  
    1.  アプリケーション プール名を右クリックし、 **[詳細設定]** をクリックします。  
  
    2.  **[ID]** を選択し、[…] (省略記号) ボタンをクリックして、[アプリケーション プール ID] ダイアログ ボックスを開きます。  
  
    3.  **[設定]** をクリックします。  
  
    4.  ユーザー名とパスワードを入力します。  
  
3.  IISRESET を実行します。 この操作を行うには、管理者コマンド プロンプトを開き、コマンドで「 **iisreset** 」と入力します。  
  
4.  SharePoint サーバーの全体管理で、[セキュリティ] の **[管理アカウントの構成]** をクリックします。  
  
5.  
  **[編集]** をクリックして、期限切れのパスワードを持つ管理アカウントの情報を更新します。  
  
6.  **[今すぐパスワードを変更]** をクリックします。  
  
7.  **[既存のパスワードを使用]** をクリックします。  
  
8.  パスワードを入力し、 **[OK]** をクリックします。  
  
 Reporting Services がインストールされている場合は、Reporting Services 構成マネージャーを使用して、レポート サーバーのパスワードとレポート サーバー データベースへの接続に使用するパスワードを更新します。 詳細については、「[レポート サーバーの構成と管理 (Reporting Services SharePoint モード)](../../reporting-services/report-server-sharepoint/configuration-and-administration-of-a-report-server.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [PowerPivot for SharePoint サーバーの開始または停止](../../analysis-services/power-pivot-sharepoint/start-or-stop-a-power-pivot-for-sharepoint-server.md)   
 [Power Pivot の構成自動データ更新アカウント (Power Pivot for SharePoint)](http://msdn.microsoft.com/81401eac-c619-4fad-ad3e-599e7a6f8493)  
  
  
