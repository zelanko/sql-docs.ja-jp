---
title: "レポートをインストールし、インターネット インフォメーション サービスのサイド バイ サイド |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [Reporting Services], IIS
ms.assetid: 9b651fa5-f582-4f18-a77d-0dde95d9d211
caps.latest.revision: 40
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: f7e12ebcec8e06828430e10c377205e2421f50f4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---

# <a name="install-reporting-and-internet-information-services-side-by-side"></a>レポートをインストールし、インターネット インフォメーション サービスのサイド バイ サイド

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

インストールして、同じコンピューターに SQL Server Reporting Services (SSRS) とインターネット インフォメーション サービス (IIS) を実行することができます。 対処する必要のある相互運用性の問題は、使用している IIS のバージョンによって異なります。  
  
|IIS のバージョン|問題|説明|  
|-----------------|------------|-----------------|  
|8.0, 8.5|あるアプリケーションに対して送信された要求が、別のアプリケーションによって受け付けられます。<br /><br /> URL 予約には、HTTP.SYS による優先順位規則が適用されます。 同じ仮想ディレクトリ名を持ち、共にポート 80 を監視するアプリケーションが複数存在するとき、これらのアプリケーションに宛てて送信された要求は、目的のアプリケーションの URL 予約が、もう一方のアプリケーションの URL 予約よりもあいまいに指定されていた場合、意図したターゲットに到達しない可能性があります。|特定の条件下では、URL 予約体系において他の URL エンドポイントに優先する登録済みのエンドポイントが、他のアプリケーション宛ての HTTP 要求を受信する場合があります。<br /><br /> この競合は、レポート サーバー Web サービスおよび [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] に対し、一意の仮想ディレクトリ名を使用することによって回避できます。<br /><br /> このシナリオについては、このトピックで詳しく説明します。|  
  
## <a name="precedence-rules-for-url-reservations"></a>URL 予約の優先順位規則  
 IIS と [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]間の相互運用性の問題を解決するには、まず URL 予約の優先順位規則を理解しておく必要があります。 優先順位規則とは、簡単に言えば、"より明示的に定義された値を持つ URL 予約が、その URL に合致した要求を先に受け取ることができる" ということです。  
  
-   仮想ディレクトリを指定する URL 予約は、仮想ディレクトリが省略された URL 予約よりも明示的である。  
  
-   単一アドレスが指定された URL 予約 (IP アドレス、完全修飾ドメイン名、ネットワーク コンピューター名、またはホスト名) は、ワイルドカードよりも明示的である。  
  
-   厳密なワイルドカードを指定する URL 予約は、弱いワイルドカードよりも明示的である。  
  
 次の表は、一連の URL 予約の例を、最も明示的なものから順に列挙したものです。  
  
|例|要求|  
|-------------|-------------|  
|`http://123.234.345.456:80/reports`|送信されるすべての要求受信`http://123.234.345.456/reports`または`http://\<computername>/reports`ドメイン名サービスがそのホスト名を IP アドレスを解決できる場合です。|  
|`http://+:80/reports`|URL に "reports" という仮想ディレクトリ名が含まれている限り、任意の IP アドレス (またはそのコンピューターの有効なホスト名) に送信されたすべての要求が受信されます。|  
|`http://123.234.345.456:80`|指定するすべての要求を受け取る`http://123.234.345.456`または`http://\<computername>`ドメイン名サービスがそのホスト名を IP アドレスを解決できる場合です。|  
|`http://+:80`|**[すべて割り当て]**にマップされたすべてのアプリケーション エンドポイントについて、まだ他のアプリケーションによって受信されていない要求が受信されます。|  
|`http://*:80`|**[すべて未割り当て]**にマップされたアプリケーション エンドポイントについて、まだ他のアプリケーションによって受信されていない要求が受信されます。|  
  
 ポートが競合している場合は、「System.IO.FileLoadException: ファイルが別のプロセスで使用されているため、プロセスはファイルにアクセスできません (HRESULT からの例外: 0x80070020)」というエラー メッセージが表示されます。  
  
## <a name="url-reservations-for-iis-80-85-with-sql-server-reporting-services"></a>IIS 8.0、8.5 と SQL Server Reporting Services の URL 予約  
 前のセクションで取り上げた優先順位規則を踏まえて考えると、Reporting Services と IIS に対して定義された URL 予約が、両者の相互運用性にどのように貢献しているかがわかります。 Reporting Services は、そのアプリケーションの仮想ディレクトリ名を明示的に指定する要求を受信します。一方、IIS は、それ以外のすべての要求を受信し、それらを IIS のプロセス モデル内で実行されるアプリケーションに送ることになります。  
  
|アプリケーション|URL 予約|説明|受信する要求|  
|-----------------|---------------------|-----------------|---------------------|  
|レポート サーバー|`http://+:80/ReportServer`|厳密なワイルドカード、ポート 80、レポート サーバーの仮想ディレクトリ|レポート サーバーの仮想ディレクトリを指定するすべての要求をポート 80 で受信します。 レポート サーバー Web サービスが http:// にすべての要求を受信\<コンピューター名 >/reportserver です。|  
|Web ポータル|`http://+:80/Reports`|厳密なワイルドカード、ポート 80、Reports という仮想ディレクトリ|reports という仮想ディレクトリを指定するすべての要求をポート 80 で受信します。 [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] Http:// に対するすべての要求を受け取る\<コンピューター名 >/reports です。|  
|IIS|`http://*:80/`|弱いワイルドカード、ポート 80|まだ他のアプリケーションによって受信されていない残りの要求をすべてポート 80 で受信します。|  

## <a name="side-by-side-deployments-of-sql-server-reporting-services-on-iis-80-85"></a>IIS 8.0 および 8.5 で SQL Server Reporting Services のサイド バイ サイド展開

 IIS と Reporting Services 間の相互運用性の問題は、IIS Web サイトに、Reporting Services で使用されているものと同じ仮想ディレクトリ名が存在する場合に発生します。 たとえば、次のような構成を考えてみます。  
  
-   ポート 80、仮想ディレクトリ名 "Reports" に割り当てられた IIS Web サイトが存在。  
  
-   ここで URL 予約もポート 80 を指定、既定の構成でインストールされているレポート サーバー インスタンスと[!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]も、アプリケーションは仮想ディレクトリ名"Reports"を使用します。  
  
 この構成では、http:// に送信される要求\<computername >: 80/reports が受け取る、[!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]です。 レポート サーバーのインスタンスをインストールした後、IIS の Reports 仮想ディレクトリ経由でアクセスされているアプリケーションは要求を受信できなくします。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の新旧のバージョンをサイド バイ サイド配置で実行した場合、前述したルーティングの問題が発生する可能性があります。 これは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のすべてのバージョンでは、レポート サーバーと [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] アプリケーションの仮想ディレクトリ名として "ReportServer" と "Reports" が使用されているため、IIS には "reports" と "reportserver" という仮想ディレクトリが高い確率で存在していると考えられるためです。  
  
 すべてのアプリケーションが確実に要求を受信できるようにするには、次のガイドラインに従います。  
  
-   Reporting Services のインストールでは、Reporting Services と同じポート上の IIS Web サイトで使用されていない仮想ディレクトリ名を使用するようにします。 競合が生じた場合は、Reporting Services を "ファイルのみ" のモード (インストール ウィザードで [サーバーを構成せずにインストールする] オプションを使用) でインストールします。こうすることで、セットアップの完了後に、仮想ディレクトリを自分で構成できるようになります。 構成が競合している場合は、「System.IO.FileLoadException: ファイルが別のプロセスで使用されているため、プロセスはファイルにアクセスできません (HRESULT からの例外: 0x80070020)」というエラー メッセージが表示されます。  
  
-   手動構成のインストールでは、構成する URL に既定の名前付け規則を採用します。 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] を名前付きインスタンスとしてインストールする場合は、仮想ディレクトリの作成時にインスタンス名を含めるようにします。  

## <a name="next-steps"></a>次の手順

[レポート サーバー Url を構成します。](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
[URL を構成します。](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
[Reporting Services ネイティブ モード レポート サーバーをインストールします。](../../reporting-services/install-windows/install-reporting-services-native-mode-report-server.md)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
