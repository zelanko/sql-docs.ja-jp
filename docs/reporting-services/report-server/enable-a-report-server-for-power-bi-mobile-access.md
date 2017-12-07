---
title: "Power BI モバイル アクセス用のレポート サーバーを有効にする | Microsoft Docs"
ms.date: 12/17/2015
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: report-server
ms.reviewer: 
ms.suite: pro-bi
ms.custom: 
ms.technology: reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1a71522-394b-46a7-b9ec-f964bdd81d82
caps.latest.revision: "7"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: d243b32fdc2565a442b21ba7ca7f040279766be6
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="enable-a-report-server-for-power-bi-mobile-access"></a>Power BI モバイル アクセス用のレポート サーバーを有効にする
Power BI モバイル アプリを使用して、モバイル レポートを使用することができます。 Power BI モバイル アプリで Reporting Services への接続を可能にするには、いくつかの構成が必要です。  
  
-   [モバイル レポートでは Reporting Services をネイティブ モードにする必要がある](#nativemode)  
-   [Reporting Services で基本認証を有効にする](#basicauth) (CTP 3.2 の場合)  
-   [クライアント デバイスの有効な証明書信頼と共に HTTPS を有効にすることが推奨される](#https)  
-   [ファイアウォール設定を確認する](#firewall)  
  
<a name="nativemode"/>  
## <a name="reporting-services-native-mode-required"></a>Reporting Services をネイティブ モードにする必要がある  
モバイル レポートは、ネイティブ モードの機能です。 SharePoint 統合モードでは使用できません。 Power BI モバイル アプリは、ネイティブ モードのインスタンスでのみ機能します。  
  
<a name="basicauth"/>  
## <a name="enable-basic-authentication"></a>基本認証を有効にする  
iOS の Power BI モバイル アプリでモバイル レポートに接続して使用するには、基本認証が必要です。 Reporting Services の既定の構成では、基本認証が有効になっていません。 基本認証を構成する方法については、「 [レポート サーバーで基本認証を構成する](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md)」を参照してください。  
  
パブリッシャーのアプリでモバイル レポートを公開するには、Windows 認証も有効にする必要があります。  
  
<a name="https"/>  
## <a name="enable-https"></a>HTTPS を有効にする  
基本認証を有効にした場合は、Reporting Services で HTTPS を有効にすることをお勧めします。 HTTPS を有効にした場合は、使用する証明書が iOS Power BI モバイル アプリを実行しているクライアント デバイスで信頼されていることを確認します。 これは、証明書チェーンが有効であり、クライアント デバイスで使用できる必要があることを意味します。  
  
開発または評価の目的で自己署名証明書を使用する必要がある場合は、レポート サーバーから証明書をエクスポートし、モバイル デバイスにインストールします。 デバイスにインストールする方法については、デバイスのドキュメントを参照してください。  
  
SSL を有効にする方法の詳細については、「 [ネイティブ モードのレポート サーバーでの SSL 接続の構成](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)」を参照してください。  
  
<a name="firewall"/>  
## <a name="review-firewall-settings"></a>ファイアウォール設定を確認する  
すべてのデバイスが Reporting Services に正常に接続できることを、ファイアウォール設定で確認することをお勧めします。   
  
Windows ファイアウォールの構成方法の詳細については、「 [レポート サーバー アクセスに対するファイアウォールの構成](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
  
[レポート サーバーで基本認証を構成する](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md)  
[ネイティブ モードのレポート サーバーでの SSL 接続の構成](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)  
[レポート サーバー アクセスに対するファイアウォールの構成](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
  
  
  
  
  
  

