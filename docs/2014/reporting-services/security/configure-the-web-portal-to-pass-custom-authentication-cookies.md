---
title: カスタム認証 Cookie を渡すようにレポートマネージャーを構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 34f637ee2d0a8235f21167df78178c4de9292c8c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66102046"
---
# <a name="configure-report-manager-to-pass-custom-authentication-cookies"></a>カスタム認証クッキーを送信するようにレポート マネージャーを構成する
  カスタム認証拡張機能を使用している場合、カスタム認証クッキーを送信するようにレポート マネージャーを構成してください。 構成しない場合、レポート マネージャーはレポート サーバー固有の HTTP 要求を使用してクッキーを送信するだけです。 追加のクッキーを送信するには、RSReportServer.Config ファイルを変更する必要があります。  
  
## <a name="modifying-the-rsreportserverconfig-file"></a>RSReportServer.Config ファイルの変更  
 RSReportServer. .config ファイルのレポートマネージャー構成設定に <`PassThroughCookies`> 要素を追加することにより、レポートサーバーに追加のクッキーを送信するレポートマネージャーを有効にすることができます。 追加のクッキーの送信は、レポート サーバーの認証クッキーだけでなく、サード パーティの認証システムのクッキーも必要なシングル サインオン認証ソリューションで便利です。  
  
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
  
  
