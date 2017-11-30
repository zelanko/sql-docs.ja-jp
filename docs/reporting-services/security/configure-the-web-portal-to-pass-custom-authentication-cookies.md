---
title: "カスタム認証クッキーを送信するように Web ポータルを構成する | Microsoft Docs"
ms.custom: 
ms.date: 04/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
caps.latest.revision: "18"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.openlocfilehash: 0f1131c191fa64c6dc6f2a074a9cd5db7a8b0e1b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="configure-the-web-portal-to-pass-custom-authentication-cookies"></a>カスタム認証クッキーを送信するように Web ポータルを構成する

カスタム認証拡張機能を使用している場合、カスタム認証クッキーを送信するように Web ポータルを構成してください。 構成しない場合、Web ポータルはレポート サーバー固有の HTTP 要求を使用してクッキーを送信するだけです。 追加のクッキーを送信するには、RSReportServer.Config ファイルを変更する必要があります。

## <a name="modifying-the-rsreportserverconfig-file"></a>RSReportServer.Config ファイルの変更

[!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] を有効にしてレポート サーバーに追加のクッキーを送信できます。RSReportServer.config ファイルの Web ポータル構成設定に \<**PassThroughCookies**> 要素を追加します。 追加のクッキーの送信は、レポート サーバーの認証クッキーだけでなく、サード パーティの認証システムのクッキーも必要なシングル サインオン認証ソリューションで便利です。

Web ポータルの使用時に HTTP 要求を使用した追加のクッキーの送信を有効にするには、RSReportServer.config ファイルに次の要素を設定してください。
  
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
  
## <a name="see-also"></a>参照

[レポート サーバーでの認証](../../reporting-services/security/authentication-with-the-report-server.md)   
[RsReportServer.config 構成ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
[セキュリティ拡張機能の概要](../../reporting-services/extensions/security-extension/security-extensions-overview.md)   
[レポート サーバーを構成および管理する &#40;SSRSネイティブ モード&#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
その他の質問 [Reporting Services のフォーラムにアクセスします](http://go.microsoft.com/fwlink/?LinkId=620231)