---
title: "URL 予約と登録 (SSRS 構成マネージャー) について |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/18/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- URL reservations
- URL registration
- Report Server service, URL reservations
ms.assetid: c2c460c3-e749-4efd-aa02-0f8a98ddbc76
caps.latest.revision: 15
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: eb1f09f1a23a6e24077357c36a0dbc136a86473f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="about-url-reservations-and-registration--ssrs-configuration-manager"></a>URL の予約と登録について (SSRS 構成マネージャー)
  Reporting Services アプリケーションの URL は、HTTP.SYS の URL 予約として定義されます。 URL 予約は、Web アプリケーションへの URL エンドポイントの構文を定義します。 レポート サーバーでアプリケーションを構成する際には、レポート サーバー Web サービスとレポート マネージャーの両方に対して URL 予約を定義します。 セットアップまたは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールで URL を構成すると、自動的に URL 予約が作成されます。  
  
-   セットアップでは、既定値を使用して URL 予約が作成されます。 既定の構成でインストールすると、レポート サーバー Web サービスの URL とレポート マネージャーの URL の 2 つの URL が予約されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを使用すると、URL をさらに追加したり、セットアップによって作成された既定の URL を変更したりできます。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールでは、ツールの **[Web サービス URL]** ページまたは **[Web ポータル URL]** ページで指定した URL に基づいて URL 予約が作成されます。  
  
 いずれの場合も、さらに、レポート サーバー サービスへの URL に対する権限の割り当て、重複するインスタンスのチェック、および HTTP.SYS への URL 予約の追加が行われます。 HttpCfg.exe やその他のツールを使用して直接 Reporting Services の URL 予約を作成したり変更したりしないでください。 手順を省略したり無効な値を設定したりすると、診断や修正が困難な問題が発生する可能性があります。  
  
> [!NOTE]  
>  HTTP.SYS は、ネットワーク要求をリッスンして要求キューにルーティングするオペレーティング システム コンポーネントです。 このリリースの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]では、HTTP.SYS によって、レポート サーバー Web サービスとレポート マネージャーの要求キューが作成され、管理されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーションのホスティングやアクセスにインターネット インフォメーション サービス (IIS) は使用されなくなりました。 HTTP.SYS 機能の詳細については、MSDN の「 [HTTP サーバー API](http://go.microsoft.com/fwlink/?LinkId=92652) 」を参照してください。  
  
##  <a name="ReportingServicesURLs"></a> Reporting Services の URL  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、以下のツール、アプリケーション、およびアイテムに URL を通じてアクセスできます。  
  
-   レポート サーバー Web サービス  
  
-   Web ポータル  
  
-   レポート サーバーにパブリッシュされたレポート  
  
 URL を指定できるその他のパブリッシュされるアイテム (共有データ ソースなど) には、URL を通じてスタンドアロンのアイテムとしてアクセスしないようにしてください。 これらのアイテムは、ブラウザー ウィンドウで表示しても意味のある形式で表示されません。  
  
> [!NOTE]  
>  このトピックでは、レポート サーバーに保存されている特定のレポートへの URL アクセスについては説明していません。 これらのアイテムへの URL アクセスの詳細については、 [オンライン ブックの「](../../reporting-services/access-report-server-items-using-url-access.md) URL アクセスを使用したレポート サーバー アイテムへのアクセス [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。  
  
##  <a name="URLreservation"></a> URL の予約と登録  
 URL 予約は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーションへのアクセスに使用できる URL を定義します。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レポート サーバー Web サービスと [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] の URL を HTTP.SYS で 1 つ以上予約して、サービスの起動時に登録します。 URL にパラメーターを追加することにより、Web サービスを通じてレポートを開くことができます。 予約と登録は、HTTP.SYS によって行われます。 詳細については、MSDN の「 [名前空間の予約、登録、およびルーティング](http://go.microsoft.com/fwlink/?LinkId=92653) 」を参照してください。  
  
 URL 予約** とは、Web アプリケーションへの URL エンドポイントを作成して HTTP.SYS に格納するプロセスです。 HTTP.SYS は、コンピューターで定義されているすべての URL 予約の共通リポジトリであり、URL 予約が一意であることを保証する一連の共通規則を定義します。  
  
 URL の登録** は、サービスの起動時に行われます。 サービスが起動すると、要求キューが作成され、HTTP.SYS がそのキューへの要求のルーティングを開始します。 URL エンドポイントは、そのエンドポイントに転送される要求がキューに追加される前に登録される必要があります。 レポート サーバー サービスの起動時には、有効化されているすべてのアプリケーションに対して予約されているすべての URL が登録されます。 したがって、登録が行われるためには Web サービスが有効化されている必要があります。 ポリシー ベースの管理の Reporting Services のセキュリティ構成ファセットで **WebServiceAndHTTPAccessEnabled** プロパティを **False** に設定すると、Web サービスの URL がサービスの起動時に登録されません。  
  
 サービスを停止するか、Web サービスや [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] アプリケーション ドメインの再利用を行うと、URL の登録が解除されます。 サービスの実行中に URL 予約を変更すると、古い URL の登録を解除して新しい URL を使用できるようにするために、アプリケーション ドメインの再利用処理が直ちに行われます。  
  
 次の例は、URL 予約の概念と、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーション用に使用される URL アドレスと URL 予約の関連付けを示しています。 URL 予約の構文が、アプリケーションへのアクセスに使用する URL とは異なる点に注目してください。  
  
|HTTP.SYS の URL 予約|[URL]|説明|  
|---------------------------------|---------|-----------------|  
|`http://+:80/reportserver`|`http://<computername>/reportserver`<br /><br /> `http://<IPAddress>/reportserver`<br /><br /> `http://localhost/reportserver`|この URL 予約では、ポート 80 でワイルドカード (+) を指定しています。 これにより、ポート 80 のレポート サーバー コンピューターに解決されるホストが指定されているすべての受信要求がレポート サーバー キューに送られます。 この URL 予約を使用すると、任意の数の URL を使用してレポート サーバーにアクセスできます。<br /><br /> ほとんどのオペレーティング システムでは、これが [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーの既定の URL 予約です。|  
|`http://123.45.67.0:80/reportserver`|`http://123.45.67.0/reportserver`|この URL 予約では IP アドレスを指定しています。これは、ワイルドカードの URL 予約よりはるかに制限の厳しい URL 予約です。 レポート サーバーへの接続に使用できるのは、この IP アドレスを含む URL だけです。 この URL 予約を要求時にレポート サーバーに`http://<computername>/reportserver`または`http://localhost/reportserver`は失敗します。|  
  
##  <a name="DefaultURLs"></a> 既定の URL  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を既定の構成でインストールすると、レポート サーバー Web サービスと [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)]の URL が自動的に予約されます。 これらの既定値は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールで URL 予約を定義するときにも使用できます。 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] をインストールした場合や、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を名前付きインスタンスとしてインストールした場合は、既定の URL にインスタンス名が含まれます。  
  
> [!IMPORTANT]  
>  インスタンスの文字はアンダースコア文字 (**_**) です。  
  
 URL 予約にはポート番号が含まれます。 以下のオペレーティング システムでは、複数の Web アプリケーションで 1 つのポートを共有できます。  
  
-   [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2  
  
-   [!INCLUDE[win8srv](../../includes/win8srv-md.md)]  
  
-   [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]  
  
-   [!INCLUDE[win7](../../includes/win7-md.md)]  
  
-   [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)]  
  
|インスタンスの種類|アプリケーション|既定の URL|HTTP.SYS の実際の URL 予約|  
|-------------------|-----------------|-----------------|----------------------------------------|  
|[既定のインスタンス]|レポート サーバー Web サービス|`http://\<servername>/reportserver`|`http://<servername>:80/reportserver`|  
|[既定のインスタンス]|Web ポータル|`http://<servername>/reportserver`|`http://<servername>:80/reportserver`|  
|[名前付きインスタンス]|レポート サーバー Web サービス|`http://<servername>/reportserver_<instancename>`|`http://<servername>:80/reportserver_<instancename>`|  
|[名前付きインスタンス]|Web ポータル|`http://<servername>/reports_<instancename>`|`http://<servername>:80/reports_<instancename>`|  
|SQL Server Express|レポート サーバー Web サービス|`http://<servername>/reportserver_SQLExpress`|`http://<servername>:80/reportserver_SQLExpress`|  
|SQL Server Express|Web ポータル|`http://<servername>/reports_SQLExpress`|`http://<servername>:80/reports_SQLExpress`|  
  
##  <a name="URLPermissionsAccounts"></a> Reporting Services の URL の認証とサービス ID  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]URL 予約では、レポート サーバー サービスのサービス アカウントを指定します。 サービスが実行されているアカウントが、同じインスタンスで実行される [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーションに対して作成されるすべての URL に対して使用されます。 レポート サーバー インスタンスのサービス ID は、RSReportServer.config ファイルに格納されます。  
  
 サービス アカウントには既定値はありません。 ただし、セットアップ時には (ファイルのみのモードでサーバーをインストールする場合でも) サービス アカウントを指定する必要があります。サービス アカウントは、RSReportServer.config の **URLReservation** に指定されます。 サービス アカウントの有効な値は、ドメイン ユーザー アカウント、 **LocalSystem**、および **NetworkService**です。  
  
 既定のセキュリティが **RSWindowsNegotiate**であるため、匿名アクセスは無効になっています。 イントラネット アクセスの場合、レポート サーバーの URL ではネットワーク コンピューターの名前が使用されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をインターネット接続用に構成する場合は、別の設定を使用する必要があります。 認証の詳細については、 [オンライン ブックで「](../../reporting-services/security/authentication-with-the-report-server.md) レポート サーバーでの認証 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。  
  
##  <a name="URLlocalAdmin"></a> ローカル管理用の URL  
 使用することができます`http://localhost/reportserver`または`http://localhost/reports`URL 予約に対して強いか弱いワイルドカードを指定した場合。  
  
 `http://localhost` URL として解釈されます`http://127.0.0.1`です。 URL 予約をコンピューター名や 1 つの IP アドレスに設定した場合は、ローカル コンピューターの 127.0.0.1 に対して追加の予約を作成しないと localhost を使用できません。 同様に、localhost や 127.0.0.1 がコンピューターで無効になっている場合も、その URL を使用できません。  
  
 [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)]と [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] 以降には、誤ってプログラムが高度な特権で実行されるリスクを最小限に抑える新しいセキュリティ機能が含まれています。 これらのオペレーティング システムでローカル管理を有効にするには、追加の手順が必要です。 詳細については、「[ローカル管理用のネイティブ モードのレポート サーバー &#40;SSRS&#41; の構成](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [URL &#40; を構成します。SSRS 構成マネージャー &#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [URL 予約構文 & #40 です。SSRS 構成マネージャー &#41;](../../reporting-services/install-windows/url-reservation-syntax-ssrs-configuration-manager.md)  
  
  

