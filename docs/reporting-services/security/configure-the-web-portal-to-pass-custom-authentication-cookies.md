---
title: "カスタム認証クッキーを渡すため Web ポータルの構成 |Microsoft ドキュメント"
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
caps.latest.revision: 18
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 0f1131c191fa64c6dc6f2a074a9cd5db7a8b0e1b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="configure-the-web-portal-to-pass-custom-authentication-cookies"></a>カスタム認証クッキーを送信するように Web ポータルを構成する

カスタム認証拡張機能を使用している場合は、カスタム認証クッキーを送信する web ポータルを構成する必要があります。 それ以外の場合、web ポータルは、レポート サーバーに固有の HTTP 要求の cookie のみを転送します。 追加のクッキーを送信するには、RSReportServer.Config ファイルを変更する必要があります。

## <a name="modifying-the-rsreportserverconfig-file"></a>RSReportServer.Config ファイルの変更

有効にすることができます、[!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)]を追加することで、レポート サーバーに追加のクッキーを送信する、 \< **PassThroughCookies**> 要素、RSReportServer.config ファイルに web ポータルの構成設定をします。 追加のクッキーの送信は、レポート サーバーの認証クッキーだけでなく、サード パーティの認証システムのクッキーも必要なシングル サインオン認証ソリューションで便利です。

Web ポータルを使用する場合、HTTP 要求を介して送信される追加のクッキーを有効にするには、RSReportServer.config ファイルで、次の要素を設定します。
  
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
[構成およびレポート サーバー &#40; を管理します。SSRS ネイティブ モード &#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
他に質問しますか。 [Reporting Services のフォーラムを再試行してください。](http://go.microsoft.com/fwlink/?LinkId=620231)
