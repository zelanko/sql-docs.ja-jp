---
title: Reporting Services WMI プロバイダー ライブラリ リファレンス (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider Library
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services], library
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: fb26c603fa3618488317981e0489499db4ca7837
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37309088"
---
# <a name="reporting-services-wmi-provider-library-reference-ssrs"></a>Reporting Services WMI プロバイダー ライブラリ リファレンス (SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) プロバイダーは WMI 操作をサポートし、レポート サーバーとレポート マネージャーの設定を修正するスクリプトとコードの記述を可能にします。  
  
 たとえば、レポート サーバーがレポート サーバー データベースと接続するときに統合セキュリティを使用するかどうかを変更する場合は、MSReportServer_ConfigurationSetting クラスのインスタンスを作成して、レポート サーバー インスタンスの DatabaseIntegratedSecurity プロパティを使用します。 次の表のクラスは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントを表しています。 これらのクラスは、 [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] 名前空間または [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] 名前空間で定義されています。 各クラスは読み取り操作と書き込み操作をサポートします。 作成操作はサポートされません。  
  
## <a name="classes"></a>クラス  
 [MSReportServer_Instance クラス](msreportserver-instance-class.md)  
 インストールされているレポート サーバーに接続するための基本情報をクライアントに提供します。  
  
 [MSReportServer_ConfigurationSetting クラス](msreportserver-configurationsetting-class.md)  
 レポート サーバー インスタンスのインストール パラメーターとランタイム パラメーターを表します。 これらのパラメーターはレポート サーバーの構成ファイルに格納されています。  
  
 WMI 操作の詳細については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK に付属の WMI SDK ドキュメントを参照してください。  
  
## <a name="see-also"></a>参照  
 [Reporting Services WMI プロバイダーへのアクセス](../tools/access-the-reporting-services-wmi-provider.md)   
 [テクニカル リファレンス (SSRS)](../technical-reference-ssrs.md)  
  
  
