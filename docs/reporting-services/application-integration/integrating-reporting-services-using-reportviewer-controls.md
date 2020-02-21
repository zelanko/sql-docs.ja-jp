---
title: レポート ビューアー コントロールを使用した統合
description: Visual Studio には、レポート表示機能をアプリケーションに統合するための 2 つのレポート ビューアー コントロールが用意されています。
ms.date: 09/18/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.custom: seo-lt-2019
ms.topic: reference
helpviewer_keywords:
- Report Viewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1ce8530e2f7afb998c14838efb91c93d0b1cae3c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "74796867"
---
# <a name="integrate-reporting-services-using-report-viewer-controls"></a>レポート ビューアー コントロールを使用した Reporting Services の統合
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 2015 には、レポート表示機能をアプリケーションに統合するための 2 つのレポート ビューアー コントロールが用意されています。 Windows フォームベース アプリケーション用のバージョンと Web フォーム アプリケーション用のバージョンがあります。 それぞれのコントロールは同様の機能を持っていますが、別々の環境を対象にして設計されています。 どちらのコントロールも、レポート サーバーに配置されたレポートの処理 (リモート処理モード) または [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がインストールされていないコンピューターにコピーされたレポートの処理 (ローカル処理モード) を行うことができます。  
  
 レポート ビューアー コントロールには、さまざまな画面の解像度を備えた各種デバイスに動的に適応するためのサポートは組み込まれていません。  
  
## <a name="remote-processing-mode"></a>リモート処理モード  
 リモート処理モードは、レポート サーバーに配置されたレポートの表示に推奨される方法です。 リモート処理モードには、次の利点があります。  
  
-   リモート処理では、レポート サーバーによってレポートの処理が行われるので、レポートを実行する最適なソリューションが提供されます。  
  
-   すべての処理はレポート サーバーで実行されるので、レポートの要求は、スケールアウト配置では複数のレポート サーバーで、スケール アップ シナリオでは複数のプロセッサを持つサーバーで処理できます。  
  
 また、リモート モードで実行されるレポートでは、すべての表示拡張機能やデータ拡張機能など、レポート サーバーの機能をすべて利用できます。  
  
> [!NOTE]  
>  レポート ビューアー コントロールをリモート処理モードで実行しているときに使用可能な拡張機能の一覧は、レポート サーバーにインストールされている [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のエディションによって異なります。  
  
## <a name="local-processing-mode"></a>ローカル処理モード  
 ローカル処理モードでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がインストールされていない場合にレポートを表示するための別の方法が用意されています。 リモート処理とは異なり、コントロールで利用できる機能は、レポート サーバーによって提供される機能のサブセットに限られます。 ローカル処理モードでは、データ処理はコントロールによって処理されず、ホスト アプリケーションに実装されます。 ただし、レポートの処理はコントロール自体で行われます。 ローカル処理モードでは、PDF、Excel、Word、および画像の表示拡張機能のみが使用可能です。  
  
## <a name="see-also"></a>参照  
 [アプリケーションへの Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [WebForms レポート ビューアー コントロールの使用](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)   
 [WinForms レポート ビューアー コントロールの使用](../../reporting-services/application-integration/using-the-winforms-reportviewer-control.md)  

  
  
