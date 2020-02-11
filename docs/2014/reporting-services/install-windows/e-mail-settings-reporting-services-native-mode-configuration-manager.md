---
title: 電子メールの設定-Configuration Manager (SSRS ネイティブモード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.emailsettings.f1
helpviewer_keywords:
- SQL11.rsconfigtool.emailsettings.F1
ms.assetid: cdad1529-bfa6-41fb-9863-d9ff1b802577
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 808ad67429ee49d6b04533863112b4cbb3af2514
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108876"
---
# <a name="e-mail-settings---configuration-manager-ssrs-native-mode"></a>電子メールの設定 - 構成マネージャー (SSRS ネイティブ モード)
  このページを使用すると、レポート サーバーからのレポート サーバー電子メール配信を有効にする簡易メール転送プロトコル (SMTP) の設定を指定できます。 レポート サーバーの電子メール配信拡張機能により、電子メール サブスクリプションを通じてレポートやレポート処理通知を配信できます。 レポート サーバーの電子メール配信拡張機能を使用するには、SMTP サーバーと、差出人フィールドに使用する電子メール アドレスが必要です。  
  
 その他の構成設定を使用することで、メール サーバーのホストを限定するための設定や表示拡張機能の使用などを含め、電子メール サブスクリプションを詳細にカスタマイズできます。 これらの設定は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーでは指定できません。 追加の設定を構成するには、RSReportServer.config ファイルを手動で編集する必要があります。 詳細については、オンライン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ブックの「[電子メール配信用のレポートサーバーの構成 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) 」および「 [Reporting Services 構成ファイル](../report-server/reporting-services-configuration-files.md)」を参照してください。  
  
 このページを開くには、Reporting Services Configuration Manager を開始し、ナビゲーションウィンドウで [**電子メールの設定**] をクリックします。 詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。  
  
## <a name="options"></a>オプション  
 **送信者アドレス**  
 生成される電子メールの送信者フィールドに使用する電子メール アドレスを指定します。 SMTP サーバーからメールを送信する権限のあるユーザー アカウントを指定する必要があります。  
  
 **[現在の SMTP 配信方法]**  
 レポート サーバー電子メールが SMTP サーバーによってルーティングされるように指定します。 これは、Reporting Services 構成マネージャーで指定できる唯一の配信方法です。  
  
 その他の配信方法には、ローカル SMTP サービス ピックアップ ディレクトリを使用する方法があります。 ネットワーク SMTP サービスが使用できない場合、この配信方法を使用できます。 ローカル SMTP サービス ピックアップ ディレクトリを指定するには、RSReportServer.config ファイルを編集する必要があります。 この構成ファイルを編集してローカル SMTP サービス ピックアップ ディレクトリを使用すると、Reporting Services 構成マネージャーの **[現在の配信方法]** オプションが *[ローカルのピックアップ ディレクトリに送ります]* に設定されて、この配信方法が構成ファイルで指定されたことを示します。  
  
 構成ファイルでは、`SendUsing` 構成設定を使用して配信方法を設定します。 設定の`SendUsing`指定の詳細については、「[電子メール配信用にレポートサーバーを構成する &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)」を参照してください。  
  
 **SMTP サーバー**  
 使用する SMTP サーバーまたはゲートウェイを指定します。 ローカル サーバーまたはネットワーク上の SMTP サーバーを使用できます。  
  
## <a name="see-also"></a>参照  
 [SSRS Configuration Manager &#40;電子メール配信用にレポートサーバーを構成&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)   
 [Reporting Services Configuration Manager F1 ヘルプトピック &#40;SSRS ネイティブモード&#41;](../../sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  
