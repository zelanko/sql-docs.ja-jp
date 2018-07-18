---
title: 電子メール、Reporting Services サービス アプリケーション (SharePoint 2010 および SharePoint 2013) の構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5432b0d2fa1c5fd7504b4706fb85b240efeb9c34
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236222"
---
# <a name="configure-e-mail-for-a-reporting-services-service-application-sharepoint-2010-and-sharepoint-2013"></a>Reporting Services サービス アプリケーションの電子メールの構成 (SharePoint 2010 および SharePoint 2013)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のデータ警告機能は、電子メール メッセージで警告を送信します。 電子メールを送信するには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを構成して、このサービス アプリケーションの電子メール配信拡張機能を変更しなければならない場合があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サブスクリプション機能の電子メール配信拡張機能を使用する場合、電子メールの設定も必要です。  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード&#124;SharePoint 2010 および SharePoint 2013。|  
  
### <a name="to-configure-e-mail-for-the-shared-service"></a>共有サービスの電子メールを構成するには  
  
1.  SharePoint の全体管理で **[アプリケーション管理]** をクリックします。  
  
2.  **[サービス アプリケーション]** グループで、 **[サービス アプリケーションの管理]** をクリックします。  
  
3.  **[名前]** ボックスの一覧で、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの名前をクリックします。  
  
4.  **[Reporting Services アプリケーションの管理]** ページの **[電子メールの設定]** をクリックします。  
  
5.  **[SMTP サーバーの使用]** を選択します。  
  
6.  **[送信 SMTP サーバー]** ボックスに、SMTP サーバーの名前を入力します。  
  
7.  **[差出人アドレス]** ボックスに、電子メール アドレスを入力します。  
  
     このアドレスはすべての警告電子メール メッセージの送信元になります。  
  
     
  **[差出人アドレス]** に指定するユーザーのアカウントは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションのアプリケーション プールを構成するときに指定した管理アカウントである必要があります。 権限がある場合、SharePoint サーバーの全体管理の [サービス アカウント] ページで既存の管理アカウントの一覧を表示できます。  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="ntlm-authentication"></a>NTLM 認証  
  
1.  NTLM 認証を必要とする電子メール環境で匿名アクセスを許可しない場合、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの電子メール配信拡張機能の構成を変更する必要があります。 **SMTPAuthenticate** の値を "2" に変更します。 この値はユーザー インターフェイスから変更することはできません。 次の PowerShell スクリプトの例では、"SSRS_TESTAPPLICATION" という名前のサービス アプリケーションについて、レポート サーバーの電子メール配信拡張機能の構成全体を更新します。 スクリプトに示されているノードの一部は、[差出人アドレス] などのユーザー インターフェイスからも設定できます。  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRS_TESTAPPLICATION *"}  
    $emailCfg = Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml   
    $emailXml = [xml]$emailCfg   
    $emailXml.SelectSingleNode("//SMTPServer").InnerText = “your email server name"  
    $emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
    $emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
    $emailXml.SelectSingleNode("//From").InnerText = “your FROM email address”  
    Set-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
    ```  
  
2.  サービス アプリケーションの名前を確認する必要がある場合は、 **Get-SPRSServiceApplication コマンドレット**を実行します。  
  
    ```  
    get-sprsserviceapplication  
    ```  
  
3.  次の例では、"SSRS_TESTAPPLICATION" という名前のサービス アプリケーションについて、電子メール拡張機能の現在の値を返します。  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRSTEST_APPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
    ```  
  
4.  次の例では、"SSRS_TESTAPPLICATION" という名前のサービス アプリケーションについて、電子メール拡張機能の現在の値を使用して "emailconfig.txt" という名前の新規ファイルを作成します。  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRS_TESTAPPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml | out-file c:\emailconfig.txt  
    ```  
  
  
