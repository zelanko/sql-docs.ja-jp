---
title: "ReportViewer コントロールを使用してサービス レポートの統合 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/06/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ReportViewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
caps.latest.revision: 26
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6247ce56394aff4f194bf9e452f36663a1112c80
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="integrating-reporting-services-using-reportviewer-controls"></a>ReportViewer コントロールを使用して Reporting Services の統合
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]Visual Studio 2015 は、レポート表示機能をアプリケーションに統合するための 2 つの ReportViewer コントロールを提供します。 Windows フォームベース アプリケーション用のバージョンと Web フォーム アプリケーション用のバージョンがあります。 それぞれのコントロールは同様の機能を持っていますが、別々の環境を対象にして設計されています。 両方のコントロールは、レポート サーバー (リモート処理モード) に展開されているか、コンピューターにコピーされているレポートを処理できる場所[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]がインストールされていない (ローカル処理モード)。  
  
 ReportViewer コントロールには、さまざまな画面の解像度を備えた各種デバイスに動的に適応するためのサポートは組み込まれていません。  
  
## <a name="remote-processing-mode"></a>リモート処理モード  
 リモート処理モードは、レポート サーバーに配置されたレポートの表示に推奨される方法です。 リモート処理モードには、次の利点があります。  
  
-   リモート処理では、レポート サーバーによってレポートの処理が行われるので、レポートを実行する最適なソリューションが提供されます。  
  
-   すべての処理はレポート サーバーで実行されるので、レポートの要求は、スケールアウト配置では複数のレポート サーバーで、スケール アップ シナリオでは複数のプロセッサを持つサーバーで処理できます。  
  
 また、リモート モードで実行されるレポートでは、すべての表示拡張機能やデータ拡張機能など、レポート サーバーの機能をすべて利用できます。  
  
> [!NOTE]  
>  ReportViewer コントロールをリモート処理モードで実行しているときに使用可能な拡張機能の一覧は、レポート サーバーにインストールされている [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のエディションによって異なります。  
  
## <a name="local-processing-mode"></a>ローカル処理モード  
 ローカル処理モードでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がインストールされていない場合にレポートを表示するための別の方法が用意されています。 リモート処理とは異なり、コントロールで利用できる機能は、レポート サーバーによって提供される機能のサブセットに限られます。 ローカル処理モードでは、データ処理はコントロールによって処理されず、ホスト アプリケーションに実装されます。 ただし、レポートの処理はコントロール自体によって処理されます。 ローカル処理モードでは、PDF、Excel、Word、および画像の表示拡張機能のみが使用可能です。  
  
## <a name="see-also"></a>参照  
 [アプリケーションへの Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [WebForms ReportViewer コントロールの使用](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)   
 [WinForms ReportViewer コントロールの使用](../../reporting-services/application-integration/using-the-winforms-reportviewer-control.md)  

  
  

