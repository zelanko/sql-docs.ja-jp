---
title: "カスタム認証クッキーを送信するようにレポート マネージャーを構成する | Microsoft Docs"
ms.custom: ""
ms.date: "08/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "認証 [Reporting Services]"
  - "拡張機能 [Reporting Services], カスタム セキュリティ"
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 18
---
# カスタム認証クッキーを送信するようにレポート マネージャーを構成する
  カスタム認証拡張機能を使用している場合、カスタム認証クッキーを送信するように [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] を構成してください。 構成しない場合、[!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] はレポート サーバー固有の HTTP 要求を使用してクッキーを送信するだけです。 追加のクッキーを送信するには、RSReportServer.Config ファイルを変更する必要があります。  
  
## RSReportServer.Config ファイルの変更  
 [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] の構成設定 (RSReportServer.config ファイル) に \<**PassThroughCookies**> 要素を追加すると、レポート マネージャーから [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] に追加のクッキーが送信されます。 追加のクッキーの送信は、レポート サーバーの認証クッキーだけでなく、サード パーティの認証システムのクッキーも必要なシングル サインオン認証ソリューションで便利です。  
  
 [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] の使用時に HTTP 要求を使用した追加のクッキーの送信を有効にするには、RSReportServer.config ファイルに次の要素を設定してください。  
  
```  
<UI>  
   <CustomAuthenticationUI>  
      ...  
      <PassThroughCookies>  
         <PassThroughCookie>cookiename1</PassThroughCookie>  
         <PassThroughCookie>cookiename2</PassThroughCookie>  
      </PassThroughCookies>  
   </CustomAuthenticationUI>  
      ...  
</UI>  
```  
  
## 参照  
 [レポート サーバーでの認証](../../reporting-services/security/authentication-with-the-report-server.md)   
 [RsReportServer.config 構成ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [セキュリティ拡張機能の概要](../../reporting-services/extensions/security-extension/security-extensions-overview.md)   
 [レポート サーバーを構成および管理する &#40;SSRSネイティブ モード&#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  