---
title: サブジェクト代替名 (SAN) を使用するように Reporting Services を構成する | Microsoft Docs
description: rsreportserver.config ファイルを変更し、Netsh.exe ツールを使用することで、SAN を使用するように SQL Server Reporting Services と Power BI Report Server を構成する方法について説明します。
ms.date: 09/27/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cf1db4f6e07609ce6da38569732f7dba333f86ff
ms.sourcegitcommit: b93beb4f03aee2c1971909cb1d15f79cd479a35c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/29/2020
ms.locfileid: "91497206"
---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name-san"></a>サブジェクト代替名 (SAN) を使用するように Reporting Services を構成する

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

このトピックでは、rsreportserver.config ファイルを変更し、Netsh.exe ツールを使用することによって、サブジェクト代替名 (SAN) を使用するように Reporting Services (SSRS) と Power BI Report Server を構成する方法について説明します。

この手順は、Web サービスの URL だけでなく、レポート サーバーの構成マネージャー ツールの Web ポータルの URL にも適用されます。

SAN を使用するには、TLS/SSL 証明書がサーバーに登録され、署名され、秘密キーを保持している必要があります。 自己署名証明書は使用できません。

Reporting Services と Power BI Report Server の URL は、TLS/SSL 証明書を使用するように構成することができます。 通常、証明書にはサブジェクト名のみが記載されているため、トランスポート層セキュリティ (TLS) (旧称 Secure Sockets Layer (SSL)) セッションに対して許可される URL は 1 つだけです。 SAN は証明書の追加フィールドであり、それにより、TLS サービスでは、さまざまな URL を待ち受け、TLS ポートを他のアプリケーションと共有することができるます。 たとえば、SAN は `www.myreports.com` のようになります。

Reporting Services の TLS 設定の詳細については、「[ネイティブ モードのレポート サーバーでの TLS 接続の構成](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)」を参照してください。  
  
## <a name="configure-to-use-a-subject-alternative-name-for-web-service-url"></a>Web サービス URL にサブジェクト代替名を使用するように構成する
  
1.  レポート サーバーの構成マネージャーを起動します。  
  
     詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)」を参照してください。  
  
2.  **[Web サービス URL]** ページで、TLS/SSL ポートおよび TLS/SSL 証明書を選択します。  
  
     ![Reporting Services 構成マネージャー](../../reporting-services/report-server-sharepoint/media/reportingservices-configurationmanager.png "Reporting Services 構成マネージャー")  
  
     構成マネージャーによって、ポート用の TLS/SSL 証明書が登録されます。  
  
3.  rsreportserver.config ファイルを開きます。  
  
     SSRS 2016 ネイティブ モードの場合、ファイルは、既定では、次のフォルダーにあります。  
  
    ```  
    \Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\ReportServer  
    ```  
  
     SSRS 2017 以降の場合、ファイルは、既定では、次のフォルダーにあります。  
  
    ```  
    \Program Files\Microsoft SQL Server Reporting Services\SSRS\ReportServer  
    ```  
    
     Power BI Report Server の場合、既定では次のフォルダーにファイルがあります。  
  
    ```  
    \Program Files\Microsoft Power BI Report Server\PBIRS\ReportServer  
    ```  
  
4.  **ReportServerWebService** アプリケーションの URL セクションをコピーします。
  
     元の URL セクションの例:  
  
    ```  
        <URL>  
         <UrlString>https://+:443</UrlString>  
         <AccountSid>S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051</AccountSid>  
         <AccountName>NT Service\ReportServer</AccountName>  
        </URL>  
  
    ```  
  
     変更後の URL セクション:
  
    ```  
    <URL>  
         <UrlString>https://+:443</UrlString>  
         <AccountSid>S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051</AccountSid>  
         <AccountName>NT Service\ReportServer</AccountName>  
        </URL>  
        <URL>  
         <UrlString>https://www.myreports.com:443</UrlString>  
         <AccountSid>S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051/AccountSid>  
         <AccountName>NT Service\ReportServer</AccountName>  
        </URL>  
  
    ```  
  
  > [!TIP]  
>  * SSRS 2017 以降の場合、`AccountSid` 値は `S-1-5-80-4050220999-2730734961-1537482082-519850261-379003301`、`AccountName` 値は `NT SERVICE\SQLServerReportingServices` です。
>  * Power BI Report Server の場合、`AccountSid` の値は `S-1-5-80-1730998386-2757299892-37364343-1607169425-3512908663`、`AccountName` の値は `NT SERVICE\PowerBIReportServer` です。
  
5.  rsreportserver.config ファイルを保存します。  
  
6.  **[管理者として実行する]** を使用してコマンド プロンプトを起動し、Netsh.exe ツールを実行します。  
  
    ```  
    C:\windows\system32\netsh  
    ```  
  
7.  次のように入力して、http コンテキストに切り替えます。  
  
    ```  
    Netsh>http  
    ```  
  
8.  次のように入力して、既存の urlacl を表示します。
  
    ```  
    Netsh http>show urlacl  
    ```  
  
     次のようなエントリが表示されます。  
  
    ```  
    Reserved URL            : https://+:443/ReportServer/  
        User: NT SERVICE\ReportServer  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051)  
    ```  
  
     urlacl は、予約された URL の DACL (任意のアクセス制御リスト) です。  
  
9. 次のように入力して、既存のエントリと同じユーザーおよび SDDL を持つ、サブジェクト代替名の新しいエントリを作成します。  
  
    ```  
    netsh http>add urlacl  url=https://www.myreports.com:443/ReportServer    
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051)  
  
    ```  
  
10. **[Web ポータル URL]** の場合、次のように入力して、サブジェクト代替名の新しいエントリを作成します。

    ```  
    netsh http>add urlacl  url=https://www.myreports.com:443/Reports  
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051)  
  
    ```  
> [!TIP]  
>  * SSRS 2017 以降の場合、`user` 値は `NT SERVICE\SQLServerReportingServices`、`sddl` 値は `D:(A;;GX;;;S-1-5-80-4050220999-2730734961-1537482082-519850261-379003301)` です。
>  * Power BI Report Server の場合、`user` の値は `NT SERVICE\PowerBIReportServer`、`sddl` の値は `S-1-5-80-1730998386-2757299892-37364343-1607169425-3512908663` です。

> [!NOTE]  
> Power BI Report Server の場合、次のように入力して、サブジェクト代替名の 2 つの追加エントリを作成する必要があります。
>  * `add urlacl url=https://www.myreports.com:443/PowerBI user="NT SERVICE\PowerBIReportServer" sddl=D:(A;;GX;;;S-1-5-80-1730998386-2757299892-37364343-1607169425-3512908663)`
>  * `add urlacl url=https://www.myreports.com:443/wopi user="NT SERVICE\PowerBIReportServer" sddl=D:(A;;GX;;;S-1-5-80-1730998386-2757299892-37364343-1607169425-3512908663)`

11. レポート サーバーの構成マネージャーの **[レポート サーバーの状態]** ページで、 **[停止]** をクリックしてから **[開始]** をクリックし、レポート サーバーを再起動します。  
  
## <a name="see-also"></a>関連項目

 [RsReportServer.config 構成ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Reporting Services 構成マネージャー](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Reporting Services の構成ファイルの変更](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)   
 [レポート サーバーの URL の構成](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)

その他の質問 [Reporting Services のフォーラムに質問してみてください](https://go.microsoft.com/fwlink/?LinkId=620231)
