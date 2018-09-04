---
title: Reporting Services WMI プロバイダー ライブラリ リファレンス (SSRS) | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.suite: pro-bi
ms.topic: conceptual
apiname:
- Reporting Services WMI Provider Library
apilocation:
- reportingservices.mof
helpviewer_keywords:
- WMI provider [Reporting Services], library
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ad028730c329857cc7072e6bda11966edfa9ba97
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2018
ms.locfileid: "43272722"
---
# <a name="reporting-services-wmi-provider-library-reference-ssrs"></a>Reporting Services WMI プロバイダー ライブラリ リファレンス (SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) プロバイダーは WMI 操作をサポートし、レポート サーバーとレポート マネージャーの設定を修正するスクリプトとコードの記述を可能にします。  
  
 たとえば、レポート サーバーがレポート サーバー データベースと接続するときに統合セキュリティを使用するかどうかを変更する場合は、MSReportServer_ConfigurationSetting クラスのインスタンスを作成して、レポート サーバー インスタンスの DatabaseIntegratedSecurity プロパティを使用します。 次の表のクラスは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントを表しています。 これらのクラスは、 [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] 名前空間または [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] 名前空間で定義されています。 各クラスは読み取り操作と書き込み操作をサポートします。 作成操作はサポートされません。  
  
## <a name="classes"></a>クラス  
 [MSReportServer_Instance クラス](../../reporting-services/wmi-provider-library-reference/msreportserver-instance-class.md)  
 インストールされているレポート サーバーに接続するための基本情報をクライアントに提供します。  
  
 [MSReportServer_ConfigurationSetting クラス](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
 レポート サーバー インスタンスのインストール パラメーターとランタイム パラメーターを表します。 これらのパラメーターはレポート サーバーの構成ファイルに格納されています。  
  
 WMI 操作の詳細については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK に付属の WMI SDK ドキュメントを参照してください。  
  
## <a name="see-also"></a>参照  
 [Reporting Services WMI プロバイダーへのアクセス](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md)   
 [テクニカル リファレンス (SSRS)](../../reporting-services/technical-reference-ssrs.md)  
  
  
