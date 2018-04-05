---
title: '[Reporting Services ログイン] ダイアログ ボックス (SSRS) | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: ''
ms.component: tools
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- sql13.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
caps.latest.revision: 31
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: db595388a1970fa37cf19dca00a58b4c4f2704ed
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="reporting-services-login-dialog-box-ssrs"></a>[Reporting Services ログイン] ダイアログ ボックス (SSRS)
  **[Reporting Services ログイン]** ダイアログ ボックスを使用すると、レポートをレポート サーバーにパブリッシュする際に使用する資格情報を指定できます。  
  
-   **注** : プロジェクトの配置プロパティ **TargetServerURL** を設定してから初めてレポートをレポート サーバーにパブリッシュする場合は、サーバー名に **reports** ではなく **server**が含まれることを確認します。 たとえば、 `http://localhost/reportserver`ではなく `http://localhost/reports`のようになります。 ローカル サーバーの `reports` ディレクトリではなく `reportserver` ディレクトリを指定すると、このダイアログ ボックスが間接的に開かれます。 **TargetServerURL** の設定の詳細については、「[配置プロパティを設定する &#40;Reporting Services&#41;](../../reporting-services/tools/set-deployment-properties-reporting-services.md)」を参照してください。  
  
## <a name="options"></a>および  
 **Server**  
 レポート サーバーの名前を表示します。 たとえば、 `http://localhost/reportserver`のようにします。 既定のポート 80 と異なるポートを使用するレポート サーバーの場合は、ポート番号を含めます。 たとえば、 `http://localhost:81/reportserver`のようにします。  
  
 **User name**  
 Web サービスへのログインに使用するユーザー名を入力します。  
  
 **Password**  
 Web サービスへのログインに使用するパスワードを入力します。  
  
## <a name="see-also"></a>参照  
 [データ接続、データ ソース、および接続文字列 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [レポート データ ソースに関する資格情報と接続情報を指定する](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [レポート デザイナーの F1 ヘルプ](../../reporting-services/tools/report-designer-f1-help.md)  
  
  
