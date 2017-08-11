---
title: "Reporting Services WMI プロバイダー ライブラリ リファレンス (SSRS) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- Reporting Services WMI Provider Library
apilocation:
- reportingservices.mof
helpviewer_keywords:
- WMI provider [Reporting Services], library
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
caps.latest.revision: 42
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ce7657f048154ab0cf68c8e160bf1e5e6d15c210
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

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
 [Reporting Services WMI プロバイダーへのアクセスします。](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md)   
 [テクニカル リファレンス & #40 です。SSRS &#41;](../../reporting-services/technical-reference-ssrs.md)  
  
  
