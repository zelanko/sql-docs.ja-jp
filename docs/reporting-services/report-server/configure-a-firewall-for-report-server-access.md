---
title: "レポート サーバー アクセスに対してファイアウォールを構成する |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 09/14/2015
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- firewall systems [Reporting Services]
- configuring servers [Reporting Services]
ms.assetid: 04dae07a-a3a4-424c-9bcb-a8000e20dc93
caps.latest.revision: 13
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4ea69363565456fda2c1adc7d48d60c6a0bef8f7
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="configure-a-firewall-for-report-server-access"></a>レポート サーバー アクセスに対するファイアウォールの構成
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバー アプリケーションとパブリッシュされたレポートには、IP アドレス、ポート、および仮想ディレクトリを指定した URL を通じてアクセスします。 Windows ファイアウォールが有効になっている場合、レポート サーバーで使用するように構成されているポートは閉じられる可能性が高くなります。 リモート クライアント コンピューターから **レポート マネージャー** を開こうとしたときに空白のページが表示される場合、またはレポート要求後に空白の Web ページが表示される場合は、ポートが閉じている可能性があります。  
  
 ポートを開くには、レポート サーバー コンピューターで Windows ファイアウォール ユーティリティを使用する必要があります。 ポートは Reporting Services によって自動的に開かれないので、この手順を手動で実行する必要があります。  
  
 既定では、レポート サーバーはポート 80 で HTTP 要求をリッスンします。 このため、以下に示す手順ではそのポートを指定しています。 別のポートを使用するようにレポート サーバーの URL を構成している場合は、以下に示す手順を実行するときにそのポート番号を指定する必要があります。  
  
 外部コンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リレーショナル データベースにアクセスする場合、またはレポート サーバー データベースが外部の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに置かれている場合は、外部コンピューターのポート 1433 および 1434 を開く必要があります。 Windows ファイアウォールの詳細については、 [オンライン ブックの「](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) データベース エンジン アクセスを有効にするための Windows ファイアウォールを構成する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。 Windows ファイアウォールの既定の設定に関する詳細と、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]に影響する TCP ポートの説明については、 [オンライン ブックの「](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) SQL Server のアクセスを許可するための Windows ファイアウォールの構成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」をご覧ください。  
  
## <a name="prerequisites"></a>前提条件  
 次の手順では、既にサービス アカウントを構成し、レポート サーバー データベースを作成し、レポート サーバー Web サービスとレポート マネージャーの URL を構成していることを前提としています。 詳細については、「 [Reporting Services ネイティブ モードのレポート サーバーの管理](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)」を参照してください。  
  
 また、ローカル レポート サーバー インスタンスへのローカル Web ブラウザー接続を通じてレポート サーバーにアクセスできることを確認しておく必要があります。 この手順によって、作業環境が整っているかどうかを検証できます。 ポートを開く前に、環境が正しく構成されているかどうかを確認する必要があります。 Windows Server でこの手順を完了するには、レポート サーバー サイトを [信頼済みサイト] に追加しておくことも必要です。 詳細については、「[ローカル管理用のネイティブ モードのレポート サーバー &#40;SSRS&#41; の構成](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)」をご覧ください。  
  
## <a name="opening-ports-in-windows-firewall"></a>Windows ファイアウォールでポートを開く  
  
#### <a name="to-open-port-80"></a>ポート 80 を開くには  
  
1.  **[スタート]** メニューの **[コントロール パネル]**をクリックし、 **[システムとセキュリティ]**、 **[Windows ファイアウォール]**の順にクリックします。 コントロール パネルの表示方法が [カテゴリ] 以外の場合は、単に **[Windows ファイアウォール]**を選択するだけでかまいません。  
  
2.  **[詳細な設定]**をクリックします。  
  
3.  **[受信の規則]**をクリックします。  
  
4.  **[操作]** ウィンドウで **[新しい規則]** をクリックします**。**  
  
5.  **[ポート]** の **[規則の種類]**をクリックします。  
  
6.  **[次へ]**をクリックします。  
  
7.  **[プロトコルおよびポート]** ページで、 **[TCP]**をクリックします。  
  
8.  **[特定のローカル ポート]** を選択し、「 **80**」という値を入力します。  
  
9. **[次へ]**をクリックします。  
  
10. **[操作]** ページで、 **[接続を許可する]**をクリックします。  
  
11. **[次へ]**をクリックします。  
  
12. **[プロファイル]** ページで、実際の環境に合った適切なオプションをクリックします。  
  
13. **[次へ]**をクリックします。  
  
14. **[名前]** ページで、「**ReportServer (TCP on port 80)**」という名前を入力します。  
  
15. **[完了]**をクリックします。  
  
16. コンピューターを再起動します。  
  
## <a name="next-steps"></a>次の手順  
 ポートを開いた後、リモート ユーザーがそのポートでレポート サーバーにアクセスできるかどうかを確認する前に、ホームに対するロールとサイト レベルのロールの割り当てを行って、レポート サーバーへのアクセスをユーザーに許可する必要があります。 ユーザーに十分な権限がない場合は、ポートを正しく開くことができてもレポート サーバーへの接続に失敗します。 詳細については、次を参照してください[レポート サーバー &#40; をユーザー アクセスの許可。レポート マネージャー &#41;](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブックの「します。  
  
 別のコンピューターでレポート マネージャーを起動することによって、ポートが正しく開かれているかどうかを確認することもできます。 詳細については、次を参照してください。[レポート マネージャー & #40 です。SSRS ネイティブ モード &#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブックの「します。  
  
## <a name="see-also"></a>参照  
 [レポート サーバー サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [レポート サーバーの Url &#40; を構成します。SSRS 構成マネージャー &#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [レポート サーバー データベース &#40; を作成します。SSRS 構成マネージャー &#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-report-server-database.md)   
 [レポート サーバー サービス アカウント &#40; を構成します。SSRS 構成マネージャー &#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Reporting Services ネイティブ モード レポート サーバーを管理します。](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)  
  
  

