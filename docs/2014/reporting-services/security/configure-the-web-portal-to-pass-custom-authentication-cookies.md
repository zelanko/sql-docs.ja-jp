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
manager: craigg
ms.openlocfilehash: 6c77560c134abf9f255837da71a079506fa0f145
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137012"
---
# <a name="configure-report-manager-to-pass-custom-authentication-cookies"></a>カスタム認証クッキーを送信するようにレポート マネージャーを構成する
  カスタム認証拡張機能を使用している場合、カスタム認証クッキーを送信するようにレポート マネージャーを構成してください。 構成しない場合、レポート マネージャーはレポート サーバー固有の HTTP 要求を使用してクッキーを送信するだけです。 追加のクッキーを送信するには、RSReportServer.Config ファイルを変更する必要があります。  
  
## <a name="modifying-the-rsreportserverconfig-file"></a>RSReportServer.Config ファイルの変更  
 レポート マネージャーを追加して、レポート サーバーに追加のクッキーを送信できるように、<`PassThroughCookies`> 要素を RSReportServer.config ファイルでレポート マネージャーの構成設定。 追加のクッキーの送信は、レポート サーバーの認証クッキーだけでなく、サード パーティの認証システムのクッキーも必要なシングル サインオン認証ソリューションで便利です。  
  
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
 [構成して、レポート サーバーの管理&#40;SSRS ネイティブ モード&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  
