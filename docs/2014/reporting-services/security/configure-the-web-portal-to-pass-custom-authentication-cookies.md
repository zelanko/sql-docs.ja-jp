---
title: カスタム認証クッキーをレポート マネージャーの構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 6787ec73d91b32e0bdb90f8a5f25499f0ac35620
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56034493"
---
# <a name="configure-report-manager-to-pass-custom-authentication-cookies"></a>カスタム認証クッキーを送信するようにレポート マネージャーを構成する
  カスタム認証拡張機能を使用している場合、カスタム認証クッキーを送信するようにレポート マネージャーを構成してください。 構成しない場合、レポート マネージャーはレポート サーバー固有の HTTP 要求を使用してクッキーを送信するだけです。 追加のクッキーを送信するには、RSReportServer.Config ファイルを変更する必要があります。  
  
## <a name="modifying-the-rsreportserverconfig-file"></a>RSReportServer.Config ファイルの変更  
 レポート マネージャーの構成設定 (RSReportServer.config ファイル) に <`PassThroughCookies`> 要素を追加すると、レポート マネージャーからレポート サーバーに追加のクッキーが送信されます。 追加のクッキーの送信は、レポート サーバーの認証クッキーだけでなく、サード パーティの認証システムのクッキーも必要なシングル サインオン認証ソリューションで便利です。  
  
 レポート マネージャーの使用時に HTTP 要求を使用した追加のクッキーの送信を有効にするには、RSReportServer.config ファイルに次の要素を設定してください。  
  
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
 [レポート サーバーでの認証](authentication-with-the-report-server.md)   
 [RSReportServer 構成ファイル](../report-server/rsreportserver-config-configuration-file.md)   
 [セキュリティ拡張機能の概要](../extensions/security-extension/security-extensions-overview.md)   
 [レポート サーバーを構成および管理する &#40;SSRSネイティブ モード&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  
