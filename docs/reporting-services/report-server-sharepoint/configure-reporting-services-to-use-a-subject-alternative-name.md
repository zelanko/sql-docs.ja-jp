---
title: "サブジェクト代替名を使用する Reporting Services の構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 73f48b2978055481f1ee93952fb3a35eb84ec416
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name"></a>サブジェクト代替名を使用する Reporting Services の構成します。

このトピックでは、Reporting Services (SSRS)、rsreportserver.config ファイルを変更し、Netsh.exe ツールを使用して、サブジェクトの別名 (SAN) を使用するを構成する方法について説明します。

この手順は、レポート サービスの URL および Web サービス URL に適用されます。

SAN を使用するには、SSL 証明書がサーバーに登録され、署名され、秘密キーを保持している必要があります。 自己署名証明書は使用できません  
  
 SSL 証明書を使用する Reporting Services の Url を構成することができます。 通常、証明書にはサブジェクト名のみが記載されているため、SSL (Secure Sockets Layer) セッションに対して許可される URL は 1 つだけです。 SAN は、多くの Url をリッスンし、他のアプリケーションとの SSL ポートを共有する SSL サービスを許可する証明書の追加フィールドです。 次のよう、SAN`www.s2.com`です。  
  
 Reporting Services の SSL 設定の詳細については、次を参照してください。[ネイティブ モードのレポート サーバーで SSL 接続の構成](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)です。  
  
## <a name="configure-ssrs-to-use-a-subject-alternative-name-for-web-service-url"></a>SSRS web サービスの URL のサブジェクトの別名を使用して構成します。
  
1.  Reporting Services 構成マネージャーを開始します。  
  
     詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)」を参照してください。  
  
2.  **[Web サービス URL]** ページで、SSL ポートおよび SSL 証明書を選択します。  
  
     ![Reporting Services 構成マネージャー](../../reporting-services/report-server-sharepoint/media/reportingservices-configurationmanager.png "Reporting Services 構成マネージャー")  
  
     構成マネージャーは、ポート用に SSL 証明書を登録します。  
  
3.  rsreportserver.config ファイルを開きます。  
  
     SSRS ネイティブ モードの場合、このファイルは既定では次のフォルダーにあります。  
  
    ```  
    \Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer  
    ```  
  
4.  レポート サーバー Web サービス アプリケーションの URL セクションをコピーします。  
  
     たとえば、次の元の URL セクションには。  
  
    ```  
        <URL>  
         <UrlString>https://localhost:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
     次の変更の URL セクションは次のとおりです。
  
    ```  
    <URL>  
         <UrlString>https://www.s1.com:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
        <URL>  
         <UrlString>https://www.s2.com:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
5.  rsreportserver.config ファイルを保存します。  
  
6.  管理者としてコマンド プロンプトを起動し、Netsh.exe ツールを実行します。  
  
    ```  
    C:\windows\system32\netsh  
    ```  
  
7.  次のように入力して、http コンテキストに切り替えます。  
  
    ```  
    Netsh>http  
    ```  
  
8.  次のように入力して、既存の urlacl を示してください。
  
    ```  
    Netsh http>show urlacl  
    ```  
  
     次のようなエントリが表示されます。  
  
    ```  
    Reserved URL            : https:// www.s1.com:443/ReportServer/  
        User: NT SERVICE\ReportServer  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;S-1-5-80-1234567890-123456789-123456789-123456789-1234567890)  
    ```  
  
     urlacl は、予約された URL の DACL (任意のアクセス制御リスト) です。  
  
9. 次のように入力して、既存のエントリと同じユーザーおよび SDDL を持つ、サブジェクト代替名の新しいエントリを作成します。  
  
    ```  
    netsh http>add urlacl  url=https://www.s2.com:443/ReportServer    
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-1234567980-12346579-123456789-123456789-1234567890)  
  
    ```  
  
10. Reporting Services 構成マネージャーの **[レポート サーバーの状態]** ページで、 **[停止]** をクリックしてから **[開始]** をクリックし、レポート サーバーを再起動します。  
  
## <a name="see-also"></a>参照

 [RsReportServer.config 構成ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Reporting Services 構成マネージャー](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Reporting Services 構成ファイルを変更します。](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)   
 [レポート サーバー Url を構成します。](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
